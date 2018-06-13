---
title: Kalıcılık en iyi uygulamalar
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 68164cc937c1c718df39c96c3d6ac490ab025fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520194"
---
# <a name="persistence-best-practices"></a>Kalıcılık en iyi uygulamalar
Bu belgenin iş akışı tasarım ve iş akışı kalıcılığı için ilgili yapılandırma en iyi yöntemleri kapsar.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Tasarım ve uygulama dayanıklı iş akışı  
 Genel olarak, iş akışlarını iş için bir olay beklediğinden sırasında iş akışı boşta olduğu sürelerine sahip araya eklemeli nokta kısa gerçekleştirin. Bu olay, bir ileti veya süresi dolan bir Zamanlayıcı gibi öğeleri olabilir. Boşta olduğunda iş akışı örneği unload yapabilmek için hizmet ana bilgisayarı iş akışı örneği kalıcı olması gerekir. Bu seçenek, yalnızca iş akışı örneği (örneğin, bir işlemin tamamlanması beklenirken veya bir zaman uyumsuz geri çağırma bekleniyor) no-persist bölgesinde değilse mümkündür. Kaldırmak bir boş iş akışı örneği izin vermek için iş akışı yazarı işlem kapsam ve zaman uyumsuz etkinlikleri yalnızca kısa süreli eylemler için kullanmanız gerekir. Özellikle, yazarın gecikme tutmalısınız bunlar içindeki etkinlikleri kalıcı Hayır dilimleri olabildiğince kısa.  
  
 Tüm iş akışı tarafından kullanılan veri türleri seri hale getirilebilir olması durumunda bir iş akışı yalnızca kalıcı. Ayrıca, kalıcı iş akışlarında kullanılan özel türler ile Serileştirilebilir olmalıdır <xref:System.Runtime.Serialization.NetDataContractSerializer> tarafından kalıcı için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Kalıcı olmadığını bir iş akışı örneği bir ana bilgisayar veya bilgisayar hatası durumunda kurtarılamıyor. Genel olarak, bir iş akışı örneği erken iş akışının ömrünü kalıcı olması önerilir.  
  
 İş akışınızı uzun bir süredir meşgul ise, iş akışı örneği, meşgul süresi boyunca düzenli olarak kalıcı öneririz. Bunu ekleyerek yapabilirsiniz <xref:System.Activities.Statements.Persist> iş akışı örneği meşgul tutan etkinlikler dizisini boyunca etkinlikler. Bu şekilde, uygulama etki alanı geri dönüştürme, ana bilgisayar hataları veya bilgisayar hatalarını meşgul dönem başlangıcı geri sisteme neden olmaz. Unutmayın, ekleme <xref:System.Activities.Statements.Persist> etkinlikler iş akışınız için bir performans düşmesine neden olabilir.  
  
 Windows Server App Fabric, yapılandırmayı ve kalıcılığı kullanımını büyük ölçüde basitleştirir. Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>Ölçeklenebilirlik parametrelerinin yapılandırması  
 Ölçeklenebilirlik ve performans gereksinimlerini aşağıdaki parametreleri ayarlarını belirleyin:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Bu parametreleri aşağıdaki gibi geçerli senaryosunu göre ayarlamanız gerekir.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Senaryo: Bir küçük sayısının en iyi yanıt süresi gerektiren iş akışı  
 Bu senaryoda, boşta olduklarında tüm iş akışı örnekleri yüklenen kalması gerekir. Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> büyük bir değer. Bu ayarı kullanın, bir iş akışı örneği bilgisayarlar arasında geçmesini önler. Aşağıdakilerden birini veya birkaçını yalnızca doğruysa, bu ayarı kullanın:  
  
-   Bir iş akışı örneği çalışma süresi boyunca tek bir ileti alır.  
  
-   Tek bir bilgisayardaki tüm iş akışı örneklerinde Çalıştır  
  
-   Bir iş akışı örneği tarafından alınan tüm iletileri aynı bilgisayar tarafından alınır.  
  
 Kullanım <xref:System.Activities.Statements.Persist> etkinlikleri veya kümesi <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> hizmet ana bilgisayar veya bilgisayar hataları sonra iş akışı örneğini kurtarmayı etkinleştirmek için 0.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Senaryo: İş akışı örnekleri olan boşta uzun süreler için  
 Bu senaryoda, ayarlamak <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> mümkün olan en kısa sürede kaynakları serbest bırakmak için 0.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Senaryo: İş akışı örnekleri kısa bir süre içinde birden fazla ileti alma  
 Bu senaryoda, ayarlamak <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> bu iletiler aynı bilgisayar tarafından alınırsa 60 saniye. Bu, kaldırma ve bir iş akışı örneğini yükleme hızlı sırası engeller. Bu ayrıca örneği için çok uzun bellekte korumaz.  
  
 Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 ve kümesi <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry ya da bu iletileri farklı bilgisayarlar tarafından alınan, AggressiveRetry. Bu iş akışı örneği başka bir bilgisayar tarafından yüklenecek sağlar.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Senaryo: İş akışı ile kısa süreli gecikme etkinliklerini kullanır  
 Bu senaryoda, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Kalıcılık veritabanı düzenli aralıklarla yoklar örnekler nedeniyle süresi dolmuş yüklenmesi gerektiğini <xref:System.Activities.Statements.Delay> etkinlik. Varsa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> SQL iş akışı örneği deposuna sonraki yoklama aralığında dolacak bir süreölçer kısaltır yoklama aralığını bulur. Sonraki yoklama süreölçeri sağ süresi dolduktan sonra sonra ortaya çıkar. Bu şekilde, SQL iş akışı örneği deposuna tarafından belirlenen yoklama aralığından daha uzun çalıştırılacağı zamanlayıcılar yüksek doğruluğunu başarır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Daha kısa gecikme zamanında işlenmesini etkinleştirmek için iş akışı örneği en az bir yoklama aralığı için bellekte kalması gerekir.  
  
 Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> sona erme zamanı Kalıcılık veritabanına yazmak için 0.  
  
 Ayarlama <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> çok uzun veya buna eşit <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> örneği en az bir yoklama aralığı için bellekte tutmak için.  
  
 Azaltma önermiyoruz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> bu artan yükü için Kalıcılık veritabanında müşteri adayları olduğundan. Kullanan her hizmet ana <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı algılama süresi başına bir kez yoklar. Ayarı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> için çok küçük bir zaman aralığı sisteminizin performansının hizmet ana bilgisayar sayısı büyükse düşmesine neden.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>SQL iş akışı örneği deposu yapılandırma  
 SQL iş akışı örneği deposuna aşağıdaki yapılandırma parametreleri içerir:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Bu parametre bildirir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı örneği durum sıkıştırmak için. Sıkıştırma Kalıcılık veritabanında depolanır ve bir adanmış veritabanı sunucusuna Kalıcılık veritabanının bulunduğu durumlarda ağ trafiğini azaltır veri miktarını azaltır. Sıkıştırma kullanılırsa, sıkıştırma ve örnek durum ayıklamak için hesaplama kaynaklarını gerektirir. Çoğu durumda, performansı artırmak sıkıştırma verir.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Bu parametre bildirir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tutun veya tamamlanmış örneklerini silmek için. Tutma örnekleri artar Kalıcılık veritabanı depolama gereksinimleri ve büyük tablolar, müşteri adaylarını tablo arama kez artıran tamamlandı. Tamamlanan örnekleri hata ayıklama veya denetim için gerekli olmadıkça istemek üzere en iyi <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> silme tamamlandı örnekleri. Yalnızca kullanıcı sonunda bunları kaldırmak için bir işlem kurarsa silinen örneklerinin tutulmalıdır. Tamamlanan iş akışı örneği örnek deposunda bulunduğu sürece bağıntı anahtarları yeniden kullanılamaz unutmayın.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Bu parametre hangi üst aralığı tanımlar <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Kalıcılık veritabanı için yoklar ne zaman yükleneceğini örnekleri bir <xref:System.Activities.Statements.Delay> etkinlik süresi dolar. Varsa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki yoklama aralığı içinde dolacak bir süreölçer bulur böylece sonraki yoklama süreölçeri sağ süresi dolduktan sonra ortaya çıkar ve yoklama aralığı kısaltır. Bu şekilde, SQL iş akışı örneği deposuna daha uzun süre çalışan zamanlayıcılar yüksek doğruluğunu başarır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Azaltma önermiyoruz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, bu artan yükü için Kalıcılık veritabanında yol gösterir. Kullanan her hizmet ana <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> veritabanı algılama süresi başına bir kez yoklar. Ayarı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> için çok küçük bir aralık hizmet ana bilgisayar sayısı büyükse, sisteminizin performansının düşmesine neden.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Bu parametre, konak kendi kilit Kalıcılık veritabanındaki yeniler aralığı tanımlar. Bir ana bilgisayar veya bilgisayar başarısız olursa bu aralığı kısaltmayı daha hızlı kurtarma iş akışı örneği olanak sağlar. Diğer taraftan, Kalıcılık veritabanı kısa kilit yenileme süresini artırır. Kullanan her hizmet ana <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kendi kilitleri veritabanında yenileme süresini başına bir kez güncelleştirilir. Bir bilgisayar birçok hizmet konakları çalıştırıyorsa, kilit yenileme tarafından neden yük sisteminizin performansını azaltamazsınız emin olun. Artırmayı deneyin varsa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Etkinleştirilirse, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonraki 30 saniye kilitli bir örneği yüklemek için yeniden deneme sayısı. Ayarlama <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry veya iş akışının kısa bir süre içinde birden fazla ileti alır ve bu iletileri farklı bilgisayarlar tarafından alınan AggressiveRetry.  
  
 Yük deneme denenmez sürece yük yeniden deneme mekanizması tüm performans yükü sunmaz çünkü <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> her zaman etkin olması.
