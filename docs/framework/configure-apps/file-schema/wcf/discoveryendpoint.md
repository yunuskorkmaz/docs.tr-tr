---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855399"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="a6d6f-101">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="a6d6f-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="a6d6f-102">Bu yapılandırma öğesi, sabit bir bulma sözleşmesiyle standart uç noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="a6d6f-103">Hizmet yapılandırmasına eklendiğinde, bulma iletilerinin nerede dinleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="a6d6f-104">İstemci yapılandırmasına eklendiğinde, bulma sorgularının nereye gönderileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="a6d6f-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6d6f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6d6f-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a6d6f-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6d6f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="a6d6f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="a6d6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="a6d6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d6f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6d6f-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6d6f-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a6d6f-110">Attributes and elements</span></span>

<span data-ttu-id="a6d6f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6d6f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6d6f-112">Attributes</span></span>

| <span data-ttu-id="a6d6f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6d6f-113">Attribute</span></span>        | <span data-ttu-id="a6d6f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6d6f-114">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="a6d6f-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="a6d6f-115">discoveryMode</span></span>    | <span data-ttu-id="a6d6f-116">Bulma protokolünün modunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="a6d6f-117">Geçerli değerler şunlardır "geçici" ve "yönetilen".</span><span class="sxs-lookup"><span data-stu-id="a6d6f-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="a6d6f-118">Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="a6d6f-119">Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="a6d6f-120">Özelliği hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-120">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="a6d6f-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="a6d6f-121">discoveryVersion</span></span> | <span data-ttu-id="a6d6f-122">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="a6d6f-123">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="a6d6f-124">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="a6d6f-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="a6d6f-125">maxResponseDelay</span></span> | <span data-ttu-id="a6d6f-126">Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="a6d6f-127">Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="a6d6f-128">Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="a6d6f-129">Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="a6d6f-130">Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="a6d6f-131">Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="a6d6f-132">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-132">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="a6d6f-133">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-133">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a6d6f-134">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-134">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="a6d6f-135">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a6d6f-135">Child elements</span></span>

<span data-ttu-id="a6d6f-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6d6f-137">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a6d6f-137">Parent elements</span></span>

| <span data-ttu-id="a6d6f-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6d6f-138">Element</span></span> | <span data-ttu-id="a6d6f-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6d6f-139">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="a6d6f-140">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a6d6f-140">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="a6d6f-141">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="a6d6f-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6d6f-142">Example</span></span>

<span data-ttu-id="a6d6f-143">Aşağıdaki örnek, bir eş ağ çok noktaya yayın aktarımı üzerinden keşif iletilerini dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-143">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="a6d6f-144">Örnek, WS-Discovery Nisan 2005 sürümünü açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-144">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="a6d6f-145">Standart uç nokta yapılandırması hizmet başına tanımlanır ve hizmet genelinde paylaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-145">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="a6d6f-146">Başka bir hizmet aynı bulma uç noktasına sahip olmak istiyorsanız, bu hizmetin bölümüne aynı yapılandırmanın eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-146">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="a6d6f-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6d6f-147">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
