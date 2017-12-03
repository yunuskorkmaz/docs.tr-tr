---
title: '&lt;sqlWorkflowInstanceStore&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d412e13dc42107d2bfe11c94e51e9690d0c5206b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsqlworkflowinstancestoregt"></a>&lt;sqlWorkflowInstanceStore&gt;
Yapılandırmanıza olanak sağlayan bir hizmet davranışı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı hizmeti örneklerinin bir SQL Server 2005 veya SQL Server 2008 veritabanına kalıcı durum bilgilerini destekleyen özelliği. Bu özellik hakkında daha fazla bilgi için bkz: [SQL iş akışı örneği deposuna](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
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
|connectionString|Temel alınan bir Kalıcılık veritabanına bağlanmak için kullanılan bağlantı dizesi içeren bir dize.|  
|connectionStringName|Veritabanı sunucusuna adlı bağlantı dizesi içeren bir dize. "DefaultConnectionString" adlı bağlantı dizesi örnektir.|  
|honstLockRenewalPeriod|Ana bilgisayar örneği kilidi yenilemeniz gerekir süre belirten bir Timespan değeri. Ana bilgisayar belirli bir süre içinde kilidi yenileme değil, örnek kilidi açılmış ve başka bir ana bilgisayar tarafından çekilmesi.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. İş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır bu öznitelik ayarlanırsa iş akışı boş olur. Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
|instanceCompletionAction|İş akışı örneği tamamlandıktan sonra iş akışı örneği verileri sürdürme deposunda olup tutulur veya bu noktada silinmiş varsa belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Numaralandırılan eylemleri sürdürme deposundan örneği verileri silme veya örnek kendi işlemi tamamlandığında örneği veri sürdürme deposundan silme değil oluşur.<br /><br /> Örnekleri engel olmak sonra tamamlama Kalıcılık oluşturuyorsa veritabanına neden olur ve bu veritabanı performansı etkiler. Performans gereksinimlerinize uygun düzenli aralıklarla veritabanının performans düzeyinde olduğundan emin olmak için bu kayıtları silmek için bir veritabanı temizleme İlkesi yapılandırmanız gerekir.|  
|instanceEncodingOption|Örnek durum bilgilerini bilgileri sürdürme deposunda kaydedilmeden önce GZip algoritmasıyla sıkıştırılıp sıkıştırılmadığını belirtir isteğe bağlı bir değer... Bu değer türünde `System.Activities.DurableInstancing.InstanceEncodingAction`. Bu özellik için olası değerler "", hiçbir sıkıştırma ve veri sıkıştırılır ve GZIP algoritmasını kullanan bu örneği belirtir "GZip" belirten yok.|  
|instanceLockedExceptionAction|Yanıt olarak ana bilgisayar örneği şu anda başka bir ana bilgisayar tarafından kilitlendiğinden örneği kilitlemek çalıştığında oluşan bir özel durum oluşur eylem belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Bu alan için izin verilen Seçenekler şunlardır: None, temel yeniden deneyin ve agresif yeniden deneyin. Varsayılan değer, Yok'tur. Aşağıdaki liste bu üç seçenek için açıklamalar sağlar:<br /><br /> -Yok. Hizmet ana bilgisayar örneği ve geçişleri kilitlemek denemez <xref:System.Runtime.DurableInstancing.InstanceLockedException> çağırana.<br />-Temel yeniden deneyin. Hizmet ana bilgisayarı doğrusal yeniden deneme aralığı örneğiyle kilitlemek reattempts ve dizisi sonunda çağırana özel durum geçirir.<br />-Agresif yeniden deneyin. Hizmet ana bilgisayarının reattempts bir üssel olarak artan gecikme ve geçişleri örnekle kilitlemek <xref:System.Runtime.DurableInstancing.InstanceLockedException> dizisi sonunda çağırana.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >, \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
 [SQL iş akışı örneği deposu](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
