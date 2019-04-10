---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 54a9833f56927568af711a103bd3831b767711e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210002"
---
# <a name="servicediscovery"></a><span data-ttu-id="8dae5-101">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="8dae5-101">\<serviceDiscovery></span></span>
<span data-ttu-id="8dae5-102">Hizmet bitiş noktası bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dae5-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="8dae5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8dae5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8dae5-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8dae5-104">\<behaviors></span></span>  
<span data-ttu-id="8dae5-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8dae5-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8dae5-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8dae5-106">\<behavior></span></span>  
<span data-ttu-id="8dae5-107">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="8dae5-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dae5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dae5-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dae5-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dae5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8dae5-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8dae5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dae5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8dae5-111">Attributes</span></span>  
 <span data-ttu-id="8dae5-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="8dae5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8dae5-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dae5-113">Child Elements</span></span>  
  
|<span data-ttu-id="8dae5-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="8dae5-114">Element</span></span>|<span data-ttu-id="8dae5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dae5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dae5-116">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="8dae5-116">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="8dae5-117">Duyuru uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="8dae5-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="8dae5-118">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="8dae5-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="8dae5-119">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="8dae5-119">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="8dae5-120">Bulma uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="8dae5-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="8dae5-121">Bulma iletileri dinlemek olan uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="8dae5-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dae5-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dae5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8dae5-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="8dae5-123">Element</span></span>|<span data-ttu-id="8dae5-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dae5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dae5-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8dae5-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8dae5-126">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dae5-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dae5-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dae5-127">Remarks</span></span>  
 <span data-ttu-id="8dae5-128">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi tüm hizmet uç noktalarına bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8dae5-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="8dae5-129">Bu uç noktaları bulma özelliklerini kullanarak daha fazla yapılandırabilirsiniz [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) veya [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8dae5-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="8dae5-130">Kullanma [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) duyuruları hizmet duyuruları (/ Hello çevrimiçi ve çevrimdışı/Bye) göndermek için kullanılması için uç nokta yapılandırması belirterek yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="8dae5-130">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="8dae5-131">Kullanım [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) bulma iletileri dinlemek için uç noktada el ile belirtmek için bölüm.</span><span class="sxs-lookup"><span data-stu-id="8dae5-131">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dae5-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="8dae5-132">Example</span></span>  
 <span data-ttu-id="8dae5-133">Aşağıdaki yapılandırma örnek belirten CalculatorService bulunabilir, için ve isteğe bağlı olarak kullanılacak duyuru uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dae5-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="8dae5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dae5-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
