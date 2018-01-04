---
title: '&lt;sendMessageChannelCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a2fe2fbeb82ea4412a85a4503a5ae950639a659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsendmessagechannelcachegt"></a><span data-ttu-id="e0d9a-102">&lt;sendMessageChannelCache&gt;</span><span class="sxs-lookup"><span data-stu-id="e0d9a-102">&lt;sendMessageChannelCache&gt;</span></span>
<span data-ttu-id="e0d9a-103">Paylaşım düzeyleri, kanal fabrikası önbellek ayarlarını ve ileti gönderme Mesajlaşma etkinlikleri kullanarak hizmet uç noktalarına gönderme iş akışları için kanal önbellek ayarlarını önbellek özelleştirmesini sağlar hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-103">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="e0d9a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0d9a-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-105">\<behaviors></span></span>  
<span data-ttu-id="e0d9a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e0d9a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-107">\<behavior></span></span>  
<span data-ttu-id="e0d9a-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-108">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d9a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0d9a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0d9a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d9a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e0d9a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0d9a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0d9a-112">Attributes</span></span>  
  
|<span data-ttu-id="e0d9a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0d9a-113">Attribute</span></span>|<span data-ttu-id="e0d9a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d9a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0d9a-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="e0d9a-115">allowUnsafeCaching</span></span>|<span data-ttu-id="e0d9a-116">Önbelleğe alma'yı açmak belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="e0d9a-117">İş akışı hizmetinizi özel bağlamaları veya özel davranışlar varsa, önbelleğe alma güvensiz olabilir ve bu nedenle varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="e0d9a-118">Etkinleştirmek istiyorsanız, ancak, önbelleğe alma üzerinde bu özelliği ayarlamak **doğru**.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0d9a-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d9a-119">Child Elements</span></span>  
  
|<span data-ttu-id="e0d9a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0d9a-120">Element</span></span>|<span data-ttu-id="e0d9a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d9a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0d9a-122">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-122">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="e0d9a-123">Kanal önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="e0d9a-124">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-124">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="e0d9a-125">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0d9a-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d9a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e0d9a-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0d9a-127">Element</span></span>|<span data-ttu-id="e0d9a-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d9a-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0d9a-129">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e0d9a-129">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e0d9a-130">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0d9a-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0d9a-131">Remarks</span></span>  
 <span data-ttu-id="e0d9a-132">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="e0d9a-133">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="e0d9a-134">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="e0d9a-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="e0d9a-135">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="e0d9a-136">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="e0d9a-137">düzeyleri paylaşımı varsayılan önbelleği değiştirmek ve kanal fabrikası ve kanal önbellek ayarlarını önbelleğe bkz [Gönder etkinlikler için önbellek paylaşımı düzeylerini değiştirme](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="e0d9a-137"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0d9a-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0d9a-138">Example</span></span>  
 <span data-ttu-id="e0d9a-139">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="e0d9a-140">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="e0d9a-141">Aşağıdaki örnek içeren bir yapılandırma dosyası içeriğini gösterir **MyChannelCacheBehavior** hizmet davranışı özel fabrika önbellek ve kanal önbellek ayarlarına.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-141">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="e0d9a-142">Bu hizmet davranışı hizmet aracılığıyla eklenen **behaviorConfiguarion** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-142">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0d9a-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d9a-143">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 [<span data-ttu-id="e0d9a-144">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e0d9a-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
