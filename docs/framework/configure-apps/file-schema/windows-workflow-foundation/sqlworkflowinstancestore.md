---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: d6c86d02e14a38c2a35ba4858c4abfea73268fd8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148717"
---
# \<sqlWorkflowInstanceStore>

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>İş akışı hizmeti örnekleri için SQL Server 2005 veya SQL Server 2008 veritabanına yönelik kalıcı durum bilgilerini destekleyen özelliği yapılandırmanıza olanak tanıyan bir hizmet davranışı. Bu özellik hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../windows-workflow-foundation/sql-workflow-instance-store.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sqlWorkflowInstanceStore>**  
  
## <a name="syntax"></a>Syntax  
  
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
|Dizisi|Temel bir kalıcılık veritabanına bağlanmak için kullanılan bağlantı dizesi içeren bir dize.|  
|connectionStringName|Veritabanı sunucusuna adlandırılmış bir bağlantı dizesi içeren bir dize. Adlandırılmış bir bağlantı dizesi örneği "DefaultConnectionString" dir.|  
|hostLockRenewalPeriod|Ana bilgisayar örneği kilidi yenilemeniz gerekir süre belirten bir Timespan değeri. Ana bilgisayar belirli bir süre içinde kilidi yenileme değil, örnek kilidi açılmış ve başka bir ana bilgisayar tarafından çekilmesi.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır. Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
|instanceCompletionAction|İş akışı örneği tamamlandıktan sonra iş akışı örneği verileri sürdürme deposunda olup tutulur veya bu noktada silinmiş varsa belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Numaralandırılan eylemleri sürdürme deposundan örneği verileri silme veya örnek kendi işlemi tamamlandığında örneği veri sürdürme deposundan silme değil oluşur.<br /><br /> Örnekleri engel olmak sonra tamamlama Kalıcılık oluşturuyorsa veritabanına neden olur ve bu veritabanı performansı etkiler. Performans gereksinimlerinize uygun düzenli aralıklarla veritabanının performans düzeyinde olduğundan emin olmak için bu kayıtları silmek için bir veritabanı temizleme İlkesi yapılandırmanız gerekir.|  
|instanceEncodingOption|Örnek durum bilgilerini bilgileri sürdürme deposunda kaydedilmeden önce GZip algoritmasıyla sıkıştırılıp sıkıştırılmadığını belirtir isteğe bağlı bir değer... Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Bu özellik için olası değerler, <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None> sıkıştırma olmadığını belirten ve <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip> örnek verilerinin sıkıştırıldığını belirten ve gzip algoritmasını kullandığı anlamına gelir.|  
|instanceLockedExceptionAction|Örnek şu anda başka bir konak tarafından kilitlendiğinden, ana bilgisayar bir örneği kilitlemeye çalıştığında oluşturulan bir özel duruma yanıt olarak oluşan eylemi belirten bir değer. Bu değer türünde <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Bu alan için izin verilen seçenekler şunlardır: None, Basic retry ve agresif yeniden deneme. Varsayılan değer, Yok'tur. Aşağıdaki liste bu üç seçenek için açıklamalar sağlar:<br /><br /> Seçim. Hizmet ana bilgisayar örneği ve geçişleri kilitlemek denemez <xref:System.Runtime.DurableInstancing.InstanceLockedException> çağırana.<br />-Temel yeniden deneme. Hizmet ana bilgisayarı, örneği doğrusal bir yeniden deneme aralığı ile kilitlemeye ve özel durumu sıranın sonunda çağrı yapana geçirir.<br />-Agresif yeniden deneme. Hizmet ana bilgisayarının reattempts bir üssel olarak artan gecikme ve geçişleri örnekle kilitlemek <xref:System.Runtime.DurableInstancing.InstanceLockedException> dizisi sonunda çağırana.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior> durumunu \<serviceBehaviors>](behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [SQL İş Akışı Örnek Deposu](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
