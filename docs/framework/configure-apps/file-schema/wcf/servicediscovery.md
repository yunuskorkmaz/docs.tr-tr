---
title: '&lt;serviceDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 73943f5f962a6963809e2c65ce8593f6181559f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587339"
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="9f2e6-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="9f2e6-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="9f2e6-103">Hizmet bitiş noktası bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="9f2e6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f2e6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f2e6-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="9f2e6-105">\<behaviors></span></span>  
<span data-ttu-id="9f2e6-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f2e6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f2e6-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9f2e6-107">\<behavior></span></span>  
<span data-ttu-id="9f2e6-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="9f2e6-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f2e6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f2e6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f2e6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f2e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9f2e6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f2e6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f2e6-112">Attributes</span></span>  
 <span data-ttu-id="9f2e6-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f2e6-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f2e6-114">Child Elements</span></span>  
  
|<span data-ttu-id="9f2e6-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f2e6-115">Element</span></span>|<span data-ttu-id="9f2e6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f2e6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f2e6-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="9f2e6-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="9f2e6-118">Duyuru uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="9f2e6-119">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="9f2e6-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="9f2e6-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="9f2e6-121">Bulma uç noktaları koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="9f2e6-122">Bulma iletileri dinlemek olan uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f2e6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f2e6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9f2e6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f2e6-124">Element</span></span>|<span data-ttu-id="9f2e6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f2e6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f2e6-126">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9f2e6-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9f2e6-127">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f2e6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f2e6-128">Remarks</span></span>  
 <span data-ttu-id="9f2e6-129">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi tüm hizmet uç noktalarına bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="9f2e6-130">Bu uç noktaları bulma özelliklerini kullanarak daha fazla yapılandırabilirsiniz [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) veya [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="9f2e6-131">Kullanma [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) duyuruları hizmet duyuruları (/ Hello çevrimiçi ve çevrimdışı/Bye) göndermek için kullanılması için uç nokta yapılandırması belirterek yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="9f2e6-132">Kullanım [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) bulma iletileri dinlemek için uç noktada el ile belirtmek için bölüm.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f2e6-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f2e6-133">Example</span></span>  
 <span data-ttu-id="9f2e6-134">Aşağıdaki yapılandırma örnek belirten CalculatorService bulunabilir, için ve isteğe bağlı olarak kullanılacak duyuru uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f2e6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-135">See also</span></span>
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
