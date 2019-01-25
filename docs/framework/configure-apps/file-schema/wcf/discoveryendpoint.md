---
title: '&lt;DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: b3254a1c3d7fa581b4f7573d693261f5a224515d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524175"
---
# <a name="ltdiscoveryendpointgt"></a><span data-ttu-id="3197e-102">&lt;DiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="3197e-102">&lt;discoveryEndpoint&gt;</span></span>

<span data-ttu-id="3197e-103">Bu yapılandırma öğesi, bir sabit keşif sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3197e-103">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="3197e-104">Hizmet yapılandırmasında eklendiğinde bulma iletileri dinlemek nereye belirtir.</span><span class="sxs-lookup"><span data-stu-id="3197e-104">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="3197e-105">İstemci yapılandırmasına eklendiğinde bulma sorguları gönderileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="3197e-105">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="3197e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3197e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3197e-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3197e-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3197e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3197e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3197e-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3197e-109">Attributes and elements</span></span>

<span data-ttu-id="3197e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3197e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3197e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3197e-111">Attributes</span></span>

| <span data-ttu-id="3197e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3197e-112">Attribute</span></span>        | <span data-ttu-id="3197e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3197e-113">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="3197e-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="3197e-114">discoveryMode</span></span>    | <span data-ttu-id="3197e-115">Bulma kuralının modu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3197e-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="3197e-116">Geçerli değerler şunlardır: "Geçici" ve "Yönetilen".</span><span class="sxs-lookup"><span data-stu-id="3197e-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="3197e-117">Yönetilen modda bir bulunabilir hizmet deposu olarak hareket eden bir keşif proxy'si, protokolü kullanır.</span><span class="sxs-lookup"><span data-stu-id="3197e-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="3197e-118">Anlık mod gerektirir UDP kullanılacak protokolü kullanılabilir hizmetleri bulmak için çok noktaya yayın mekanizması.</span><span class="sxs-lookup"><span data-stu-id="3197e-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="3197e-119">Özelliği hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3197e-119">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="3197e-120">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="3197e-120">discoveryVersion</span></span> | <span data-ttu-id="3197e-121">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3197e-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="3197e-122">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="3197e-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="3197e-123">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="3197e-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="3197e-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="3197e-124">maxResponseDelay</span></span> | <span data-ttu-id="3197e-125">Araştırma eşleşme veya eşleşme gidermek gibi belirli iletileri göndermeden önce gecikme Bulma Protokolü için maksimum değeri belirten bir Timespan değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="3197e-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="3197e-126">Aynı anda tüm ProbeMatches gönderiliyorsa, ağ storm neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3197e-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="3197e-127">Bunun gerçekleşmesini önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3197e-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="3197e-128">Bu öznitelik tarafından ayarlanan değer için 0 aralığındaki rastgele gecikme var.</span><span class="sxs-lookup"><span data-stu-id="3197e-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="3197e-129">Bu öznitelik 0 olarak ayarlanırsa, herhangi bir gecikme olmadan sıkı bir döngüde ProbeMatches iletileri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3197e-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="3197e-130">Aksi takdirde, tüm ProbeMatches ileti göndermek için geçen toplam süre maxResponseDelay aşmayacak şekilde ProbeMatches iletileri rastgele bir gecikme süresi ile gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3197e-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="3197e-131">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3197e-131">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="3197e-132">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="3197e-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="3197e-133">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="3197e-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="3197e-134">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3197e-134">Child elements</span></span>

<span data-ttu-id="3197e-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="3197e-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3197e-136">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3197e-136">Parent elements</span></span>

| <span data-ttu-id="3197e-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="3197e-137">Element</span></span> | <span data-ttu-id="3197e-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3197e-138">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="3197e-139">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3197e-139">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="3197e-140">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="3197e-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="3197e-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="3197e-141">Example</span></span>

<span data-ttu-id="3197e-142">Aşağıdaki örnek, bir ağ çok noktaya yayın eş bulma iletileri dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="3197e-142">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="3197e-143">Örneğin, WS-bulma açıkça belirtir Nisan 2005 sürümü.</span><span class="sxs-lookup"><span data-stu-id="3197e-143">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="3197e-144">Standart uç nokta yapılandırması hizmete göre tanımlanır ve hizmet arasında paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="3197e-144">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="3197e-145">Başka bir hizmete sahip aynı bulma uç noktası istiyorsanız, aynı yapılandırmayı hizmetin bölümüne eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3197e-145">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3197e-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3197e-146">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
