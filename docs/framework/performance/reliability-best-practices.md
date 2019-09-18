---
title: Güvenilirlik En İyi Yöntemleri
ms.date: 03/30/2017
helpviewer_keywords:
- marking locks
- rebooting databases
- denial of service attacks
- back-out code
- SQL Server [.NET Framework], reliability
- synchronization, reliability
- single-threaded COM components
- slow leaks
- suspending threads
- asynchronous exception handling
- leaked resources [.NET Framework]
- unmanaged memory
- memory, reliability
- threading [.NET Framework], reliability
- process-wide domain shared states
- shared states
- SafeHandle class, reliability
- reliability contracts [.NET Framework]
- cleanup operations
- constrained execution regions
- CERs
- finalizers, reliability
- reliability [.NET Framework]
- blocks, reliability
- finally clauses
- cross-application domain shared states
- catch blocks
- identifying locks
- writing reliable code
- impersonation
- GC.KeepAlive method
- managed threading
- locks, reliability
- STA-dependent features
- fibers
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8c47091d943aa0d710cec1af83e039bca9ee2d2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046251"
---
# <a name="reliability-best-practices"></a>Güvenilirlik En İyi Yöntemleri

Aşağıdaki güvenilirlik kuralları SQL Server için yönelimlidir; Ancak, bunlar ana bilgisayar tabanlı sunucu uygulamaları için de geçerlidir. SQL Server gibi sunucularda kaynakları sızıntı ve bunların yapılmaması çok önemlidir.  Ancak, bir nesnenin durumunu değiştiren her yöntem için geri dönüş kodu yazılarak gerçekleştirilemez.  Amaç, her konumdaki herhangi bir hatalardan geri dönüş kodu ile kurtarılacak, yüzde 100 güvenilir yönetilen kod yazmak değildir.  Bu, kısa bir süre sonra çok düşük bir görev olacaktır.  Ortak dil çalışma zamanı (CLR), mükemmel kod yazmayı olanaklı hale getirmek için, yönetilen koda kolayca güçlü bir garanti sağlayamaz.  ASP.NET aksine SQL Server, bir veritabanını kabul edilemez bir süre için bir veritabanı kapatılmadan geri dönüştürülmeden yalnızca bir işlem kullandığını unutmayın.

Bu daha zayıf garanti ve tek bir işlemde çalışırken, güvenilirlik, gerekli olduğunda iş parçacıklarını sonlandırarak veya uygulama etki alanlarını geri dönüşüme göre yapılır ve işlemler ya da bellek gibi işletim sistemi kaynaklarının sızmasını sağlamak için önlemler alır.  Bu daha basit bir güvenilirlik kısıtlaması olsa da, önemli bir güvenilirlik gereksinimi de vardır:

- İşletim sistemi kaynaklarını hiçbir şekilde sızıntı.

- Tüm formlardaki tüm yönetilen kilitleri CLR 'ye belirler.

- Çapraz uygulama etki alanı paylaşılan durumunu hiçbir şekilde kesmeyin <xref:System.AppDomain> ve geri dönüşüme sorunsuz bir şekilde çalışır.

Teorik olarak, yönetilen kodu işlemek, <xref:System.Threading.ThreadAbortException> <xref:System.StackOverflowException>ve <xref:System.OutOfMemoryException> özel durumları işlemek üzere yazmak, ancak geliştiricilerin tüm uygulama genelinde bu tür güçlü kodlar yazması beklenmez.  Bu nedenle, bant dışı özel durumlar, yürütülmekte olan iş parçacığının sonlandırılmasının sonucu olarak sonuçlanır; ve sonlandırılan iş parçacığı paylaşılan durumu düzenleiyorsa, iş parçacığının bir kilit <xref:System.AppDomain> içerip içermediğini tespit ederek, kaldırılır.  Paylaşılan durumu düzenleyen bir yöntem sonlandırıldığında, paylaşılan duruma güncelleştirmeler için güvenilir bir geri alma kodu yazılması mümkün olmadığından durum bozuk olur.

.NET Framework sürüm 2,0 ' de, güvenilirlik gerektiren tek konak SQL Server.  Derlemeniz üzerinde çalışacağınızı SQL Server, veritabanında çalışırken devre dışı bırakılan belirli özellikler olsa bile, bu derlemenin her bölümü için güvenilirlik işini yapmalısınız.  Kod Analizi altyapısı kodu derleme düzeyinde incelediği ve devre dışı bırakılan kodu ayırt edemediği için bu gereklidir. Başka bir SQL Server programlama, <xref:System.AppDomain> SQL Server her şeyi tek bir işlemde çalıştırmasının yanı sıra bellek ve işletim sistemi tanıtıcıları gibi tüm kaynakları temizlemek için de geri dönüşüm kullanılır.

Sonlandırıcılara veya kod yıkıcılarına veya `try/finally` geri alma kodu bloklarına bağlı olamaz. Bunlar kesintiye uğramış veya çağrılmayabilir.

Zaman uyumsuz özel durumlar beklenmeyen konumlarda, muhtemelen her makine yönergesi: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>ve <xref:System.OutOfMemoryException>olur.

Yönetilen iş parçacıklarının SQL 'de Win32 iş parçacığı olmaması gerekmez; Bunlar fibers olabilir.

İşlem genelinde veya çapraz uygulama etki alanı kesilebilir paylaşılan durum güvenli bir şekilde değiştirilebilir ve mümkün olduğunda kaçınılmalıdır.

Yetersiz bellek koşulları SQL Server nadir değildir.

SQL Server ' de barındırılan kitaplıklar paylaşılan durumlarını doğru güncelleştirmediğinden, veritabanı yeniden başlatılana kadar kodun kurtarılmaması büyük bir olasılık olur.  Ayrıca, bazı çok büyük durumlarda bu durum SQL Server işleminin başarısız olmasına neden olabilir ve veritabanının yeniden başlatılmasına neden olabilir.  Veritabanının yeniden başlatılması bir Web sitesi alabilir veya şirket işlemlerini, kullanım dışı bir şekilde etkileyebilir.  Bellek veya tanıtıcı gibi işletim sistemi kaynaklarının yavaş sızıntısı, sunucunun, bir kurtarma işlemi olmadan bir veya daha fazla performans düşmesine neden olabilir veya bir müşterinin uygulamasını azaltabilecek sonrası.  Bu senaryolarınızı açıkça önlemek istiyoruz.

## <a name="best-practice-rules"></a>En iyi yöntem kuralları

Sunucuda çalışan yönetilen koda yönelik kod incelemesinin, Framework 'ün kararlılığını ve güvenilirliğini artırmak için yakalayabilecekleri tanıtım. Tüm bu denetimler, genel olarak iyi bir uygulamadır ve sunucuda bir mutlak olmalıdır.

Kullanılmayan bir kilit veya kaynak kısıtlaması durumunda SQL Server bir iş parçacığını durdurur veya bir <xref:System.AppDomain>alt kümesini yok eder.  Bu durumda, yalnızca kısıtlı yürütme bölgesindeki (CER) bir yedek kodun çalıştırılması garanti edilir.

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Kaynak sızıntılarını önlemek için SafeHandle kullanın

Bir <xref:System.AppDomain> kaldırma durumunda, yürütülen `finally` bloklara veya sonlandırıcılara bağlı olamaz, bu nedenle tüm işletim <xref:System.Runtime.InteropServices.SafeHandle> sistemi kaynak erişiminin <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, veya yerine sınıfı aracılığıyla soyut olması önemlidir. benzer sınıflar. Bu, clr 'nin, <xref:System.AppDomain> koparma durumunda bile kullandığınız tutamaçları izlemesine ve kapatılmasına izin verir.  <xref:System.Runtime.InteropServices.SafeHandle>, CLR 'nin her zaman çalışacağı kritik bir Sonlandırıcı kullanacaktır.

İşletim sistemi tanıtıcısı, serbest bırakılana kadar, oluşturulduğu andan itibaren güvenli tanıtıcıda depolanır.  Bir tutamacı sızmak için bir <xref:System.Threading.ThreadAbortException> pencere meydana gelebilir.  Buna ek olarak, platform Invoke, tanıtıcının yaşam süresini izlemeye izin veren tanıtıcıyı sayacaktır. Bu, tanıtıcının yaşam süresinin `Dispose` kapatılmasını sağlar

Yalnızca bir işletim sistemi işleyicisini temizlemek için bir sonlandırıcısı olan çoğu sınıf artık sonlandırıcıyı gerektirmez. Bunun yerine, Sonlandırıcı <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfta olur.

Bunun yerine bir değiştirme değildir. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.SafeHandle>  İşletim sistemi kaynaklarını açıkça atılırken hala olası kaynak çekişmesi ve performans avantajları vardır.  `finally` Kaynakları açıkça atma işleminin tamamlamada yürütülemeyebilir.

<xref:System.Runtime.InteropServices.SafeHandle>, bir işletim sistemi tutamacı boşaltma <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yordamını veya bir döngüde bir dizi tanıtıcıyı boşaltmayı sağlayan, tanıtıcıyı serbest bırakmak için çalışmayı gerçekleştiren kendi yönteminizi uygulamanıza olanak tanır.  CLR bu yöntemin çalıştırılmasını garanti eder.  Bu, tanıtıcının tüm koşullarda serbest bırakılacağını sağlamak için <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> uygulamanın yazarının sorumluluğundadır. Bunun yapılmaması, tanıtıcının sızmasına neden olur, bu da genellikle tanıtıcıyla ilişkili yerel kaynakların sızıntısını sağlar. Bu nedenle, <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfların, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> uygulamanın çağrı sırasında kullanılamayan kaynakların ayrılmasını gerektirmeyecek şekilde oluşturulması önemlidir. Kodunuzun, bu tür arızaları işleyebilmesi ve yerel tanıtıcıyı serbest bırakmak için sözleşmeyi <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> tamamlamasıdır. Hata ayıklama amacıyla, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> kaynak serbest <xref:System.Boolean> bırakmaya engel olan çok zararlı bir hatayla `false` karşılaşıldığında, bir dönüş değeri vardır. Bunun yapılması, sorunu tanımlamaya yardımcı olması için, etkinleştirilirse [releaseHandleFailed](../debug-trace-profile/releasehandlefailed-mda.md) MDA öğesini etkinleştirir. Çalışma zamanını başka hiçbir şekilde etkilemez; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> aynı kaynak için yeniden çağrılmayacak ve sonuç olarak tanıtıcı sızacaktır.

<xref:System.Runtime.InteropServices.SafeHandle>belirli bağlamlarda uygun değildir.  Yöntem bir <xref:System.GC> Sonlandırıcı iş parçacığında çalıştırılabileceğinizden, belirli bir iş parçacığında serbest olması gereken tüm tutamaçlar bir <xref:System.Runtime.InteropServices.SafeHandle>içinde sarmalanmamalıdır. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>

Çalışma zamanı çağrılabilir sarmalayıcılar (RCWs) ek kod olmadan CLR tarafından temizlenebilir.  Platform Invoke kullanan ve bir com nesnesini bir `IUnknown*` <xref:System.IntPtr>veya olarak karşılayan kod için, kodun bir RCW kullanması için yeniden yazılması gerekir.  <xref:System.Runtime.InteropServices.SafeHandle>yönetilen koda geri çağıran yönetilmeyen bir yayın yöntemi olma olasılığı nedeniyle bu senaryo için yeterli olmayabilir.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

İşletim <xref:System.Runtime.InteropServices.SafeHandle> sistemi kaynaklarını kapsüllemek için kullanın. Veya türündeki <xref:System.Runtime.InteropServices.HandleRef> <xref:System.IntPtr>alanları kullanmayın.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Işletim sistemi kaynaklarının sızmasını engellemek için sonlandırıcılardan çalıştırmak zorunda olmadığından emin olun

Sonlandırıcılarınızı dikkatlice inceleyerek, çalıştırılmasa bile önemli bir işletim sistemi kaynağı sızdırılmaz.  Uygulama kararlı bir <xref:System.AppDomain> durumda yürütülürken veya SQL Server gibi bir sunucu kapandığında normal bellekten farklı olarak, bir <xref:System.AppDomain> ani kaldırma işlemi sırasında nesneler sonlandırılmaz.  Bir uygulamanın doğruluğu garanti edilemez, ancak sunucunun bütünlüğü, kaynak sızıntısı olmadan tutulması gerektiğinden, kaynakların bir ani kaldırma durumunda sızdırılmadığından emin olun.  Tüm <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi kaynaklarını serbest bırakmak için kullanın.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Işletim sistemi kaynaklarının sızmasını engellemek için finally yan tümcelerinin çalıştırmak zorunda olmadığından emin olun

`finally`yan tümceleri CERs dışında çalışacak şekilde garanti edilmez ve bu, kitaplık geliştiricilerinin yönetilmeyen kaynakları serbest bırakmak için bir `finally` blok içindeki koda dayanmasını gerektirir.  Kullanılması <xref:System.Runtime.InteropServices.SafeHandle> önerilen çözümdür.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Yerine işletim sistemi kaynaklarını temizlemek için kullanın <xref:System.Runtime.InteropServices.SafeHandle>. `Finalize` Kullanın <xref:System.IntPtr>; kaynakları kapsüllemek <xref:System.Runtime.InteropServices.SafeHandle> için kullanın. Finally yan tümcesinin çalışması gerekiyorsa, bunu bir CER içine koyun.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Tüm kilitler mevcut yönetilen kilitleme kodu ' na gitmelidir

CLR, kod bir kilit içinde olduğunda bilmelidir; böylece iş parçacığını iptal etmek <xref:System.AppDomain> yerine onu kaldırmak için kullanılır.  İş parçacığı tarafından çalıştırılan veriler tutarsız bir durumda bırakılmış olduğundan iş parçacığını iptal etmek tehlikeli olabilir. Bu nedenle, tamamının <xref:System.AppDomain> geri dönüştürülmesi gerekir.  Bir kilidi tespit etmek için başarısız olma sonuçları kilitlenmeler veya hatalı sonuçlar olabilir. Yöntemlerini <xref:System.Threading.Thread.BeginCriticalRegion%2A> ve<xref:System.Threading.Thread.EndCriticalRegion%2A> kilitleme bölgelerini belirlemek için kullanın.  Yalnızca geçerli iş parçacığına uygulanan <xref:System.Threading.Thread> sınıfta statik yöntemlerdir, bir iş parçacığının başka bir iş parçacığının kilit sayısını düzenlemesini önlemeye yardımcı olur.

<xref:System.Threading.Monitor.Enter%2A>ve <xref:System.Threading.Monitor.Exit%2A> bu CLR bildiriminin yerleşik olmasını sağlamak için, bunların kullanımları ve bu yöntemleri kullanan [Lock ifadesinin](../../csharp/language-reference/keywords/lock-statement.md)kullanımı önerilir.

Döndürme kilitleri <xref:System.Threading.AutoResetEvent> gibi diğer kilitleme mekanizmaları, clr 'ye kritik bir bölümün girildiğini bildirmek için bu yöntemleri çağırmalıdır.  Bu yöntemler herhangi bir kilit almaz; kritik bir bölümde kodun yürütüldüğü CLR 'yi bilgilendirir ve iş parçacığını iptal etmek paylaşılan durumu tutarsız bırakabilir.  Özel <xref:System.Threading.ReaderWriterLock> bir sınıf gibi kendi kilit türünü tanımladıysanız, bu kilit sayısı yöntemlerini kullanın.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

<xref:System.Threading.Thread.BeginCriticalRegion%2A> Ve<xref:System.Threading.Thread.EndCriticalRegion%2A>kullanarak tüm kilitleri işaretleyin ve belirler. , <xref:System.Threading.Interlocked.CompareExchange%2A> <xref:System.Threading.Interlocked.Increment%2A>Ve birdöngüsündekullanmayın.<xref:System.Threading.Interlocked.Decrement%2A>  Bu yöntemlerin Win32 türevleri için platform çağırma kullanmayın.  Bir döngüde kullanmayın <xref:System.Threading.Thread.Sleep%2A> .  Geçici alanları kullanmayın.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Temizleme kodu bir catch ve catch bloğunda olmalıdır, catch takip edilmez

Temizleme kodu asla bir `catch` blok izlemelidir; `catch` blok içinde `finally` veya bloğunda olmalıdır.  Bu, normal bir iyi uygulama olmalıdır.  Bir `finally` blok genellikle tercih edilir çünkü her ikisi de bir özel durum oluştuğunda ve `try` bloğunun sonuna genellikle rastlamadığında aynı kodu çalıştırır.  Oluşan beklenmeyen bir özel durum durumunda, örneğin <xref:System.Threading.ThreadAbortException>, temizlik kodu çalışmaz.  Üzerinde `finally` temizleyene olan yönetilmeyen tüm kaynaklar, sızıntıları engellemek için ideal olarak bir <xref:System.Runtime.InteropServices.SafeHandle> öğesine sarmalanmış olmalıdır.  C# , tutamaçlar dahil olmak üzere nesneleri atmak için etkili bir şekilde kullanılabileceğini aklınızda bulabilirsiniz. `using`

Geri <xref:System.AppDomain> dönüşüm, Sonlandırıcı iş parçacığında kaynakları temizleyebilse de, temizleme kodunu doğru yere yerleştirmek de önemlidir.  Bir iş parçacığı kilidi olmayan bir zaman uyumsuz özel durum alırsa, CLR 'yi geri dönüştürmek <xref:System.AppDomain>zorunda kalmadan iş parçacığını sonlandırmayı dener.  Kaynakların daha sonra daha önce temizlenmesini sağlamak yerine daha fazla kaynak kullanılabilir hale getirerek ve yaşam süresini daha iyi yönetebilmenizi sağlar.  Bazı hata kodu yollarındaki bir dosyayı bir tutamacı açık bir şekilde kapatmadıysanız, bir sonraki kod çalıştırıldığında, <xref:System.Runtime.InteropServices.SafeHandle> sonlandırıcının zaten çalıştırılmamasından sonra tam olarak aynı dosyaya erişme girişimi başarısız olabilir.  Bu nedenle, temizleme kodunun var olduğunu ve düzgün çalışmasını sağlamak, kesin olarak gerekli olmasa bile hatalardan daha düzgün ve hızlı bir şekilde kurtarılmasına yardımcı olur.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Temizleme kodunun `catch` bir `finally` blokta olması gerekir. Finally bloğunda Dispose için çağrılar yerleştir.  `catch`blokların bir throw veya Rethrow ile bitmesi gerekir.  Çok sayıda özel durum alabileceğiniz yerde bir ağ bağlantısının yapılıp yapılmayacağını algılayan kod gibi özel durumlar da olsa da, normal koşullarda bir dizi özel durum yakalamak gerektiren tüm kodlar bir kodun başarılı olup olmadığını görmek için test edilmiş olması gerektiğini belirtir.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Uygulama etki alanları arasında işlem genelindeki kesilebilir paylaşılan durum, elemeli veya kısıtlı bir yürütme bölgesi kullanmalıdır

Giriş bölümünde açıklandığı gibi, uygulama etki alanları genelinde işlem genelinde paylaşılan durumları güvenli bir şekilde izleyen yönetilen kodu yazmak çok zor olabilir.  İşlem genelinde paylaşılan durum, uygulama etki alanları arasında, Win32 kodunda, CLR içinde veya uzaktan iletişim kullanılarak yönetilen kodda paylaşılan bir veri yapısı sıralarından oluşur.  Herhangi bir kesilebilir paylaşılan durum, yönetilen kodda doğru şekilde yazılması çok zordur ve statik paylaşılan durum yalnızca harika bir sorun ile yapılabilir.  İşlem genelinde veya makine genelinde paylaşılan durumdaysa, bu dosyayı ortadan kaldırmanın veya kısıtlanmış bir yürütme bölgesi (CER) kullanarak paylaşılan durumu korumanın bir yolunu bulun.  Tanımlanmayan ve düzeltilen paylaşılan durum içeren herhangi bir kitaplığın, kilitlenme için temiz <xref:System.AppDomain> kaldırma gerektiren SQL Server gibi bir konağa neden olabileceğini unutmayın.

Kod bir COM nesnesi kullanıyorsa, bu COM nesnesinin uygulama etki alanları arasında paylaşılmasını önleyin.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Kilitler Işlem genelinde veya uygulama etki alanları arasında çalışmaz.

Geçmişte <xref:System.Threading.Monitor.Enter%2A> ve [Lock deyimleri](../../csharp/language-reference/keywords/lock-statement.md) genel işlem kilitleri oluşturmak için kullanılmıştır.  Örneğin, bu durum, paylaşılan olmayan derlemelerin <xref:System.AppDomain> , <xref:System.Threading.Thread> nesnelerin, yerleşik dizelerin <xref:System.Type> ve uzaktan iletişim ile uygulama etki alanları arasında paylaşılan bazı dizelerin örnekleri gibi çevik sınıflarda kilitlenirken meydana gelir.  Bu kilitler artık işlem genelinde değildir.  İşlem genelinde bir uygulama etki alanı kilidinin varlığını belirlemek için, kilit içindeki kodun diskteki bir dosya veya muhtemelen bir veritabanı gibi herhangi bir harici, kalıcı kaynak kullanıp kullanmadığını belirler.

Bu kod birden çok uygulama etki alanında <xref:System.AppDomain> aynı anda çalıştırılabildiğinden, bir kilit, bir dış kaynak kullanıyorsa, bir kilit alınması sorun oluşmasına neden olabilir.  Bu, bir günlük dosyasına yazarken veya tüm işlem için bir yuvaya bağlamakla ilgili bir sorun olabilir.  Bu değişiklikler, adlandırılmış <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore> örnek kullanmaktan başka bir işlem genel kilidi almak için, yönetilen kod kullanmanın kolay bir yolu olmadığı anlamına gelir.  Aynı anda iki uygulama etki alanında çalıştırmayan kodu oluşturun veya <xref:System.Threading.Mutex> ya <xref:System.Threading.Semaphore> da sınıflarını kullanın.  Varolan kod değiştirilemediğinden, bu eşitlemeye ulaşmak için Win32 adlı bir mutex kullanmayın çünkü fiber modda çalıştırmak, aynı işletim sistemi iş parçacığının bir mutex 'i elde edeceğini ve yayınlamadığını garanti edemeyeceğiniz anlamına gelir.  Kod kilidini, yönetilmeyen kod <xref:System.Threading.Mutex> kullanarak kilidi eşitlemek yerine clr 'nin <xref:System.Threading.AutoResetEvent>farkında olacak şekilde <xref:System.Threading.Semaphore> eşitlemek için, yönetilen sınıf veya bir adlandırılmış, ya da bir adı <xref:System.Threading.ManualResetEvent>kullanmanız gerekir.

#### <a name="avoid-locktypeofmytype"></a>Kilit kullanmaktan kaçının (typeof (MyType))

Paylaşılan derlemelerdeki <xref:System.Type> özel ve ortak nesneler, tüm uygulama etki alanları genelinde paylaşılan kodun yalnızca bir kopyasına sahiptir ve sorunlar da sunar.  Paylaşılan derlemeler için, işlem <xref:System.Type> başına yalnızca bir örnek vardır. Bu, birden çok uygulama etki alanının tam aynı <xref:System.Type> örneği paylaştığı anlamına gelir.  Bir <xref:System.Type> örnek üzerinde kilit alınması, <xref:System.AppDomain>yalnızca ' a değil, tüm işlemi etkileyen bir kilit alır.  Bir nesne<xref:System.Type> üzerinde bir kilit alırsa,buişparçacığıanideniptaledildiğindekilidi<xref:System.AppDomain> serbest bırakmaz.  Bu kilit daha sonra diğer uygulama etki alanlarının kilitlenmesine neden olabilir.

Statik yöntemlerde kilit almanın iyi bir yolu, koda statik bir iç eşitleme nesnesi eklemekten oluşur.  Bu, bir tane varsa sınıf oluşturucusunda başlatılabilir, ancak şu şekilde başlatılabilir:

```csharp
private static Object s_InternalSyncObject;
private static Object InternalSyncObject
{
    get
    {
        if (s_InternalSyncObject == null)
        {
            Object o = new Object();
            Interlocked.CompareExchange(
                ref s_InternalSyncObject, o, null);
        }
        return s_InternalSyncObject;
    }
}
```

Ardından bir kilit alırken, `InternalSyncObject` özelliğini kullanarak kilitlenecek bir nesne elde edin.  Sınıf oluşturucuda iç eşitleme nesnesini oluşturduysanız özelliğini kullanmanız gerekmez.  Çift denetim kilidi başlatma kodu şu örnekteki gibi görünmelidir:

```csharp
public static MyClass SingletonProperty
{
    get
    {
        if (s_SingletonProperty == null)
        {
            lock(InternalSyncObject)
            {
                // Do not use lock(typeof(MyClass))
                if (s_SingletonProperty == null)
                {
                    MyClass tmp = new MyClass(…);
                    // Do all initialization before publishing
                    s_SingletonProperty = tmp;
                }
            }
        }
        return s_SingletonProperty;
    }
}
```

#### <a name="a-note-about-lockthis"></a>Kilit (Bu) ile Ilgili bir nota

Genel olarak erişilebilen tek bir nesne üzerinde kilit almak için genellikle kabul edilebilir.  Ancak nesne, tüm alt sistemin kilitlenmesine neden olabilecek bir tekil nesnedeyse, yukarıdaki tasarım modelini de kullanmayı göz önünde bulundurun.  Örneğin, bir <xref:System.Security.SecurityManager> nesne üzerindeki bir kilit, tüm <xref:System.AppDomain> kullanılamaz <xref:System.AppDomain> hale getirilmesi sırasında kilitlenmeyle sonuçlanabilir. Bu türden herkese açık erişilebilen bir nesne üzerinde kilit almak iyi bir uygulamadır.  Ancak, tek bir koleksiyon veya dizide bir kilit genellikle bir sorun sunmamalıdır.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Uygulama etki alanları genelinde kullanılabilecek veya tanımlayıcı bir kimlik tanıma olmayan türler üzerinde kilit almaz. ,,, <xref:System.Threading.Monitor.Enter%2A> ,, Veya ' den <xref:System.String> <xref:System.ValueType> <xref:System.Reflection.MethodInfo> <xref:System.Reflection.PropertyInfo> türetilen<xref:System.MarshalByRefObject>herhangi bir <xref:System.Type> nesneyi<xref:System.Threading.Thread>çağırmayın.

### <a name="remove-gckeepalive-calls"></a>GC 'yi kaldırın. Canlı tutma çağrıları

Uygun olmayan, var olan kodun önemli bir miktarı, <xref:System.GC.KeepAlive%2A> bunu kullanması veya kullanması durumunda kullanmaz.  <xref:System.Runtime.InteropServices.SafeHandle>' A dönüştürdükten sonra, bir sonlandırıcısı olmadığı ve <xref:System.GC.KeepAlive%2A>işletim sistemi tutamaçlarını sonuçlandırmak için açık <xref:System.Runtime.InteropServices.SafeHandle> olan sınıfların çağrı yapması gerekmez.  Bir çağrıyı <xref:System.GC.KeepAlive%2A> tutmaya yönelik performans maliyeti göz ardı edilebilir olsa da, bir <xref:System.GC.KeepAlive%2A> çağrının, artık mevcut olmayan bir yaşam süresi sorununu gidermek için gerekli veya yeterli olması, kodun bakımını daha zor hale getirir.  Ancak, com birlikte çalışabilirlik clr çağrılabilir sarmalayıcıları (RCWs) <xref:System.GC.KeepAlive%2A> kullanılırken kod için hala gerekli olur.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Kaldırın <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-host-protection-attribute"></a>Konak koruma özniteliğini kullanma

<xref:System.Security.Permissions.HostProtectionAttribute> (HPa), ana bilgisayar koruma gereksinimlerini belirleyen bildirim temelli güvenlik eylemlerinin kullanımını, ana bilgisayarın, belirli bir konak için uygun olmayan şekilde <xref:System.Environment.Exit%2A>tamolarakgüvenilenkodun,örneğin veya<xref:System.Windows.Forms.MessageBox.Show%2A> SQL Server.

HPA yalnızca ortak dil çalışma zamanını barındıran ve SQL Server gibi konak korumasını uygulayan yönetilmeyen uygulamaları etkiler. Uygulandığında, güvenlik eylemi, sınıf veya yöntemin açığa çıkardığı konak kaynaklarına dayalı bir bağlantı talebi oluşturulmasına neden olur. Kod bir istemci uygulamasında veya konak korumalı olmayan bir sunucuda çalışıyorsa, "oturum" özniteliği algılanmadı ve bu nedenle uygulanmadı.

> [!IMPORTANT]
> Bu özniteliğin amacı, güvenlik davranışını değil, konağa özgü programlama modeli kılavuzlarını zorlayasağlamaktır.  Model gereksinimleri <xref:System.Security.Permissions.HostProtectionAttribute> programlama ile uygunluğu denetlemek için bir bağlantı isteği kullanılmasına karşın, güvenlik izni değildir.

Konağın programlama modeli gereksinimleri yoksa bağlantı talepleri gerçekleşmez.

Bu öznitelik aşağıdakileri tanımlar:

- Konak programlama modeline uymayan, ancak zararsız olan Yöntemler veya sınıflar.

- Konak programlama modeline uymayan Yöntemler veya sınıflar ve sunucu tarafından yönetilen kullanıcı kodunun sabitleştirilmesi için yol açabilir.

- Konak programlama modeline uymayan Yöntemler veya sınıflar ve sunucu işleminin sabitinin kararlı hale getirilmesine neden olabilir.

> [!NOTE]
> Konak korumalı bir ortamda yürütülebileceği uygulamalar tarafından çağrılacak bir sınıf kitaplığı oluşturuyorsanız, bu özniteliği kaynak kategorilerini açığa çıkaran <xref:System.Security.Permissions.HostProtectionResource> üyelere uygulamalısınız. Bu özniteliğe sahip .NET Framework sınıf kitaplığı üyeleri yalnızca hemen çağıranın denetlenmesi için yol açabilir.  Kitaplık üyeüme aynı zamanda kendi arayanın aynı şekilde denetimine neden olmalıdır.

Lütfen HPA <xref:System.Security.Permissions.HostProtectionAttribute>hakkında daha fazla bilgi edinin.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

SQL Server için, eşitleme veya iş parçacığı tanıtmak için kullanılan tüm yöntemlerin HPA ile tanımlanması gerekir. Bu durum, durumu paylaşan, eşitlenen veya dış süreçler yöneten yöntemleri içerir. SQL Server etkileyen <xref:System.Security.Permissions.HostProtectionResource.SharedState>değerler, <xref:System.Security.Permissions.HostProtectionResource.Synchronization> ve<xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>'dir. <xref:System.Security.Permissions.HostProtectionResource> Ancak, herhangi <xref:System.Security.Permissions.HostProtectionResource> bir yöntemi ortaya çıkaran herhangi bir yöntem yalnızca SQL 'i etkileyen kaynakları kullanan bir hPa tarafından tanımlanmalıdır.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Yönetilmeyen kodda süresiz olarak Engellenmeyin

Yönetilen kod yerine yönetilmeyen kodda engelleme, CLR iş parçacığını durduramadığı için hizmet reddi saldırısına neden olabilir.  Engellenen bir iş parçacığı, en azından, son <xref:System.AppDomain>derece güvenli olmayan işlemler yapmadan clr 'nin kaldırılmasını engeller.  Windows eşitleme temel kullanımını engellemek, izin verdiğimiz bir şeyin açık bir örneğidir.  Mümkünse, bir yuva üzerinde `ReadFile` yapılan bir çağrıda engelleme yapılabilmelidir — ideal olarak, Windows API bunun zaman aşımı gibi bir işlem için bir mekanizma sağlamalıdır.

Doğal olarak çağıran herhangi bir yöntem ideal, sınırlı bir zaman aşımıyla bir Win32 çağrısı kullanmalıdır.  Kullanıcının zaman aşımını belirtmesini izin veriliyorsa, kullanıcının belirli bir güvenlik izni olmadan sonsuz bir zaman aşımı belirtmemelidir.  Bir kılavuz olarak, bir yöntem ~ 10 saniyeden uzun bir süre boyunca engellense, zaman aşımlarını destekleyen bir sürüm kullanmanız veya ek CLR desteği almanız gerekir.

Soruna neden olan API 'Ler örnekleri aşağıda verilmiştir.  Kanallar (hem anonim hem de adlandırılmış), bir zaman aşımı ile oluşturulabilir; ancak kod, hiçbir şekilde NMPWAIT_WAIT_FOREVER veya `CreateNamedPipe` `WaitNamedPipe` ile hiçbir şekilde çağrı olmamasını sağlamalıdır.  Ayrıca, zaman aşımı belirtilmiş olsa bile beklenmedik engelleme olabilir.  Anonim `WriteFile` bir kanalda çağırmak, tüm baytlar yazılana kadar engeller, yani arabellekte okunmamış veriler varsa `WriteFile` , bu, okuyucu kanal arabelleğinde alan boşaltana kadar engeller.  Yuvalar her zaman bir zaman aşımı mekanizmasını karşılayan bazı API 'leri kullanmalıdır.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Yönetilmeyen kodda zaman aşımı olmadan engelleme, bir hizmet reddi saldırıdır. ,,, Ve `WaitForSingleObject` `WaitForMultipleObjects` `WaitForSingleObjectEx` içinPlatform`MsgWaitForMultipleObjects`çağırma çağrıları gerçekleştirmeyin. `MsgWaitForMultipleObjectsEx`  NMPWAIT_WAIT_FOREVER kullanmayın.

### <a name="identify-any-sta-dependent-features"></a>Herhangi bir STA bağımlı özelliği belirler.

COM tek iş parçacıklı apartmanlar (STAs) kullanan herhangi bir kodu belirler.  SQL Server işleminde STAs devre dışı bırakıldı.  Performans sayaçları veya Pano `CoInitialize`gibi temel özellikler, SQL Server içinde devre dışı bırakılmalıdır.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Sonlandırıcılar eşitleme sorunlarından muaf olduğundan emin olun

.NET Framework sonraki sürümlerinde birden çok Sonlandırıcı iş parçacığı bulunabilir, yani aynı türdeki farklı örneklere yönelik sonlandırıcılar aynı anda çalışır.  Tamamen iş parçacığı güvenli olması gerekmez; Çöp toplayıcı, belirli bir nesne örneği için sonlandırıcıyı yalnızca bir iş parçacığının çalıştıracaktır.  Ancak, birden çok farklı nesne örneğinde eşzamanlı olarak çalışırken yarış durumlarının ve kilitlenmeleri önlemek için Sonlandırıcıların kodlanmış olması gerekir.  Bir günlük dosyasına yazma gibi herhangi bir dış durumu kullanırken, bir sonlandırıcının iş parçacığı sorunları ele alınmalıdır.  İş parçacığı güvenliği sağlamak için sonlandırmada güvenmeyin. Sonlandırıcı iş parçacığında durumu depolamak için iş parçacığı yerel depolama, yönetilen veya yerel olarak kullanmayın.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Sonlandırıcılar, eşitleme sorunlarından muaf olmalıdır. Sonlandırıcıda statik kesilebilir durum kullanmayın.

### <a name="avoid-unmanaged-memory-if-possible"></a>Mümkünse yönetilmeyen belleği önleyin

Yönetilmeyen bellek, tıpkı bir işletim sistemi tutamacı gibi sızmış olabilir. Mümkünse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) [veya bir](../../csharp/language-reference/keywords/fixed-statement.md) Byte [] <xref:System.Runtime.InteropServices.GCHandle> kullanımı gibi sabitlenmiş bir yönetilen nesne kullanarak yığındaki belleği kullanmayı deneyin. <xref:System.GC> Sonuç olarak bunları temizler. Ancak, yönetilmeyen bellek ayırmanız gerekiyorsa, bellek ayırmayı kaydırmak için öğesinden <xref:System.Runtime.InteropServices.SafeHandle> türetilen bir sınıf kullanmayı düşünün.

Yeterli olmayan en az bir büyük harf <xref:System.Runtime.InteropServices.SafeHandle> olduğunu unutmayın.  Bellek ayıran veya boşaltan com Yöntem çağrıları için, bir dll 'nin bellek `CoTaskMemAlloc` ayırması ve bu belleğin ile `CoTaskMemFree`bir başka dll 'nin serbest olması yaygındır.  Bu <xref:System.Runtime.InteropServices.SafeHandle> yerlerde kullanılması, yönetilmeyen belleğin yaşam süresini, diğer dll 'nin belleğin yaşam süresini sağlamak yerine, <xref:System.Runtime.InteropServices.SafeHandle> bu süre boyunca kullanım ömrüne bağlamak için uygun olmayabilir.

### <a name="review-all-uses-of-catchexception"></a>Tüm catch (özel durum) kullanımlarını gözden geçirin

Belirli bir özel durum yerine tüm özel durumları yakalayacak catch blokları artık zaman uyumsuz özel durumları da yakalar.  Her catch (özel durum) bloğunu inceleyerek, atlanan önemli bir kaynak bırakma veya geri alma kodu yoksa, ya da bir <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>veya <xref:System.OutOfMemoryException>işlemek için de catch bloğunun kendisi içinde hatalı davranış olup olmadığını araştırın.  Bu kodun günlüğe kaydedilmesine veya yalnızca belirli özel durumları görebileceğine veya bir özel durumun tam olarak tek bir nedenden dolayı başarısız olduğu varsayımda olabileceğini unutmayın.  Bu varsayımlar dahil <xref:System.Threading.ThreadAbortException>etmek için güncelleştirilmeleri gerekebilir.

Bir <xref:System.FormatException> dizi biçimlendirme yöntemi gibi, sizin belirttiğiniz özel durum türünü yakalamak için tüm özel durumları yakalayan tüm yerleri değiştirmeyi göz önünde bulundurun.  Bu, catch bloğunun beklenmeyen özel durumlar üzerinde çalışmasını önler ve kodun beklenmeyen özel durumları yakalayarak hataları gizlemez olmasını sağlamaya yardımcı olur.  Genel bir kural olarak kitaplık kodunda bir özel durumu işlemez (bir özel durum yakalamanızı gerektiren kod, aradığınız kodda bir tasarım kusurunu belirtebilir).  Bazı durumlarda, bir özel durumu yakalamak ve daha fazla veri sağlamak için farklı bir özel durum türü oluşturmak isteyebilirsiniz.  Bu durumda iç içe geçmiş özel durumları kullanın ve hatanın <xref:System.Exception.InnerException%2A> gerçek nedenini yeni özel durumun özelliğinde depolayarak.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Tüm nesneleri yakalar veya tüm özel durumları yakalayacak Yönetilen koddaki tüm catch bloklarını gözden geçirin.  İçinde C#, bu hem hem de `catch` {} `catch(Exception)`olarakbayrak anlamına gelir. {}  Özel durum türünü çok özel yapmayı düşünün veya beklenmeyen bir özel durum türünü yakaladığı için hatalı bir şekilde hareket etmemesini sağlamak üzere kodu gözden geçirin.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Yönetilen bir Iş parçacığının bir Win32 Iş parçacığı olduğunu varsaymayın; bu bir fiber

Yönetilen iş parçacığı yerel depolama kullanmak çalışır, ancak yönetilmeyen iş parçacığı yerel depolama birimini veya kodun geçerli işletim sistemi iş parçacığında yeniden çalışacağını varsayabilirsiniz.  İş parçacığının yerel ayarı gibi ayarları değiştirmeyin.  Bir kilit giren `InitializeCriticalSection` işletim `CreateMutex` sistemi iş parçacığını gerektirdiğinden ya da kilitden çıkmak için platform Invoke 'ı çağırmayın.  Fibers kullanılırken bu durum olmadığı için, Win32 kritik bölümleri ve zaman uyumu sağlayıcılar doğrudan SQL 'de kullanılamaz.  Yönetilen <xref:System.Threading.Mutex> sınıfın bu iş parçacığı benzeşim sorunlarını işlemediğini unutmayın.

Yönetilen iş parçacığı yerel depolama alanı ve iş parçacığının geçerli kullanıcı <xref:System.Threading.Thread> arabirimi kültürü dahil olmak üzere, yönetilen bir nesne üzerinde durumun büyük bir bölümünü güvenle kullanabilirsiniz.  Ayrıca, mevcut bir statik <xref:System.ThreadStaticAttribute>değişkenin değerini yalnızca geçerli yönetilen iş parçacığı (clr 'de fiber yerel depolama yapmanın başka bir yolu) ile erişilebilir hale getiren öğesini de kullanabilirsiniz.  Programlama modeli nedenleriyle, SQL 'de çalışırken bir iş parçacığının geçerli kültürünü değiştiremezsiniz.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

SQL Server, fiber modda çalışır; iş parçacığı yerel depolama kullanmayın. ,, Ve için `TlsAlloc` `TlsFree` `TlsGetValue`platform çağırma çağrıları kullanmaktan kaçının`TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>SQL Server tanıtıcı kimliğe bürünmeye izin ver

Kimliğe bürünme iş parçacığı düzeyinde çalışır ve SQL fiber modda çalışabilir, yönetilen kod kullanıcıları taklit etmez ve çağırmamalıdır `RevertToSelf`.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

SQL Server tanıtıcı kimliğe bürünmeye izin verin. `RevertToSelf` ,`ImpersonateDdeClientWindow` ,,`SetThreadToken`,, ,`ImpersonateSelf`,,, ,`RpcRevertToSelfEx`Veya kullanmayın. `RpcImpersonateClient` `ImpersonateNamedPipeClient` `RpcRevertToSelf` `ImpersonateAnonymousToken` `DdeImpersonateClient` `ImpersonateLoggedOnUser`

### <a name="do-not-call-threadsuspend"></a>Thread:: Suspend çağrısını çağırma

Bir iş parçacığını askıya alma özelliği basit bir işlem görünebilir, ancak kilitlenmeleri neden olabilir.  Kilit tutan bir iş parçacığı ikinci bir iş parçacığı tarafından askıya alınırsa ve ikinci iş parçacığı aynı kilidi gerçekleştirmeye çalışırsa, bir kilitlenme oluşur.  <xref:System.Threading.Thread.Suspend%2A>Güvenlik, sınıf yükleme, uzaktan iletişim ve yansıma Şu anda kesintiye uğratabilirler.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

' İ çağırmayın <xref:System.Threading.Thread.Suspend%2A>. <xref:System.Threading.Semaphore> Veya<xref:System.Threading.ManualResetEvent> gibi gerçek bir eşitleme temel kullanmayı düşünün.

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Kısıtlı yürütme bölgeleri ve güvenilirlik sözleşmeleri ile kritik Işlemleri koruma

Paylaşılan bir durumu güncelleştiren veya tamamen başarılı ya da tamamen başarısız olması gereken karmaşık bir işlem gerçekleştirirken, kısıtlı bir yürütme bölgesi (CER) tarafından korunduğundan emin olun. Bu, kodun her durumda, ani bir iş parçacığı iptali veya ani <xref:System.AppDomain> kaldırmaların kaldırılması durumunda çalışmasını güvence altına alır.

Bir cer, bir `try/finally` <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>çağrısıyla hemen önce gelen belirli bir bloğudur.

Bunu yapmak, `try` tam zamanında derleyiciye bloğunu çalıştırmadan önce finally bloğundaki tüm kodu hazırlamasını söyler. Bu, finally bloğundaki kodun oluşturuldığına ve her durumda çalışacak şekilde emin olur. Bir cer 'de boş `try` bir bloğa sahip olmayan bir çok seyrek değildir. Bir CER kullanılması zaman uyumsuz iş parçacığı iptal ve bellek dışı özel durumlara karşı koruma sağlar. Ayrıca <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> , daha fazla derin kod için yığın taşlarının de işlediği bir cer formu için bkz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.ConstrainedExecution>
- [SQL Server Programlama ve Konak Koruması Öznitelikleri](sql-server-programming-and-host-protection-attributes.md)
