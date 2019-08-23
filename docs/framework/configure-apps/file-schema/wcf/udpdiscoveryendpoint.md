---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: e6e567e8a657b4c1683ae4abfb14f96a0f272e4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934588"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="adcdd-101">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="adcdd-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="adcdd-102">Bu yapılandırma öğesi, bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="adcdd-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="adcdd-103">Bu uç nokta, sabit bir sözleşmeye sahiptir ve iki WS-bulma protokol sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="adcdd-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="adcdd-104">Ayrıca, WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery V 1.1) içinde belirtilen bir sabit UDP bağlaması ve varsayılan bir adres vardır.</span><span class="sxs-lookup"><span data-stu-id="adcdd-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="adcdd-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="adcdd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="adcdd-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="adcdd-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adcdd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adcdd-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adcdd-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="adcdd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="adcdd-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="adcdd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adcdd-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="adcdd-110">Attributes</span></span>  
  
|<span data-ttu-id="adcdd-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="adcdd-111">Attribute</span></span>|<span data-ttu-id="adcdd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adcdd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adcdd-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="adcdd-113">discoveryMode</span></span>|<span data-ttu-id="adcdd-114">Bulma protokolünün modunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="adcdd-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="adcdd-115">Geçerli değerler şunlardır "geçici" ve "yönetilen".</span><span class="sxs-lookup"><span data-stu-id="adcdd-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="adcdd-116">Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır.</span><span class="sxs-lookup"><span data-stu-id="adcdd-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="adcdd-117">Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="adcdd-118">Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="adcdd-118">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="adcdd-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="adcdd-119">discoveryVersion</span></span>|<span data-ttu-id="adcdd-120">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="adcdd-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="adcdd-121">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="adcdd-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="adcdd-122">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="adcdd-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="adcdd-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="adcdd-123">maxResponseDelay</span></span>|<span data-ttu-id="adcdd-124">Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="adcdd-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="adcdd-125">Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="adcdd-126">Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="adcdd-127">Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır.</span><span class="sxs-lookup"><span data-stu-id="adcdd-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="adcdd-128">Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="adcdd-129">Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="adcdd-130">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="adcdd-130">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="adcdd-131">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="adcdd-131">multicastAddress</span></span>|<span data-ttu-id="adcdd-132">Bulma iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="adcdd-132">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="adcdd-133">Varsayılan değer, protokol belirtimine uyumlu olan çok noktaya yayın adresidir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-133">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="adcdd-134">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="adcdd-134">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="adcdd-135">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="adcdd-135">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adcdd-136">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="adcdd-136">Child Elements</span></span>  
  
|<span data-ttu-id="adcdd-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="adcdd-137">Element</span></span>|<span data-ttu-id="adcdd-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adcdd-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adcdd-139">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="adcdd-139">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="adcdd-140">UDP uç noktası için UDP aktarımını yapılandırmanıza izin veren ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="adcdd-140">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adcdd-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="adcdd-141">Parent Elements</span></span>  
  
|<span data-ttu-id="adcdd-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="adcdd-142">Element</span></span>|<span data-ttu-id="adcdd-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adcdd-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adcdd-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="adcdd-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="adcdd-145">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="adcdd-145">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="adcdd-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="adcdd-146">Example</span></span>  
 <span data-ttu-id="adcdd-147">Aşağıdaki örnek, bir UDP çok noktaya yayın aktarımı üzerinden bulma iletilerini dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="adcdd-147">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adcdd-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adcdd-148">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
