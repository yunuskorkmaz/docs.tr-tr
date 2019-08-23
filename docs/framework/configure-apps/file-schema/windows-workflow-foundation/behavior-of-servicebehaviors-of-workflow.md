---
title: <behavior><serviceBehaviors> iş akışının
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 91883c42aa7bc0aa8fa0c63c3c45184ba69225d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946074"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<iş akışının \<ServiceBehavior > davranış >
**Behavior** öğesi, bir hizmetin davranışına yönelik ayarların bir koleksiyonunu içerir. Her davranışın **adına**göre dizini oluşturulur. Hizmetler, [ \<uç nokta >](../wcf/endpoint-element.md) öğesinin **behaviorConfiguration** özniteliğini kullanarak bu ad aracılığıyla her davranışa bağlanabilir. Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.  
  
\<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
  
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
                                  hostLockRenewalPeriod="TimeSpan" 
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
|name|Davranışın yapılandırma adını içeren benzersiz bir dize. Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bufferReceive >](bufferreceive.md)|Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.|  
|[\<Yönlendirme >](../wcf/routing-of-servicebehavior.md)|Bir hizmetin, kullanarak <xref:System.Activities.Tracking.EtwTrackingParticipant>etw izlemeyi kullanmasına izin veren bir hizmet davranışı.|  
|[\<sendMessageChannelCache >](sendmessagechannelcache.md)|Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.|  
|[\<SqlWorkflowInstanceStore >](sqlworkflowinstancestore.md)|İş akışı hizmeti örnekleri için SQL Server 2005 veya SQL Server <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 2008 veritabanına yönelik kalıcı durum bilgilerini destekleyen özelliği yapılandırmanıza olanak tanıyan bir hizmet davranışı.|  
|[\<workflowIdle >](workflowidle.md)|Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.|  
|[\<workflowInstanceManagement >](workflowinstancemanagement.md)|Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.|  
|[\<workflowUnhandledException >](workflowunhandledexception.md)|Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Servicedavranışlar >](servicebehaviors-of-workflow.md)|Hizmet davranışı öğelerinin koleksiyonu.|
