---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8a6c874d7d2930b969f2cc9778534aa99eab78f5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145828"
---
# <a name="ltudpannoucementendpointgt"></a><span data-ttu-id="dddd2-102">&lt;udpAnnoucementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="dddd2-102">&lt;udpAnnoucementEndpoint&gt;</span></span>
<span data-ttu-id="dddd2-103">Bu yapılandırma öğesi, bir UDP bağlama üzerinden Duyurunun ileti göndermek için hizmetler tarafından kullanılan standart bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dddd2-103">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="dddd2-104">Bu, sabit bir sözleşme içeriyor ve iki bulma sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="dddd2-104">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="dddd2-105">Buna ek olarak sabit bir UDP bağlama ve WS-bulma (WS-bulma Nisan 2005 veya WS-bulma sürüm 1.1) belirtimleri belirtilen varsayılan adresi değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="dddd2-105">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="dddd2-106">Duyurunun ileti alma ve gönderme için kullanmak üzere çok noktaya yayın adresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dddd2-106">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="dddd2-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dddd2-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="dddd2-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="dddd2-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dddd2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dddd2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dddd2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dddd2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dddd2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dddd2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dddd2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dddd2-112">Attributes</span></span>  
  
|<span data-ttu-id="dddd2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dddd2-113">Attribute</span></span>|<span data-ttu-id="dddd2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dddd2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dddd2-115">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="dddd2-115">discoveryVersion</span></span>|<span data-ttu-id="dddd2-116">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dddd2-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="dddd2-117">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="dddd2-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="dddd2-118">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="dddd2-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="dddd2-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="dddd2-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="dddd2-120">Gecikme için maksimum değeri belirten bir Timespan değeri bulma protokolünü selamlama iletisine göndermeden önce bekleyin.</span><span class="sxs-lookup"><span data-stu-id="dddd2-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="dddd2-121">İleti gönderilmeden önce bir rastgele bir zaman değeri 0 ile bu özniteliğin değeri arasında bekler.</span><span class="sxs-lookup"><span data-stu-id="dddd2-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="dddd2-122">Bu öznitelik, bir ağ gider ve aynı anda tüm hizmetleri yeniden çevrimiçi duruma ağ fırtınalarını önlemek için küçük, rastgele bir gecikme ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dddd2-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="dddd2-123">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="dddd2-123">multicastAddress</span></span>|<span data-ttu-id="dddd2-124">Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="dddd2-124">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="dddd2-125">Varsayılan değer uyumlu protokolü belirtimi için çok noktaya yayın adresi gibidir.</span><span class="sxs-lookup"><span data-stu-id="dddd2-125">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="dddd2-126">name</span><span class="sxs-lookup"><span data-stu-id="dddd2-126">name</span></span>|<span data-ttu-id="dddd2-127">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="dddd2-127">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="dddd2-128">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="dddd2-128">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dddd2-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dddd2-129">Child Elements</span></span>  
  
|<span data-ttu-id="dddd2-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="dddd2-130">Element</span></span>|<span data-ttu-id="dddd2-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dddd2-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dddd2-132">\<Udpannouncementendpoint ></span><span class="sxs-lookup"><span data-stu-id="dddd2-132">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="dddd2-133">UDP taşıma için UDP uç nokta yapılandırmanıza olanak tanıyan ayarların koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="dddd2-133">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dddd2-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dddd2-134">Parent Elements</span></span>  
  
|<span data-ttu-id="dddd2-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="dddd2-135">Element</span></span>|<span data-ttu-id="dddd2-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dddd2-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dddd2-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="dddd2-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="dddd2-138">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="dddd2-138">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dddd2-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="dddd2-139">Example</span></span>  
 <span data-ttu-id="dddd2-140">Aşağıdaki örnek, bir istemci için Duyurunun bir UDP üzerinden dinlemeyi gösterir. çok noktaya yayın adresi ve UDP çok noktaya yayın taşımasıyla varsayılan belirtilen çok noktaya yayın adresi ile çok noktaya yayın aktarma.</span><span class="sxs-lookup"><span data-stu-id="dddd2-140">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dddd2-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dddd2-141">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
