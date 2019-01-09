---
title: '&lt;AnnouncementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: fe278da539af59a32edf5a626461dbec0ba3887d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151650"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="b7db9-102">&lt;AnnouncementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="b7db9-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="b7db9-103">Bu yapılandırma öğesi, bir sabit duyuru sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b7db9-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="b7db9-104">Bir hizmet isteğe bağlı olarak, açık veya kapalı sırasıyla bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek duyurmaktan.</span><span class="sxs-lookup"><span data-stu-id="b7db9-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="b7db9-105">Bir Windows Communication Foundation (WCF) hizmeti duyurusunu uç noktaların belirtir [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi ve duyuruları gerçekleştirmek için AnnouncementClient kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7db9-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="b7db9-106">Diğer hizmetinden duyuru için dinleme isteyen bir istemci aslında bir WCF hizmeti olarak hareket; Bu istemci için Duyurunun uç noktaları yapılandırmak zorunda böylece [ \<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="b7db9-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="b7db9-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7db9-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7db9-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b7db9-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7db9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7db9-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7db9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7db9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7db9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7db9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7db9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7db9-112">Attributes</span></span>  
  
|<span data-ttu-id="b7db9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b7db9-113">Attribute</span></span>|<span data-ttu-id="b7db9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7db9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7db9-115">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="b7db9-115">discoveryVersion</span></span>|<span data-ttu-id="b7db9-116">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b7db9-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="b7db9-117">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="b7db9-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="b7db9-118">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="b7db9-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="b7db9-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="b7db9-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="b7db9-120">Gecikme için maksimum değeri belirten bir Timespan değeri bulma protokolünü selamlama iletisine göndermeden önce bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7db9-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="b7db9-121">İleti gönderilmeden önce bir rastgele bir zaman değeri 0 ile bu özniteliğin değeri arasında bekler.</span><span class="sxs-lookup"><span data-stu-id="b7db9-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="b7db9-122">Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri yeniden çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7db9-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="b7db9-123">name</span><span class="sxs-lookup"><span data-stu-id="b7db9-123">name</span></span>|<span data-ttu-id="b7db9-124">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b7db9-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b7db9-125">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="b7db9-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7db9-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7db9-126">Child Elements</span></span>  
 <span data-ttu-id="b7db9-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="b7db9-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7db9-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7db9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b7db9-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7db9-129">Element</span></span>|<span data-ttu-id="b7db9-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7db9-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7db9-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b7db9-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b7db9-132">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="b7db9-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7db9-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7db9-133">Example</span></span>  
 <span data-ttu-id="b7db9-134">Aşağıdaki örnek, bir istemci, http ve peernet üzerinden duyuruları iletiler için dinleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7db9-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7db9-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7db9-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
