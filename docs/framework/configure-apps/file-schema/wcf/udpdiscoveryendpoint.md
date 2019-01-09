---
title: '&lt;UdpDiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 6508f73de7920a339e40284c86b0d1d649e7eabe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145438"
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="f8783-102">&lt;UdpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="f8783-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="f8783-103">Bu yapılandırma öğesi, bir UDP üzerinden bulma işlemleri için önceden yapılandırılmış olan bir standart uç nokta tanımlar. çok noktaya yayın bağlaması.</span><span class="sxs-lookup"><span data-stu-id="f8783-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="f8783-104">Bu uç nokta, sabit bir sözleşme içeriyor ve iki WS bulma protokolünü sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f8783-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="f8783-105">Ayrıca, sabit bir UDP bağlama ve WS-bulma belirtimleri (WS-bulma Nisan 2005 veya WS-bulma V1.1) belirtildiği gibi varsayılan bir adresi vardır.</span><span class="sxs-lookup"><span data-stu-id="f8783-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="f8783-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f8783-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8783-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f8783-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8783-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8783-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8783-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8783-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f8783-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8783-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8783-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f8783-111">Attributes</span></span>  
  
|<span data-ttu-id="f8783-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f8783-112">Attribute</span></span>|<span data-ttu-id="f8783-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8783-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8783-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="f8783-114">discoveryMode</span></span>|<span data-ttu-id="f8783-115">Bulma kuralının modu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f8783-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="f8783-116">Geçerli değerler şunlardır: "Geçici" ve "Yönetilen".</span><span class="sxs-lookup"><span data-stu-id="f8783-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="f8783-117">Yönetilen modda bir bulunabilir hizmet deposu olarak hareket eden bir keşif proxy'si, protokolü kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8783-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="f8783-118">Anlık mod gerektirir UDP kullanılacak protokolü kullanılabilir hizmetleri bulmak için çok noktaya yayın mekanizması.</span><span class="sxs-lookup"><span data-stu-id="f8783-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="f8783-119">Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="f8783-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="f8783-120">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f8783-120">discoveryVersion</span></span>|<span data-ttu-id="f8783-121">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f8783-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f8783-122">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="f8783-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f8783-123">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="f8783-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="f8783-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="f8783-124">maxResponseDelay</span></span>|<span data-ttu-id="f8783-125">Araştırma eşleşme veya eşleşme gidermek gibi belirli iletileri göndermeden önce gecikme Bulma Protokolü için maksimum değeri belirten bir Timespan değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="f8783-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="f8783-126">Aynı anda tüm ProbeMatches gönderiliyorsa, ağ storm neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8783-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="f8783-127">Bunun gerçekleşmesini önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f8783-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="f8783-128">Bu öznitelik tarafından ayarlanan değer için 0 aralığındaki rastgele gecikme var.</span><span class="sxs-lookup"><span data-stu-id="f8783-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="f8783-129">Bu öznitelik 0 olarak ayarlanırsa, herhangi bir gecikme olmadan sıkı bir döngüde ProbeMatches iletileri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f8783-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="f8783-130">Aksi takdirde, tüm ProbeMatches ileti göndermek için geçen toplam süre maxResponseDelay aşmayacak şekilde ProbeMatches iletileri rastgele bir gecikme süresi ile gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f8783-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="f8783-131">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f8783-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="f8783-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="f8783-132">multicastAddress</span></span>|<span data-ttu-id="f8783-133">Bulma ileti alma ve gönderme için kullanılacak bir çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="f8783-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="f8783-134">Varsayılan değer uyumlu protokolü belirtimi için çok noktaya yayın adresi gibidir.</span><span class="sxs-lookup"><span data-stu-id="f8783-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="f8783-135">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="f8783-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f8783-136">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="f8783-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8783-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8783-137">Child Elements</span></span>  
  
|<span data-ttu-id="f8783-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8783-138">Element</span></span>|<span data-ttu-id="f8783-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8783-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8783-140">\<Udpannouncementendpoint ></span><span class="sxs-lookup"><span data-stu-id="f8783-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="f8783-141">UDP taşıma için UDP uç nokta yapılandırmanıza olanak tanıyan ayarların koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="f8783-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8783-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f8783-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f8783-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8783-143">Element</span></span>|<span data-ttu-id="f8783-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8783-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8783-145">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f8783-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f8783-146">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="f8783-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8783-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8783-147">Example</span></span>  
 <span data-ttu-id="f8783-148">Aşağıdaki örnek, bir UDP üzerinden bulma iletiler için dinleme hizmet gösterir. çok noktaya yayın taşıma.</span><span class="sxs-lookup"><span data-stu-id="f8783-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="f8783-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8783-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
