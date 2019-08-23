---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936270"
---
# <a name="servicediscovery"></a><span data-ttu-id="042e8-101">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="042e8-101">\<serviceDiscovery></span></span>
<span data-ttu-id="042e8-102">Hizmet uç noktalarının bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="042e8-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="042e8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="042e8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="042e8-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="042e8-104">\<behaviors></span></span>  
<span data-ttu-id="042e8-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="042e8-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="042e8-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="042e8-106">\<behavior></span></span>  
<span data-ttu-id="042e8-107">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="042e8-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042e8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="042e8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="042e8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="042e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="042e8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="042e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="042e8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="042e8-111">Attributes</span></span>  
 <span data-ttu-id="042e8-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="042e8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="042e8-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="042e8-113">Child Elements</span></span>  
  
|<span data-ttu-id="042e8-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="042e8-114">Element</span></span>|<span data-ttu-id="042e8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="042e8-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="042e8-116">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="042e8-116">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="042e8-117">Duyuru uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="042e8-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="042e8-118">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="042e8-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="042e8-119">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="042e8-119">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="042e8-120">Bulma uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="042e8-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="042e8-121">Bulma iletilerinin dinleyeceği uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="042e8-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="042e8-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="042e8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="042e8-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="042e8-123">Element</span></span>|<span data-ttu-id="042e8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="042e8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="042e8-125">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="042e8-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="042e8-126">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="042e8-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="042e8-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="042e8-127">Remarks</span></span>  
 <span data-ttu-id="042e8-128">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bu hizmetin tüm uç noktalarını bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="042e8-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="042e8-129">Bu uç noktaların bulma özelliklerini, [ \<DiscoveryEndpoint >](discoveryendpoint.md) veya [ \<AnnouncementEndpoint >](announcementendpoint.md) alt öğelerini kullanarak daha ayrıntılı bir şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="042e8-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="042e8-130">Hizmet duyuruları göndermek için kullanılacak uç nokta yapılandırmasını belirterek duyuruları yapılandırmak için [ AnnouncementEndpoint>bölümünükullanın(çevrimiçi/Merhabaveçevrimdışı/bye).\<](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="042e8-130">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="042e8-131">Bulma iletilerinin dinleyeceği uç noktayı el ile belirtmek için [ DiscoveryEndpoint>bölümünükullanın.\<](discoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="042e8-131">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="042e8-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="042e8-132">Example</span></span>  
 <span data-ttu-id="042e8-133">Aşağıdaki yapılandırma örneği, Hesaplatorservice 'in keşfedilecek olduğunu belirtir ve isteğe bağlı olarak kullanılacak duyuru uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="042e8-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="042e8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="042e8-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
