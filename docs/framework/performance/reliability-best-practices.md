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
ms.openlocfilehash: 37e6b995a84a54dfcb52460d11e9843a933a5684
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353081"
---
# <a name="reliability-best-practices"></a>Güvenilirlik En İyi Yöntemleri

SQL Server için aşağıdaki güvenilirlik kuralları yerleştirilir; Ancak, bunlar da herhangi bir ana bilgisayar tabanlı sunucu uygulama uygulanır. SQL Server gibi sunucu kaynak sızıntısı değil ve duruma değil, son derece önemlidir.  Ancak, bir nesnenin durumunu değiştiren her yöntem için geri çekme kodu yazarak yapılamaz.  Geri çekme kodu ile her yerde herhangi bir hata geri yüklenecek yüzde 100 güvenilir yönetilen kod yazma değil olmaktır.  Bu, çok az başarı olasılığını göz korkutucu görevle olacaktır.  Ortak dil çalışma zamanı (CLR) yönetilen kod için yeterince güçlü garanti uygun mükemmel kod yazmak için kolayca sağlayamaz.  ASP.NET, SQL Server veritabanı edilemeyecek kadar uzun bir süredir kesinti olmadan dönüştürülemez yalnızca bir işlem kullandığını unutmayın.

Bu zayıf garantiler ve tek bir işlemde çalışan ile güvenilirlik iş parçacıklarını sonlandırma veya tanıtıcıları veya bellek gibi işletim sistemi kaynakları sağlamak için gerekli ve alınması önlemler sızdırılmaz olduğunda uygulama etki alanları geri dönüşümü temel alır.  Bile bu basit güvenilirlik kısıtlamayla, yine de önemli güvenilirlik gereksinimi vardır:

- Hiçbir zaman sızıntısı işletim sistem kaynakları.

- Tüm yönetilen kilitleri CLR tüm raporlarda belirleyin.

- Hiçbir zaman kesme çapraz uygulama etki alanı paylaşılan izin verme durumuna <xref:System.AppDomain> düzgün çalışması için Geri Dönüşüm.

Teorik olarak işlemek için yönetilen kod yazmanıza olanak olmasına rağmen <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, ve <xref:System.OutOfMemoryException> özel durumlar, geliştiricilerin yazma gibi güçlü kod tüm uygulamanın tamamında mantıksız bekleniyor.  Bu nedenle, bant dışı özel durumları sonlandırılıyor yürütülen iş parçacığında sonucu; ve sonlandırılan iş parçacığının iş parçacığının bir kilidi tutan tarafından belirlenebilir, paylaşılan durum düzenliyorsanız sonra <xref:System.AppDomain> kaldırılır.  Paylaşılan durum düzenleme bir yöntem sonlandırıldığında için paylaşılan durum güncelleştirmeleri için güvenilir geri çekme kodu yazmayı mümkün olmadığı için durumu bozuk olacaktır.

.NET Framework 2.0 sürümünde, yalnızca ana SQL Server güvenilirlik gerektirir.  Derlemenizi SQL sunucu üzerinde çalışacaksa veritabanında çalıştırırken devre dışı bırakılmış belirli özellikleri olsa bile, derleme, her bir bölümü için güvenilirlik iş yapmanız gerekir.  Kod Analizi motoru derleme düzeyinde kodu inceler ve devre dışı kod ayırt edemez çünkü bu gereklidir. Başka bir SQL Server programlama dikkat etmeniz gereken SQL Server her şey tek bir işlemde çalıştırılır ve <xref:System.AppDomain> geri dönüştürme kullanılan bellek ve işletim sistemi tanıtıcıları gibi tüm kaynakları Temizleme için.

Sonlandırıcılar veya yıkıcıları bağımlı olamaz veya `try/finally` geri çekme kodu için engeller. Bunlar kesintiye ya da çağrılmadığı.

Zaman uyumsuz özel durumları beklenmeyen konumlarda büyük olasılıkla her makine yönerge durum: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, ve <xref:System.OutOfMemoryException>.

Yönetilen iş parçacıklarını mutlaka SQL Win32 iş parçacığı değildir; Bunlar iyileştirmesini olabilir.

İşlem genelinde veya çapraz uygulama etki alanı değişebilir paylaşılan durum güvenli bir şekilde değiştirmek son derece zordur ve mümkün olduğunca kaçınılmalıdır.

Bellek yetersiz koşullar SQL Server'da nadir değildir.

SQL Server'da barındırılan kitaplıkları paylaşılan durumlarını doğru şekilde güncelleştirilmiyor, kodu değil kurtarılacak yüksek bir olasılık yoktur veritabanı yeniden başlatılana kadar.  Ayrıca, bazı olağanüstü durumlarda, yeniden başlatmak veritabanına neden bu SQL Server işleminin başarısız olmasına neden olabilir mümkündür.  Veritabanını yeniden bir Web sitesini veya kullanılabilirlik mutsuz şirket işlemlerini etkiler.  Yavaş bir sızıntısı bellek veya tanıtıcıları gibi işletim sistemi kaynak sunucunun kurtarma kaybetme riski ayırma tutamaçlı sonunda başarısız olmasına neden olabilir veya potansiyel olarak sunucu yavaş performans düşebilir ve bir müşterinin uygulaması azaltır Kullanılabilirlik.  Açıkça bu senaryoları önlemek istiyoruz.

## <a name="best-practice-rules"></a>En iyi yöntem kuralları

Giriş ne sunucusunda çalışan yönetilen kod için kod incelemesi kararlılığını ve framework güvenilirliğini artırmak için catch zorunda odaklanır. Bu denetimler iyi genel aşamasındadır ve sunucu üzerinde mutlak olmalıdır.

Bir ölü kilidi veya kaynak kısıtlama karşılaşıldığında, SQL Server bir iş parçacığını durdurmak veya kapatabilirsiniz bir <xref:System.AppDomain>.  Bu durumda, yalnızca geri çekme kodu kısıtlı yürütme bölgede (CER) çalıştırılması sağlanır.

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Kaynak sızıntılarını önlemek için SafeHandle kullanın

Durumunda, bir <xref:System.AppDomain> kaldırma, size bağlı olamaz üzerinde `finally` blokları veya tüm işletim sistemi kaynak erişimi aracılığıyla soyutlamak önemlidir, yürütülen sonlandırıcılar <xref:System.Runtime.InteropServices.SafeHandle> sınıfı yerine <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, veya benzer sınıflar. İzleme ve kullandığınız bile tutamaçları kapatmak CLR böylece <xref:System.AppDomain> kapatmayı çalışması.  <xref:System.Runtime.InteropServices.SafeHandle> CLR her zaman çalıştır kritik bir sonlandırıcı kullanacaklardır.

İşletim sistemi tanıtıcıyı serbest şu kadar oluşturulduğu andan güvenli tanıtıcı depolanır.  Penceresi yok aşamasında bir <xref:System.Threading.ThreadAbortException> yönelik bir tanıtıcı ortaya çıkabilir.  Ayrıca, platform çağırma başvuru sayısı, kullanım ömrü tanıtıcıyı bir yarış durumu arasında bir güvenlik sorunu engelleme, yakın izleme sağlayan tanıtıcı `Dispose` ve tanıtıcı kullanmakta olduğu bir yöntem.

Şu anda yalnızca temiz bir işletim sistemini kurmak işlemek için bir Sonlandırıcısı olan çoğu sınıf Sonlandırıcı artık gerekli değildir. Bunun yerine, sonlandırıcı açık olacak <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıf.

Unutmayın <xref:System.Runtime.InteropServices.SafeHandle> yerine değil <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Açıkça işletim sistemi kaynaklarını silmek için Çekişme ve performans avantajları hala olası kaynak vardır.  Yalnızca fark `finally` açıkça kaynaklarını silmek blokları tamamlanana kadar çalışmayabilir.

<xref:System.Runtime.InteropServices.SafeHandle> uygulamak kendi sağlar <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yordamı serbest bırakma veya bir dizi döngü içinde tanıtıcıları boşaltma bir işletim sistemi tanıtıcısı durumuna geçirme gibi tanıtıcı ücretsiz çalışma gerçekleştirir yöntemi.  CLR, bu yöntem çalıştırıldığını garanti eder.  Yazarı sorumluluğundadır <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> tanıtıcı tüm durumlarda yayımlanan emin olmak için uygulama. Bunun yapılmaması, sızıntı tanıtıcısı ile ilişkili yerel kaynakların genellikle sonuçlanır be leaked tanıtıcı neden olur. Bu nedenle yapısına kritik <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıflar gibi <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> uygulamasını çağırma anda kullanılamayabilir herhangi bir kaynak ayırma gerektirmez. İçinde uygulamanın başarısız olabileceği çağrı yöntemlere izin verilen olduğuna dikkat edin <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> koşuluyla kodunuz bu tür hataları işlemek ve yerel tanıtıcısını bırakmak için sözleşme tamamlayın. Hata ayıklama amacıyla, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sahip bir <xref:System.Boolean> döndürmek için ayarlanabilir değeri `false` yayın kaynağının önleyen işlemi yıkıcı hatayla karşılaşılırsa. Bunu yaptığınızda etkinleşir [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) etkinleştirilirse sorun tanımlanmasına yardımcı olmak için MDA. Çalışma zamanı başka bir şekilde etkilemez. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yeniden aynı kaynak için çağrılmayacak ve tanıtıcı sızmasına sonuç.

<xref:System.Runtime.InteropServices.SafeHandle> belirli bağlamlarda uygun değil.  Bu yana <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi, çalıştırılabilir bir <xref:System.GC> Sonlandırıcı iş parçacığı, belirli bir iş parçacığında boşaltılması için gerekli olan tanıtıcıları değil içinde kaydırılır bir <xref:System.Runtime.InteropServices.SafeHandle>.

Çalışma zamanı aranabilir sarmalayıcılarını (RCW), ek kod olmadan CLR tarafından temizlenebilir.  Kullanan kod için platform çağırma ve bir COM nesnesi olarak değerlendirir bir `IUnknown*` veya <xref:System.IntPtr>, kodu bir RCW kullanılacak yazılması.  <xref:System.Runtime.InteropServices.SafeHandle> bir yönetilmeyen yayın yöntemi yönetilen koda geri çağırma olasılığı nedeniyle bu senaryo için yeterli olmayabilir.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Kullanım <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi kaynakları kapsamak için. Kullanmayın <xref:System.Runtime.InteropServices.HandleRef> veya türünde alanlar <xref:System.IntPtr>.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Sonlandırıcılar işletim sistemi kaynaklarını sızdırılmasını önlemek için çalışmaya olmadığından olun

Dikkatli bir şekilde çalıştırmadıkları olsa bile, bir kritik işletim sistemi kaynağı sızdırılmaz emin olmak için bir sonlandırıcı gözden geçirin.  Normal aksine <xref:System.AppDomain> uygulama kararlı bir duruma veya SQL Server kapatır gibi bir sunucusu olmayan kesin bir ani sırasında nesneleri yürütülürken kaldırma <xref:System.AppDomain> kaldırın.  Kaynakları ani bir kaldırma durumunda olduğundan, bir uygulamanın doğruluğu garanti edilemez, ancak sunucu bütünlüğünü kaynak sızıntısı değil tarafından korunmalıdır sızdırılmaz emin olun.  Kullanım <xref:System.Runtime.InteropServices.SafeHandle> herhangi bir işletim sistemi kaynakları serbest bırakacak.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Son olarak, işletim sistemi kaynaklarını sızmasını önlemek için çalıştırılacak yan tümceleri gerekmez emin olun

`finally` yan tümceleri garanti edilmez CERs dışında çalıştırmak için kitaplık geliştiricilerin kod içinde bağımlı kalmayacak gerektiren bir `finally` blok yönetilmeyen kaynakları serbest bırakacak.  Kullanarak <xref:System.Runtime.InteropServices.SafeHandle> önerilen çözümdür.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Kullanım <xref:System.Runtime.InteropServices.SafeHandle> yerine işletim sistemi kaynakları Temizleme için `Finalize`. Kullanmayın <xref:System.IntPtr>; kullanma <xref:System.Runtime.InteropServices.SafeHandle> kaynakları kapsamak için. Varsa finally yan tümcesi gerekir çalıştırın, içinde bir CER yerleştirin.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Tüm kilitleri yönetilen mevcut kilitleme kod tamamlamalıdır.

CLR böylece onu kapatabilirsiniz bilirsiniz kod bir kilit zaman olduğunu bilmeniz gerekir <xref:System.AppDomain> yerine yalnızca iş parçacığını iptal ediliyor.  Üzerinde iş parçacığı tarafından işletilen veri tutarsız bir durumda bıraktığınız iş parçacığının çalışmasını tehlikeli olabilir. Bu nedenle, tüm <xref:System.AppDomain> geri dönüştürülmesi gerekir.  Kilit tanımlamak başarısız olan sonuçlarını kilitlenmeleri veya hatalı sonuçları olabilir. Yöntemleri kullanın <xref:System.Threading.Thread.BeginCriticalRegion%2A> ve <xref:System.Threading.Thread.EndCriticalRegion%2A> kilit bölgeleri.  Statik yöntemler üzerinde olduklarından <xref:System.Threading.Thread> yalnızca tek bir iş parçacığı başka bir iş parçacığının kilit sayacını düzenlemesini önlemek için yardımcı olan geçerli iş parçacığı için geçerli bir sınıf.

<xref:System.Threading.Monitor.Enter%2A> ve <xref:System.Threading.Monitor.Exit%2A> kullanımlarını yanı sıra kullanımı önerilir. Bu nedenle, yerleşik bu CLR bildirim sahip [lock deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md), bu yöntemler kullanır.

Döndürme kilitler gibi kilitleme başka mekanizmalar ve <xref:System.Threading.AutoResetEvent> kritik bölüm giriliyor CLR bildirmek için bu yöntemi çağırmanız gerekir.  Bu yöntemler kilitleri almayan; iş parçacığı durduruluyor paylaşılan durum tutarsız bırakabilir ve bunlar kritik bir bölümde kodu yürüten CLR bildirin.  Özel bir gibi kendi kilit türü tanımladığınız varsa <xref:System.Threading.ReaderWriterLock> sınıfı, bu kilit sayısı yöntemleri kullanın.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

İşaretleme ve kullanarak tüm kilitleri tanımlama <xref:System.Threading.Thread.BeginCriticalRegion%2A> ve <xref:System.Threading.Thread.EndCriticalRegion%2A>. Kullanmayın <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>, ve <xref:System.Threading.Interlocked.Decrement%2A> döngü içinde.  Bir platform yapmak bu yöntemlerin Win32 türevleri çağırır.  Kullanmayın <xref:System.Threading.Thread.Sleep%2A> döngü içinde.  Volatile alanları kullanmayın.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Temizleme kodu olmalıdır bir finally ya da bir catch bloğunun bir catch değil aşağıdaki

Temizleme kodunu izlemelidir hiçbir zaman bir `catch` engelle; olmalıdır bir `finally` veya `catch` kendisini engelleyin.  Bu, normal iyi bir uygulama olmalıdır.  A `finally` hem bir özel durum oluştuğunda hem de aynı kodu çalıştırdığı için blok genellikle tercih edilen sonuna `try` blok normalde karşılaşıldı.  Durumunda, örneğin oluşturulan beklenmeyen bir özel durum bir <xref:System.Threading.ThreadAbortException>, temizleme kodu çalışmayacak.  Herhangi bir yönetilmeyen, içinde temizlemek kaynakları bir `finally` , ideal olarak sarılacağını bir <xref:System.Runtime.InteropServices.SafeHandle> sızıntılarını önlemek için.  Not C# `using` anahtar sözcüğü etkin tanıtıcıları gibi nesnelerin dispose için kullanılabilir.

Ancak <xref:System.AppDomain> geri dönüştürme temiz Sonlandırıcı iş parçacığında kaynakları, temizleme kodu doğru konuma yerleştirmek yine de önemlidir.  Bir iş parçacığı zaman uyumsuz bir özel bir kilit olmadan alırsa, CLR geri dönüştürmek zorunda kalmadan iş parçacığının kendisinde son denemesi Not <xref:System.AppDomain>.  Kaynakları daha çabuk yerine sonraki yardımcı daha fazla kaynağı kullanılabilir hale getirme ve daha iyi kullanım ömrü Yönetimi temizlendiğinden emin olma.  Ardından beklerken bazı hata kodu yolda bir dosya için bir tanıtıcı açıkça kapatmazsanız <xref:System.Runtime.InteropServices.SafeHandle> ilk kez kodunuzu çalıştığında, temizlemek için Sonlandırıcı Sonlandırıcı olmayan zaten çalıştırıldıysa tam aynı dosyaya erişmeyi deneyen başarısız olabilir.  Bu nedenle, temizleme kodunu var ve düzgün çalıştığını sağlamaya yardımcı olacak kesinlikle gerekli olmamasına rağmen daha temiz bir şekilde ve hızla hatalardan kurtarma.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Sonra temizleme kodunu `catch` olması gereken bir `finally` blok. Silinecek nda aramayı bir finally bloğunda.  `catch` blok içinde bir throw son veya rethrow gerekir.  Özel durumlar olacaktır ancak bir ağ bağlantısı kuruldu olup olmadığını algılama kodu gibi herhangi bir sayıda özel durum, bir özel durum sayısı normal koşullarda yakalama gerektiren herhangi bir kod burada alabilirsiniz vermelisiniz bir kod olmalıdır bir gösterge başarılı olur, görmek için test.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>İşlem genelinde değişebilir paylaşılan durum uygulama etki alanları arasında ortadan ya da kısıtlı yürütme bölgeyi kullanın

Giriş açıklandığı gibi paylaşılan işlem genelinde durum uygulama etki alanları arasında güvenilir bir şekilde izler. yönetilen kod yazmak oldukça zor olabilir.  İşlem genelinde paylaşılan durum uygulama etki alanları arasında Win32 kodda, CLR içinde ya da uzaktan iletişimi kullanarak yönetilen kodda ya da paylaşılan veri yapısının herhangi bir sıralama ' dir.  Değişebilir bir paylaşılan durum doğru yönetilen kodda yazma çok zordur ve herhangi bir statik paylaşılan durum yalnızca harika dikkatli yapılabilir.  İşlem genelinde veya makine genelinde paylaşılan durum varsa, bunu ortadan kaldırın veya kısıtlı yürütme bölge (CER) kullanarak paylaşılan durumunu korumak için bir şekilde bulun.  Herhangi bir kitaplığı ile tanımlanan düzeltildi ve dağıtılmamış paylaşılan durum temiz gerektiren SQL Server gibi bir konak neden olabileceğini unutmayın <xref:System.AppDomain> çökmesine kaldırma.

Kod bir COM nesnesi kullanıyorsa, uygulama etki alanları arasında bu COM nesnesi paylaşımı kaçının.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Kilitler işlem genelinde veya uygulama etki alanları arasında çalışmaz.

Geçmişte, <xref:System.Threading.Monitor.Enter%2A> ve [lock deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md) genel işlem kilitleri oluşturmak için kullanılır.  Örneğin, bu üzerinde kilitleme ortaya çıkar <xref:System.AppDomain> Çevik sınıflar gibi <xref:System.Type> örnekleri paylaşılmayan derlemelerden <xref:System.Threading.Thread> nesneleri, interned dizeleri ve Uzaktan iletişimi kullanarak uygulama etki alanları arasında paylaşılan herhangi bir dize.  Bu kilitleri artık işlem genelinde değildir.  İşlem genelinde interapplication etki alanı kilit varlığı tanımlamak için kilit içindeki kod dosyası diskte veya büyük olasılıkla bir veritabanı gibi herhangi bir harici, kalıcı kaynak kullanıp kullanmadığını belirleyin.

Bu süre sonu içinde kilit almayı unutmayın bir <xref:System.AppDomain> korunan kod, bir dış kaynağa kullanır, çünkü bu kodu aynı anda birden çok uygulama etki alanları arasında çalışabilir sorunlara neden olabilir.  Bu yazma sırasında bir sorun olabilir bir günlük dosyası veya işlem için bir yuva bağlama.  Bu değişiklikler, adlandırılmış kullanarak başka bir işlem genel kilidi almak için yönetilen kod kullanarak etmenin kolay bir yolu yoktur anlamına geliyor <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore> örneği.  İki uygulama etki alanlarında aynı anda çalıştırmak, veya kullanmak kod oluşturma <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore> sınıfları.  Varolan kod değiştirilemez, mutex adlı bir Win32 fiber modda çalışan aynı işletim sistemi iş parçacığı almak ve bir mutex yayın garanti edemez anlamına gelir çünkü bu eşitleme elde etmek için kullanmayın.  Yönetilen kullanmalısınız <xref:System.Threading.Mutex> sınıf veya bir adlandırılmış <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, veya bir <xref:System.Threading.Semaphore> CLR yönetilmeyen kod kullanarak kilit eşitleme yerine farkında bir şekilde kod kilit eşitlenecek.

#### <a name="avoid-locktypeofmytype"></a>Lock(typeof(MyType)) kaçının

Özel ve genel <xref:System.Type> paylaşılan derlemeler ile tüm uygulama etki alanları arasında paylaşılan kod yalnızca bir kopyasını nesneleri sorunları da sunar.  Paylaşılan derlemeler için yalnızca bir örneği olduğu bir <xref:System.Type> her işlem, birden çok uygulama etki alanları tam aynı paylaşıma anlamı <xref:System.Type> örneği.  Kilit almayı bir <xref:System.Type> örneği alır değil sürecinin tamamını etkileyen bir kilit yalnızca <xref:System.AppDomain>.  Varsa <xref:System.AppDomain> kilit vereceğine bir <xref:System.Type> iş parçacığı aniden durduruldu, kilit yayınlamayacaktır nesne.  Bu kilit ardından kilitlemek diğer uygulama etki alanları neden olabilir.

Statik yöntemleri kilitleri yararlanmak için en iyi yolu, kodu bir statik iç eşitleme nesnesi eklenmesini kapsar.  Bu sınıf oluşturucuda varsa, ancak bunu şu şekilde başlatılmamış başlatılamadı:

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

Ardından kilit, kullanım çekerken `InternalSyncObject` özelliği bir nesne üzerinde kilit elde edilir.  Özelliği kullanırsanız, sınıf oluşturucusu içinde iç eşitleme nesnesi başlatılmadı gerekmez.  Çift denetimi kilidi başlatma kodunu şu örnekteki gibi görünmelidir:

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

#### <a name="a-note-about-lockthis"></a>Lock(this) hakkında bir Not

Genel olarak erişilebilir olan tek bir nesne üzerinde bir kilidi almak için genel olarak kullanılabilir.  Ancak, nesne bir kilitlenme tüm alt sistemine neden olabilecek bir tekil nesnesi ise, yukarıdaki tasarım deseni de kullanmayı düşünün.  Örneğin, bir kilit <xref:System.Security.SecurityManager> nesnesi içindeki bir kilitlenme neden <xref:System.AppDomain> tüm yapmadan <xref:System.AppDomain> kullanılamaz. Bu türün ortak olarak erişilebilen bir nesnede kilit olmayacağına iyi bir uygulamadır.  Ancak bir tek bir koleksiyon veya dizi kilit genellikle bir sorun yoktur.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Kilitleri, uygulama etki alanları arasında kullanılıyor olabilir ya da güçlü bir algılama kimliği olmayan türlerde almaz. Çağırmayın <xref:System.Threading.Monitor.Enter%2A> üzerinde bir <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>, ya da türetilen herhangi bir nesne <xref:System.MarshalByRefObject>.

### <a name="remove-gckeepalive-calls"></a>GC kaldırın. KeepAlive çağrıları

Varolan kodu önemli ölçüde kullanmaz <xref:System.GC.KeepAlive%2A> zaman gerekir veya uygun olmadığı durumlarda kullanır.  Dönüştürme sonra <xref:System.Runtime.InteropServices.SafeHandle>, sınıfları çağırmaya gerek yoktur <xref:System.GC.KeepAlive%2A>, bir sonlandırıcı olmayan ancak dayanır varsayılarak <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi sonlandırmak için işler.  While çağrısı koruma performans maliyeti <xref:System.GC.KeepAlive%2A> durum, göz ardı edilebilir markanızın, çağrı <xref:System.GC.KeepAlive%2A> gerekli ya da artık mevcut olmayabilir sorun kodu korumak daha zor yapar bir ömrü çözmek yeterli.  Ancak, COM birlikte çalışma CLR aranabilir sarmalayıcılarını (RCW) kullanırken <xref:System.GC.KeepAlive%2A> kod tarafından hala gereklidir.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Kaldırma <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-host-protection-attribute"></a>Konak koruma özniteliğini kullanın

<xref:System.Security.Permissions.HostProtectionAttribute> (HPA) bile tam güvenilir kod gibibelirlianabilgisayariçinuygunolanbazıyöntemlerçağırmasınıengellemekiçinanaizinvererekkonakkorumagereksinimlerinibelirlemekiçinbildirimedayalıgüvenlikeylemlerikullanımınısağlar<xref:System.Environment.Exit%2A>veya <xref:System.Windows.Forms.MessageBox.Show%2A> SQL Server için.

HPA barındıran ortak dil çalışma zamanı ve uygulama konak koruma, SQL Server gibi yalnızca yönetilmeyen uygulamaları etkiler. Uygulandığında, bağlantı talebi oluşturulmasını güvenlik eylemi sonuçları sınıfta veya yöntemde kullanıma sunan konak kaynaklar temelinde. Kod bir istemci uygulamasında veya konağı korumalı olmayan bir sunucuda çalıştırırsanız öznitelik "evaporates"; değil algılanır ve bu nedenle geçerli olmaz.

> [!IMPORTANT]
> Bu özniteliğin amacı, konağa özgü programlama modeli yönergeleri, güvenlik davranışı zorlamak sağlamaktır.  Bağlantı talebi, model gereksinimleri programlamaya uyumluluğu denetlemek için kullanılır ancak <xref:System.Security.Permissions.HostProtectionAttribute> bir güvenlik izni değil.

Konak programlama modeli gereksinimlerine sahip değilse, bağlantı talepleri gerçekleşmez.

Bu öznitelik aşağıdakileri tanımlar:

- Yöntem veya programlama modeli, konak uymayan sınıfları ancak Aksi halde zararsız.

- Yöntemleri veya konak programlama modeli uymayan ve kullanıcı sunucusu yönetilen kodu kararsız hale getiren için yol açabilir.

- Yöntemleri veya programlama konak uymayan sınıfları model ve sunucu işlemi, bir destabilization için neden olabilir.

> [!NOTE]
> Bir korumalı konak ortamında yürütme uygulamalarla çağrılacak olan bir sınıf kitaplığı oluşturuyorsanız, bu öznitelik kullanıma sunan üyeleri uygulamalıdır <xref:System.Security.Permissions.HostProtectionResource> kaynak kategoriler. Bu öznitelik ile .NET Framework sınıf kitaplığı üyeleri yalnızca şu anki çağırıcı denetlenecek neden.  Kitaplık üyesini, aynı şekilde, şu anki çağırıcı kontrol neden gerekir.

İçinde HPA hakkında daha fazla bilgi edinmek <xref:System.Security.Permissions.HostProtectionAttribute>.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

SQL Server için eşitleme veya iş parçacığı sunmak için kullanılan tüm yöntemler gerekir tanımlanan HPA ile. Bu durum paylaşma, eşitlenen veya dış işlemleri yönetme yöntemleri içerir. <xref:System.Security.Permissions.HostProtectionResource> SQL Server'ı etkileyen değerler <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, ve <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Ancak, herhangi bir kullanıma sunan herhangi bir yöntemi <xref:System.Security.Permissions.HostProtectionResource> bir HPA tarafından yalnızca SQL etkileyen kaynakları kullananlar tanımlanmalıdır.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Yönetilmeyen kodda süresiz olarak Engellemesi değil

Yönetilen kod yerine yönetilmeyen kodda engelleme, CLR iş parçacığı durdurmak mümkün olmadığı için bir hizmet reddi saldırısına neden olabilir.  Engellenen bir iş parçacığı kaldırılmasını CLR engeller <xref:System.AppDomain>, en az son derece güvenli olmayan bazı işlemler yapmaya gerek kalmadan.  Bir Win32 kullanarak engelleme eşitleme temel öğesi bir açık bir şey izin veremez örneğidir.  Bir çağrıda engelleme `ReadFile` bir yuvada mümkünse kaçınılmalıdır; ideal olarak, Win32 API şunun gibi bir işlem zaman aşımına için bir mekanizma sağlamalıdır.

Yerel çağıran herhangi bir yöntemi, ideal olarak makul, sınırlı zaman aşımı ile Win32 çağrı kullanmalısınız.  Kullanıcı zaman aşımını belirtmek için izin veriliyorsa, kullanıcı bazı belirli güvenlik izinleri olmadan sonsuz zaman aşımını belirtmek için izin verilmeyen.  Bir kılavuz olarak, bir yöntem ~ 10 saniyeden fazla için engeller, zaman aşımları destekleyen bir sürüm kullanması gerekir veya ek CLR desteği gerekir.

Sorunlu API'leri bazı örnekleri aşağıda verilmiştir.  Kanallar (anonim ve adlandırılmış), bir zaman aşımı ile oluşturulabilir; Ancak, kod, hiçbir zaman çağrıları sağlamalısınız `CreateNamedPipe` ya da `WaitNamedPipe` NMPWAIT_WAIT_FOREVER ile.  Ayrıca olabilir bir zaman aşımı belirtilmiş olsa bile engelleme beklenmeyen.  Çağırma `WriteFile` arabellek varsa, yani tüm bayt yazılır kadar anonim bir kanalda engeller, okunmamış verilerinde `WriteFile` çağrı kanalın arabellek alan okuyucu tarafından serbest kadar engeller.  Yuva zaman aşımı mekanizması geliştirir bazı API her zaman kullanmalısınız.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Yönetilmeyen kod zaman aşımı olmadan engelleyen bir saldırı hizmet reddi olur. Platform gerçekleştirmeyin çağrılarını çağırmak `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`, ve `MsgWaitForMultipleObjectsEx`.  NMPWAIT_WAIT_FOREVER kullanmayın.

### <a name="identify-any-sta-dependent-features"></a>Tüm STA'ya bağımlı özellikler tanımlayın.

Tek iş parçacıklı COM apartmanlar (STAs) kullanan herhangi bir kod belirleyin.  SQL Server işleminde STAs devre dışıdır.  Bağımlı Özellikler `CoInitialize`içinde SQL Server gibi performans sayaçlarını veya Pano devre dışı bırakılmalıdır.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Sonlandırıcılar eşitleme sorunlarını boş olduğundan emin olun

Birden çok Sonlandırıcı iş parçacığı, gelecekte sonlandırıcılar eşzamanlı olarak aynı türde farklı örnekleri için anlamına gelir. .NET Framework sürümleri bulunuyor olabilir.  İş parçacığı güvenli tamamen olması gerekmez; Çöp toplayıcı, yalnızca bir iş parçacığı Sonlandırıcı verilen nesne örneği için çalışacağını garanti eder.  Ancak, bir sonlandırıcı aynı anda birden çok farklı nesne örneklerinde çalıştırıldığında, yarış durumlarını ve kilitlenmeleri önlemek için kodlanmış olmalıdır.  İş parçacığı oluşturma sorunları, bir günlük dosyasında bir sonlandırıcı yazma gibi dış durumlarını kullanırken ele alınması gerekir.  İş parçacığı güvenliği sağlamak için sonlandırma üzerinde güvenmeyin. İş parçacığı yerel depolaması, yönetilen veya yerel, sonlandırıcı iş parçacığında durumunu depolamak için kullanmayın.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Sonlandırıcılar eşitleme sorunlarını boş olmalıdır. Bir sonlandırıcı bir statik değişebilir durum kullanmayın.

### <a name="avoid-unmanaged-memory-if-possible"></a>Yönetilmeyen bellek mümkün olduğunda kaçının

Yönetilmeyen bellek, yalnızca bir işletim sistemi tanıtıcısı gibi be leaked.  Mümkünse, kullanarak yığın bellek kullanmaya çalıştığınızda [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) veya sabitlenmiş bir yönetilen nesne gibi [fixed Statement](~/docs/csharp/language-reference/keywords/fixed-statement.md) veya <xref:System.Runtime.InteropServices.GCHandle> kullanarak bir byte [].  <xref:System.GC> Sonunda bunlar temizler.  Yönetilmeyen bellek gerekir, ancak türetilen bir sınıf kullanmayı düşünün <xref:System.Runtime.InteropServices.SafeHandle> bellek ayırma sarmalamak için.

En az bir durumu olduğunu unutmayın. burada <xref:System.Runtime.InteropServices.SafeHandle> yeterli değil.  Ayırma ya da boş bellek COM yöntem çağrılarında aracılığıyla bellek ayırmak bir DLL için ortak olan `CoTaskMemAlloc` başka bir DLL ile bu bellek serbest bırakma sonra `CoTaskMemFree`.  Kullanarak <xref:System.Runtime.InteropServices.SafeHandle> yaşam ömrü yönetilmeyen bellek tie dener olduğundan bu sayfalarda uygunsuz olacaktır <xref:System.Runtime.InteropServices.SafeHandle> bir DLL denetim bellek kullanım ömrünü izin vermek yerine.

### <a name="review-all-uses-of-catchexception"></a>Tüm kullanımları Catch(Exception) gözden geçirin

Catch blokları catch tüm özel durumlar yerine bir özel durum artık zaman uyumsuz özel durumları da yakalar.  İncelemek, olası yanlış bir davranışı catch bloğu içinde kendisi için işleme yanı sıra atlanabilir hiçbir önemli kaynak serbest bırakma veya geri çıkma kodu aranıyor, her bir catch(Exception) bloğu bir <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, veya <xref:System.OutOfMemoryException>.  Bu kod günlüğü ya da tam olarak bir belirli neden için başarısız bir özel durum gerçekleştiğinde, yalnızca belirli özel durumları veya görebileceği bazı varsayımlar yapmak mümkün olduğunu unutmayın.  Bu varsayımları içerecek şekilde güncelleştirilmesi gerekebilir <xref:System.Threading.ThreadAbortException>.

Tüm değiştirme yerleştirir belirli türde bir beklediğiniz özel durumu yakalamak için tüm özel durumları oluşturulur, bu catch gibi göz önünde bir <xref:System.FormatException> dizeden biçimlendirme yöntemleri.  Bu yakalama bloğunun beklenmeyen özel durumlar üzerinde çalışmasını engeller ve kod hataları beklenmeyen özel durumları yakalama tarafından gizlemez olmanıza yardımcı olur.  Genel bir kural olarak, hiçbir zaman kitaplık kodu bir özel durum işleme (bir özel durum yakalamak gereken kod, çağırdığınız kod uygulamadaki bir tasarım kusurunun belirtebilir).  Bazı durumlarda bir özel durum catch ve throw daha fazla veri sağlamak için farklı bir özel durum türü isteyebilirsiniz.  İç içe geçmiş özel durumları, bu durumda, gerçek hata nedenini depolamak kullanın <xref:System.Exception.InnerException%2A> yeni özel durum özelliği.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Yönetilen kodda tüm catch bloğu bu catch tüm nesneleri veya tüm catch özel durumları gözden geçirin.  İçinde C#, her ikisi de işaretlemesini yani `catch` {} ve `catch(Exception)` {}.  Özel durum türü belirli yapmayı düşünün veya bir beklenmeyen özel durum türü yakalarsa hatalı bir şekilde davranmaz emin olmak için kodu gözden geçirin.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Varsaymayın Win32 iş parçacığı – bir Fiber olan yönetilen bir iş parçacığı

Yönetilen iş parçacığı yerel depolama çalışır ama değil yönetilmeyen iş parçacığı yerel depolaması kullanıyorsanız veya kodu geçerli işletim sistemi iş parçacığı üzerinde yeniden çalıştıracak varsayar kullanarak.  Ayarları gibi iş parçacığının yerel ayarını değiştirmeyin.  Çağırmayın `InitializeCriticalSection` veya `CreateMutex` kilit girer işletim sistemi iş parçacığı de kilit çıkmak gerektirdiğinden platform çağırma.  Bu durum iyileştirmesini kullanırken bulunmaz, Win32 kritik bölümler ve mutex'leri SQL'de doğrudan kullanılamaz.  Unutmayın yönetilen <xref:System.Threading.Mutex> sınıfı, bu iş parçacığı benzeşimini sorunlar işlemez.

Güvenli bir şekilde durumu çoğunu yönetilen üzerinde kullanabileceğiniz <xref:System.Threading.Thread> yönetilen iş parçacığı yerel depolama ve iş parçacığının geçerli UI kültürünün dahil olmak üzere bir nesne.  Ayrıca <xref:System.ThreadStaticAttribute>, getiren mevcut bir statik değişken değerini erişilebilir (Bu, CLR yerel depolamada fiber yapmanın başka bir yolu) yalnızca geçerli yönetilen iş parçacığı tarafından.  Programlama modeli nedeniyle, bir iş parçacığının geçerli kültürü SQL'de çalıştırırken değiştirilemiyor.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

SQL Server fiber modda çalışır; iş parçacığı yerel depolama kullanmayın. Platform önlemek için çağrıları `TlsAlloc`, `TlsFree`, `TlsGetValue`, ve `TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>SQL Server tanıtıcı kimliğe bürünme sağlar

Kimliğe bürünme iş parçacığı düzeyinde çalışır ve SQL çalışma zamanı fiber modunda olduğundan, yönetilen kod kullanıcıların kimliğine değil ve çağırmamalıdır `RevertToSelf`.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

SQL Server'ın kimliğe bürünme işlemek olanak tanır. Kullanmayın `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`, veya `SetThreadToken`.

### <a name="do-not-call-threadsuspend"></a>Thread::suspend çağırmayın

Bir iş parçacığını askıya alma olanağı, basit bir işlemle görünebilir, ancak kilitlenmeleri neden olabilir.  İkinci bir iş parçacığı ve ardından ikinci bir iş parçacığı tarafından askıya bir kilidi tutan bir iş parçacığı aynı kilit almayı denerse bir kilitlenme oluşur.  <xref:System.Threading.Thread.Suspend%2A> Güvenlik, sınıf yükleme, uzaktan iletişim ve yansıma ile şu anda engelleyebilir.

#### <a name="code-analysis-rule"></a>Kod çözümleme kural

Çağırmayın <xref:System.Threading.Thread.Suspend%2A>. Gerçek bir eşitleme kullanmayı bunun yerine, gibi ilkel bir <xref:System.Threading.Semaphore> veya <xref:System.Threading.ManualResetEvent> .

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Kısıtlı yürütme bölgeleri ve güvenilirlik sözleşmeleri kritik işlemler koruyun

Paylaşılan durum güncelleştirmelerinin karmaşık bir işlemi gerçekleştirirken veya, gerekiyor belirleyici ya da tamamen başarılı ya da tamamen başarısız kısıtlı yürütme bölgeye göre (CER) korumalı olduğundan emin olun. Bu kod her durumda bile bir ani iş parçacığı durdurma veya bir ani çalışır garanti eder <xref:System.AppDomain> kaldırın.

Belirli bir CER olan `try/finally` bloğu için bir çağrı tarafından hemen öncesinde <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.

Bunu yapmak, bu nedenle tüm kodu hazırlamak için tam zamanında derleyici bildirir çalıştırmadan önce finally bloğunda `try` blok. Bu, kod içinde garanti finally bloğu yerleşik olarak bulunur ve tüm durumlarda çalıştırılır. Boş olması, bir CER durumdur `try` blok. Bir CER kullanarak zaman uyumsuz iş parçacığı iptalleri ve bellek yetersiz özel durumları karşı korur. Bkz: <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> ayrıca tanıtıcıları yığın verebilmesine derin kodunu taşmaları bir CER formu.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.ConstrainedExecution>
- [SQL Server Programlama ve Konak Koruması Öznitelikleri](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
