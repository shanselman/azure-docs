---
title: ExpressRoute locations | Microsoft Docs
description: This article provides a detailed overview of locations where services are offered and how to connect to Azure regions.
services: expressroute
documentationcenter: na
author: cherylmc
manager: carmonm
editor: ''
ms.assetid: c878513a-d594-42ad-8b0e-403efd0c4b25
ms.service: expressroute
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 01/12/2017
ms.author: cherylmc

---
# ExpressRoute partners and peering locations
The tables in this article provide information on ExpressRoute connectivity providers, ExpressRoute geographical coverage, Microsoft cloud services supported over ExpressRoute, and ExpressRoute System Integrators (SIs).

## <a name="partners"></a>ExpressRoute connectivity providers
ExpressRoute is supported across all Azure regions and locations. The following map provides a list of Azure regions and ExpressRoute locations. ExpressRoute locations refer to those where Microsoft peers with several service providers.

![Location map][0]

You will have access to Azure services across all regions within a geopolitical region if you connected to at least one ExpressRoute location within the geopolitical region.

### Azure regions to ExpressRoute locations within a geopolitical region.
The following table provides a map of Azure regions to ExpressRoute locations within a geopolitical region.

| **Geopolitical region** | **Azure regions** | **ExpressRoute locations** |
| --- | --- | --- |
| **North America** |East US, West US, East US 2, West US 2, Central US, South Central US, North Central US, West Central US, Canada Central, Canada East |Atlanta, Chicago, Dallas, Las Vegas, Los Angeles, New York, Seattle, Silicon Valley, Washington DC, Montreal+, Quebec City+, Toronto |
| **South America** |Brazil South |Sao Paulo |
| **Europe** |North Europe, West Europe, UK West, UK South |Amsterdam, Dublin, London, Newport(Wales), Paris |
| **Asia** |East Asia, Southeast Asia |Hong Kong, Singapore |
| **Japan** |Japan West, Japan East |Osaka, Tokyo |
| **Australia** |Australia Southeast, Australia East |Melbourne, Sydney |
| **India** |India West, India Central, India South |Chennai, Mumbai |
| **South Korea** | Korea Central, Korea South | Busan, Seoul |

### Regions and geopolitical boundaries for national clouds
The table below provides information on regions and geopolitical boundaries for national clouds.

| **Geopolitical region** | **Azure regions** | **ExpressRoute locations** |
| --- | --- | --- | --- |
| **US Government cloud** |US Gov Iowa, US Gov Virginia, US DoD Central+, US DoD East+  |Chicago, Dallas, New York, Silicon Valley+, Washington DC |
| **China** |China North, China East |Beijing, Shanghai |
| **Germany** |Germany Central, Germany East |Berlin, Frankfurt |

Connectivity across geopolitical regions is not supported on the standard ExpressRoute SKU. You will need to enable the ExpressRoute premium add-on to support global connectivity. Connectivity to national cloud environments is not supported. You can work with your connectivity provider if such a need arises.

## <a name="locations"></a>Connectivity provider locations
> [!div class="op_single_selector"]
> * [Locations By Provider](expressroute-locations.md#locations)
> * [Providers By Location](expressroute-locations-providers.md#locations)
>
>

### Production Azure
| **Service provider** | **Microsoft Azure** | **Office 365 and CRM Online** | **Locations** |
| --- | --- | --- | --- |
| **[AARNet](https://www.aarnet.edu.au/network-and-services/cloud-services-applications/azure-expressroute/)** |Supported |Supported |Melbourne, Sydney |
| **[Aryaka Networks](http://www.aryaka.com/)** |Supported |Supported |Amsterdam, Dallas, Silicon Valley, Singapore, Tokyo, Washington DC |
| **[AT&T NetBond](https://www.synaptic.att.com/clouduser/html/productdetail/ATT_NetBond.htm)** |Supported |Supported |Amsterdam, Chicago, Dallas, London, Silicon Valley, Singapore, Sydney, Washington DC |
| **[Bell Canada](https://business.bell.ca/shop/enterprise/cloud-connect-access-to-cloud-partner-services)** |Supported |Supported |Toronto |
| **[British Telecom](http://www.globalservices.bt.com/uk/en/news/bt_to_provide_connectivity_to_microsoft_azure)** |Supported |Supported |Amsterdam, Hong Kong, London, Silicon Valley, Singapore, Sydney, Tokyo, Washington DC |
| **[CenturyLink](http://www.centurylink.com/business/enterprise/services/data-network/mpls-vpn.html)** |Coming soon |Coming soon |Silicon Valley |
| **China Telecom Global** |Supported |Not Supported |Hong Kong |
| **[Cologix](http://www.cologix.com/solutions/cloud-connect/public-clouds/microsoft-cloud/)** |Supported |Supported |Dallas, Montreal, Toronto |
| **[Colt](http://www.colt.net/uk/en/news/colt-announces-dedicated-cloud-access-for-microsoft-azure-services-en.htm)** |Supported |Supported |Amsterdam, Dublin, London, Tokyo |
| **Comcast** |Supported |Supported |Chicago, Silicon Valley, Washington DC |
| **Console**| Supported | Supported |Silicon Valley |
| **[CoreSite](http://www.coresite.com/solutions/cloud-services/public-cloud-providers/microsoft-azure-expressroute)** |Supported |Supported |Los Angeles , New York |
| **[Equinix](http://www.equinix.com/partners/microsoft-azure/)** |Supported |Supported |Amsterdam, Atlanta, Chicago, Dallas, Hong Kong, London, Los Angeles, Melbourne, New York, Osaka, Paris+, Sao Paulo, Seattle, Silicon Valley, Singapore, Sydney, Tokyo, Toronto, Washington DC |
| **euNetworks** |Supported |Supported |Amsterdam |
| **GÉANT** |Supported |Supported |Amsterdam |
| **[Internet Initiative Japan Inc. - IIJ](http://www.iij.ad.jp/en/news/pressrelease/2015/1216-2.html)** |Supported |Supported |Osaka, Tokyo |
| **[InterCloud](https://www.intercloud.com/)** |Supported |Supported |Amsterdam, London, Singapore, Washington DC |
| **Internet Solutions - Cloud Connect** |Supported |Supported |Amsterdam, London |
| **[Interxion](http://www.interxion.com/why-interxion/colocate-with-the-clouds/colocated-hybrid-cloud/microsoft-azure/)** |Supported |Supported |Amsterdam, London, Paris |
| **Jisc** |Supported |Supported |London |
| **[KPN](http://www.kpn.com/cloudconnect)** | Supported | Supported | Amsterdam | 
| **[Level 3 Communications](http://your.level3.com/LP=882?WT.tsrc=02192014LP882AzureVanityAzureText)** |Supported |Supported |Amsterdam, Chicago, Dallas, Las Vegas+, London, Seattle, Silicon Valley, Singapore, Washington DC |
| **[Megaport](https://www.megaport.com/services/microsoft-expressroute/)** |Supported |Supported |Dallas, Hong Kong, Las Vegas, Los Angeles, Melbourne, New York, Seattle, Singapore, Sydney, Toronto, Washington DC |
| **MTN** |Supported |Supported |London |
| **[Next Generation Data](http://www.nextgenerationdata.co.uk/ngd-cloud-gateway/)** |Supported |Supported |Newport(Wales) |
| **NEXTDC** |Supported |Supported |Melbourne, Sydney |
| **NTT Communications** |Supported |Supported |London, Los Angeles, Osaka, Singapore, Tokyo, Washington DC |
| **[Orange](http://www.orange-business.com/en/products/business-vpn-galerie)** |Supported |Supported |Amsterdam, Hong Kong, London, Silicon Valley, Singapore, Sydney, Washington DC |
| **PCCW Global Limited** |Supported |Supported |Hong Kong |
| **[SIFY](http://telecom.sify.com/azure-expressroute.html)** |Supported |Supported |Chennai |
| **[SingTel](http://info.singtel.com/about-us/news-releases/singtel-provide-secure-private-access-microsoft-azure-public-cloud)** |Supported |Supported |Singapore |
| **Softbank** |Supported |Supported |Osaka, Tokyo |
| **[Tata Communications](http://www.tatacommunications.com/lp/izo/azure/azure_index.html)** |Supported |Supported |Amsterdam, Chennai, Hong Kong, London, Mumbai, Silicon Valley, Singapore, Washington DC |
| **[TeleCity Group](http://www.telecitygroup.com/investor-centre/news_details.htm?locid=03100500400b00d&xml)** |Supported |Supported |Amsterdam, Dublin, London |
| **[Telefonica](https://www.business-solutions.telefonica.com/es/enterprise/solutions/efficient-infrastructure/managed-voice-data-connectivity/)** |Supported |Supported |Sao Paulo |
| **Telenor** |Supported |Supported |Amsterdam, London |
| **[Telstra Corporation](http://www.telstra.com.au/business-enterprise/network-services/networks/cloud-direct-connect/)** |Supported |Supported |Melbourne, Sydney |
| **[Verizon](http://www.verizonenterprise.com/products/networking/secure-cloud-interconnect/)** |Supported |Supported |Amsterdam, Hong Kong, London, Silicon Valley, Singapore, Sydney, Tokyo, Washington DC |
| **[Vodafone](http://www.vodafone.com/business/global-enterprise/global-connectivity/vodafone-ip-vpn-cloud-connect)** |Supported |Not Supported |London |
| **[Zayo Group](http://www.zayo.com/solutions/industries/cloud-connectivity/microsoft-expressroute)** |Supported |Supported |Chicago, Los Angeles, New York, Silicon Valley, Toronto, Washington DC |

 **+** denotes coming soon

### National cloud environment

### US Government cloud
| **Service provider** | **Microsoft Azure** | **Office 365** | **Locations** |
| --- | --- | --- | --- |
| **[AT&T NetBond](https://www.synaptic.att.com/clouduser/html/productdetail/ATT_NetBond.htm)** |Supported |Supported |Chicago, Washington DC |
| **[Equinix](http://www.equinix.com/partners/microsoft-azure/)** |Supported |Supported |Chicago, Dallas, New York, Silicon Valley+, Washington DC |
| **[Level 3 Communications](http://your.level3.com/LP=882?WT.tsrc=02192014LP882AzureVanityAzureText)** |Supported |Supported |Chicago, New York+, Washington DC |
| **[Megaport](https://www.megaport.com/services/microsoft-expressroute/)** |Supported | Supported | Dallas |
| **[Verizon](http://news.verizonenterprise.com/2014/04/secure-cloud-interconnect-solutions-enterprise/)** |Supported |Supported |Chicago, Dallas, New York, Washington DC |

### China
| **Service provider** | **Microsoft Azure** | **Office 365** | **Locations** |
| --- | --- | --- | --- |
| **China Telecom** |Supported |Not Supported |Beijing, Shanghai |

To learn more, see [ExpressRoute in China](http://www.windowsazure.cn/home/features/expressroute/).

### Germany
| **Service provider** | **Microsoft Azure** | **Office 365** | **Locations** |
| --- | --- | --- | --- |
| **[Colt](http://www.colt.net/uk/en/news/colt-announces-dedicated-cloud-access-for-microsoft-azure-services-en.htm)** |Supported |Not Supported |Berlin+, Frankfurt |
| **[Equinix](http://www.equinix.com/partners/microsoft-azure/)** |Supported |Not Supported |Frankfurt |
| **e-shelter** |Supported |Not Supported |Berlin |
| **Interxion** |Supported |Not Supported |Frankfurt |
| **[Megaport](https://www.megaport.com/services/microsoft-expressroute/)** |Supported  | Not Supported | Berlin+ |

## <a name="nonpartners"></a>Connectivity through service providers not listed
If your connectivity provider is not listed in previous sections, you can still create a connection.

* Check with your connectivity provider to see if they are connected to any of the exchanges in the table above. You can check the following links to gather more information about services offered by exchange providers. Several connectivity providers are already connected to Ethernet exchanges.
  * [Cologix](http://www.cologix.com/)
  * [CoreSite](http://www.coresite.com/)
  * [Equinix Cloud Exchange](http://www.equinix.com/services/interconnection-connectivity/cloud-exchange/)
  * [Interxion](http://www.interxion.com/why-interxion/colocate-with-the-clouds/colocated-hybrid-cloud/microsoft-azure/)
  * [Megaport](https://www.megaport.com/services/microsoft-expressroute/)
  * [NextDC](http://www.nextdc.com/)
  * [TeleCity CloudIX](http://www.telecitygroup.com/colocation-services/cloud-ix.htm)
* Have your connectivity provider extend your network to the peering location of choice.
  * Ensure that your connectivity provider extends your connectivity in a highly available manner so that there are no single points of failure.
* Order an ExpressRoute circuit with the exchange as your connectivity provider to connect to Microsoft.
  * Follow steps in [Create an ExpressRoute circuit](expressroute-howto-circuit-classic.md) to set up connectivity.

| **Connectivity provider** | **Exchange** | **Locations** |
| --- | --- | --- |
| **[1CLOUDSTAR](http://www.1cloudstar.com/service/cloudconnect-azure-expressroute/)** |Equinix |Singapore |
| **[Arteria Networks Corporation](https://arteria-net.com/business/service/cloud_access/sca/)** |Equinix |Tokyo |
| **[Alaska Communications](http://www.alaskacommunications.com/For-Your-Business/Direct-Cloud-Service)** |Equinix |Seattle |
| **[Eurofiber](https://eurofiber.nl/microsoft-azure/)** | Equinix | Amsterdam |
| **[Exponential E](http://www.exponential-e.com/services/connectivity-services/cloud-connect-exchange)** | Equinix | London |
| **[HSO](http://www.hso.co.uk/products/cloud-direct)** |Equinix | London, Slough |
| **[Lightower](http://www.lightower.com/network-solutions/cloud-connect/#microsoft-azure)** |Equinix |New York, Washington DC |
| **[Macquarie Telecom Group](https://macquariegovernment.com/secure-cloud/secure-cloud-exchange/)** | Megaport | Sydney |
| **[Masergy](https://www.masergy.com/solutions/hybrid-networking/cloud-marketplace/microsoft-azure)** | Equinix | Washington DC |
| **[Nianet](https://nianet.dk/produkter/internet/microsoft-expressroute)** |Telecity | Amsterdam, Frankfurt |  
| **[Transtelco](http://www.transtelco.net/tcloud/microsoft)** |Equinix | Dallas, Los Angeles |  
| **[QSC AG](https://www.qsc.de/de/produkte-loesungen/cloud-services-und-it-outsourcing/pure-enterprise-cloud/multi-cloud-management/azure-expressroute/)** |Interxion | Frankfurt |  
| **[Windstream](http://www.windstreambusiness.com/solutions/cloud-services/cloud-and-managed-hosting-services)**| Equinix |Chicago, Silicon Valley, Washington DC |
| **[XO Communications](http://www.xo.com/)** |Equinix |Silicon Valley |
| **[Zertia](http://www.zertia.es/index.php/novedades)**| Level 3 | Madrid |


## ExpressRoute system integrators
Enabling private connectivity to fit your needs can be challenging, based on the scale of your network. You can work with any of the system integrators listed in the following table to assist you with onboarding to ExpressRoute.

| **System integrator** | **Continent** |
| --- | --- |
| **[Avanade Inc.](http://www.avanade.com/)** |Asia, Europe, US |
| **[Dotnet Solutions](http://www.dotnetsolutions.co.uk/)** |Europe |
| **[Equinix Professional Services](http://www.equinix.com/services/consulting/)** |US |
| **[IT Consultancy](http://itconsult.com.au/microsoft-expressroute)** | Australia |
| **[MSG Services](https://www.msg-services.de/it-services/managed-services/cloud-outsourcing/)** | Europe (Germany) |
| **[Nelite](http://nelite.com/)** |Europe |
| **[OneAs1a](http://www.oneas1a.com/express-connect-any-cloud-ecac)** |Asia |
| **[Perficient](http://www.perficient.com/Partners/Microsoft/Cloud/Azure-ExpressRoute)** |US |
| **[Project Leadership](http://www.projectleadership.net/azure)** |US |


## Next steps
* For more information about ExpressRoute, see the [ExpressRoute FAQ](expressroute-faqs.md).
* Ensure that all prerequisites are met. See [ExpressRoute prerequisites](expressroute-prerequisites.md).

<!--Image References-->
[0]: ./media/expressroute-locations/expressroute-locations-map.png "Location map"
