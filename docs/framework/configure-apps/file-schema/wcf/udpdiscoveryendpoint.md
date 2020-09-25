---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: f02cbddcdd4390d754f93e6f6d9aae6646cb137b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183630"
---
# \<udpDiscoveryEndpoint>

<span data-ttu-id="4559d-101">Bu yapılandırma öğesi, bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4559d-101">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="4559d-102">Bu uç nokta, sabit bir sözleşmeye sahiptir ve iki WS-bulma protokol sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="4559d-102">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="4559d-103">Ayrıca, WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery V 1.1) içinde belirtilen bir sabit UDP bağlaması ve varsayılan bir adres vardır.</span><span class="sxs-lookup"><span data-stu-id="4559d-103">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="4559d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4559d-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4559d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4559d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4559d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4559d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4559d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4559d-107">Attributes</span></span>  
  
|<span data-ttu-id="4559d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4559d-108">Attribute</span></span>|<span data-ttu-id="4559d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4559d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4559d-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="4559d-110">discoveryMode</span></span>|<span data-ttu-id="4559d-111">Bulma protokolünün modunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4559d-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="4559d-112">Geçerli değerler şunlardır "geçici" ve "yönetilen".</span><span class="sxs-lookup"><span data-stu-id="4559d-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="4559d-113">Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır.</span><span class="sxs-lookup"><span data-stu-id="4559d-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="4559d-114">Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4559d-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="4559d-115">Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="4559d-115">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="4559d-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="4559d-116">discoveryVersion</span></span>|<span data-ttu-id="4559d-117">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4559d-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="4559d-118">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="4559d-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="4559d-119">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="4559d-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="4559d-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="4559d-120">maxResponseDelay</span></span>|<span data-ttu-id="4559d-121">Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="4559d-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="4559d-122">Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir.</span><span class="sxs-lookup"><span data-stu-id="4559d-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="4559d-123">Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4559d-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="4559d-124">Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır.</span><span class="sxs-lookup"><span data-stu-id="4559d-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="4559d-125">Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="4559d-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="4559d-126">Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir.</span><span class="sxs-lookup"><span data-stu-id="4559d-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="4559d-127">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="4559d-127">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="4559d-128">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="4559d-128">multicastAddress</span></span>|<span data-ttu-id="4559d-129">Bulma iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="4559d-129">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="4559d-130">Varsayılan değer, protokol belirtimine uyumlu olan çok noktaya yayın adresidir.</span><span class="sxs-lookup"><span data-stu-id="4559d-130">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="4559d-131">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4559d-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="4559d-132">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4559d-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4559d-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4559d-133">Child Elements</span></span>  
  
|<span data-ttu-id="4559d-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="4559d-134">Element</span></span>|<span data-ttu-id="4559d-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4559d-135">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="4559d-136">UDP uç noktası için UDP aktarımını yapılandırmanıza izin veren ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4559d-136">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4559d-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4559d-137">Parent Elements</span></span>  
  
|<span data-ttu-id="4559d-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="4559d-138">Element</span></span>|<span data-ttu-id="4559d-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4559d-139">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="4559d-140">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4559d-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4559d-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="4559d-141">Example</span></span>  

 <span data-ttu-id="4559d-142">Aşağıdaki örnek, bir UDP çok noktaya yayın aktarımı üzerinden bulma iletilerini dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="4559d-142">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4559d-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4559d-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
