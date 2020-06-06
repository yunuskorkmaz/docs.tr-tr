---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855399"
---
# \<discoveryEndpoint>

<span data-ttu-id="a88f9-101">Bu yapılandırma öğesi, sabit bir bulma sözleşmesiyle standart uç noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a88f9-101">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="a88f9-102">Hizmet yapılandırmasına eklendiğinde, bulma iletilerinin nerede dinleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-102">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="a88f9-103">İstemci yapılandırmasına eklendiğinde, bulma sorgularının nereye gönderileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-103">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a88f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a88f9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a88f9-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a88f9-105">Attributes and elements</span></span>

<span data-ttu-id="a88f9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a88f9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a88f9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a88f9-107">Attributes</span></span>

| <span data-ttu-id="a88f9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a88f9-108">Attribute</span></span>        | <span data-ttu-id="a88f9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a88f9-109">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="a88f9-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="a88f9-110">discoveryMode</span></span>    | <span data-ttu-id="a88f9-111">Bulma protokolünün modunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a88f9-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="a88f9-112">Geçerli değerler şunlardır "geçici" ve "yönetilen".</span><span class="sxs-lookup"><span data-stu-id="a88f9-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="a88f9-113">Yönetilen modda protokol, keşfedilebilir hizmetlerin bir deposu görevi gören bir bulma proxy 'Sine dayanır.</span><span class="sxs-lookup"><span data-stu-id="a88f9-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="a88f9-114">Geçici mod, kullanılabilir hizmetleri bulmak için protokolün UDP çok noktaya yayın mekanizmasını kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="a88f9-115">Özelliği hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> ..</span><span class="sxs-lookup"><span data-stu-id="a88f9-115">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="a88f9-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="a88f9-116">discoveryVersion</span></span> | <span data-ttu-id="a88f9-117">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a88f9-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="a88f9-118">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="a88f9-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="a88f9-119">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="a88f9-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="a88f9-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="a88f9-120">maxResponseDelay</span></span> | <span data-ttu-id="a88f9-121">Bulma protokolünün, araştırma eşleşmesi veya eşleşmeyi çözme gibi belirli iletileri göndermeden önce bekleyeceği gecikme süresinin en büyük değerini belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="a88f9-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="a88f9-122">Tüm Probeeşleri aynı anda gönderiliyorsa, bir ağ fırtınası sonuç verebilir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="a88f9-123">Bunun oluşmasını önlemek için, Probeeşleşmelerin her bir ProbeMatch arasında rastgele bir gecikmeyle gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="a88f9-124">Rastgele gecikme, bu öznitelik tarafından ayarlanan değere 0 aralığındadır.</span><span class="sxs-lookup"><span data-stu-id="a88f9-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="a88f9-125">Bu öznitelik 0 olarak ayarlandıysa, Probeeşleşmelerin iletileri herhangi bir gecikme olmadan sıkı bir döngüde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="a88f9-126">Aksi takdirde, Probeeşleşmelerin iletileri, tüm Probeeşleşmelerin iletilerini göndermek için geçen toplam süre maxResponseDelay değerini aşmadığı için bazı rastgele gecikmeyle gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="a88f9-127">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a88f9-127">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="a88f9-128">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a88f9-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a88f9-129">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a88f9-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="a88f9-130">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a88f9-130">Child elements</span></span>

<span data-ttu-id="a88f9-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="a88f9-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a88f9-132">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a88f9-132">Parent elements</span></span>

| <span data-ttu-id="a88f9-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="a88f9-133">Element</span></span> | <span data-ttu-id="a88f9-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a88f9-134">Description</span></span> |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | <span data-ttu-id="a88f9-135">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a88f9-135">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="a88f9-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="a88f9-136">Example</span></span>

<span data-ttu-id="a88f9-137">Aşağıdaki örnek, bir eş ağ çok noktaya yayın aktarımı üzerinden keşif iletilerini dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-137">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="a88f9-138">Örnek, WS-Discovery Nisan 2005 sürümünü açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-138">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="a88f9-139">Standart uç nokta yapılandırması hizmet başına tanımlanır ve hizmet genelinde paylaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="a88f9-139">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="a88f9-140">Başka bir hizmet aynı bulma uç noktasına sahip olmak istiyorsanız, bu hizmetin bölümüne aynı yapılandırmanın eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a88f9-140">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a88f9-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a88f9-141">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
