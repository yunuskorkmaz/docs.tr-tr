---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 581da860a490c95d5d621194c7f6643fc15118fe
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398677"
---
# <a name="sqlworkflowinstancestore"></a>\<SqlWorkflowInstanceStore >
İş akışı hizmeti örnekleri için SQL Server 2005 veya SQL Server <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 2008 veritabanına yönelik kalıcı durum bilgilerini destekleyen özelliği yapılandırmanıza olanak tanıyan bir hizmet davranışı. Bu özellik hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../windows-workflow-foundation/sql-workflow-instance-store.md).  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<SqlWorkflowInstanceStore >**  
  
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
|connectionString|Temel bir kalıcılık veritabanına bağlanmak için kullanılan bağlantı dizesi içeren bir dize.|  
|connectionStringName|Veritabanı sunucusuna adlandırılmış bir bağlantı dizesi içeren bir dize. Adlandırılmış bir bağlantı dizesi örneği "DefaultConnectionString" dir.|  
|hostLockRenewalPeriod|Ana bilgisayar örneği kilidi yenilemeniz gerekir süre belirten bir Timespan değeri. Ana bilgisayar belirli bir süre içinde kilidi yenileme değil, örnek kilidi açılmış ve başka bir ana bilgisayar tarafından çekilmesi.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır. Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
|instanceCompletionAction|İş akışı örneği tamamlandıktan sonra iş akışı örneği verileri sürdürme deposunda olup tutulur veya bu noktada silinmiş varsa belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Numaralandırılan eylemleri sürdürme deposundan örneği verileri silme veya örnek kendi işlemi tamamlandığında örneği veri sürdürme deposundan silme değil oluşur.<br /><br /> Örnekleri engel olmak sonra tamamlama Kalıcılık oluşturuyorsa veritabanına neden olur ve bu veritabanı performansı etkiler. Performans gereksinimlerinize uygun düzenli aralıklarla veritabanının performans düzeyinde olduğundan emin olmak için bu kayıtları silmek için bir veritabanı temizleme İlkesi yapılandırmanız gerekir.|  
|instanceEncodingOption|Örnek durum bilgilerini bilgileri sürdürme deposunda kaydedilmeden önce GZip algoritmasıyla sıkıştırılıp sıkıştırılmadığını belirtir isteğe bağlı bir değer... Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Bu özellik için olası değerler, <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>sıkıştırma olmadığını belirten ve <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>örnek verilerinin sıkıştırıldığını belirten ve gzip algoritmasını kullandığı anlamına gelir.|  
|instanceLockedExceptionAction|Örnek şu anda başka bir konak tarafından kilitlendiğinden, ana bilgisayar bir örneği kilitlemeye çalıştığında oluşturulan bir özel duruma yanıt olarak oluşan eylemi belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Bu alan için izin verilen seçenekler şunlardır: None, Basic retry ve agresif yeniden deneme. Varsayılan değer, Yok'tur. Aşağıdaki liste bu üç seçenek için açıklamalar sağlar:<br /><br /> Seçim. Hizmet ana bilgisayar örneği ve geçişleri kilitlemek denemez <xref:System.Runtime.DurableInstancing.InstanceLockedException> çağırana.<br />-Temel yeniden deneme. Hizmet ana bilgisayarı, örneği doğrusal bir yeniden deneme aralığı ile kilitlemeye ve özel durumu sıranın sonunda çağrı yapana geçirir.<br />-Agresif yeniden deneme. Hizmet ana bilgisayarının reattempts bir üssel olarak artan gecikme ve geçişleri örnekle kilitlemek <xref:System.Runtime.DurableInstancing.InstanceLockedException> dizisi sonunda çağırana.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<\<ServiceBehavior > davranış >](behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [SQL İş Akışı Örnek Deposu](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
