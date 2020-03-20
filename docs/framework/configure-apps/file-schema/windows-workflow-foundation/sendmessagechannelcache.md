---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152007"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="665ac-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="665ac-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="665ac-102">İleti gönder etkinliklerini kullanarak hizmet uç noktalarına ileti gönderen iş akışları için önbellek paylaşım düzeylerinin, kanal fabrika önbelleğinin ayarlarını ve kanal önbelleğinin ayarlarını özelleştirmeyi sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="665ac-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="665ac-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="665ac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="665ac-104">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="665ac-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="665ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="665ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="665ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="665ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="665ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="665ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="665ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span><span class="sxs-lookup"><span data-stu-id="665ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="665ac-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="665ac-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="665ac-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="665ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="665ac-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="665ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="665ac-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="665ac-112">Attributes</span></span>  
  
|<span data-ttu-id="665ac-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="665ac-113">Attribute</span></span>|<span data-ttu-id="665ac-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="665ac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="665ac-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="665ac-115">allowUnsafeCaching</span></span>|<span data-ttu-id="665ac-116">Önbelleğe alma'yı açmak belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="665ac-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="665ac-117">İş akışı hizmetinizi özel bağlamaları veya özel davranışlar varsa, önbelleğe alma güvensiz olabilir ve bu nedenle varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="665ac-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="665ac-118">Ancak, bu özelliği **doğru**ayarlamak önbelleğe açmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="665ac-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="665ac-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="665ac-119">Child Elements</span></span>  
  
|<span data-ttu-id="665ac-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="665ac-120">Element</span></span>|<span data-ttu-id="665ac-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="665ac-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="665ac-122">\<kanalAyarlar></span><span class="sxs-lookup"><span data-stu-id="665ac-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="665ac-123">Kanal önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="665ac-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="665ac-124">\<factoryAyarlar></span><span class="sxs-lookup"><span data-stu-id="665ac-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="665ac-125">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="665ac-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="665ac-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="665ac-126">Parent Elements</span></span>  
  
|<span data-ttu-id="665ac-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="665ac-127">Element</span></span>|<span data-ttu-id="665ac-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="665ac-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="665ac-129">\<hizmet davranış \<>Davranışlar></span><span class="sxs-lookup"><span data-stu-id="665ac-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="665ac-130">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="665ac-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="665ac-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="665ac-131">Remarks</span></span>  
 <span data-ttu-id="665ac-132">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="665ac-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="665ac-133">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="665ac-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="665ac-134">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="665ac-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="665ac-135">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="665ac-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="665ac-136">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="665ac-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="665ac-137">Kanal fabrikası ve kanal önbelleği için varsayılan önbellek paylaşım düzeyleri ve önbellek ayarlarının nasıl değiştirilebildiği hakkında daha fazla bilgi için, [Etkinlikler Gönder için Önbellek Paylaşım Düzeylerini Değiştirme](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="665ac-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="665ac-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="665ac-138">Example</span></span>  
 <span data-ttu-id="665ac-139">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="665ac-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="665ac-140">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="665ac-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="665ac-141">Aşağıdaki örnek, özel fabrika önbelleği `MyChannelCacheBehavior` ve kanal önbelleği ayarlarıyla hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="665ac-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="665ac-142">Bu hizmet davranışı öznitelik aracılığıyla `behaviorConfiguration` hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="665ac-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="665ac-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="665ac-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="665ac-144">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="665ac-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
