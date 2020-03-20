---
title: <behavior>iş <serviceBehaviors> akışının
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152326"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<hizmet davranış \<>İş akışı> Davranışlar
**Davranış** öğesi, bir hizmetin davranışı için ayarlar bir koleksiyon içerir. Her davranış **kendi adıyla**dizine dizinlenir. Hizmetler, [ \<bitiş noktası>](../wcf/endpoint-element.md) öğesinin **davranışYapılandırma** özniteliğini kullanarak her davranışa bu ad üzerinden bağlanabilir. Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<davranış>**  
  
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
|ad|Davranışın yapılandırma adını içeren benzersiz bir dize. Bu değer, öğenin tanımlama dizesi olarak hareket ettiği için benzersiz olması gereken kullanıcı tanımlı bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.|  
|[\<yönlendirme>](../wcf/routing-of-servicebehavior.md)|Bir hizmetin ETW izlemesini kullanmasına izin <xref:System.Activities.Tracking.EtwTrackingParticipant>veren bir hizmet davranışı.|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|İleti gönder etkinliklerini kullanarak hizmet uç noktalarına ileti gönderen iş akışları için önbellek paylaşım düzeylerinin, kanal fabrika önbelleğinin ayarlarını ve kanal önbelleğinin ayarlarını özelleştirmeyi sağlayan bir hizmet davranışı.|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|İş akışı hizmeti örnekleri için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı durum bilgilerini bir SQL Server 2005 veya SQL Server 2008 veritabanında destekleyen özelliği yapılandırmanızı sağlayan bir hizmet davranışı.|  
|[\<iş akışıBoş>](workflowidle.md)|Boşta kalan iş akışı örnekleri boşaldığında ve kalıcı olduğunda denetleyen bir hizmet davranışı.|  
|[\<iş akışıInstanceManagement>](workflowinstancemanagement.md)|Kalıcılık, işlenmemiş Özel Durum davranışı ve boşta kalan davranışlar dahil olmak üzere iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenizi sağlayan bir hizmet davranışı.|  
|[\<iş akışıUnhandledException>](workflowunhandledexception.md)|Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|Hizmet davranışı öğelerinin koleksiyonu.|
