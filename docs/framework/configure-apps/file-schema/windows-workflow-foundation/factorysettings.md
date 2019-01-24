---
title: '&lt;factorySettings&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: bb57378ab692d3ddb0728a7f6c4e5bf039e59d15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637852"
---
# <a name="ltfactorysettingsgt"></a><span data-ttu-id="ba911-102">&lt;factorySettings&gt;</span><span class="sxs-lookup"><span data-stu-id="ba911-102">&lt;factorySettings&gt;</span></span>
<span data-ttu-id="ba911-103">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba911-103">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="ba911-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba911-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba911-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="ba911-105">\<behaviors></span></span>  
<span data-ttu-id="ba911-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ba911-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ba911-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ba911-107">\<behavior></span></span>  
<span data-ttu-id="ba911-108">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="ba911-108">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="ba911-109">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="ba911-109">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba911-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba911-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba911-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba911-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ba911-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba911-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba911-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ba911-113">Attributes</span></span>  
  
|<span data-ttu-id="ba911-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ba911-114">Attribute</span></span>|<span data-ttu-id="ba911-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba911-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba911-116">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="ba911-116">idleTimeout</span></span>|<span data-ttu-id="ba911-117">En fazla kendisi için nesne önbellekte atıldı önce boşta kalacağını zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ba911-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="ba911-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="ba911-118">leaseTimeout</span></span>|<span data-ttu-id="ba911-119">Önbellekten kaldırılır bir nesne sonra zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ba911-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="ba911-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="ba911-120">maxItemsInCache</span></span>|<span data-ttu-id="ba911-121">Bir tamsayı önbellekte olabilir nesneleri sayısı üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba911-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba911-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba911-122">Child Elements</span></span>  
 <span data-ttu-id="ba911-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="ba911-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba911-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba911-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ba911-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba911-125">Element</span></span>|<span data-ttu-id="ba911-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba911-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba911-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="ba911-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="ba911-128">Özelleştirme düzeyleri, kanal üreteci önbellek ayarlarını ve ileti göndermek için hizmet bitiş noktası etkinlikler ileti gönderme kullanarak iş akışları için kanal önbellek ayarlarını paylaşımı önbellek sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="ba911-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba911-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba911-129">Remarks</span></span>  
 <span data-ttu-id="ba911-130">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ba911-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="ba911-131">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ba911-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="ba911-132">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="ba911-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="ba911-133">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba911-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="ba911-134">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ba911-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="ba911-135">Düzeyleri ve kanal fabrikası ve kanal önbellek için önbellek ayarlarını paylaşımı varsayılan önbelleği değiştirmek konusunda daha fazla bilgi için bkz. [etkinlikleri göndermek için önbellek paylaşımı düzeylerini değiştirme](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="ba911-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba911-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba911-136">Example</span></span>  
 <span data-ttu-id="ba911-137">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba911-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="ba911-138">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba911-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="ba911-139">Aşağıdaki örnek, içeren bir yapılandırma dosyası içeriğini gösterir **MyChannelCacheBehavior** özel üreteci önbellek ve kanal önbellek ayarları ile hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="ba911-139">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="ba911-140">Bu hizmet davranışını hizmet aracılığıyla eklenen **behaviorConfiguarion** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ba911-140">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ba911-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba911-141">See also</span></span>
- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="ba911-142">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ba911-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
