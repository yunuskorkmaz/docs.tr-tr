---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: d1a3371872f5587a682b8242c29b71808508ca3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704062"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="ecbf0-101">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="ecbf0-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="ecbf0-102">Bu yapılandırma öğesi, bir sabit keşif sözleşmesiyle standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="ecbf0-103">Hizmet yapılandırmasında eklendiğinde bulma iletileri dinlemek nereye belirtir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="ecbf0-104">İstemci yapılandırmasına eklendiğinde bulma sorguları gönderileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="ecbf0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ecbf0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ecbf0-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ecbf0-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbf0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecbf0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecbf0-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ecbf0-108">Attributes and elements</span></span>

<span data-ttu-id="ecbf0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecbf0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ecbf0-110">Attributes</span></span>

| <span data-ttu-id="ecbf0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ecbf0-111">Attribute</span></span>        | <span data-ttu-id="ecbf0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecbf0-112">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="ecbf0-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="ecbf0-113">discoveryMode</span></span>    | <span data-ttu-id="ecbf0-114">Bulma kuralının modu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="ecbf0-115">Geçerli değerler şunlardır: "Geçici" ve "Yönetilen".</span><span class="sxs-lookup"><span data-stu-id="ecbf0-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="ecbf0-116">Yönetilen modda bir bulunabilir hizmet deposu olarak hareket eden bir keşif proxy'si, protokolü kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="ecbf0-117">Anlık mod gerektirir UDP kullanılacak protokolü kullanılabilir hizmetleri bulmak için çok noktaya yayın mekanizması.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="ecbf0-118">Özelliği hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-118">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="ecbf0-119">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="ecbf0-119">discoveryVersion</span></span> | <span data-ttu-id="ecbf0-120">Bir WS bulma protokolünü iki sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="ecbf0-121">Geçerli değerler şunlardır: WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="ecbf0-122">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="ecbf0-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="ecbf0-123">maxResponseDelay</span></span> | <span data-ttu-id="ecbf0-124">Araştırma eşleşme veya eşleşme gidermek gibi belirli iletileri göndermeden önce gecikme Bulma Protokolü için maksimum değeri belirten bir Timespan değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="ecbf0-125">Aynı anda tüm ProbeMatches gönderiliyorsa, ağ storm neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="ecbf0-126">Bunun gerçekleşmesini önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="ecbf0-127">Bu öznitelik tarafından ayarlanan değer için 0 aralığındaki rastgele gecikme var.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="ecbf0-128">Bu öznitelik 0 olarak ayarlanırsa, herhangi bir gecikme olmadan sıkı bir döngüde ProbeMatches iletileri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="ecbf0-129">Aksi takdirde, tüm ProbeMatches ileti göndermek için geçen toplam süre maxResponseDelay aşmayacak şekilde ProbeMatches iletileri rastgele bir gecikme süresi ile gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="ecbf0-130">Bu değer yalnızca hizmetler için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-130">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="ecbf0-131">Standart uç nokta yapılandırmasını adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ecbf0-132">Adı kullanılıyor `endpointConfiguration` özniteliği bir standart uç noktası yapılandırmasına bağlamak için hizmet uç noktası.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="ecbf0-133">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ecbf0-133">Child elements</span></span>

<span data-ttu-id="ecbf0-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecbf0-135">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ecbf0-135">Parent elements</span></span>

| <span data-ttu-id="ecbf0-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecbf0-136">Element</span></span> | <span data-ttu-id="ecbf0-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecbf0-137">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="ecbf0-138">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ecbf0-138">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="ecbf0-139">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="ecbf0-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecbf0-140">Example</span></span>

<span data-ttu-id="ecbf0-141">Aşağıdaki örnek, bir ağ çok noktaya yayın eş bulma iletileri dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-141">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="ecbf0-142">Örneğin, WS-bulma açıkça belirtir Nisan 2005 sürümü.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-142">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="ecbf0-143">Standart uç nokta yapılandırması hizmete göre tanımlanır ve hizmet arasında paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-143">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="ecbf0-144">Başka bir hizmete sahip aynı bulma uç noktası istiyorsanız, aynı yapılandırmayı hizmetin bölümüne eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-144">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecbf0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecbf0-145">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
