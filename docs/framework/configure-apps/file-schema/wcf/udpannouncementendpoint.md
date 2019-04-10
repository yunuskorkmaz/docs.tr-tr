---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 04f5fb27a0da7e553ff3c0308f7fb2e2df2e0b20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210015"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="48955-101">\<Udptransportsettings ></span><span class="sxs-lookup"><span data-stu-id="48955-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="48955-102">Bu yapılandırma öğesi, bir UDP bağlama üzerinden Duyurunun ileti göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48955-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="48955-103">Bu, sabit bir sözleşme içeriyor ve iki bulma sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="48955-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="48955-104">Buna ek olarak sabit bir UDP bağlama ve WS-bulma (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtimleri belirtilen varsayılan adresi değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="48955-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="48955-105">Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48955-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="48955-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="48955-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="48955-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="48955-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48955-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48955-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48955-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48955-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48955-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48955-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48955-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48955-111">Attributes</span></span>  
  
|<span data-ttu-id="48955-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48955-112">Attribute</span></span>|<span data-ttu-id="48955-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48955-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48955-114">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="48955-114">discoveryVersion</span></span>|<span data-ttu-id="48955-115">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="48955-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="48955-116">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="48955-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="48955-117">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="48955-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="48955-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="48955-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="48955-119">Gecikme için maksimum değeri belirten bir Timespan değeri bulma protokolünü selamlama iletisine göndermeden önce bekleyin.</span><span class="sxs-lookup"><span data-stu-id="48955-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="48955-120">İleti gönderilmeden önce bir rastgele bir zaman değeri 0 ile bu özniteliğin değeri arasında bekler.</span><span class="sxs-lookup"><span data-stu-id="48955-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="48955-121">Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri yeniden çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48955-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="48955-122">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="48955-122">multicastAddress</span></span>|<span data-ttu-id="48955-123">Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="48955-123">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="48955-124">Varsayılan değer uyumlu protokolü belirtimi için çok noktaya yayın adresi gibidir.</span><span class="sxs-lookup"><span data-stu-id="48955-124">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="48955-125">name</span><span class="sxs-lookup"><span data-stu-id="48955-125">name</span></span>|<span data-ttu-id="48955-126">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="48955-126">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="48955-127">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="48955-127">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48955-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48955-128">Child Elements</span></span>  
  
|<span data-ttu-id="48955-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="48955-129">Element</span></span>|<span data-ttu-id="48955-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48955-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48955-131">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="48955-131">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="48955-132">UDP taşıma için UDP uç nokta yapılandırmanıza olanak tanıyan ayarların koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="48955-132">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48955-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48955-133">Parent Elements</span></span>  
  
|<span data-ttu-id="48955-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="48955-134">Element</span></span>|<span data-ttu-id="48955-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48955-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48955-136">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="48955-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="48955-137">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="48955-137">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48955-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="48955-138">Example</span></span>  
 <span data-ttu-id="48955-139">Aşağıdaki örnek, bir istemci için Duyurunun bir UDP üzerinden dinlemeyi gösterir. çok noktaya yayın adresi ve UDP çok noktaya yayın taşımasıyla varsayılan belirtilen çok noktaya yayın adresi ile çok noktaya yayın aktarma.</span><span class="sxs-lookup"><span data-stu-id="48955-139">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="48955-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48955-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
