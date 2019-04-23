---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: 60847f423c61b9e7f49a4a7594c965fb75354714
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140185"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="b0c4e-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="b0c4e-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="b0c4e-102">Özelleştirme düzeyleri, kanal üreteci önbellek ayarlarını ve ileti göndermek için hizmet bitiş noktası etkinlikler ileti gönderme kullanarak iş akışları için kanal önbellek ayarlarını paylaşımı önbellek sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="b0c4e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b0c4e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0c4e-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="b0c4e-104">\<behaviors></span></span>  
<span data-ttu-id="b0c4e-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b0c4e-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="b0c4e-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b0c4e-106">\<behavior></span></span>  
<span data-ttu-id="b0c4e-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="b0c4e-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0c4e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0c4e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0c4e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0c4e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b0c4e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0c4e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0c4e-111">Attributes</span></span>  
  
|<span data-ttu-id="b0c4e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0c4e-112">Attribute</span></span>|<span data-ttu-id="b0c4e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0c4e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0c4e-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="b0c4e-114">allowUnsafeCaching</span></span>|<span data-ttu-id="b0c4e-115">Önbelleğe alma'yı açmak belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="b0c4e-116">İş akışı hizmetinizi özel bağlamaları veya özel davranışlar varsa, önbelleğe alma güvensiz olabilir ve bu nedenle varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="b0c4e-117">Etkinleştirmek istiyorsanız, ancak önbelleğe alma üzerinde bu özelliği ayarlamak **true**.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0c4e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0c4e-118">Child Elements</span></span>  
  
|<span data-ttu-id="b0c4e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0c4e-119">Element</span></span>|<span data-ttu-id="b0c4e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0c4e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0c4e-121">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="b0c4e-121">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="b0c4e-122">Kanal önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="b0c4e-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="b0c4e-123">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="b0c4e-124">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0c4e-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0c4e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b0c4e-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0c4e-126">Element</span></span>|<span data-ttu-id="b0c4e-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0c4e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0c4e-128">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b0c4e-128">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b0c4e-129">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0c4e-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0c4e-130">Remarks</span></span>  
 <span data-ttu-id="b0c4e-131">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="b0c4e-132">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="b0c4e-133">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="b0c4e-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="b0c4e-134">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="b0c4e-135">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="b0c4e-136">Düzeyleri ve kanal fabrikası ve kanal önbellek için önbellek ayarlarını paylaşımı varsayılan önbelleği değiştirmek konusunda daha fazla bilgi için bkz. [etkinlikleri göndermek için önbellek paylaşımı düzeylerini değiştirme](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="b0c4e-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c4e-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0c4e-137">Example</span></span>  
 <span data-ttu-id="b0c4e-138">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="b0c4e-139">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="b0c4e-140">Aşağıdaki örnek, içeren bir yapılandırma dosyası içeriğini gösterir **MyChannelCacheBehavior** özel üreteci önbellek ve kanal önbellek ayarları ile hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-140">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="b0c4e-141">Bu hizmet davranışını hizmet aracılığıyla eklenen **behaviorConfiguarion** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-141">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0c4e-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0c4e-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="b0c4e-143">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b0c4e-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
