---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152007"
---
# \<sendMessageChannelCache>
<span data-ttu-id="12c56-101">Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="12c56-101">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**  
  
## <a name="syntax"></a><span data-ttu-id="12c56-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12c56-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12c56-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c56-103">Attributes and Elements</span></span>  
 <span data-ttu-id="12c56-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12c56-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12c56-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12c56-105">Attributes</span></span>  
  
|<span data-ttu-id="12c56-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12c56-106">Attribute</span></span>|<span data-ttu-id="12c56-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c56-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12c56-108">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="12c56-108">allowUnsafeCaching</span></span>|<span data-ttu-id="12c56-109">Önbelleğe alma'yı açmak belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="12c56-109">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="12c56-110">İş akışı hizmetinizi özel bağlamaları veya özel davranışlar varsa, önbelleğe alma güvensiz olabilir ve bu nedenle varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="12c56-110">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="12c56-111">Ancak, bu özelliği **true**olarak ayarlamak için önbelleğe alma özelliğini etkinleştirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="12c56-111">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12c56-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c56-112">Child Elements</span></span>  
  
|<span data-ttu-id="12c56-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="12c56-113">Element</span></span>|<span data-ttu-id="12c56-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c56-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelSettings>](channelsettings.md)|<span data-ttu-id="12c56-115">Kanal önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="12c56-115">Specifies the settings of the channel cache.</span></span>|  
|[\<factorySettings>](factorysettings.md)|<span data-ttu-id="12c56-116">Kanal üreteci önbellek ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="12c56-116">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12c56-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c56-117">Parent Elements</span></span>  
  
|<span data-ttu-id="12c56-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="12c56-118">Element</span></span>|<span data-ttu-id="12c56-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c56-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12c56-120">\<behavior>durumunu\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="12c56-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="12c56-121">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="12c56-121">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12c56-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12c56-122">Remarks</span></span>  
 <span data-ttu-id="12c56-123">Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="12c56-123">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="12c56-124">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="12c56-124">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="12c56-125">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="12c56-125">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="12c56-126">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12c56-126">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="12c56-127">Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="12c56-127">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="12c56-128">Kanal fabrikası ve kanal önbelleği için varsayılan önbellek paylaşım düzeylerini ve önbellek ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [gönderme etkinlikleri Için önbellek paylaşımı düzeylerini değiştirme](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="12c56-128">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12c56-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="12c56-129">Example</span></span>  
 <span data-ttu-id="12c56-130">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12c56-130">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="12c56-131">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12c56-131">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="12c56-132">Aşağıdaki örnek, `MyChannelCacheBehavior` özel fabrika önbelleği ve kanal önbelleği ayarları ile hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12c56-132">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="12c56-133">Bu hizmet davranışı, özelliği aracılığıyla hizmete eklenir `behaviorConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="12c56-133">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12c56-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12c56-134">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="12c56-135">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="12c56-135">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
