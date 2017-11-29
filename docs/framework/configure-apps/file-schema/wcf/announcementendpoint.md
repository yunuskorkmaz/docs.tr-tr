---
title: '&lt;announcementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d49ea0b2dbabd5e747d912b76e493559b2a96ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="9e3c9-102">&lt;announcementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9e3c9-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="9e3c9-103">Bu yapılandırma öğesi, standart bir uç nokta sabit duyuru sözleşme ile tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="9e3c9-104">Bir hizmet açıldığında veya sırasıyla kapalı bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek, kullanılabilirlik isteğe bağlı olarak Duyurusu.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="9e3c9-105">A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmeti belirtir duyuru uç noktalardan [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi ve duyuruları gerçekleştirmek için AnnouncementClient kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-105">A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="9e3c9-106">Başka bir hizmet duyurudan gerçekten olarak davranan için dinleme isteyen bir istemci bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet; böylece, bu istemci için duyuru uç noktaları yapılandırmak zorunda [ \<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-106">A client wishing to listen for the announcement from other service is actually acting as a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="9e3c9-107">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9e3c9-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e3c9-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9e3c9-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e3c9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e3c9-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan" 
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e3c9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e3c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9e3c9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e3c9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e3c9-112">Attributes</span></span>  
  
|<span data-ttu-id="9e3c9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9e3c9-113">Attribute</span></span>|<span data-ttu-id="9e3c9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e3c9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e3c9-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="9e3c9-115">discoveryVersion</span></span>|<span data-ttu-id="9e3c9-116">WS bulma protokolünü iki sürümü birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="9e3c9-117">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="9e3c9-118">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="9e3c9-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="9e3c9-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="9e3c9-120">Gecikme için maksimum değeri belirten bir Timespan değerine Bulma Protokolü Hello iletiyi göndermeden önce bekler.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="9e3c9-121">İleti gönderilmeden önce bir rastgele saat değeri 0 ile bu özniteliğin değeri arasında bekler.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="9e3c9-122">Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri tekrar çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="9e3c9-123">name</span><span class="sxs-lookup"><span data-stu-id="9e3c9-123">name</span></span>|<span data-ttu-id="9e3c9-124">Standart uç noktasının yapılandırma adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="9e3c9-125">Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e3c9-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e3c9-126">Child Elements</span></span>  
 <span data-ttu-id="9e3c9-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e3c9-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e3c9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9e3c9-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e3c9-129">Element</span></span>|<span data-ttu-id="9e3c9-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e3c9-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e3c9-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9e3c9-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9e3c9-132">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9e3c9-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e3c9-133">Example</span></span>  
 <span data-ttu-id="9e3c9-134">Aşağıdaki örnek, bir istemci http ve peernet duyuruları iletiler için dinleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
    <endpoint name="httpAnnouncementEndpoint"  
              kind="announcementEndpoint"  
              binding="basicHttpBinding"  
              address="announcements" />  
    <endpoint name="peerNetAnnouncementEndpoint"  
              kind="announcementEndpoint"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />  
  ...  
  </service>  
</services>  
  
<standardEndpoints>  
  <announcementEndpoint>  
    <standardEndpoint name="httpAnnouncementEndpoint"                         
                      version="WSDiscoveryApril2005" />  
    <standardEndpoint name="peerNetAnnouncementEndpoint"                         
                      version="WSDiscoveryApril2005" />  
   </announcementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e3c9-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
