---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 8601f1c7f4e1dbf911020c328652c371bf039124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119086"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore >
Yapılandırmanıza olanak tanıyan bir hizmet davranışını <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> özellik, bir SQL Server 2005 veya SQL Server 2008 veritabanına iş akışı hizmet örneklerine yönelik sürüyor durumu bilgileri destekler. Bu özellik hakkında daha fazla bilgi için bkz. [SQL iş akışı örneği Store](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<sqlWorkflowInstanceStore >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                honstLockRenewalPeriod="TimeSpan" 
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
|connectionString|Temel alınan bir Kalıcılık veritabanına bağlanmak için kullanılan bir bağlantı dizesi içeren bir dize.|  
|connectionStringName|Veritabanı sunucusu için bir adlandırılmış bağlantı dizesi içeren bir dize. Bir adlandırılmış bağlantı dizesi "DefaultConnectionString" örneğidir.|  
|honstLockRenewalPeriod|Ana bilgisayar örneği kilidi yenilemeniz gerekir süre belirten bir Timespan değeri. Ana bilgisayar belirli bir süre içinde kilidi yenileme değil, örnek kilidi açılmış ve başka bir ana bilgisayar tarafından çekilmesi.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik iş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır olarak ayarlanırsa, iş akışı boş olur. Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
|instanceCompletionAction|İş akışı örneği tamamlandıktan sonra iş akışı örneği verileri sürdürme deposunda olup tutulur veya bu noktada silinmiş varsa belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Numaralandırılan eylemleri sürdürme deposundan örneği verileri silme veya örnek kendi işlemi tamamlandığında örneği veri sürdürme deposundan silme değil oluşur.<br /><br /> Örnekleri engel olmak sonra tamamlama Kalıcılık oluşturuyorsa veritabanına neden olur ve bu veritabanı performansı etkiler. Performans gereksinimlerinize uygun düzenli aralıklarla veritabanının performans düzeyinde olduğundan emin olmak için bu kayıtları silmek için bir veritabanı temizleme İlkesi yapılandırmanız gerekir.|  
|instanceEncodingOption|Örnek durum bilgilerini bilgileri sürdürme deposunda kaydedilmeden önce GZip algoritmasıyla sıkıştırılıp sıkıştırılmadığını belirtir isteğe bağlı bir değer... Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Bu özellik için olası değerler <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>, hiçbir sıkıştırma belirtir ve <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>, örnek veri sıkıştırılmış ve gzip algoritma belirtir.|  
|instanceLockedExceptionAction|Yanıt olarak ana bilgisayar örneği şu anda başka bir ana bilgisayar tarafından kilitlendiğinden örneği kilitlemek çalıştığında oluşturulan bir özel durum ortaya çıkan eylem belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Bu alan için izin verilen Seçenekler şunlardır: None, temel yeniden deneyin ve etkin yeniden deneyin. Varsayılan değer, Yok'tur. Aşağıdaki liste bu üç seçenek için açıklamalar sağlar:<br /><br /> -Yok. Hizmet ana bilgisayar örneği ve geçişleri kilitlemek denemez <xref:System.Runtime.DurableInstancing.InstanceLockedException> çağırana.<br />-Temel yeniden deneyin. Hizmet Konağı bir doğrusal yeniden deneme aralığı örnekle kilitlemek tekrar dener ve dizisi sonunda çağırana özel durum geçirir.<br />-Etkin yeniden deneyin. Hizmet ana bilgisayarının reattempts bir üssel olarak artan gecikme ve geçişleri örnekle kilitlemek <xref:System.Runtime.DurableInstancing.InstanceLockedException> dizisi sonunda çağırana.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >, \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [SQL İş Akışı Örnek Deposu](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
