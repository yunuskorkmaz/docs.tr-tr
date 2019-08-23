---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: fed7fe192e7bc5cb37347d2eae42f75bbf1b7dee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946322"
---
# <a name="factorysettings"></a><span data-ttu-id="a77e8-101">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="a77e8-101">\<factorySettings></span></span>
<span data-ttu-id="a77e8-102">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a77e8-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="a77e8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a77e8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a77e8-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a77e8-104">\<behaviors></span></span>  
<span data-ttu-id="a77e8-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a77e8-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a77e8-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="a77e8-106">\<behavior></span></span>  
<span data-ttu-id="a77e8-107">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="a77e8-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="a77e8-108">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="a77e8-108">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77e8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a77e8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a77e8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a77e8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a77e8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a77e8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a77e8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a77e8-112">Attributes</span></span>  
  
|<span data-ttu-id="a77e8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a77e8-113">Attribute</span></span>|<span data-ttu-id="a77e8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a77e8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a77e8-115">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a77e8-115">idleTimeout</span></span>|<span data-ttu-id="a77e8-116">En fazla kendisi için nesne önbellekte atıldı önce boşta kalacağını zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="a77e8-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="a77e8-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="a77e8-117">leaseTimeout</span></span>|<span data-ttu-id="a77e8-118">Bir nesne önbellekten kaldırıldıktan sonra geçen zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="a77e8-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="a77e8-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="a77e8-119">maxItemsInCache</span></span>|<span data-ttu-id="a77e8-120">Bir tamsayı önbellekte olabilir nesneleri sayısı üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a77e8-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a77e8-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a77e8-121">Child Elements</span></span>  
 <span data-ttu-id="a77e8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="a77e8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a77e8-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a77e8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a77e8-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a77e8-124">Element</span></span>|<span data-ttu-id="a77e8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a77e8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a77e8-126">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="a77e8-126">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="a77e8-127">Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a77e8-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a77e8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a77e8-128">Remarks</span></span>  
 <span data-ttu-id="a77e8-129">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a77e8-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="a77e8-130">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a77e8-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="a77e8-131">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="a77e8-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="a77e8-132">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a77e8-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="a77e8-133">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="a77e8-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="a77e8-134">Kanal fabrikası ve kanal önbelleği için varsayılan önbellek paylaşım düzeylerini ve önbellek ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [gönderme etkinlikleri Için önbellek paylaşımı düzeylerini değiştirme](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="a77e8-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a77e8-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="a77e8-135">Example</span></span>  
 <span data-ttu-id="a77e8-136">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a77e8-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="a77e8-137">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a77e8-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="a77e8-138">Aşağıdaki örnek, özel fabrika önbelleği ve kanal önbelleği ayarları ile `MyChannelCacheBehavior` hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a77e8-138">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="a77e8-139">Bu hizmet davranışı, `behaviorConfiguration` özelliği aracılığıyla hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="a77e8-139">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a77e8-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a77e8-140">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="a77e8-141">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a77e8-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
