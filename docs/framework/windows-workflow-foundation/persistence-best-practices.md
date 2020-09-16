---
title: Kalıcılık En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: b0276bdfd6dcf2e12357224d9a92484a5da9eac3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558257"
---
# <a name="persistence-best-practices"></a>Kalıcılık En İyi Uygulamaları
Bu belge iş akışı tasarımı ve iş akışı kalıcılığı ile ilgili yapılandırma için en iyi yöntemleri içerir.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Dayanıklı Iş akışlarının tasarımı ve uygulanması  
 Genel olarak, iş akışları, bir olayı beklediği için iş akışının boşta olduğu zamanlarla birlikte Aralanmış kısa dönemlerde çalışır. Bu olay, ileti veya süresi dolan bir zamanlayıcı gibi şeyler olabilir. İş akışı örneğini boşta kaldığında kaldırabilmek için, hizmet ana bilgisayarı iş akışı örneğini kalıcı hale vermelidir. Bu, yalnızca iş akışı örneği kalıcı olmayan bir bölgede değilse (örneğin, bir işlemin tamamlanmasını bekliyorsa veya zaman uyumsuz geri çağırma için beklerken) mümkündür. Boş bir iş akışı örneğinin kaldırılmasına izin vermek için, iş akışı yazarı yalnızca kısa süreli eylemler için işlem kapsamlarını ve zaman uyumsuz etkinlikleri kullanmalıdır. Özellikle yazar, gecikme etkinliklerini bu kalıcı olmayan bölgeler içinde mümkün olduğunca kısa tutmaya devam etmelidir.  
  
 İş akışı yalnızca, iş akışı tarafından kullanılan tüm veri türleri seri hale getirilebilir ise kalıcı olabilir. Ayrıca, kalıcı iş akışlarında kullanılan özel türlerin, <xref:System.Runtime.Serialization.NetDataContractSerializer> tarafından kalıcı hale getirilemeyen şekilde seri hale getirilebilir olması gerekir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .  
  
 Kalıcı olmayan bir konak veya bilgisayar arızası durumunda bir iş akışı örneği kurtarılamaz. Genel olarak, iş akışı örneğini iş akışının yaşam döngüsünün başlarında kalıcı yapmanızı öneririz.  
  
 İş akışınız uzun süredir meşgulse, iş akışı örneğini meşgul dönemi boyunca düzenli olarak kalıcı hale getirmek için önerilir. <xref:System.Activities.Statements.Persist>İş akışı örneğini meşgul tutan etkinlik sırasına göre etkinlik ekleyerek bunu yapabilirsiniz. Bu şekilde, uygulama etki alanı geri dönüştürme, ana bilgisayar sorunları veya bilgisayar sorunları sistemin meşgul döneminin başlangıcına geri alınmasına neden olmaz. <xref:System.Activities.Statements.Persist>İş akışınıza etkinlik eklemenin bir performans düşüşüne neden olduğunu unutmayın.  
  
 Windows Server App Fabric, kalıcılığı yapılandırmayı ve kullanımını büyük ölçüde basitleştirir. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="configuration-of-scalability-parameters"></a>Ölçeklenebilirlik parametrelerinin yapılandırması  
 Ölçeklenebilirlik ve performans gereksinimleri aşağıdaki parametrelerin ayarlarını belirlemenizi ister:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Bu parametrelerin geçerli senaryoya göre aşağıdaki şekilde ayarlanması gerekir.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Senaryo: En Iyi yanıt süresi gerektiren az sayıda Iş akışı örneği  
 Bu senaryoda, tüm iş akışı örneklerinin Boşta olduklarında yüklenmiş olarak kalması gerekir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>Büyük bir değere ayarlayın. Bu ayarın kullanılması, bir iş akışı örneğinin bilgisayarlar arasında taşınmasına engel olur. Bu ayarı yalnızca aşağıdakilerden biri veya daha fazlası geçerliyse kullanın:  
  
- Bir iş akışı örneği, ömrü boyunca tek bir ileti alır.  
  
- Tüm iş akışı örnekleri tek bir bilgisayarda çalışır  
  
- Bir iş akışı örneği tarafından alınan tüm iletiler aynı bilgisayar tarafından alınır.  
  
 <xref:System.Activities.Statements.Persist> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Hizmet ana bilgisayarı veya bilgisayar hatalarından sonra iş akışı örneğinizin kurtarılmasını etkinleştirmek için etkinlikleri kullanın veya 0 olarak ayarlayın.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Senaryo: Iş akışı örnekleri uzun süre boşta kalır  
 Bu senaryoda, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> kaynakları mümkün olan en kısa sürede serbest bırakmak için 0 olarak ayarlayın.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Senaryo: Iş akışı örnekleri kısa bir süre içinde birden çok Ileti alır  
 Bu senaryoda, bu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> iletiler aynı bilgisayar tarafından alınmışsa, bu senaryoda 60 saniyeye ayarlanır. Bu, bir iş akışı örneğinin kaldırılmasının ve yüklenmesinin hızlı bir sırasını önler. Bu aynı zamanda örneği çok uzun süre boyunca bellekte tutmaz.  
  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>0 olarak ayarlayın ve <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> Bu iletiler farklı bilgisayarlar tarafından alınmışsa, BasicRetry veya kararlılığı olarak ayarlayın. Bu, iş akışı örneğinin başka bir bilgisayar tarafından yüklenmesine izin verir.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Senaryo: Iş akışı kısa sürelerle gecikme etkinlikleri kullanır  
 Bu senaryoda, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zaman aşımına uğradı bir etkinlik nedeniyle yüklenmesi gereken örnekler için kalıcılık veritabanını düzenli olarak yoklar <xref:System.Activities.Statements.Delay> . <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>Bir sonraki yoklama aralığında sona erecektir bir Zamanlayıcı bulursa, SQL Iş akışı örnek deposu yoklama aralığını kısaltır. Sonraki yoklama, Zamanlayıcının süresi dolduktan sonra doğru yapılır. Bu şekilde, SQL Iş akışı örneği deposu tarafından ayarlanan yoklama aralığından daha uzun süre çalışan zamanlayıcılar üzerinde yüksek bir doğrulukla ulaşır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> . Kısa gecikmelerin zamanında işlenmesini sağlamak için, en az bir yoklama aralığı için iş akışı örneğinin bellekte kalması gerekir.  
  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>Son kullanma süresini kalıcılık veritabanına yazmak için 0 olarak ayarlayın.  
  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> Örneği en az bir yoklama aralığı için bellekte tutmak üzere daha uzun veya eşit olarak ayarlayın.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>Bu, kalıcılık veritabanındaki daha fazla yüke yol ettiğinden, bunun azalmasını önermiyoruz. Öğesini kullanan her hizmet ana bilgisayarı, her <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> algılama dönemi için veritabanını bir kez yoklar. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>Bir zaman aralığı çok küçük olarak ayarlandığında, hizmet ana bilgisayarlarının sayısı büyükse sisteminizin performansının azalmasına neden olabilir.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>SQL Iş akışı örnek deposunu yapılandırma  
 SQL Iş akışı örneği deposunda aşağıdaki yapılandırma parametreleri vardır:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Bu parametre, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı örneği durumunu sıkıştırmak için öğesine bildirir. Sıkıştırma, kalıcılık veritabanında depolanan veri miktarını azaltır ve kalıcılık veritabanının adanmış bir veritabanı sunucusunda bulunduğu durumlarda ağ trafiğini azaltır. Sıkıştırma kullanılıyorsa, örnek durumunu sıkıştırmak ve ayıklamak için hesaplama kaynakları gerekir. Çoğu durumda, sıkıştırma performansı artar.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Bu parametre, ' ın <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tamamlanmış örnekleri tutaveya silmesine izin verir. Tamamlanan örneklerin tutulması, Kalıcılık veritabanı depolama gereksinimlerini artırır ve tablo arama sürelerini artıran daha büyük tablolara yönlendirir. Hata ayıklama veya denetim için tamamlanan örnekler gerekli değilse, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tamamlanmış örnekleri silmek için en iyisi. Silinen örnekler yalnızca Kullanıcı tarafından son olarak kaldırılmakta olan bir işlem kurduğunda tutulmalıdır. Tamamlanan iş akışı örneği örnek deposunda bulunduğu sürece bağıntı anahtarlarının tekrar kullanılamayacağını unutmayın.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Bu parametre, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bir <xref:System.Activities.Statements.Delay> Etkinliğin süresi dolarsa yüklenmesi gereken örneklerin kalıcılık veritabanını yokladığı en büyük aralığı tanımlar. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>Bir sonraki yoklama aralığında süresi dolacak bir Zamanlayıcı bulursa, bir sonraki yoklamanın zamanlayıcı süresi dolduktan sonra gerçekleşmesi için yoklama aralığını kısaltacaktır. Bu şekilde, SQL Iş akışı örneği deposu, daha uzun süre çalışan zamanlayıcılar için yüksek doğrulukla ulaşır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> .  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>Bu, kalıcılık veritabanındaki daha fazla yüke yol ettiğinden, ' ı azaltmanızı önermiyoruz. Öğesini kullanan her hizmet ana bilgisayarı, her <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> algılama dönemi için veritabanını bir kez yoklar. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>Bir aralığa çok küçük olarak ayarlandığında, hizmet ana bilgisayarlarının sayısı büyükse sisteminizin performansının azalmasına neden olabilir.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Bu parametre, ana bilgisayarın kilitlenme veritabanında kilidini yenilediğini belirleyen aralığı tanımlar. Bu aralığı kısaltaştırın, bir konağın veya bilgisayarın başarısız olması durumunda iş akışı örneklerinin daha hızlı kurtarılmasını sağlar. Öte yandan, bir kısa kilit yenileme süresi Kalıcılık veritabanının yükünü arttırır. ' İ kullanan her hizmet ana bilgisayarı, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> yenileme süresi başına veritabanında bir kez kilitleri güncelleştirir. Bir bilgisayar birçok hizmet ana bilgisayarı çalıştırıyorsa kilit yenilemesinin neden olduğu yükün sisteminizin performansını azaltmadığından emin olun. Varsa, artırmayı düşünün <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A> .  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Etkinleştirilirse, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki 30 saniye boyunca kilitli bir örnek yüklemeye yeniden denemeler yapılır. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>İş akışı kısa bir süre içinde birden çok ileti alırsa ve bu iletiler farklı bilgisayarlar tarafından alındığında, BasicRetry veya kararlılığı olarak ayarlayın.  
  
 Yük yeniden deneme mekanizması, yük yeniden denemeleri denenmediği sürece herhangi bir performans yükü sunmaz, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> her zaman etkinleştirilmelidir.
