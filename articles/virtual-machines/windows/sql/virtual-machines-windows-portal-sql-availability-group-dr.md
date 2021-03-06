---
title: SQL Server Availability Groups - Azure Virtual Machines - Disaster Recovery | Microsoft Docs 
description: "This article explains how to configure a SQL Server availability group on Azure virtual machines with a replica in a different region."
services: virtual-machines
documentationCenter: na
authors: MikeRayMSFT
manager: jhubbard
editor: monicar
tags: azure-service-management

ms.assetid: 388c464e-a16e-4c9d-a0d5-bb7cf5974689
ms.service: virtual-machines-sql
ms.devlang: na
ms.custom: na
ms.topic: article
ms.tgt_pltfrm: vm-windows-sql-server
ms.workload: iaas-sql-server
ms.date: "01/09/2017"
ms.author: mikeray

---

# Configure a SQL Server Always On Availability Group on Azure Virtual Machines in Different Regions

This article explains how to configure a SQL Server Always On Availability Group replica on Azure Virtual Machines in a remote Azure location. Use this configuration to support disaster recovery.

This article applies to Azure Virtual Machines in Resource Manager mode. 

The following image shows a common deployment of an availability group on Azure virtual machines:

   ![Availability Group](./media/virtual-machines-windows-portal-sql-availability-group-dr/00-availability-group-basic.png)

In this deployment, all virtual machines are in one Azure region. The availability group replicas can have synchronous commit with automatic failover on SQL-1 and SQL-2. You can build this architecture [Availability Group template or tutorial](virtual-machines-windows-portal-sql-availability-group-overview.md).

This architecture is vulnerable downtime if the Azure region becomes inaccessible. To overcome this vulnerability, add a replica in a different Azure region. The following diagram shows how the new architecture would look:

   ![Availability Group DR](./media/virtual-machines-windows-portal-sql-availability-group-dr/00-availability-group-basic-dr.png)

The preceding diagram shows a new virtual machine called SQL-3. SQL-3 is in a different Azure region. SQL-3 is added to the Windows Server Failover Cluster. SQL-3 can host an availability group replica. Finally, notice that the Azure region for SQL-3 has a new Azure load balancer.

>[!NOTE]
> An Azure availability set is required when more than one virtual machine is in the same region. If only one virtual machine is in the region, then the availability set is not required. You can only place a virtual machine in an availability set at creation time. If the virtual machine is already in an availability set, you can add a virtual machine for an additional replica later. 

In this architecture, the replica in the remote region is normally configured with asynchronous commit availability mode and manual failover mode.

When availability group replicas are on Azure virtual machines in different Azure regions, each region requires:

* A virtual network gateway 
* A virtual network gateway connection

The following diagram shows how the networks communicate between data centers.

   ![Availability Group](./media/virtual-machines-windows-portal-sql-availability-group-dr/01-vpngateway-example.png)

## Create remote replica

To create a replica in a remote data center, do the following steps:

1. [Create a virtual network in the new region](../../../virtual-network/virtual-networks-create-vnet-arm-pportal.md).

1. [Configure a VNet-to-VNet connection using the Azure portal](../../../vpn-gateway/vpn-gateway-howto-vnet-vnet-resource-manager-portal.md).

   >[!NOTE]
   >In some cases, you may have to use PowerShell to create the VNet-to-VNet connection. For example, if you use different Azure accounts you cannot configure the connection in the portal. In this case see, [Configure a VNet-to-VNet connection using the Azure portal](../../../vpn-gateway/vpn-gateway-vnet-vnet-rm-ps.md).

1. [Create a domain controller in the new region](../../../active-directory/active-directory-new-forest-virtual-machine.md).

   This domain controller provides authentication if the domain controller in the primary site is not available. 

1. [Create a SQL Server virtual machine in the new region](virtual-machines-windows-portal-sql-server-provision.md).

1. [Create an Azure load balancer in the network on the new region](virtual-machines-windows-portal-sql-alwayson-availability-groups-manual.md#configure-internal-load-balancer).

   This load balancer must:
   
   - Be in the same network and subnet as the new virtual machine.
   - Have a static IP address for the Availability Group listener.
   - Include backend pool consisting of only the virtual machines in the same region as the load balancer.
   - Use a TCP port probe specific to the IP address.
   - Have a load balancing rule specific to the SQL Server in the same region.  

1. [Add Failover Clustering feature to the new SQL Server](virtual-machines-windows-portal-sql-availability-group-prereq.md#add-failover-cluster-features-to-both-sql-servers).

1. [Join the new SQL Server to the domain](virtual-machines-windows-portal-sql-availability-group-prereq.md#joinDomain).

1. [Set the new SQL Server service account to use a domain account](virtual-machines-windows-portal-sql-availability-group-prereq.md#setServiceAccount).

1. [Add the new SQL Server to the Windows Server Failover Cluster](virtual-machines-windows-portal-sql-availability-group-tutorial.md#addNode).

1. Create an IP address resource on the cluster. 

   You can create the IP address resource in Failover Cluster Manager. Right-click the availability group role, click **Add Resource**, **More Resources**, and click **IP Address**.

   ![Create IP Address](./media/virtual-machines-windows-portal-sql-availability-group-dr/20-add-ip-resource.png)

   Configure this IP address as follows:
   
   - Use the network from the remote data center.
   - Assign the IP address from the new Azure load balancer. 

1. In SQL Server Configuration Manager, [enable Always On Availability Groups](http://msdn.microsoft.com/library/ff878259.aspx).

1. [Open firewall ports on the new SQL Server](virtual-machines-windows-portal-sql-availability-group-prereq.md#a-nameendpoint-firewall-configure-the-firewall-on-each-sql-server). 

   The port numbers you need to open depend on your environment. Open ports for the mirroring endpoint and Azure load balancer health probe.

1. [Add a replica to the availability group on the new SQL Server](http://msdn.microsoft.com/library/hh213239.aspx).

   For a replica in a remote Azure region, set it for asynchronous replication with manual failover.  

1. Add the IP address resource as a dependency for the listener client access point (network name) cluster. 

   The following screenshot shows a properly configured IP address cluster resource:

   ![Availability Group](./media/virtual-machines-windows-portal-sql-availability-group-dr/50-configure-dependency-multiple-ip.png)

   >[!IMPORTANT]
   >The cluster resource group includes both IP addresses. Both IP addresses are dependencies for the listener client access point. Use the **OR** operator in the cluster dependency configuration.

1. [Set the cluster parameters in PowerShell](virtual-machines-windows-portal-sql-availability-group-tutorial.md#setparam).

   >[!IMPORTANT]
   >Run the PowerShell script with the IP address and probe port that you configured on the load balancer in the new region.

## Set connection for multi subnets

The replica in the remote data center is part of the availability group but it is in a different subnet. If this replica becomes the primary replica, application connection time-outs may occur. This behavior is the same as an on-premises availability group in a multi-subnet deployment. To allow connections from client applications, either update the client connection or configure name resolution caching on the cluster network name resource.

Preferably, update the client connection strings to set `MultiSubnetFailover=Yes`. See [Connecting With MultiSubnetFailover](http://msdn.microsoft.com/library/gg471494#Anchor_0).

If you cannot modify the connection strings, you can configure name resolution caching. See [Connection Timeouts in Multi-subnet Availability Group](http://blogs.msdn.microsoft.com/alwaysonpro/2014/06/03/connection-timeouts-in-multi-subnet-availability-group/).

## Fail over to remote region 

To test listener connectivity to the remote region, you can fail over the replica to the remote region. While the replica is asynchronous, fail over is subject to potential data loss. To fail over without data loss, change the availability mode to synchronous and set the failover mode to automatic. Use the following steps:

1. In **Object Explorer**, connect to the instance of SQL Server that hosts the primary replica.
1. Under **AlwaysOn Availability Groups**, **Availability Groups**, right-click your availability group and click **Properties**.
1. On the **General** page, under **Availability Replicas**, set the secondary replica in the DR site to use **Synchronous Commit** availability mode and **Automatic** failover mode. 
1. If you have a secondary replica in same site as your primary replica for high availability, set this replica to **Asynchronous Commit** and **Manual**.
1. Click OK.
1. In **Object Explorer**, right-click the availability group, and click **Show Dashboard**.
1. On the dashboard, verify that the replica on the DR site is synchronized. 
1. In **Object Explorer**, right-click the availability group, and click **Failover...**. SQL Server Management Studios opens a wizard to fail over SQL Server.  
1. Click **Next**, and select the SQL Server instance in the DR site. Click **Next** again.
1. Connect to the SQL Server instance in the DR site and click **Next**. 
1. On the **Summary** page, verify the settings and click **Finish**.

After testing connectivity, move the primary replica back to your primary data center and set the availability mode back to their normal operating settings. The following table shows the normal operational settings for the architecture described in this document:

| Location | Server Instance | Role | Availability Mode | Failover Mode
| ----- | ----- | ----- | ----- | ----- 
| Primary data center | SQL-1 | Primary | Synchronous | Automatic
| Primary data center | SQL-2 | Secondary | Synchronous | Automatic
| Secondary or remote data center | SQL-3 | Secondary | Asynchronous | Manual


### More information about planned and forced manual failover

For more information, see the following topics:

- [Perform a Planned Manual Failover of an Availability Group (SQL Server)](http://msdn.microsoft.com/library/hh231018.aspx)
- [Perform a Forced Manual Failover of an Availability Group (SQL Server)](http://msdn.microsoft.com/library/ff877957.aspx)

## Additional Links

* [Always On Availability Groups](http://msdn.microsoft.com/library/hh510230.aspx)
* [Azure Virtual Machines](http://docs.microsoft.com/azure/virtual-machines/windows/)
* [Azure Load Balancers](virtual-machines-windows-portal-sql-alwayson-availability-groups-manual.md#configure-internal-load-balancer)
* [Azure Availability Sets](../../virtual-machines-windows-manage-availability.md)
