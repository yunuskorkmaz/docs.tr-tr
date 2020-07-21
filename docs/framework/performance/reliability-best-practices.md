---
title: Güvenilirlik En İyi Yöntemleri
description: SQL Server gibi .NET ana bilgisayar tabanlı sunucu uygulamalarında güvenilirlik için en iyi uygulamalar bölümüne bakın. Kaynakların sızmasını veya alınmasını önleyin.
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
ms.openlocfilehash: 134b71153f95dffd4525f307d291ce4389e0ce60
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474247"
---
# <a name="reliability-best-practices"></a>Güvenilirlik En İyi Yöntemleri

Aşağıdaki güvenilirlik kuralları SQL Server için yönelimlidir; Ancak, bunlar ana bilgisayar tabanlı sunucu uygulamaları için de geçerlidir. SQL Server gibi sunucularda kaynakları sızıntı ve bunların yapılmaması çok önemlidir.  Ancak, bir nesnenin durumunu değiştiren her yöntem için geri dönüş kodu yazılarak gerçekleştirilemez.  Amaç, her konumdaki herhangi bir hatalardan geri dönüş kodu ile kurtarılacak, yüzde 100 güvenilir yönetilen kod yazmak değildir.  Bu, kısa bir süre sonra çok düşük bir görev olacaktır.  Ortak dil çalışma zamanı (CLR), mükemmel kod yazmayı olanaklı hale getirmek için, yönetilen koda kolayca güçlü bir garanti sağlayamaz.  ASP.NET aksine SQL Server, bir veritabanını kabul edilemez bir süre için bir veritabanı kapatılmadan geri dönüştürülmeden yalnızca bir işlem kullandığını unutmayın.

Bu daha zayıf garanti ve tek bir işlemde çalışırken, güvenilirlik, gerekli olduğunda iş parçacıklarını sonlandırarak veya uygulama etki alanlarını geri dönüşüme göre yapılır ve işlemler ya da bellek gibi işletim sistemi kaynaklarının sızmasını sağlamak için önlemler alır.  Bu daha basit bir güvenilirlik kısıtlaması olsa da, önemli bir güvenilirlik gereksinimi de vardır:

- İşletim sistemi kaynaklarını hiçbir şekilde sızıntı.

- Tüm formlardaki tüm yönetilen kilitleri CLR 'ye belirler.

- Çapraz uygulama etki alanı paylaşılan durumunu hiçbir şekilde kesmeyin ve <xref:System.AppDomain> geri dönüşüme sorunsuz bir şekilde çalışır.

Teorik olarak, yönetilen kodu işlemek, ve özel durumları işlemek üzere yazmak, ancak <xref:System.Threading.ThreadAbortException> <xref:System.StackOverflowException> <xref:System.OutOfMemoryException> geliştiricilerin tüm uygulama genelinde bu tür güçlü kodlar yazması beklenmez.  Bu nedenle, bant dışı özel durumlar, yürütülmekte olan iş parçacığının sonlandırılmasının sonucu olarak sonuçlanır; ve sonlandırılan iş parçacığı paylaşılan durumu düzenleiyorsa, iş parçacığının bir kilit içerip içermediğini tespit ederek, <xref:System.AppDomain> kaldırılır.  Paylaşılan durumu düzenleyen bir yöntem sonlandırıldığında, paylaşılan duruma güncelleştirmeler için güvenilir bir geri alma kodu yazılması mümkün olmadığından durum bozuk olur.

.NET Framework sürüm 2,0 ' de, güvenilirlik gerektiren tek konak SQL Server.  Derlemeniz üzerinde çalışacağınızı SQL Server, veritabanında çalışırken devre dışı bırakılan belirli özellikler olsa bile, bu derlemenin her bölümü için güvenilirlik işini yapmalısınız.  Kod Analizi altyapısı kodu derleme düzeyinde incelediği ve devre dışı bırakılan kodu ayırt edemediği için bu gereklidir. Başka bir SQL Server programlama, SQL Server her şeyi tek bir işlemde çalıştırmasının yanı sıra <xref:System.AppDomain> bellek ve işletim sistemi tanıtıcıları gibi tüm kaynakları temizlemek için de geri dönüşüm kullanılır.

Sonlandırıcılara veya `try/finally` kod yıkıcılarına veya geri alma kodu bloklarına bağlı olamaz. Bunlar kesintiye uğramış veya çağrılmayabilir.

Zaman uyumsuz özel durumlar beklenmeyen konumlarda, muhtemelen her makine yönergesi: <xref:System.Threading.ThreadAbortException> , ve olur <xref:System.StackOverflowException> <xref:System.OutOfMemoryException> .

Yönetilen iş parçacıklarının SQL 'de Win32 iş parçacığı olmaması gerekmez; Bunlar fibers olabilir.

İşlem genelinde veya çapraz uygulama etki alanı kesilebilir paylaşılan durum güvenli bir şekilde değiştirilebilir ve mümkün olduğunda kaçınılmalıdır.

Yetersiz bellek koşulları SQL Server nadir değildir.

SQL Server ' de barındırılan kitaplıklar paylaşılan durumlarını doğru güncelleştirmediğinden, veritabanı yeniden başlatılana kadar kodun kurtarılmaması büyük bir olasılık olur.  Ayrıca, bazı çok büyük durumlarda bu durum SQL Server işleminin başarısız olmasına neden olabilir ve veritabanının yeniden başlatılmasına neden olabilir.  Veritabanının yeniden başlatılması bir Web sitesi alabilir veya şirket işlemlerini, kullanım dışı bir şekilde etkileyebilir.  Bellek veya tanıtıcı gibi işletim sistemi kaynaklarının yavaş sızıntısı, sunucunun, bir kurtarma işlemi olmadan bir veya daha fazla performans düşmesine neden olabilir ve bir müşterinin uygulama kullanılabilirliğini düşürür.  Bu senaryolarınızı açıkça önlemek istiyoruz.

## <a name="best-practice-rules"></a>En iyi yöntem kuralları

Sunucuda çalışan yönetilen koda yönelik kod incelemesinin, Framework 'ün kararlılığını ve güvenilirliğini artırmak için yakalayabilecekleri tanıtım. Tüm bu denetimler, genel olarak iyi bir uygulamadır ve sunucuda bir mutlak olmalıdır.

Kullanılmayan bir kilit veya kaynak kısıtlaması durumunda SQL Server bir iş parçacığını durdurur veya bir alt kümesini yok eder <xref:System.AppDomain> .  Bu durumda, yalnızca kısıtlı yürütme bölgesindeki (CER) bir yedek kodun çalıştırılması garanti edilir.

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Kaynak sızıntılarını önlemek için SafeHandle kullanın

Bir kaldırma durumunda, <xref:System.AppDomain> `finally` yürütülen bloklara veya sonlandırıcılara bağlı olamaz, bu nedenle tüm işletim sistemi kaynak erişiminin <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.IntPtr> , veya benzer sınıflar yerine sınıf aracılığıyla soyut olması önemlidir <xref:System.Runtime.InteropServices.HandleRef> . Bu, CLR 'nin, koparma durumunda bile kullandığınız tutamaçları izlemesine ve kapatılmasına izin verir <xref:System.AppDomain> .  <xref:System.Runtime.InteropServices.SafeHandle>, CLR 'nin her zaman çalışacağı kritik bir Sonlandırıcı kullanacaktır.

İşletim sistemi tanıtıcısı, serbest bırakılana kadar, oluşturulduğu andan itibaren güvenli tanıtıcıda depolanır.  Bir <xref:System.Threading.ThreadAbortException> tutamacı sızmak için bir pencere meydana gelebilir.  Buna ek olarak, platform Invoke, tanıtıcının yaşam süresini izlemeye izin veren tanıtıcıyı sayacaktır. Bu, tanıtıcının yaşam süresinin kapatılmasını sağlar `Dispose`

Yalnızca bir işletim sistemi işleyicisini temizlemek için bir sonlandırıcısı olan çoğu sınıf artık sonlandırıcıyı gerektirmez. Bunun yerine, Sonlandırıcı <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfta olur.

Bunun <xref:System.Runtime.InteropServices.SafeHandle> yerine bir değiştirme değildir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> .  İşletim sistemi kaynaklarını açıkça atılırken hala olası kaynak çekişmesi ve performans avantajları vardır.  `finally`Kaynakları açıkça atma işleminin tamamlamada yürütülemeyebilir.

<xref:System.Runtime.InteropServices.SafeHandle><xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, bir işletim sistemi tutamacı boşaltma yordamını veya bir döngüde bir dizi tanıtıcıyı boşaltmayı sağlayan, tanıtıcıyı serbest bırakmak için çalışmayı gerçekleştiren kendi yönteminizi uygulamanıza olanak tanır.  CLR bu yöntemin çalıştırılmasını garanti eder.  Bu, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> tanıtıcının tüm koşullarda serbest bırakılacağını sağlamak için uygulamanın yazarının sorumluluğundadır. Bunun yapılmaması, tanıtıcının sızmasına neden olur, bu da genellikle tanıtıcıyla ilişkili yerel kaynakların sızıntısını sağlar. Bu nedenle, <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfların, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> uygulamanın çağrı sırasında kullanılamayan kaynakların ayrılmasını gerektirmeyecek şekilde oluşturulması önemlidir. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Kodunuzun, bu tür arızaları işleyebilmesi ve yerel tanıtıcıyı serbest bırakmak için sözleşmeyi tamamlamasıdır. Hata ayıklama amacıyla, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> <xref:System.Boolean> `false` kaynak serbest bırakmaya engel olan çok zararlı bir hatayla karşılaşıldığında, bir dönüş değeri vardır. Bunun yapılması, sorunu tanımlamaya yardımcı olması için, etkinleştirilirse [releaseHandleFailed](../debug-trace-profile/releasehandlefailed-mda.md) MDA öğesini etkinleştirir. Çalışma zamanını başka hiçbir şekilde etkilemez; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>aynı kaynak için yeniden çağrılmayacak ve sonuç olarak tanıtıcı sızacaktır.

<xref:System.Runtime.InteropServices.SafeHandle>belirli bağlamlarda uygun değildir.  <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Yöntem bir <xref:System.GC> Sonlandırıcı iş parçacığında çalıştırılabileceğinizden, belirli bir iş parçacığında serbest olması gereken tüm tutamaçlar bir içinde sarmalanmamalıdır <xref:System.Runtime.InteropServices.SafeHandle> .

Çalışma zamanı çağrılabilir sarmalayıcılar (RCWs) ek kod olmadan CLR tarafından temizlenebilir.  Platform Invoke kullanan ve bir COM nesnesini bir veya olarak karşılayan kod için `IUnknown*` <xref:System.IntPtr> , kodun bir RCW kullanması için yeniden yazılması gerekir.  <xref:System.Runtime.InteropServices.SafeHandle>yönetilen koda geri çağıran yönetilmeyen bir yayın yöntemi olma olasılığı nedeniyle bu senaryo için yeterli olmayabilir.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

<xref:System.Runtime.InteropServices.SafeHandle>İşletim sistemi kaynaklarını kapsüllemek için kullanın. <xref:System.Runtime.InteropServices.HandleRef>Veya türündeki alanları kullanmayın <xref:System.IntPtr> .

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>İşletim sistemi kaynaklarının sızmasını engellemek için sonlandırıcılardan çalıştırmak zorunda olmadığından emin olun

Sonlandırıcılarınızı dikkatlice inceleyerek, çalıştırılmasa bile önemli bir işletim sistemi kaynağı sızdırılmaz.  <xref:System.AppDomain>Uygulama kararlı bir durumda yürütülürken veya SQL Server gibi bir sunucu kapandığında normal bellekten farklı olarak, bir ani kaldırma işlemi sırasında nesneler sonlandırılmaz <xref:System.AppDomain> .  Bir uygulamanın doğruluğu garanti edilemez, ancak sunucunun bütünlüğü, kaynak sızıntısı olmadan tutulması gerektiğinden, kaynakların bir ani kaldırma durumunda sızdırılmadığından emin olun.  <xref:System.Runtime.InteropServices.SafeHandle>Tüm işletim sistemi kaynaklarını serbest bırakmak için kullanın.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>İşletim sistemi kaynaklarının sızmasını engellemek için finally yan tümcelerinin çalıştırmak zorunda olmadığından emin olun

`finally`yan tümceleri CERs dışında çalışacak şekilde garanti edilmez ve bu, kitaplık geliştiricilerinin `finally` yönetilmeyen kaynakları serbest bırakmak için bir blok içindeki koda dayanmasını gerektirir.  Kullanılması <xref:System.Runtime.InteropServices.SafeHandle> önerilen çözümdür.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

<xref:System.Runtime.InteropServices.SafeHandle>Yerine işletim sistemi kaynaklarını temizlemek için kullanın `Finalize` . Kullanın <xref:System.IntPtr> ; <xref:System.Runtime.InteropServices.SafeHandle> kaynakları kapsüllemek için kullanın. Finally yan tümcesinin çalışması gerekiyorsa, bunu bir CER içine koyun.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Tüm kilitler mevcut yönetilen kilitleme kodu ' na gitmelidir

CLR, kod bir kilit içinde olduğunda bilmelidir; böylece iş parçacığını iptal etmek yerine onu kaldırmak için kullanılır <xref:System.AppDomain> .  İş parçacığı tarafından çalıştırılan veriler tutarsız bir durumda bırakılmış olduğundan iş parçacığını iptal etmek tehlikeli olabilir. Bu nedenle, tamamının <xref:System.AppDomain> geri dönüştürülmesi gerekir.  Bir kilidi tespit etmek için başarısız olma sonuçları kilitlenmeler veya hatalı sonuçlar olabilir. Yöntemlerini <xref:System.Threading.Thread.BeginCriticalRegion%2A> ve <xref:System.Threading.Thread.EndCriticalRegion%2A> kilitleme bölgelerini belirlemek için kullanın.  <xref:System.Threading.Thread>Yalnızca geçerli iş parçacığına uygulanan sınıfta statik yöntemlerdir, bir iş parçacığının başka bir iş parçacığının kilit sayısını düzenlemesini önlemeye yardımcı olur.

<xref:System.Threading.Monitor.Enter%2A>ve <xref:System.Threading.Monitor.Exit%2A> Bu clr bildiriminin yerleşik olmasını sağlamak için, bunların kullanımları ve bu yöntemleri kullanan [Lock ifadesinin](../../csharp/language-reference/keywords/lock-statement.md)kullanımı önerilir.

Döndürme kilitleri gibi diğer kilitleme mekanizmaları <xref:System.Threading.AutoResetEvent> , clr 'ye kritik bir bölümün girildiğini bildirmek için bu yöntemleri çağırmalıdır.  Bu yöntemler herhangi bir kilit almaz; kritik bir bölümde kodun yürütüldüğü CLR 'yi bilgilendirir ve iş parçacığını iptal etmek paylaşılan durumu tutarsız bırakabilir.  Özel bir sınıf gibi kendi kilit türünü tanımladıysanız <xref:System.Threading.ReaderWriterLock> , bu kilit sayısı yöntemlerini kullanın.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Ve kullanarak tüm kilitleri işaretleyin ve <xref:System.Threading.Thread.BeginCriticalRegion%2A> belirler <xref:System.Threading.Thread.EndCriticalRegion%2A> . <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A> Ve <xref:System.Threading.Interlocked.Decrement%2A> bir döngüsünde kullanmayın.  Bu yöntemlerin Win32 türevleri için platform çağırma kullanmayın.  <xref:System.Threading.Thread.Sleep%2A>Bir döngüde kullanmayın.  Geçici alanları kullanmayın.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Temizleme kodu bir catch ve catch bloğunda olmalıdır, catch takip edilmez

Temizleme kodu asla bir blok izlemelidir `catch` ; `finally` blok içinde veya `catch` bloğunda olmalıdır. Bu, normal bir iyi uygulama olmalıdır. Bir `finally` blok genellikle tercih edilir çünkü her ikisi de bir özel durum oluştuğunda ve `try` bloğunun sonuna genellikle rastlamadığında aynı kodu çalıştırır.  Oluşan beklenmeyen bir özel durum durumunda, örneğin <xref:System.Threading.ThreadAbortException> , temizlik kodu çalışmaz.  Üzerinde temizleyene olan yönetilmeyen tüm kaynaklar, `finally` sızıntıları engellemek için ideal olarak bir öğesine sarmalanmış olmalıdır <xref:System.Runtime.InteropServices.SafeHandle> .  C# `using` anahtar sözcüğünün tutamaçlar dahil olmak üzere nesneleri atmak için etkili bir şekilde kullanılabileceğini aklınızda bulabilirsiniz.

<xref:System.AppDomain>Geri dönüşüm, Sonlandırıcı iş parçacığında kaynakları temizleyebilse de, temizleme kodunu doğru yere yerleştirmek de önemlidir. Bir iş parçacığı kilidi olmayan bir zaman uyumsuz özel durum alırsa, CLR 'yi geri dönüştürmek zorunda kalmadan iş parçacığını sonlandırmayı dener <xref:System.AppDomain> .  Kaynakların daha sonra daha önce temizlenmesini sağlamak yerine daha fazla kaynak kullanılabilir hale getirerek ve yaşam süresini daha iyi yönetebilmenizi sağlar. Bazı hata kodu yollarındaki bir dosyayı bir tutamacı açık bir şekilde kapatmadıysanız <xref:System.Runtime.InteropServices.SafeHandle> , bir sonraki kod çalıştırıldığında, sonlandırıcının zaten çalıştırılmamasından sonra tam olarak aynı dosyaya erişme girişimi başarısız olabilir.  Bu nedenle, temizleme kodunun var olduğunu ve düzgün çalışmasını sağlamak, kesin olarak gerekli olmasa bile hatalardan daha düzgün ve hızlı bir şekilde kurtarılmasına yardımcı olur.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Temizleme kodunun `catch` bir blokta olması gerekir `finally` . Finally bloğunda Dispose için çağrılar yerleştir. `catch`blokların bir throw veya Rethrow ile bitmesi gerekir. Çok sayıda özel durum almanızı sağlayan bir ağ bağlantısının yapılıp yapılmayacağını algılayan kod gibi özel durumlar da olsa da, normal koşullarda bir dizi özel durumun yakalanmasını gerektiren tüm kodlar kodun başarılı olup olmayacağını görmek için kodun test edilip edilmeyeceğini belirten bir bildirim vermelidir.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Uygulama etki alanları arasında işlem genelindeki kesilebilir paylaşılan durum, elemeli veya kısıtlı bir yürütme bölgesi kullanmalıdır

Giriş bölümünde açıklandığı gibi, uygulama etki alanları genelinde işlem genelinde paylaşılan durumları güvenli bir şekilde izleyen yönetilen kodu yazmak çok zor olabilir.  İşlem genelinde paylaşılan durum, uygulama etki alanları arasında, Win32 kodunda, CLR içinde veya uzaktan iletişim kullanılarak yönetilen kodda paylaşılan bir veri yapısı sıralarından oluşur.  Herhangi bir kesilebilir paylaşılan durum, yönetilen kodda doğru şekilde yazılması çok zordur ve statik paylaşılan durum yalnızca harika bir sorun ile yapılabilir.  İşlem genelinde veya makine genelinde paylaşılan durumdaysa, bu dosyayı ortadan kaldırmanın veya kısıtlanmış bir yürütme bölgesi (CER) kullanarak paylaşılan durumu korumanın bir yolunu bulun.  Tanımlanmayan ve düzeltilen paylaşılan durum içeren herhangi bir kitaplığın, kilitlenme için temiz kaldırma gerektiren SQL Server gibi bir konağa neden olabileceğini unutmayın <xref:System.AppDomain> .

Kod bir COM nesnesi kullanıyorsa, bu COM nesnesinin uygulama etki alanları arasında paylaşılmasını önleyin.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Kilitler işlem genelinde veya uygulama etki alanları arasında çalışmaz.

Geçmişte <xref:System.Threading.Monitor.Enter%2A> ve [Lock deyimleri](../../csharp/language-reference/keywords/lock-statement.md) genel işlem kilitleri oluşturmak için kullanılmıştır.  Örneğin, bu durum, <xref:System.AppDomain> <xref:System.Type> paylaşılan olmayan derlemelerin, <xref:System.Threading.Thread> nesnelerin, yerleşik dizelerin ve uzaktan iletişim ile uygulama etki alanları arasında paylaşılan bazı dizelerin örnekleri gibi çevik sınıflarda kilitlenirken meydana gelir.  Bu kilitler artık işlem genelinde değildir.  İşlem genelinde bir uygulama etki alanı kilidinin varlığını belirlemek için, kilit içindeki kodun diskteki bir dosya veya muhtemelen bir veritabanı gibi herhangi bir harici, kalıcı kaynak kullanıp kullanmadığını belirler.

<xref:System.AppDomain>Bu kod birden çok uygulama etki alanında aynı anda çalıştırılabildiğinden, bir kilit, bir dış kaynak kullanıyorsa, bir kilit alınması sorun oluşmasına neden olabilir.  Bu, bir günlük dosyasına yazarken veya tüm işlem için bir yuvaya bağlamakla ilgili bir sorun olabilir.  Bu değişiklikler, adlandırılmış veya örnek kullanmaktan başka bir işlem genel kilidi almak için, yönetilen kod kullanmanın kolay bir yolu olmadığı anlamına gelir <xref:System.Threading.Mutex> <xref:System.Threading.Semaphore> .  Aynı anda iki uygulama etki alanında çalıştırmayan kodu oluşturun veya <xref:System.Threading.Mutex> ya da <xref:System.Threading.Semaphore> sınıflarını kullanın.  Varolan kod değiştirilemediğinden, bu eşitlemeye ulaşmak için Win32 adlı bir mutex kullanmayın çünkü fiber modda çalıştırmak, aynı işletim sistemi iş parçacığının bir mutex 'i elde edeceğini ve yayınlamadığını garanti edemeyeceğiniz anlamına gelir.  <xref:System.Threading.Mutex> <xref:System.Threading.ManualResetEvent> <xref:System.Threading.AutoResetEvent> <xref:System.Threading.Semaphore> Kod kilidini, yönetilmeyen kod kullanarak kilidi eşitlemek yerine clr 'nin farkında olacak şekilde eşitlemek için, yönetilen sınıf veya bir adlandırılmış, ya da bir adı kullanmanız gerekir.

#### <a name="avoid-locktypeofmytype"></a>Kilit kullanmaktan kaçının (typeof (MyType))

<xref:System.Type>Paylaşılan derlemelerdeki özel ve ortak nesneler, tüm uygulama etki alanları genelinde paylaşılan kodun yalnızca bir kopyasına sahiptir ve sorunlar da sunar.  Paylaşılan derlemeler için, işlem başına yalnızca bir örnek vardır <xref:System.Type> . Bu, birden çok uygulama etki alanının tam aynı örneği paylaştığı anlamına gelir <xref:System.Type> .  Bir örnek üzerinde kilit alınması <xref:System.Type> , yalnızca ' a değil, tüm işlemi etkileyen bir kilit alır <xref:System.AppDomain> .  Bir <xref:System.AppDomain> nesne üzerinde bir kilit alırsa <xref:System.Type> , bu iş parçacığı aniden iptal edildiğinde kilidi serbest bırakmaz.  Bu kilit daha sonra diğer uygulama etki alanlarının kilitlenmesine neden olabilir.

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

#### <a name="a-note-about-lockthis"></a>Kilit (Bu) ile ilgili bir nota

Genel olarak erişilebilen tek bir nesne üzerinde kilit almak için genellikle kabul edilebilir.  Ancak nesne, tüm alt sistemin kilitlenmesine neden olabilecek bir tekil nesnedeyse, yukarıdaki tasarım modelini de kullanmayı göz önünde bulundurun.  Örneğin, bir nesne üzerindeki bir kilit, <xref:System.Security.SecurityManager> <xref:System.AppDomain> Tüm kullanılamaz hale getirilmesi sırasında kilitlenmeyle sonuçlanabilir <xref:System.AppDomain> . Bu türden herkese açık erişilebilen bir nesne üzerinde kilit almak iyi bir uygulamadır.  Ancak, tek bir koleksiyon veya dizide bir kilit genellikle bir sorun sunmamalıdır.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Uygulama etki alanları genelinde kullanılabilecek veya tanımlayıcı bir kimlik tanıma olmayan türler üzerinde kilit almaz. ,,,,, <xref:System.Threading.Monitor.Enter%2A> <xref:System.Type> Veya ' <xref:System.Reflection.MethodInfo> <xref:System.Reflection.PropertyInfo> <xref:System.String> <xref:System.ValueType> <xref:System.Threading.Thread> den türetilen herhangi bir nesneyi <xref:System.MarshalByRefObject> çağırmayın.

### <a name="remove-gckeepalive-calls"></a>GC 'yi kaldırın. Canlı tutma çağrıları

Uygun olmayan, var olan kodun önemli bir miktarı, bunu kullanması <xref:System.GC.KeepAlive%2A> veya kullanması durumunda kullanmaz.  <xref:System.Runtime.InteropServices.SafeHandle>' A dönüştürdükten sonra, <xref:System.GC.KeepAlive%2A> bir sonlandırıcısı olmadığı ve <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi tutamaçlarını sonuçlandırmak için açık olan sınıfların çağrı yapması gerekmez.  Bir çağrıyı tutmaya yönelik performans maliyeti göz ardı edilebilir olsa da <xref:System.GC.KeepAlive%2A> , bir çağrının, <xref:System.GC.KeepAlive%2A> artık mevcut olmayan bir yaşam süresi sorununu gidermek için gerekli veya yeterli olması, kodun bakımını daha zor hale getirir.  Ancak, COM birlikte çalışabilirlik CLR çağrılabilir sarmalayıcıları (RCWs) kullanılırken <xref:System.GC.KeepAlive%2A> kod için hala gerekli olur.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Kaldırın <xref:System.GC.KeepAlive%2A> .

### <a name="use-the-hostprotection-attribute"></a>HostProtection özniteliğini kullanma

<xref:System.Security.Permissions.HostProtectionAttribute>(HPa), konak koruma gereksinimlerini belirlemede, ana bilgisayarın, örneğin veya SQL Server gibi belirli bir konak için uygun olmayan belirli yöntemleri aramasını engellemesine olanak tanımak için bildirim temelli güvenlik eylemlerinin kullanımını sağlar <xref:System.Environment.Exit%2A> <xref:System.Windows.Forms.MessageBox.Show%2A> .

HPA yalnızca ortak dil çalışma zamanını barındıran ve SQL Server gibi konak korumasını uygulayan yönetilmeyen uygulamaları etkiler. Uygulandığında, güvenlik eylemi, sınıf veya yöntemin açığa çıkardığı konak kaynaklarına dayalı bir bağlantı talebi oluşturulmasına neden olur. Kod bir istemci uygulamasında veya konak korumalı olmayan bir sunucuda çalışıyorsa, "oturum" özniteliği algılanmadı ve bu nedenle uygulanmadı.

> [!IMPORTANT]
> Bu özniteliğin amacı, güvenlik davranışını değil, konağa özgü programlama modeli kılavuzlarını zorlayasağlamaktır.  Model gereksinimleri programlama ile uygunluğu denetlemek için bir bağlantı isteği kullanılmasına karşın, <xref:System.Security.Permissions.HostProtectionAttribute> güvenlik izni değildir.

Konağın programlama modeli gereksinimleri yoksa bağlantı talepleri gerçekleşmez.

Bu öznitelik aşağıdakileri tanımlar:

- Konak programlama modeline uymayan, ancak zararsız olan Yöntemler veya sınıflar.

- Konak programlama modeline uymayan Yöntemler veya sınıflar ve sunucu tarafından yönetilen kullanıcı kodunun sabitleştirilmesi için yol açabilir.

- Konak programlama modeline uymayan Yöntemler veya sınıflar ve sunucu işleminin sabitinin kararlı hale getirilmesine neden olabilir.

> [!NOTE]
> Konak korumalı bir ortamda yürütülebileceği uygulamalar tarafından çağrılacak bir sınıf kitaplığı oluşturuyorsanız, bu özniteliği kaynak kategorilerini açığa çıkaran üyelere uygulamalısınız <xref:System.Security.Permissions.HostProtectionResource> . Bu özniteliğe sahip .NET Framework sınıf kitaplığı üyeleri yalnızca hemen çağıranın denetlenmesi için yol açabilir.  Kitaplık üyeüme aynı zamanda kendi arayanın aynı şekilde denetimine neden olmalıdır.

Lütfen HPA hakkında daha fazla bilgi edinin <xref:System.Security.Permissions.HostProtectionAttribute> .

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

SQL Server için, eşitleme veya iş parçacığı tanıtmak için kullanılan tüm yöntemlerin HPA ile tanımlanması gerekir. Bu durum, durumu paylaşan, eşitlenen veya dış süreçler yöneten yöntemleri içerir. <xref:System.Security.Permissions.HostProtectionResource>SQL Server etkileyen değerler <xref:System.Security.Permissions.HostProtectionResource.SharedState> , ve ' dir <xref:System.Security.Permissions.HostProtectionResource.Synchronization> <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt> . Ancak, herhangi bir yöntemi ortaya çıkaran herhangi <xref:System.Security.Permissions.HostProtectionResource> bir yöntem yalnızca SQL 'i etkileyen kaynakları kullanan BIR HPA tarafından tanımlanmalıdır.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Yönetilmeyen kodda süresiz olarak engellenmeyin

Yönetilen kod yerine yönetilmeyen kodda engelleme, CLR iş parçacığını durduramadığı için hizmet reddi saldırısına neden olabilir.  Engellenen bir iş parçacığı, <xref:System.AppDomain> en azından, son derece güvenli olmayan işlemler yapmadan clr 'nin kaldırılmasını engeller.  Windows eşitleme temel kullanımını engellemek, izin verdiğimiz bir şeyin açık bir örneğidir.  `ReadFile`Mümkünse, bir yuva üzerinde yapılan bir çağrıda engelleme yapılabilmelidir — ideal olarak, WINDOWS API bunun zaman aşımı gibi bir işlem için bir mekanizma sağlamalıdır.

Doğal olarak çağıran herhangi bir yöntem ideal, sınırlı bir zaman aşımıyla bir Win32 çağrısı kullanmalıdır.  Kullanıcının zaman aşımını belirtmesini izin veriliyorsa, kullanıcının belirli bir güvenlik izni olmadan sonsuz bir zaman aşımı belirtmemelidir.  Bir kılavuz olarak, bir yöntem ~ 10 saniyeden uzun bir süre boyunca engellense, zaman aşımlarını destekleyen bir sürüm kullanmanız veya ek CLR desteği almanız gerekir.

Soruna neden olan API 'Ler örnekleri aşağıda verilmiştir.  Kanallar (hem anonim hem de adlandırılmış), bir zaman aşımı ile oluşturulabilir; Ancak, kod NMPWAIT_WAIT_FOREVER hiçbir şekilde hiçbir şekilde çağrı olmamasını sağlamalıdır `CreateNamedPipe` `WaitNamedPipe` .  Ayrıca, zaman aşımı belirtilmiş olsa bile beklenmedik engelleme olabilir.  `WriteFile`Anonim bir kanalda çağırmak, tüm baytlar yazılana kadar engeller, yani arabellekte okunmamış veriler varsa, bu, `WriteFile` okuyucu kanal arabelleğinde alan boşaltana kadar engeller.  Yuvalar her zaman bir zaman aşımı mekanizmasını karşılayan bazı API 'leri kullanmalıdır.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Yönetilmeyen kodda zaman aşımı olmadan engelleme, bir hizmet reddi saldırıdır. ,,, Ve için platform çağırma çağrıları gerçekleştirmeyin `WaitForSingleObject` `WaitForSingleObjectEx` `WaitForMultipleObjects` `MsgWaitForMultipleObjects` `MsgWaitForMultipleObjectsEx` .  NMPWAIT_WAIT_FOREVER kullanmayın.

### <a name="identify-any-sta-dependent-features"></a>STA bağımlı tüm özellikleri tanımla

COM tek iş parçacıklı apartmanlar (STAs) kullanan herhangi bir kodu belirler.  SQL Server işleminde STAs devre dışı bırakıldı.  `CoInitialize`Performans sayaçları veya pano gibi temel özellikler, SQL Server içinde devre dışı bırakılmalıdır.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Sonlandırıcılar eşitleme sorunlarından muaf olduğundan emin olun

.NET Framework sonraki sürümlerinde birden çok Sonlandırıcı iş parçacığı bulunabilir, yani aynı türdeki farklı örneklere yönelik sonlandırıcılar aynı anda çalışır.  Tamamen iş parçacığı güvenli olması gerekmez; Çöp toplayıcı, belirli bir nesne örneği için sonlandırıcıyı yalnızca bir iş parçacığının çalıştıracaktır.  Ancak, birden çok farklı nesne örneğinde eşzamanlı olarak çalışırken yarış durumlarının ve kilitlenmeleri önlemek için Sonlandırıcıların kodlanmış olması gerekir.  Bir günlük dosyasına yazma gibi herhangi bir dış durumu kullanırken, bir sonlandırıcının iş parçacığı sorunları ele alınmalıdır.  İş parçacığı güvenliği sağlamak için sonlandırmada güvenmeyin. Sonlandırıcı iş parçacığında durumu depolamak için iş parçacığı yerel depolama, yönetilen veya yerel olarak kullanmayın.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Sonlandırıcılar, eşitleme sorunlarından muaf olmalıdır. Sonlandırıcıda statik kesilebilir durum kullanmayın.

### <a name="avoid-unmanaged-memory-if-possible"></a>Mümkünse yönetilmeyen belleği önleyin

Yönetilmeyen bellek, tıpkı bir işletim sistemi tutamacı gibi sızmış olabilir. Mümkünse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) [veya bir](../../csharp/language-reference/keywords/fixed-statement.md) <xref:System.Runtime.InteropServices.GCHandle> Byte [] kullanımı gibi sabitlenmiş bir yönetilen nesne kullanarak yığındaki belleği kullanmayı deneyin. <xref:System.GC>Sonuç olarak bunları temizler. Ancak, yönetilmeyen bellek ayırmanız gerekiyorsa, <xref:System.Runtime.InteropServices.SafeHandle> bellek ayırmayı kaydırmak için öğesinden türetilen bir sınıf kullanmayı düşünün.

Yeterli olmayan en az bir büyük harf olduğunu unutmayın <xref:System.Runtime.InteropServices.SafeHandle> . Bellek ayıran veya boşaltan COM Yöntem çağrıları için, bir DLL 'nin bellek ayırması ve `CoTaskMemAlloc` Bu belleğin ile bir başka dll 'nin serbest olması yaygındır `CoTaskMemFree` .  <xref:System.Runtime.InteropServices.SafeHandle>Bu yerlerde kullanılması, yönetilmeyen belleğin yaşam süresini, <xref:System.Runtime.InteropServices.SafeHandle> diğer dll 'nin belleğin yaşam süresini sağlamak yerine, bu süre boyunca kullanım ömrüne bağlamak için uygun olmayabilir.

### <a name="review-all-uses-of-catchexception"></a>Tüm catch (özel durum) kullanımlarını gözden geçirin

Belirli bir özel durum yerine tüm özel durumları yakalayacak catch blokları artık zaman uyumsuz özel durumları da yakalar. Her catch (özel durum) bloğunu inceleyerek, atlanan önemli bir kaynak bırakma veya geri alma kodu yoksa, ya da bir, veya işlemek için de catch bloğunun kendisi içinde hatalı davranış olup olmadığını araştırın <xref:System.Threading.ThreadAbortException> <xref:System.StackOverflowException> <xref:System.OutOfMemoryException> .  Bu kodun günlüğe kaydedilmesine veya yalnızca belirli özel durumları görebileceğine veya bir özel durumun tam olarak tek bir nedenden dolayı başarısız olduğu varsayımda olabileceğini unutmayın.  Bu varsayımlar dahil etmek için güncelleştirilmeleri gerekebilir <xref:System.Threading.ThreadAbortException> .

Bir dizi biçimlendirme yöntemi gibi, sizin belirttiğiniz özel durum türünü yakalamak için tüm özel durumları yakalayan tüm yerleri değiştirmeyi göz önünde bulundurun <xref:System.FormatException> .  Bu, catch bloğunun beklenmeyen özel durumlar üzerinde çalışmasını önler ve kodun beklenmeyen özel durumları yakalayarak hataları gizlemez olmasını sağlamaya yardımcı olur.  Genel bir kural olarak kitaplık kodunda bir özel durumu işlemez (bir özel durum yakalamanızı gerektiren kod, aradığınız kodda bir tasarım kusurunu belirtebilir).  Bazı durumlarda, bir özel durumu yakalamak ve daha fazla veri sağlamak için farklı bir özel durum türü oluşturmak isteyebilirsiniz.  Bu durumda iç içe geçmiş özel durumları kullanın ve hatanın gerçek nedenini <xref:System.Exception.InnerException%2A> Yeni özel durumun özelliğinde depolayarak.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

Tüm nesneleri yakalar veya tüm özel durumları yakalayacak Yönetilen koddaki tüm catch bloklarını gözden geçirin.  C# dilinde, bu hem hem de olarak bayrak anlamına gelir `catch` {} `catch(Exception)` {} .  Özel durum türünü çok özel yapmayı düşünün veya beklenmeyen bir özel durum türünü yakaladığı için hatalı bir şekilde hareket etmemesini sağlamak üzere kodu gözden geçirin.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Yönetilen bir iş parçacığının bir Win32 iş parçacığı olduğunu varsaymayın; bu bir fiber

Yönetilen iş parçacığı yerel depolama kullanmak çalışır, ancak yönetilmeyen iş parçacığı yerel depolama birimini veya kodun geçerli işletim sistemi iş parçacığında yeniden çalışacağını varsayabilirsiniz. İş parçacığının yerel ayarı gibi ayarları değiştirmeyin. `InitializeCriticalSection` `CreateMutex` Bir kilit giren işletim sistemi iş parçacığını gerektirdiğinden ya da kilitden çıkmak için platform Invoke 'ı çağırmayın. Fibers kullanılırken bu durum olmadığı için, Win32 kritik bölümleri ve zaman uyumu sağlayıcılar doğrudan SQL 'de kullanılamaz.  Yönetilen <xref:System.Threading.Mutex> sınıfın bu iş parçacığı benzeşim sorunlarını işlemediğini unutmayın.

<xref:System.Threading.Thread>Yönetilen iş parçacığı yerel depolama alanı ve iş parçacığının geçerli kullanıcı arabirimi kültürü dahil olmak üzere, yönetilen bir nesne üzerinde durumun büyük bir bölümünü güvenle kullanabilirsiniz. Ayrıca, <xref:System.ThreadStaticAttribute> mevcut bir statik değişkenin değerini yalnızca geçerli yönetilen iş parçacığı (clr 'de fiber yerel depolama yapmanın başka bir yolu) ile erişilebilir hale getiren öğesini de kullanabilirsiniz. Programlama modeli nedenleriyle, SQL 'de çalışırken bir iş parçacığının geçerli kültürünü değiştiremezsiniz.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

SQL Server, fiber modda çalışır; iş parçacığı yerel depolama kullanmayın. ,, Ve için platform çağırma çağrıları kullanmaktan kaçının `TlsAlloc` `TlsFree` `TlsGetValue``TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>SQL Server tanıtıcı kimliğe bürünmeye izin ver

Kimliğe bürünme iş parçacığı düzeyinde çalışır ve SQL fiber modda çalışabilir, yönetilen kod kullanıcıları taklit etmez ve çağırmamalıdır `RevertToSelf` .

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

SQL Server tanıtıcı kimliğe bürünmeye izin verin. ,,,,, `RevertToSelf` `ImpersonateAnonymousToken` `DdeImpersonateClient` `ImpersonateDdeClientWindow` `ImpersonateLoggedOnUser` `ImpersonateNamedPipeClient` , `ImpersonateSelf` , `RpcImpersonateClient` , `RpcRevertToSelf` , `RpcRevertToSelfEx` , Veya kullanmayın `SetThreadToken` .

### <a name="do-not-call-threadsuspend"></a>Thread:: Suspend çağrısını çağırma

Bir iş parçacığını askıya alma özelliği basit bir işlem görünebilir, ancak kilitlenmeleri neden olabilir.  Kilit tutan bir iş parçacığı ikinci bir iş parçacığı tarafından askıya alınırsa ve ikinci iş parçacığı aynı kilidi gerçekleştirmeye çalışırsa, bir kilitlenme oluşur.  <xref:System.Threading.Thread.Suspend%2A>Güvenlik, sınıf yükleme, uzaktan iletişim ve yansıma Şu anda kesintiye uğratabilirler.

#### <a name="code-analysis-rule"></a>Kod Analizi kuralı

' İ çağırmayın <xref:System.Threading.Thread.Suspend%2A> . Veya gibi gerçek bir eşitleme temel kullanmayı düşünün <xref:System.Threading.Semaphore> <xref:System.Threading.ManualResetEvent> .

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Kısıtlı yürütme bölgeleri ve güvenilirlik sözleşmeleri ile kritik işlemleri koruma

Paylaşılan bir durumu güncelleştiren veya tamamen başarılı ya da tamamen başarısız olması gereken karmaşık bir işlem gerçekleştirirken, kısıtlı bir yürütme bölgesi (CER) tarafından korunduğundan emin olun. Bu, kodun her durumda, ani bir iş parçacığı iptali veya ani kaldırmaların kaldırılması durumunda çalışmasını güvence altına alır <xref:System.AppDomain> .

Bir CER, bir `try/finally` çağrısıyla hemen önce gelen belirli bir bloğudur <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> .

Bunu yapmak, tam zamanında derleyiciye bloğunu çalıştırmadan önce finally bloğundaki tüm kodu hazırlamasını söyler `try` . Bu, finally bloğundaki kodun oluşturuldığına ve her durumda çalışacak şekilde emin olur. Bir CER 'de boş bir bloğa sahip olmayan bir çok seyrek değildir `try` . Bir CER kullanılması zaman uyumsuz iş parçacığı iptal ve bellek dışı özel durumlara karşı koruma sağlar. <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>Ayrıca, daha fazla derin kod için yığın taşlarının de işlediği BIR cer formu için bkz..

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.ConstrainedExecution>
- [SQL Server Programlama ve Ana Bilgisayar Koruması Öznitelikleri](sql-server-programming-and-host-protection-attributes.md)
