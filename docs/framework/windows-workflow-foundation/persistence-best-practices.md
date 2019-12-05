---
title: Kalıcılık En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 8ffbb3ebfa8f85e2b0052a9df9ada30766accd8e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802524"
---
# <a name="persistence-best-practices"></a>Kalıcılık En İyi Uygulamaları
Bu belge iş akışı tasarımı ve iş akışı kalıcılığı ile ilgili yapılandırma için en iyi yöntemleri içerir.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Dayanıklı Iş akışlarının tasarımı ve uygulanması  
 Genel olarak, iş akışları, bir olayı beklediği için iş akışının boşta olduğu zamanlarla birlikte Aralanmış kısa dönemlerde çalışır. Bu olay, ileti veya süresi dolan bir zamanlayıcı gibi şeyler olabilir. İş akışı örneğini boşta kaldığında kaldırabilmek için, hizmet ana bilgisayarı iş akışı örneğini kalıcı hale vermelidir. Bu, yalnızca iş akışı örneği kalıcı olmayan bir bölgede değilse (örneğin, bir işlemin tamamlanmasını bekliyorsa veya zaman uyumsuz geri çağırma için beklerken) mümkündür. Boş bir iş akışı örneğinin kaldırılmasına izin vermek için, iş akışı yazarı yalnızca kısa süreli eylemler için işlem kapsamlarını ve zaman uyumsuz etkinlikleri kullanmalıdır. Özellikle yazar, gecikme etkinliklerini bu kalıcı olmayan bölgeler içinde mümkün olduğunca kısa tutmaya devam etmelidir.  
  
 İş akışı yalnızca, iş akışı tarafından kullanılan tüm veri türleri seri hale getirilebilir ise kalıcı olabilir. Ayrıca, kalıcı iş akışlarında kullanılan özel türlerin <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>kalıcı olması için <xref:System.Runtime.Serialization.NetDataContractSerializer> seri hale getirilebilir olması gerekir.  
  
 Kalıcı olmayan bir konak veya bilgisayar arızası durumunda bir iş akışı örneği kurtarılamaz. Genel olarak, iş akışı örneğini iş akışının yaşam döngüsünün başlarında kalıcı yapmanızı öneririz.  
  
 İş akışınız uzun süredir meşgulse, iş akışı örneğini meşgul dönemi boyunca düzenli olarak kalıcı hale getirmek için önerilir. Bunu, iş akışı örneğini meşgul tutan etkinliklerin sırası boyunca <xref:System.Activities.Statements.Persist> etkinlikleri ekleyerek yapabilirsiniz. Bu şekilde, uygulama etki alanı geri dönüştürme, ana bilgisayar sorunları veya bilgisayar sorunları sistemin meşgul döneminin başlangıcına geri alınmasına neden olmaz. <xref:System.Activities.Statements.Persist> etkinliklerinin iş akışınıza eklenmesinin performans azalmasına yol açabileceğini unutmayın.  
  
 Windows Server App Fabric, kalıcılığı yapılandırmayı ve kullanımını büyük ölçüde basitleştirir. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="configuration-of-scalability-parameters"></a>Ölçeklenebilirlik parametrelerinin yapılandırması  
 Ölçeklenebilirlik ve performans gereksinimleri aşağıdaki parametrelerin ayarlarını belirlemenizi ister:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Bu parametrelerin geçerli senaryoya göre aşağıdaki şekilde ayarlanması gerekir.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Senaryo: En Iyi yanıt süresi gerektiren az sayıda Iş akışı örneği  
 Bu senaryoda, tüm iş akışı örneklerinin Boşta olduklarında yüklenmiş olarak kalması gerekir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> büyük bir değere ayarlayın. Bu ayarın kullanılması, bir iş akışı örneğinin bilgisayarlar arasında taşınmasına engel olur. Bu ayarı yalnızca aşağıdakilerden biri veya daha fazlası geçerliyse kullanın:  
  
- Bir iş akışı örneği, ömrü boyunca tek bir ileti alır.  
  
- Tüm iş akışı örnekleri tek bir bilgisayarda çalışır  
  
- Bir iş akışı örneği tarafından alınan tüm iletiler aynı bilgisayar tarafından alınır.  
  
 Hizmet ana bilgisayarı veya bilgisayar hatalarından sonra iş akışı örneğinizin kurtarılmasını etkinleştirmek için <xref:System.Activities.Statements.Persist> etkinlikleri kullanın veya <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> 0 olarak ayarlayın.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Senaryo: Iş akışı örnekleri uzun süre boşta kalır  
 Bu senaryoda, kaynakları mümkün olan en kısa sürede serbest bırakmak için <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 olarak ayarlayın.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Senaryo: Iş akışı örnekleri kısa bir süre içinde birden çok Ileti alır  
 Bu senaryoda, bu iletiler aynı bilgisayar tarafından alınmışsa, bu durumda <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> değerini 60 saniyeye ayarlayın. Bu, bir iş akışı örneğinin kaldırılmasının ve yüklenmesinin hızlı bir sırasını önler. Bu aynı zamanda örneği çok uzun süre boyunca bellekte tutmaz.  
  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 olarak ayarlayın ve bu iletilerin farklı bilgisayarlar tarafından alınabilmesi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry veya kararlılığı olarak ayarlayın. Bu, iş akışı örneğinin başka bir bilgisayar tarafından yüklenmesine izin verir.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Senaryo: Iş akışı kısa sürelerle gecikme etkinlikleri kullanır  
 Bu senaryoda <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, zaman aşımına uğradı bir <xref:System.Activities.Statements.Delay> etkinliği nedeniyle yüklenmesi gereken örnekler için kalıcılık veritabanını düzenli olarak yoklar. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki yoklama aralığında sona erecektir bir Zamanlayıcı bulursa, SQL Iş akışı örnek deposu yoklama aralığını kısaltır. Sonraki yoklama, Zamanlayıcının süresi dolduktan sonra doğru yapılır. Bu şekilde, SQL Iş akışı örneği deposu, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>tarafından ayarlanan yoklama aralığından daha uzun süre çalışan zamanlayıcılar üzerinde yüksek bir doğrulukla ulaşır. Kısa gecikmelerin zamanında işlenmesini sağlamak için, en az bir yoklama aralığı için iş akışı örneğinin bellekte kalması gerekir.  
  
 Son kullanma süresini kalıcılık veritabanına yazmak için <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> 0 olarak ayarlayın.  
  
 Örneği en az bir yoklama aralığı için bellekte tutmak üzere <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> daha uzun veya eşit olarak ayarlayın.  
  
 Bu, kalıcılık veritabanındaki daha fazla yüke yol ettiğinden <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> azaltmanızı önermiyoruz. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kullanan her hizmet ana bilgisayarı, veritabanını her algılama dönemi için bir kez yoklar. Hizmet ana bilgisayarlarının sayısı büyükse, bir zaman aralığı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> çok küçük olarak ayarlanması sisteminizin performansının azalmasına neden olabilir.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>SQL Iş akışı örnek deposunu yapılandırma  
 SQL Iş akışı örneği deposunda aşağıdaki yapılandırma parametreleri vardır:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Bu parametre, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı örneği durumunu sıkıştırmak için yönlendirir. Sıkıştırma, kalıcılık veritabanında depolanan veri miktarını azaltır ve kalıcılık veritabanının adanmış bir veritabanı sunucusunda bulunduğu durumlarda ağ trafiğini azaltır. Sıkıştırma kullanılıyorsa, örnek durumunu sıkıştırmak ve ayıklamak için hesaplama kaynakları gerekir. Çoğu durumda, sıkıştırma performansı artar.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Bu parametre, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tamamlanmış örnekleri tutaveya silmesine izin verir. Tamamlanan örneklerin tutulması, Kalıcılık veritabanı depolama gereksinimlerini artırır ve tablo arama sürelerini artıran daha büyük tablolara yönlendirir. Hata ayıklama veya denetim için tamamlanan örnekler gerekli değilse, tamamlanmış örnekleri silmek için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> söylemek en iyisidir. Silinen örnekler yalnızca Kullanıcı tarafından son olarak kaldırılmakta olan bir işlem kurduğunda tutulmalıdır. Tamamlanan iş akışı örneği örnek deposunda bulunduğu sürece bağıntı anahtarlarının tekrar kullanılamayacağını unutmayın.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Bu parametre, <xref:System.Activities.Statements.Delay> bir etkinliğin süresi dolarsa yüklenmesi gereken örnekler için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcılık veritabanını yokladığı maksimum aralığı tanımlar. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki yoklama aralığında süresi dolacak bir Zamanlayıcı bulursa, zamanlayıcı süresi dolduktan sonra sonraki yoklamanın gerçekleşmesi için yoklama aralığını kısaltacaktır. Bu şekilde, SQL Iş akışı örneği deposu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>daha uzun süre çalışan zamanlayıcılar üzerinde yüksek bir doğrulukla erişir.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>azaltmanızı önermeyiz çünkü bu, kalıcılık veritabanındaki daha fazla yüke yol açar. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kullanan her hizmet ana bilgisayarı, veritabanını her algılama dönemi için bir kez yoklar. Hizmet ana bilgisayarlarının sayısı büyükse, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> bir aralığa çok küçük olarak ayarlamak sisteminizin performansının azaltılmasına neden olabilir.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Bu parametre, ana bilgisayarın kilitlenme veritabanında kilidini yenilediğini belirleyen aralığı tanımlar. Bu aralığı kısaltaştırın, bir konağın veya bilgisayarın başarısız olması durumunda iş akışı örneklerinin daha hızlı kurtarılmasını sağlar. Öte yandan, bir kısa kilit yenileme süresi Kalıcılık veritabanının yükünü arttırır. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kullanan her bir hizmet ana bilgisayarı, veritabanında yenileme süresi başına bir kez kilitlerinin güncelleştirilmesini sağlayacak. Bir bilgisayar birçok hizmet ana bilgisayarı çalıştırıyorsa kilit yenilemesinin neden olduğu yükün sisteminizin performansını azaltmadığından emin olun. Varsa, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>artırmayı düşünün.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Etkinleştirilirse, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki 30 saniye boyunca kilitli bir örnek yüklemeyi yeniden dener. İş akışı kısa bir süre içinde birden çok ileti alırsa ve bu iletiler farklı bilgisayarlar tarafından alındığında <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry veya kararlılığı olarak ayarlayın.  
  
 Yük yeniden deneme mekanizması, yük yeniden denemeleri denenmediği sürece herhangi bir performans yükü sunmaz, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> her zaman etkinleştirilmelidir.
