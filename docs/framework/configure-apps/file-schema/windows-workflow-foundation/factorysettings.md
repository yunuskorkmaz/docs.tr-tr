---
title: '&lt;factorySettings&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: 36f0b82afa8aa8738d2927dc52e1b00e07e72bb1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756468"
---
# <a name="ltfactorysettingsgt"></a><span data-ttu-id="040d2-102">&lt;factorySettings&gt;</span><span class="sxs-lookup"><span data-stu-id="040d2-102">&lt;factorySettings&gt;</span></span>
<span data-ttu-id="040d2-103">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="040d2-103">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="040d2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="040d2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="040d2-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="040d2-105">\<behaviors></span></span>  
<span data-ttu-id="040d2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="040d2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="040d2-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="040d2-107">\<behavior></span></span>  
<span data-ttu-id="040d2-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="040d2-108">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="040d2-109">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="040d2-109">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040d2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="040d2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="040d2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="040d2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="040d2-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="040d2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="040d2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="040d2-113">Attributes</span></span>  
  
|<span data-ttu-id="040d2-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="040d2-114">Attribute</span></span>|<span data-ttu-id="040d2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="040d2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="040d2-116">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="040d2-116">idleTimeout</span></span>|<span data-ttu-id="040d2-117">En fazla kendisi için nesne önbellekte atıldı önce boşta kalacağını zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="040d2-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="040d2-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="040d2-118">leaseTimeout</span></span>|<span data-ttu-id="040d2-119">Nesneyi önbellekten kaldırıldı zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="040d2-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="040d2-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="040d2-120">maxItemsInCache</span></span>|<span data-ttu-id="040d2-121">Bir tamsayı önbellekte olabilir nesneleri sayısı üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="040d2-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="040d2-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="040d2-122">Child Elements</span></span>  
 <span data-ttu-id="040d2-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="040d2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="040d2-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="040d2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="040d2-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="040d2-125">Element</span></span>|<span data-ttu-id="040d2-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="040d2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="040d2-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="040d2-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="040d2-128">Paylaşım düzeyleri, kanal fabrikası önbellek ayarlarını ve ileti gönderme Mesajlaşma etkinlikleri kullanarak hizmet uç noktalarına gönderme iş akışları için kanal önbellek ayarlarını önbellek özelleştirmesini sağlar hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="040d2-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="040d2-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="040d2-129">Remarks</span></span>  
 <span data-ttu-id="040d2-130">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="040d2-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="040d2-131">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="040d2-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="040d2-132">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="040d2-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="040d2-133">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="040d2-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="040d2-134">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="040d2-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="040d2-135">Varsayılan önbellek paylaşımı düzeylerini ve kanal fabrikası ve kanal önbelleği için önbellek ayarlarını değiştirme hakkında daha fazla bilgi için bkz: [Gönder etkinlikler için önbellek paylaşımı düzeylerini değiştirme](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="040d2-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="040d2-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="040d2-136">Example</span></span>  
 <span data-ttu-id="040d2-137">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="040d2-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="040d2-138">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="040d2-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="040d2-139">Aşağıdaki örnek içeren bir yapılandırma dosyası içeriğini gösterir **MyChannelCacheBehavior** hizmet davranışı özel fabrika önbellek ve kanal önbellek ayarlarına.</span><span class="sxs-lookup"><span data-stu-id="040d2-139">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="040d2-140">Bu hizmet davranışı hizmet aracılığıyla eklenen **behaviorConfiguarion** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="040d2-140">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="040d2-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="040d2-141">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>  
 [<span data-ttu-id="040d2-142">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="040d2-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
