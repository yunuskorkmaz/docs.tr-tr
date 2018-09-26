---
title: '&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 9b16aad6138d79d3dbff4994250f05d617d54140
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216571"
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a>&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı
**Davranışı** öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar. Her davranış tarafından dizine kendi **adı**. Hizmetleri bağlantısını kullanarak bu adı aracılığıyla her davranışı **behaviorConfiguration** özniteliği [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi. Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.  
  
\<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Davranış yapılandırma adını içeren benzersiz bir dize. Bu öğe için kimlik dizesi görür bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bufferReceive >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışını bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.|  
|[\<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|Özelleştirme düzeyleri, kanal üreteci önbellek ayarlarını ve ileti göndermek için hizmet bitiş noktası etkinlikler ileti gönderme kullanarak iş akışları için kanal önbellek ayarlarını paylaşımı önbellek sağlayan bir hizmet davranışı.|  
|[\<sqlWorkflowInstanceStore >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|Yapılandırmanıza olanak tanıyan bir hizmet davranışını <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> özellik, bir SQL Server 2005 veya SQL Server 2008 veritabanına iş akışı hizmet örneklerine yönelik sürüyor durumu bilgileri destekler.|  
|[\<workflowIdle >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|Boş iş akışı örnekleri zaman kaldırıldı ve kalıcı denetleyen bir hizmet davranışı.|  
|[\<workflowInstanceManagement >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|Nasıl iş akışı örnekleri, Kalıcılık, İşlenmeyen özel durum davranışını ve boşta davranışlarını çalıştırılır denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.|  
|[\<workflowUnhandledException >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Hizmet davranışı öğelerinin koleksiyonu.|
