---
description: 'Hakkında daha fazla bilgi edinin: <udpDiscoveryEndpoint>'
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 9863b4bc768b9c1cca933d001f0db596ce502fa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749239"
---
# \<udpDiscoveryEndpoint>

<span data-ttu-id="3eb9e-102">Bu yapılandırma öğesi, bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="3eb9e-103">Bu uç nokta, sabit bir sözleşmeye sahiptir ve iki WS-Discovery protokol sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="3eb9e-104">Ayrıca, WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery V 1.1) içinde belirtilen şekilde, sabit bir UDP bağlaması ve varsayılan bir adres vardır.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="3eb9e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3eb9e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eb9e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3eb9e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3eb9e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eb9e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3eb9e-108">Attributes</span></span>  
  
|<span data-ttu-id="3eb9e-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3eb9e-109">Attribute</span></span>|<span data-ttu-id="3eb9e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eb9e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3eb9e-111">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="3eb9e-111">discoveryMode</span></span>|<span data-ttu-id="3eb9e-112">Bulma protokolünün modunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-112">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="3eb9e-113">Geçerli değerler şunlardır "geçici" ve "yönetilen".</span><span class="sxs-lookup"><span data-stu-id="3eb9e-113">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="3eb9e-114">Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-114">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="3eb9e-115">Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-115">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="3eb9e-116">Bu değer türünde <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-116">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="3eb9e-117">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="3eb9e-117">discoveryVersion</span></span>|<span data-ttu-id="3eb9e-118">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-118">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="3eb9e-119">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-119">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="3eb9e-120">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-120">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="3eb9e-121">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="3eb9e-121">maxResponseDelay</span></span>|<span data-ttu-id="3eb9e-122">Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-122">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="3eb9e-123">Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-123">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="3eb9e-124">Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-124">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="3eb9e-125">Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-125">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="3eb9e-126">Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-126">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="3eb9e-127">Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-127">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="3eb9e-128">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-128">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="3eb9e-129">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="3eb9e-129">multicastAddress</span></span>|<span data-ttu-id="3eb9e-130">Bulma iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-130">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="3eb9e-131">Varsayılan değer, protokol belirtimine uyumlu olan çok noktaya yayın adresidir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-131">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="3eb9e-132">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="3eb9e-133">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eb9e-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3eb9e-134">Child Elements</span></span>  
  
|<span data-ttu-id="3eb9e-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="3eb9e-135">Element</span></span>|<span data-ttu-id="3eb9e-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eb9e-136">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="3eb9e-137">UDP uç noktası için UDP aktarımını yapılandırmanıza izin veren ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-137">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3eb9e-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3eb9e-138">Parent Elements</span></span>  
  
|<span data-ttu-id="3eb9e-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="3eb9e-139">Element</span></span>|<span data-ttu-id="3eb9e-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eb9e-140">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="3eb9e-141">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3eb9e-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="3eb9e-142">Example</span></span>  

 <span data-ttu-id="3eb9e-143">Aşağıdaki örnek, bir UDP çok noktaya yayın aktarımı üzerinden bulma iletilerini dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-143">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3eb9e-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eb9e-144">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
