---
title: <udpAnnoucementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 7c7c92db479efa9f6fdf2dafc9a6d512df4254e3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265200"
---
# <a name="udpannoucementendpoint"></a><span data-ttu-id="1da8a-101">\<udpAnnoucementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="1da8a-101">\<udpAnnoucementEndpoint></span></span>
<span data-ttu-id="1da8a-102">Bu yapılandırma öğesi, bir UDP bağlama üzerinden Duyurunun ileti göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1da8a-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="1da8a-103">Bu, sabit bir sözleşme içeriyor ve iki bulma sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1da8a-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="1da8a-104">Buna ek olarak sabit bir UDP bağlama ve WS-bulma (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtimleri belirtilen varsayılan adresi değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="1da8a-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="1da8a-105">Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1da8a-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="1da8a-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1da8a-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="1da8a-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1da8a-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da8a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1da8a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1da8a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1da8a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1da8a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1da8a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1da8a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1da8a-111">Attributes</span></span>  
  
|<span data-ttu-id="1da8a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1da8a-112">Attribute</span></span>|<span data-ttu-id="1da8a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1da8a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1da8a-114">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="1da8a-114">discoveryVersion</span></span>|<span data-ttu-id="1da8a-115">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1da8a-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="1da8a-116">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="1da8a-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="1da8a-117">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="1da8a-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="1da8a-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="1da8a-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="1da8a-119">Gecikme için maksimum değeri belirten bir Timespan değeri bulma protokolünü selamlama iletisine göndermeden önce bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1da8a-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="1da8a-120">İleti gönderilmeden önce bir rastgele bir zaman değeri 0 ile bu özniteliğin değeri arasında bekler.</span><span class="sxs-lookup"><span data-stu-id="1da8a-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="1da8a-121">Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri yeniden çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1da8a-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="1da8a-122">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="1da8a-122">multicastAddress</span></span>|<span data-ttu-id="1da8a-123">Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="1da8a-123">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="1da8a-124">Varsayılan değer uyumlu protokolü belirtimi için çok noktaya yayın adresi gibidir.</span><span class="sxs-lookup"><span data-stu-id="1da8a-124">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="1da8a-125">name</span><span class="sxs-lookup"><span data-stu-id="1da8a-125">name</span></span>|<span data-ttu-id="1da8a-126">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="1da8a-126">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1da8a-127">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="1da8a-127">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1da8a-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1da8a-128">Child Elements</span></span>  
  
|<span data-ttu-id="1da8a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="1da8a-129">Element</span></span>|<span data-ttu-id="1da8a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1da8a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1da8a-131">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="1da8a-131">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="1da8a-132">UDP taşıma için UDP uç nokta yapılandırmanıza olanak tanıyan ayarların koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="1da8a-132">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1da8a-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1da8a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1da8a-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="1da8a-134">Element</span></span>|<span data-ttu-id="1da8a-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1da8a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1da8a-136">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1da8a-136">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1da8a-137">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="1da8a-137">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1da8a-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="1da8a-138">Example</span></span>  
 <span data-ttu-id="1da8a-139">Aşağıdaki örnek, bir istemci için Duyurunun bir UDP üzerinden dinlemeyi gösterir. çok noktaya yayın adresi ve UDP çok noktaya yayın taşımasıyla varsayılan belirtilen çok noktaya yayın adresi ile çok noktaya yayın aktarma.</span><span class="sxs-lookup"><span data-stu-id="1da8a-139">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1da8a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da8a-140">See also</span></span>
- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
