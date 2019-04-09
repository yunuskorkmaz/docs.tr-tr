---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 4f3cf2748acc75b0ec83732664c5f97114f3663a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195130"
---
# <a name="announcementendpoint"></a><span data-ttu-id="bbf99-101">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="bbf99-101">\<announcementEndpoint></span></span>
<span data-ttu-id="bbf99-102">Bu yapılandırma öğesi, bir sabit duyuru sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbf99-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="bbf99-103">Bir hizmet isteğe bağlı olarak, açık veya kapalı sırasıyla bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek duyurmaktan.</span><span class="sxs-lookup"><span data-stu-id="bbf99-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="bbf99-104">Bir Windows Communication Foundation (WCF) hizmeti duyurusunu uç noktaların belirtir [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi ve duyuruları gerçekleştirmek için AnnouncementClient kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbf99-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="bbf99-105">Diğer hizmetinden duyuru için dinleme isteyen bir istemci aslında bir WCF hizmeti olarak hareket; Bu istemci için Duyurunun uç noktaları yapılandırmak zorunda böylece [ \<Hizmetleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="bbf99-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="bbf99-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bbf99-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="bbf99-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="bbf99-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf99-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbf99-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbf99-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbf99-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bbf99-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbf99-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbf99-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbf99-111">Attributes</span></span>  
  
|<span data-ttu-id="bbf99-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bbf99-112">Attribute</span></span>|<span data-ttu-id="bbf99-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbf99-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbf99-114">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="bbf99-114">discoveryVersion</span></span>|<span data-ttu-id="bbf99-115">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bbf99-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="bbf99-116">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="bbf99-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="bbf99-117">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="bbf99-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="bbf99-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="bbf99-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="bbf99-119">Gecikme için maksimum değeri belirten bir Timespan değeri bulma protokolünü selamlama iletisine göndermeden önce bekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbf99-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="bbf99-120">İleti gönderilmeden önce bir rastgele bir zaman değeri 0 ile bu özniteliğin değeri arasında bekler.</span><span class="sxs-lookup"><span data-stu-id="bbf99-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="bbf99-121">Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri yeniden çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbf99-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="bbf99-122">name</span><span class="sxs-lookup"><span data-stu-id="bbf99-122">name</span></span>|<span data-ttu-id="bbf99-123">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="bbf99-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="bbf99-124">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="bbf99-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbf99-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbf99-125">Child Elements</span></span>  
 <span data-ttu-id="bbf99-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbf99-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbf99-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbf99-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bbf99-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbf99-128">Element</span></span>|<span data-ttu-id="bbf99-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbf99-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbf99-130">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="bbf99-130">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="bbf99-131">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="bbf99-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bbf99-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbf99-132">Example</span></span>  
 <span data-ttu-id="bbf99-133">Aşağıdaki örnek, bir istemci, http ve peernet üzerinden duyuruları iletiler için dinleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf99-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bbf99-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf99-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
