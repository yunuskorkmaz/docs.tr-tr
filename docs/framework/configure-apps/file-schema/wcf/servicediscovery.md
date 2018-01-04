---
title: '&lt;serviceDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7469f06567ec8dab98592118ed392a680d4fb81a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="aa345-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="aa345-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="aa345-103">Hizmet uç noktaları bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa345-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="aa345-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="aa345-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aa345-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="aa345-105">\<behaviors></span></span>  
<span data-ttu-id="aa345-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="aa345-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="aa345-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="aa345-107">\<behavior></span></span>  
<span data-ttu-id="aa345-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="aa345-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa345-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa345-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa345-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa345-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aa345-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa345-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa345-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa345-112">Attributes</span></span>  
 <span data-ttu-id="aa345-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa345-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aa345-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa345-114">Child Elements</span></span>  
  
|<span data-ttu-id="aa345-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa345-115">Element</span></span>|<span data-ttu-id="aa345-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa345-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa345-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="aa345-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="aa345-118">Duyuru uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="aa345-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="aa345-119">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa345-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="aa345-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="aa345-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="aa345-121">Bulma uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="aa345-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="aa345-122">Uç noktalarını bulma iletiler için dinleme yapılacak belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa345-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa345-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa345-123">Parent Elements</span></span>  
  
|<span data-ttu-id="aa345-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa345-124">Element</span></span>|<span data-ttu-id="aa345-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa345-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa345-126">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="aa345-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="aa345-127">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa345-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa345-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa345-128">Remarks</span></span>  
 <span data-ttu-id="aa345-129">Hizmetin davranışı yapılandırmaya eklenmiş olduğunda, bu yapılandırma öğesi tüm hizmet uç noktalarına bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="aa345-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="aa345-130">Bu tür uç noktalarını bulma özelliklerini kullanarak daha fazla yapılandırabilirsiniz [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) veya [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="aa345-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="aa345-131">Kullanmak [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) duyuruları hizmet duyuruları (çevrimiçi/Hello ve çevrimdışı/Bye) göndermek için kullanılacak için uç nokta yapılandırması belirterek yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="aa345-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="aa345-132">Kullanım [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) uç noktası için bulma iletileri Dinlemenin yapılacağı el ile belirtmek için bölüm.</span><span class="sxs-lookup"><span data-stu-id="aa345-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa345-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa345-133">Example</span></span>  
 <span data-ttu-id="aa345-134">Aşağıdaki yapılandırma örneği belirleyen bulunabilir, CalculatorService ve isteğe bağlı olarak kullanılacak duyuru uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa345-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa345-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa345-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
