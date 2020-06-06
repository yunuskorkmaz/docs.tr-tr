---
title: <channelSettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
ms.openlocfilehash: f6a57e2cc1e7c5e114fd38ee3534ab7c4e629b36
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152280"
---
# \<channelSettings>
<span data-ttu-id="ad92c-101">Kanal önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad92c-101">Specifies the settings of the channel cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="ad92c-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad92c-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad92c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad92c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ad92c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad92c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad92c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad92c-105">Attributes</span></span>  
  
|<span data-ttu-id="ad92c-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ad92c-106">Attribute</span></span>|<span data-ttu-id="ad92c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad92c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad92c-108">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="ad92c-108">idleTimeout</span></span>|<span data-ttu-id="ad92c-109">En fazla kendisi için nesne önbellekte atıldı önce boşta kalacağını zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ad92c-109">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="ad92c-110">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="ad92c-110">leaseTimeout</span></span>|<span data-ttu-id="ad92c-111">Bir nesne önbellekten kaldırıldıktan sonra geçen zaman aralığını belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ad92c-111">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="ad92c-112">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="ad92c-112">maxItemsInCache</span></span>|<span data-ttu-id="ad92c-113">Bir tamsayı önbellekte olabilir nesneleri sayısı üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad92c-113">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad92c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad92c-114">Child Elements</span></span>  
 <span data-ttu-id="ad92c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad92c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad92c-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad92c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad92c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad92c-117">Element</span></span>|<span data-ttu-id="ad92c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad92c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="ad92c-119">Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="ad92c-119">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad92c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad92c-120">Remarks</span></span>  
 <span data-ttu-id="ad92c-121">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ad92c-121">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="ad92c-122">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ad92c-122">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="ad92c-123">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="ad92c-123">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="ad92c-124">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ad92c-124">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="ad92c-125">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ad92c-125">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="ad92c-126">Kanal fabrikası ve kanal önbelleği için varsayılan önbellek paylaşım düzeylerini ve önbellek ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [gönderme etkinlikleri Için önbellek paylaşımı düzeylerini değiştirme](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="ad92c-126">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad92c-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad92c-127">Example</span></span>  
 <span data-ttu-id="ad92c-128">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad92c-128">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="ad92c-129">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ad92c-129">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="ad92c-130">Aşağıdaki örnek, `MyChannelCacheBehavior` özel fabrika önbelleği ve kanal önbelleği ayarları ile hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad92c-130">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="ad92c-131">Bu hizmet davranışı, özelliği aracılığıyla hizmete eklenir `behaviorConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ad92c-131">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad92c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad92c-132">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="ad92c-133">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ad92c-133">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
