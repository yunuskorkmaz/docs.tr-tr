---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 56a44fdb62062903ca3ad00f8105a66ccab02cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151968"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
İş akışı hizmeti örnekleri için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı durum bilgilerini bir SQL Server 2005 veya SQL Server 2008 veritabanında destekleyen özelliği yapılandırmanızı sağlayan bir hizmet davranışı. Bu özellik hakkında daha fazla bilgi için [SQL İş Akışı Örneği Deposu'na](../../../windows-workflow-foundation/sql-workflow-instance-store.md)bakın.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sqlWorkflowInstanceStore>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String"
                                hostLockRenewalPeriod="TimeSpan"
                                instanceCompletionAction="DeleteNothing/DeleteAll"
                                instanceEncodingAction="None/GZip"
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Connectionstring|Altta yatan kalıcılık veritabanına bağlanmak için kullanılan bir bağlantı dizesi içeren bir dize.|  
|Connectionstringname|Veritabanı sunucusuna adlandırılmış bir bağlantı dizesi içeren bir dize. Adlandırılmış bir bağlantı dizesi örneği "DefaultConnectionString"tir.|  
|hostLockRenewalPeriod|Ana bilgisayar örneği kilidi yenilemeniz gerekir süre belirten bir Timespan değeri. Ana bilgisayar belirli bir süre içinde kilidi yenileme değil, örnek kilidi açılmış ve başka bir ana bilgisayar tarafından çekilmesi.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik sıfırolarak ayarlanırsa, iş akışı örneği kalıcı dır ve iş akışı boşta kaldıktan hemen sonra boşaltılır. Bu özniteliği TimeSpan.MaxValue olarak ayarlamak, boşaltma işlemini etkin bir şekilde devre dışı eder. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
|instanceCompletionAction|İş akışı örneği tamamlandıktan sonra iş akışı örneği verileri sürdürme deposunda olup tutulur veya bu noktada silinmiş varsa belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Numaralandırılan eylemleri sürdürme deposundan örneği verileri silme veya örnek kendi işlemi tamamlandığında örneği veri sürdürme deposundan silme değil oluşur.<br /><br /> Örnekleri engel olmak sonra tamamlama Kalıcılık oluşturuyorsa veritabanına neden olur ve bu veritabanı performansı etkiler. Performans gereksinimlerinize uygun düzenli aralıklarla veritabanının performans düzeyinde olduğundan emin olmak için bu kayıtları silmek için bir veritabanı temizleme İlkesi yapılandırmanız gerekir.|  
|instanceEncodingOption|Örnek durum bilgilerini bilgileri sürdürme deposunda kaydedilmeden önce GZip algoritmasıyla sıkıştırılıp sıkıştırılmadığını belirtir isteğe bağlı bir değer... Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Bu özellik için <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>olası değerler , hiçbir sıkıştırma <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>belirtir ve , hangi örnek veri sıkıştırılmış ve gzip algoritması kullanır belirtir.|  
|instanceLockedExceptionAction|Örnek şu anda başka bir ana bilgisayar tarafından kilitlendiğinden, ana bilgisayar bir örneği kilitlemeye çalıştığında atılan bir özel duruma yanıt olarak oluşan eylemi belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Bu alan için izin verilen seçenekler şunlardır: Yok, Temel Yeniden Deneme ve Agresif Yeniden Deneme. Varsayılan değer, Yok'tur. Aşağıdaki liste bu üç seçenek için açıklamalar sağlar:<br /><br /> - Yok. Hizmet ana bilgisayar örneği ve geçişleri kilitlemek denemez <xref:System.Runtime.DurableInstancing.InstanceLockedException> çağırana.<br />- Temel Yeniden Deneme. Hizmet ana bilgisayarı, örneği doğrusal yeniden deneme aralığıyla kilitlemeyi yeniden dener ve sıranın sonundaki özel durumu arayana geçirir.<br />- Agresif Retry. Hizmet ana bilgisayarının reattempts bir üssel olarak artan gecikme ve geçişleri örnekle kilitlemek <xref:System.Runtime.DurableInstancing.InstanceLockedException> dizisi sonunda çağırana.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<hizmet davranış \<>Davranışlar>](behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [SQL İş Akışı Örnek Deposu](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
