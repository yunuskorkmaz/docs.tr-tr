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
# <a name="sendmessagechannelcache"></a>\<sendMessageChannelCache>
İleti gönder etkinliklerini kullanarak hizmet uç noktalarına ileti gönderen iş akışları için önbellek paylaşım düzeylerinin, kanal fabrika önbelleğinin ayarlarını ve kanal önbelleğinin ayarlarını özelleştirmeyi sağlayan bir hizmet davranışı.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowUnsafeCaching|Önbelleğe alma'yı açmak belirten bir Boolean değeri. İş akışı hizmetinizi özel bağlamaları veya özel davranışlar varsa, önbelleğe alma güvensiz olabilir ve bu nedenle varsayılan olarak devre dışıdır. Ancak, bu özelliği **doğru**ayarlamak önbelleğe açmak istiyorsanız.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kanalAyarlar>](channelsettings.md)|Kanal önbellek ayarlarını belirtir.|  
|[\<factoryAyarlar>](factorysettings.md)|Kanal üreteci önbellek ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<hizmet davranış \<>Davranışlar>](behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu hizmet davranışını ileti göndermek için hizmet bitiş noktası iş akışları için yöneliktir. Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.  
  
 Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>, tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> etkinlikler ileti sistemi tüm iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi). Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir. Önbelleğe alma herhangi bir gönderme etkinlik bitiş noktaları yapılandırmasında tanımlandığı sahip akışınızın için varsayılan olarak devre dışıdır.  
  
 Kanal fabrikası ve kanal önbelleği için varsayılan önbellek paylaşım düzeyleri ve önbellek ayarlarının nasıl değiştirilebildiği hakkında daha fazla bilgi için, [Etkinlikler Gönder için Önbellek Paylaşım Düzeylerini Değiştirme](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)bölümüne bakın.  
  
## <a name="example"></a>Örnek  
 Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz. Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin. Aşağıdaki örnek, özel fabrika önbelleği `MyChannelCacheBehavior` ve kanal önbelleği ayarlarıyla hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir. Bu hizmet davranışı öznitelik aracılığıyla `behaviorConfiguration` hizmete eklenir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
