---
title: '&lt;DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6a352fbfced08001f76dceaff283d6bca25f56f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747404"
---
# <a name="ltdiscoveryendpointgt"></a><span data-ttu-id="651e8-102">&lt;DiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="651e8-102">&lt;discoveryEndpoint&gt;</span></span>

<span data-ttu-id="651e8-103">Bu yapılandırma öğesi, standart bir uç nokta sabit bulma sözleşme ile tanımlar.</span><span class="sxs-lookup"><span data-stu-id="651e8-103">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="651e8-104">Hizmet yapılandırmasında eklendiğinde, bulma iletilerini dinlemek konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="651e8-104">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="651e8-105">İstemci yapılandırmasında eklendiğinde bulma sorguları göndermek konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="651e8-105">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="651e8-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="651e8-106">\<system.serviceModel></span></span>  
<span data-ttu-id="651e8-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="651e8-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="651e8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="651e8-108">Syntax</span></span>

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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="651e8-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="651e8-109">Attributes and elements</span></span>

<span data-ttu-id="651e8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="651e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="651e8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="651e8-111">Attributes</span></span>

| <span data-ttu-id="651e8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="651e8-112">Attribute</span></span>        | <span data-ttu-id="651e8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="651e8-113">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="651e8-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="651e8-114">discoveryMode</span></span>    | <span data-ttu-id="651e8-115">Keşif Protokolü modu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="651e8-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="651e8-116">Geçerli değerler "Geçici" ve "Yönetilen" dir.</span><span class="sxs-lookup"><span data-stu-id="651e8-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="651e8-117">Yönetilen modunda bulunabilirlik Hizmetleri depo olarak davranan bir keşif proxy'si, protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="651e8-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="651e8-118">Adhoc modu, UDP kullanılacak protokolü gerektirir kullanılabilir hizmetler bulmak için çok noktaya yayın mekanizması.</span><span class="sxs-lookup"><span data-stu-id="651e8-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="651e8-119">Özelliği hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="651e8-119">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="651e8-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="651e8-120">discoveryVersion</span></span> | <span data-ttu-id="651e8-121">WS bulma protokolünü iki sürümü birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="651e8-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="651e8-122">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005 ' dir.</span><span class="sxs-lookup"><span data-stu-id="651e8-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="651e8-123">Bu değer türünde <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="651e8-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="651e8-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="651e8-124">maxResponseDelay</span></span> | <span data-ttu-id="651e8-125">Keşif Protokolü gecikme için maksimum değeri belirten bir Timespan değerine araştırma eşleşme veya eşleşme çözmek gibi belirli iletileri göndermeden önce bekler.</span><span class="sxs-lookup"><span data-stu-id="651e8-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="651e8-126">Aynı anda tüm ProbeMatches gönderirse ağ storm neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="651e8-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="651e8-127">Bu oluşmasını önlemek için her ProbeMatch arasında rastgele bir gecikme ile ProbeMatches gönderilir.</span><span class="sxs-lookup"><span data-stu-id="651e8-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="651e8-128">Bu öznitelik tarafından ayarlanan değer için 0 aralığı rastgele gecikmeyi kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="651e8-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="651e8-129">Bu öznitelik 0 olarak ayarlanırsa, ProbeMatches iletileri sıkı bir döngü herhangi bir gecikme olmadan gönderilir.</span><span class="sxs-lookup"><span data-stu-id="651e8-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="651e8-130">Aksi takdirde, tüm ProbeMatches iletileri göndermek için geçen toplam süre maxResponseDelay aşmadığından emin ProbeMatches iletileri bazı rastgele gecikme ile gönderilir.</span><span class="sxs-lookup"><span data-stu-id="651e8-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="651e8-131">Bu değer yalnızca Hizmetleri için geçerlidir, istemciler tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="651e8-131">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="651e8-132">Standart uç noktasının yapılandırma adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="651e8-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="651e8-133">Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.</span><span class="sxs-lookup"><span data-stu-id="651e8-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="651e8-134">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="651e8-134">Child elements</span></span>

<span data-ttu-id="651e8-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="651e8-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="651e8-136">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="651e8-136">Parent elements</span></span>

| <span data-ttu-id="651e8-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="651e8-137">Element</span></span> | <span data-ttu-id="651e8-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="651e8-138">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="651e8-139">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="651e8-139">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="651e8-140">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="651e8-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="651e8-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="651e8-141">Example</span></span>

<span data-ttu-id="651e8-142">Aşağıdaki örnek, bulma iletileri eş net çok noktaya yayın aktarım üzerinde dinleyen bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="651e8-142">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="651e8-143">WS-bulma örnek açıkça belirtir Nisan 2005 sürümü.</span><span class="sxs-lookup"><span data-stu-id="651e8-143">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="651e8-144">Standart uç nokta yapılandırması her hizmeti tanımlanır ve hizmet arasında paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="651e8-144">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="651e8-145">Başka bir hizmet aynı bulma uç nokta içerecek şekilde almak istiyorsanız, aynı yapılandırmayı hizmetin bölümüne eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="651e8-145">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="651e8-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="651e8-146">See also</span></span>

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
