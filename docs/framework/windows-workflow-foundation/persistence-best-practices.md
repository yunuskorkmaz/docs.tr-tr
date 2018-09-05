---
title: Kalıcılık en iyi uygulamalar
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: fdbf61e559efbd978df1c5a46fcbbbbc528ec98a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558881"
---
# <a name="persistence-best-practices"></a>Kalıcılık en iyi uygulamalar
Bu belge, iş akışı tasarım ve iş akışı kalıcılığı için ilgili yapılandırma için en iyi uygulamaları kapsar.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Tasarım ve uygulama dayanıklı iş akışı  
 Genel olarak, iş akışlarını iş için bir olay beklediği sırasında iş akışı boş olduğu zamanları ile aralıklı nokta kısa gerçekleştirin. Bu olay, bir ileti veya sona eren bir Zamanlayıcı gibi şeyler olabilir. İş akışı örneği boşta kaldığında kaldırabilmek için için hizmet ana iş akışı örneği kalıcı gerekir. Bu seçenek, yalnızca iş akışı örneği (örneğin, bir işlemin tamamlanması beklenirken veya zaman uyumsuz bir geri çağırma bekleniyor) no-persist bölgede değilse mümkündür. Boş iş akışı örneğini kaldırmaya izin vermek için iş akışı Yazar işlem kapsamları ve zaman uyumsuz etkinlikler yalnızca kısa süreli eylemlerini kullanmanız gerekir. Özellikle, yazarın gecikme tutmalısınız içindeki bu etkinlikleri kalıcı Hayır bölgeleri olabildiğince kısa.  
  
 Tüm iş akışı tarafından kullanılan veri türleri, seri hale getirilebilir olması durumunda iş akışı yalnızca kalıcı. Ayrıca, kalıcı iş akışlarında kullanılan özel türler ile Serileştirilebilir olmalıdır <xref:System.Runtime.Serialization.NetDataContractSerializer> tarafından kalıcı için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Bir iş akışı örneği kalıcı olmadığını ana bilgisayar veya bilgisayar hata durumunda geri alınamaz. Genel olarak, iş akışının yaşam döngüsü erken bir iş akışı örneği kalıcı öneririz.  
  
 İş akışınızı uzun bir süredir meşgul ise, meşgul süresi boyunca düzenli olarak iş akışı örneği kalıcı öneririz. Bunu ekleyerek yapabilirsiniz <xref:System.Activities.Statements.Persist> etkinlikleri iş akışı örneği meşgul tutar etkinlik dizisini boyunca. Bu şekilde, uygulama etki alanı geri dönüştürme, ana bilgisayar hataları veya bilgisayar hatalarını sistemin meşgul dönemin başlangıcını geri neden olmaz. Unutmayın, ekleme <xref:System.Activities.Statements.Persist> etkinlikleri iş akışınız için bir performans düşüşüne neden olabilir.  
  
 Windows Server App Fabric, büyük ölçüde Kalıcılık kullanımını ve yapılandırmayı basitleştirir. Daha fazla bilgi için [Windows Server App Fabric kalıcılığı](https://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>Ölçeklenebilirlik parametrelerinin yapılandırması  
 Ölçeklenebilirlik ve performans gereksinimlerini aşağıdaki parametreleri ayarlarını belirleyin:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Bu parametreleri gibi geçerli senaryoya göre ayarlamanız gerekir.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Senaryo: Az sayıda en iyi yanıt süresi gerektiren, iş akışı örnekleri  
 Bu senaryoda, boşta kaldıklarında tüm iş akışı örnekleri yüklenen kalması gerekir. Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> büyük bir değer. Bu ayarın kullanılması, bir iş akışı örneği bilgisayarlar arasında taşınmasını engeller. Bir veya daha fazlasını yalnızca doğruysa, bu ayarı kullanın:  
  
-   Bir iş akışı örneği ömrü boyunca tek bir ileti alır.  
  
-   Tek bilgisayardaki tüm iş akışı örnekleri çalıştırma  
  
-   Bir iş akışı örneği tarafından alınan tüm iletiler aynı bilgisayar tarafından alınır.  
  
 Kullanım <xref:System.Activities.Statements.Persist> etkinlikler veya set <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> kurtarma iş akışı örneğinizin hizmet ana bilgisayarı veya bilgisayar hatasından sonra etkinleştirmek için 0.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Senaryo: İş akışı örnekleri olan boşta uzun süreler için  
 Bu senaryoda ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> kaynakları hemen serbest bırakmak için 0.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Senaryo: İş akışı örnekleri kısa bir süre içinde birden çok ileti alma  
 Bu senaryoda ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> bu iletiler aynı bilgisayar tarafından alınırsa 60 saniyedir. Bu, kaldırma ve bir iş akışı örneğini yükleme hızlı sırası engeller. Bu ayrıca örneği çok uzun bellekte tutmaz.  
  
 Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0'kümesi <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry ya da farklı bilgisayarlar tarafından bu iletiler aldığında, AggressiveRetry. Bu iş akışı örneği başka bir bilgisayar tarafından yüklenmesine izin verir.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Senaryo: İş akışı ile kısa süreli gecikme etkinlikleri kullanır  
 Bu senaryoda, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Kalıcılık veritabanı düzenli olarak yoklar örnekler nedeniyle süresi dolmuş yüklenmesi gerektiğini <xref:System.Activities.Statements.Delay> etkinlik. Varsa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki yoklama aralığı içinde SQL iş akışı örneği Store dolacak bir zamanlayıcı kısaltır ve yoklama aralığı bulur. Sonraki yoklama sonra sağ Zamanlayıcı süresi dolduktan sonra meydana gelir. Bu şekilde bir yüksek tarafından ayarlanan yoklama aralığından daha uzun çalışması zamanlayıcılar doğruluğunu SQL iş akışı örneği Store başarır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Daha kısa bir gecikme zamanında işlenmesini etkinleştirmek için iş akışı örneği için en az bir yoklama aralığı bellekte kalması gerekir.  
  
 Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> sona erme zamanı Kalıcılık veritabanına yazmak için 0.  
  
 Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> çok uzun veya buna eşit <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> örneği için en az bir yoklama aralığı bellekte tutmak için.  
  
 Azaltma önermiyoruz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> çünkü bu artan yükü için Kalıcılık veritabanı yol açar. Kullanan her bir hizmet konağı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> algılama dönemi başına bir kez veritabanı yoklar. Ayar <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> hizmet konakları sayısı büyükse azaltmak, sisteminizin performansı için çok küçük bir zaman aralığı neden olabilir.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>SQL iş akışı örneği Store yapılandırma  
 SQL iş akışı örneği Store aşağıdaki yapılandırma parametrelerini sahiptir:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Bu parametre bildirir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı örneği durumu sıkıştırmak için. Sıkıştırma, Kalıcılık veritabanında depolanır ve bir adanmış veritabanı sunucusuna Kalıcılık veritabanı bulunduğu durumlarda ağ trafiğini azaltır veri miktarını azaltır. Sıkıştırma kullandıysanız, sıkıştırma ve çıkarma örnek durumu için hesaplama kaynaklarını gerektirir. Çoğu durumda, sıkıştırma artan performans verir.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Bu parametre bildirir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tutmak veya tamamlanmış örneklerini silin. Tutma örnekleri artar Kalıcılık veritabanı depolama gereksinimleri ve daha büyük tablolar, müşteri adaylarını tablo arama sürelerini artırır tamamlandı. Tamamlanan örnekleri hata ayıklama veya denetim için gerekli olmadığı sürece, istemek en iyi <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> örneklerine silme tamamlandı. Yalnızca kullanıcı sonunda da bunları kaldırmak için bir işlem kurarsa silinen örneklerinin tutulmalıdır. Tamamlanan iş akışı örneği örnek deposunda bulunduğu sürece bağıntı anahtarları kullanılamayacak unutmayın.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Bu parametre hangi en uzun aralığı tanımlar <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> için Kalıcılık veritabanı yoklar ne zaman yükleneceğini örnekleri bir <xref:System.Activities.Statements.Delay> etkinlik süresi dolar. Varsa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki yoklama aralığı içinde sona erecek olan bir zamanlayıcı bulur böylece sonraki yoklama süreölçeri sağ süresi dolduktan sonra meydana gelir, yoklama aralığını kısaltır. Bu şekilde, yüksek bir uzun süre çalışan zamanlayıcılar doğruluğunu SQL iş akışı örneği Store ulaşır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Azaltma önermiyoruz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, bu artan yükü için Kalıcılık veritabanı yol açar. Kullanan her bir hizmet konağı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> algılama dönemi başına bir kez veritabanı yoklar. Ayar <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> için çok küçük bir aralık hizmet konakları sayısı büyükse sistem performansının düşmesine neden.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Bu parametre hangi konak kilidin Kalıcılık veritabanında yeniler aralığı tanımlar. Bu zaman aralığını kısaltmayı, bir ana bilgisayar veya bilgisayar başarısız olması durumunda iş akışı örnekleri daha hızlı kurtarma olanak sağlar. Öte yandan, bir kısa kilidi yenileme dönemi Kalıcılık veritabanı üzerindeki yükü artırır. Kullanan her bir hizmet konağı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı, kilitler yenileme dönemi başına bir kez güncelleştirilir. Birçok hizmet konakları çalıştıran bir bilgisayara, sisteminizin performansı kilidi yenileme tarafından neden yük azalmaz emin olun. Artırmayı düşünün <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Etkinleştirilirse, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki 30 saniye için kilitli bir örneği yüklemek için yeniden deneme sayısı. Ayarlama <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry veya AggressiveRetry iş akışı, kısa bir süre içinde birden çok ileti alır ve bu iletiler farklı bilgisayarlar tarafından alınır.  
  
 Yük deneme denenmez sürece yük yeniden deneme mekanizması herhangi bir performans yükü sunmaz çünkü <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> her zaman etkin olması.
