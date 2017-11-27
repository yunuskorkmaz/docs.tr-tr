---
title: "Güvenilirlik En İyi Yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ed637cd5d173e12114f436b739ce3c114bb420f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reliability-best-practices"></a>Güvenilirlik En İyi Yöntemleri
Aşağıdaki güvenilirlik kurallar SQL Server'a yerleştirilir; Ancak, bunlar da herhangi bir ana bilgisayar tabanlı sunucu uygulama için geçerlidir. SQL Server gibi sunucu kaynakları sızıntısı değil ve duruma getirilmesi değil, son derece önemlidir.  Ancak, bir nesnenin durumu değiştirir her yöntemi için geri çekme kodu yazarak yapılamaz.  Hedef geri çekme kodu her konumdaki tüm hataları kurtarır yüzde 100 güvenilir yönetilen kodu değil yazmaktır.  Çok az fırsat başarı ile zorlu bir görev olabilir.  Ortak dil çalışma zamanı (CLR), yönetilen kod için yeterince güçlü garanti kusursuz kod uygun yazma yapmak için kolayca sağlayamaz.  ASP.NET farklı olarak, SQL Server veritabanı edilemeyecek uzunlukta bir süre boyunca sürüyor olmadan geri dönüştürüldüğünde olamaz yalnızca bir işlem kullandığını unutmayın.  
  
 Bu zayıf garantiler ve tek bir işlemde çalışan, güvenilirlik iş parçacıklarını sonlandırma veya işletim sistemi kaynaklarını tanıtıcıları veya bellek gibi emin olmak için gereklidir ve alınması önlemleri sızdırılmaz olduğunda uygulama etki alanları geri dönüştürme temel alır.  Bile bu daha basit güvenilirlik kısıtlaması ile hala bir önemli güvenilirlik gereksinim vardır:  
  
-   Hiçbir zaman sızıntısı işletim sistemi kaynakları.  
  
-   Tüm yönetilen kilitleri CLR tüm raporlarda tanımlayın.  
  
-   Paylaşılan hiçbir zaman sonu çapraz uygulama etki alanı belirtin, izin verme <xref:System.AppDomain> düzgün çalışması için Geri Dönüşüm.  
  
 İşlemek için yönetilen kod yazmaya teorik olarak mümkün olsa <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, ve <xref:System.OutOfMemoryException> özel durumlar, geliştiricilerin yazma sağlam gibi tüm uygulama kodunuzda aşırı bekleniyor.  Bu nedenle, bant dışı özel durumlar sonlandırılıyor yürütülen iş parçacığında neden; ve iş parçacığını sonlandırdı iş parçacığı bir kilidi tutan tarafından belirlenebilir, paylaşılan durum düzenleme sonra <xref:System.AppDomain> kaldırılır.  Paylaşılan durum düzenleme yöntemi sonlandırıldığında paylaşılan durum güncelleştirmeleri için güvenilir geri çekme kodu yazmak mümkün olmadığı için durumu bozuk olacaktır.  
  
 .NET Framework sürüm 2. 0'da, SQL Server, güvenilirlik gerektirir yalnızca ana bilgisayardır.  Derlemenizi SQL Server üzerinde çalıştırılacak varsa veritabanında çalıştırırken devre dışı belirli özellikler olsa bile bu derleme her kısmı için güvenilirlik iş yapmanız gerekir.  Kod Çözümleme altyapısı kod derleme düzeyinde inceler ve devre dışı kod ayrım olduğundan, bu gereklidir. Başka bir SQL Server programlama dikkat etmeniz gereken SQL Server her şey tek bir işlemde çalıştırır ve <xref:System.AppDomain> geri dönüştürme kullanılan bellek ve işletim sistemi tanıtıcıları gibi tüm kaynakları temizleniyor.  
  
 Sonlandırıcılar veya Yıkıcılar bağımlı olamaz veya `try/finally` geri çekme kodu engeller. Bunlar kesintiye veya çağrılmaz.  
  
 Zaman uyumsuz özel beklenmedik konumlarda büyük olasılıkla her makine yönerge durum: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, ve <xref:System.OutOfMemoryException>.  
  
 Yönetilen iş parçacığı mutlaka SQL Win32 parçacıklarında değildir; Bunlar lifleri olabilir.  
  
 İşlem genelinde veya çapraz uygulama etki alanı değişebilir paylaşılan durumu güvenle alter oldukça zor ve mümkün olduğunda kaçınılmalıdır.  
  
 Bellek koşullarını SQL Server'da nadir değildir.  
  
 SQL Server barındırılan kitaplıkları paylaşılan durumlarına doğru güncelleştirmezseniz kodu değil kurtarır yüksek olasılık yoktur veritabanını yeniden başlatılana kadar.  Ayrıca, bazı olağanüstü durumlarda, bu veritabanını yeniden başlatmak neden SQL Server işleminin başarısız olmasına neden olabilir mümkündür.  Veritabanını yeniden başlatma bir Web sitesi alabilir ya da kullanılabilirlik mutsuz şirket işlemlerini etkiler.  Yavaş sızıntısı bellek veya tanıtıcıları gibi işletim sistemi kaynak sunucunun sonunda ayırma tanıtıcıları ile olası kurtarma başarısız olmasına neden olabilir veya potansiyel olarak sunucunun yavaş performansı düşebilir ve Müşteri'nin uygulama azaltır Kullanılabilirlik.  Açıkça bu senaryoları önlemek istiyoruz.  
  
## <a name="best-practice-rules"></a>En iyi yöntem kuralları  
 Giriş ne sunucusunda çalışan yönetilen kod için kod incelemesi kararlılık ve framework güvenilirliğini artırmak için catch gerekirdi odaklanmıştır. Tüm bu denetimlerinin genel iyi bir uygulama olduğundan ve sunucuda mutlak gerekir.  
  
 Ölü kilit ya da kaynak kısıtlama karşısında SQL Server bir iş parçacığı iptal etmek veya kesmeden bir <xref:System.AppDomain>.  Bu durumda, yalnızca geri çekme kodu kısıtlı yürütme bölgede (CER) çalıştırılması sağlanır.  
  
### <a name="use-safehandle-to-avoid-resource-leaks"></a>Kaynak sızıntıları önlemek için SafeHandle kullanın  
 Durumunda bir <xref:System.AppDomain> kaldırma, size olamaz bağlı `finally` blokları veya tüm işletim sistemi kaynak erişimi aracılığıyla soyut önemlidir, yürütülen sonlandırıcılar <xref:System.Runtime.InteropServices.SafeHandle> sınıfı yerine <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, veya benzer sınıflar. Böylece, izlemek ve kullandığınız bile tanıtıcıları kapatmak CLR <xref:System.AppDomain> kapatmayı aşağı durumu.  <xref:System.Runtime.InteropServices.SafeHandle>CLR her zaman çalışacak bir kritik Sonlandırıcı kullanacak.  
  
 İşletim sistemi tanıtıcı yayınlanmasından şu kadar oluşturulan andan güvenli tanıtıcı depolanır.  Penceresi yok sırasında bir <xref:System.Threading.ThreadAbortException> bir tanıtıcı sızıntısı için oluşabilir.  Ayrıca, platform çağırma başvuru-count yakın bir yarış durumu arasında bir güvenlik sorunu önleme tanıtıcının kullanım ömrü, izleme sağlayan tanıtıcı `Dispose` ve şu anda tanıtıcısını kullanarak bir yöntem.  
  
 Şu anda yalnızca temiz bir işletim sistemini oluşturan işlemek için bir sonlandırıcı sahip çoğu sınıf sonlandırıcıyı artık ihtiyacınız olmayacaktır. Bunun yerine, açık sonlandırıcıyı olacak <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıf.  
  
 Unutmayın <xref:System.Runtime.InteropServices.SafeHandle> için yenileme değildir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Açıkça işletim sistemi kaynaklarını silmek için Çekişme ve performans avantajı hala olası kaynak vardır.  Yalnızca fark `finally` açıkça kaynaklarını silmek blokları tamamlanıncaya kadar değil yürütme.  
  
 <xref:System.Runtime.InteropServices.SafeHandle>uygulama kendi sayesinde <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yordamı boşaltma veya döngü tanıtıcıları kümesi boşaltma bir işletim sistemi tanıtıcısı geçirme durumuna gibi tanıtıcı boşaltmak için çalışma gerçekleştirir yöntemi.  CLR bu yöntem çalıştırıldığını güvence altına alır.  Yazarı sorumluluğundadır <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> tanıtıcı her koşulda yayımlanan emin olmak için uygulama. Bunun Sağlanamaması, genellikle tanıtıcı ile ilişkili yerel kaynakları sızıntısını sonuçlanır sızmasını tanıtıcı neden olur. Bu nedenle yapısına kritik <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfları şekilde <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> uygulama çağırma aynı anda kullanılamayabilir herhangi bir kaynağa ayırma gerektirmez. İzin verilen uygulanması içinde başlatılamayabilir çağrısı yöntemlerine olduğuna dikkat edin <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> koşuluyla kodunuzu böyle hataları işlemek ve yerel işleyici yayımlamayı sözleşme tamamlayın. Hata ayıklama amacıyla, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sahip bir <xref:System.Boolean> dönmek için ayarlanabilir değeri `false` kaynak sürümü önleyen işlemi yıkıcı hatayla karşılaşılırsa. Bunun yapılması etkinleşir [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) sorun tanımlanmasına yardımcı olmak için etkinleştirilirse, MDA. Çalışma zamanı başka bir şekilde etkilemez; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yeniden için aynı kaynak çağrılmaz ve tanıtıcı sızmasını sonuç.  
  
 <xref:System.Runtime.InteropServices.SafeHandle>Bazı bağlamlarda uygun değil.  Bu yana <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi, çalıştırılabilir bir <xref:System.GC> sonlandırıcıyı iş parçacığı, belirli bir iş parçacığı üzerinde boşaltılması için gerekli olan tanıtıcıları değil Sarmalanan içinde bir <xref:System.Runtime.InteropServices.SafeHandle>.  
  
 Çalışma zamanı aranabilir sarmalayıcıları (RCWs) ek kod olmadan CLR tarafından temizlenebilir.  Platform çağırma ve bir COM nesnesi değerlendirir kullanan kodu için bir `IUnknown*` veya bir <xref:System.IntPtr>, bir RCW kullanmak için kodu yazılması.  <xref:System.Runtime.InteropServices.SafeHandle>yönetilen kod geri çağırma bir yönetilmeyen yayın yöntemi olasılığı nedeniyle bu senaryo için yeterli olmayabilir.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Kullanım <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi kaynakları için. Kullanmayın <xref:System.Runtime.InteropServices.HandleRef> veya türünde alanlar <xref:System.IntPtr>.  
  
### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Sonlandırıcılar işletim sistemi kaynaklarını sızmasını önlemek için Çalıştır olarak yok emin olun  
 Dikkatle bunlar çalıştırmayın olsa bile, kritik işletim sistemi kaynağı sızdırılmaz emin olmak için sonlandırıcılar gözden geçirin.  Normal bir aksine <xref:System.AppDomain> uygulama kararlı bir duruma veya SQL Server kapatır gibi bir sunucu değil kesin bir ani sırasında nesneleri yürütülürken unload <xref:System.AppDomain> kaldırın.  Kaynakları ani bir unload söz konusu olduğunda, bir uygulamanın doğruluğu garanti edilemez, ancak sunucu bütünlüğünü kaynakları sızmasını değil tarafından korunmalıdır beri sızdırılmaz emin olun.  Kullanım <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi kaynakları serbest bırakma olanağı.  
  
### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Son olarak bu yan tümceleri sızmasını işletim sistemi kaynaklarını önlemek için çalışma gerekmez emin olun  
 `finally`yan tümceleri garanti edilmez CERs dışında çalıştırma kitaplığı geliştiricilerin içindeki kod kalmamanız gerektiren bir `finally` yönetilmeyen kaynakları serbest bloğu.  Kullanarak <xref:System.Runtime.InteropServices.SafeHandle> önerilen çözümdür.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Kullanım <xref:System.Runtime.InteropServices.SafeHandle> yerine işletim sistemi kaynakları Temizleme için `Finalize`. Kullanmayın <xref:System.IntPtr>; kullanın <xref:System.Runtime.InteropServices.SafeHandle> kaynakları için. Varsa yan tümcesi son gerekir, çalıştırmak bir CER yerleştirin.  
  
### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Tüm kilitleri mevcut yönetilen kilitleme kod üzerinden gitmesi gereken  
 CLR kesmeden bilmesini kod bir kilit olduğunda bilmelisiniz <xref:System.AppDomain> yerine yalnızca iş parçacığı durduruluyor.  Üzerinde iş parçacığı tarafından işletilen veri tutarsız bir durumda bıraktığınız iş parçacığı durduruluyor tehlikeli olabilir. Bu nedenle, tüm <xref:System.AppDomain> geri dönüştürülmesi gerekiyor.  Kilit tanımlamak başarısız olan sonuçlarıyla kilitlenmeleri veya hatalı sonuçları olabilir. Yöntemleri kullanın <xref:System.Threading.Thread.BeginCriticalRegion%2A> ve <xref:System.Threading.Thread.EndCriticalRegion%2A> kilit bölgeleri tanımlamak için.  Üzerinde statik yöntemler olduğu <xref:System.Threading.Thread> yalnızca tek bir iş parçacığı başka bir iş parçacığının kilit sayısı düzenleme engellemeye yardımcı olacak geçerli iş parçacığının uygulamak sınıfı.  
  
 <xref:System.Threading.Monitor.Enter%2A>ve <xref:System.Threading.Monitor.Exit%2A> kullanımları yanı sıra kullanılması önerilir, yerleşik bu CLR bildirim sahip [lock deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md), bu yöntemleri kullanır.  
  
 Döndürme kilitleri gibi diğer kilitleme mekanizmaları ve <xref:System.Threading.AutoResetEvent> önemli bir bölümü giriliyor CLR bildirmek için bu yöntemleri çağırmanız gerekir.  Bu yöntemler kilitleri almayan; kod kritik bölümünde yürütüyor CLR bildirin ve iş parçacığı durduruluyor paylaşılan durum tutarsız bırakabilir.  Özel bir gibi kendi kilit türü tanımlı değilse <xref:System.Threading.ReaderWriterLock> sınıfı, bu kilit sayısı yöntemlerini kullanın.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 İşaretleyin ve kullanarak tüm kilitleri tanımlamak <xref:System.Threading.Thread.BeginCriticalRegion%2A> ve <xref:System.Threading.Thread.EndCriticalRegion%2A>. Kullanmayın <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>, ve <xref:System.Threading.Interlocked.Decrement%2A> döngü.  Bir platform yapmak bu yöntemleri Win32 çeşitlemelerini çağırma.  Kullanmayın <xref:System.Threading.Thread.Sleep%2A> döngü.  Volatile alanları kullanmayın.  
  
### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Temizleme kodu içinde olmalıdır bir son olarak veya bir catch bloğu bir catch değil aşağıdaki  
 Kodu temizleme hiçbir zaman izlemelidir bir `catch` engelle; olmalıdır bir `finally` veya `catch` kendisini engelleyin.  Bu, normal iyi bir uygulama olmalıdır.  A `finally` bloğu, genellikle tercih edilen bir özel durum yakalandığında hem zaman aynı kodu çalıştırdığı için sonuna `try` blok normalde karşılaştı.  Örneğin oluşturulan beklenmeyen bir özel durum durumunda bir <xref:System.Threading.ThreadAbortException>, temizleme kod çalışmayacak.  İçinde temizlenmesi kaynakları yönetilmeyen herhangi bir `finally` , ideal olarak alınmalı bir <xref:System.Runtime.InteropServices.SafeHandle> sızıntıları önlemek için.  C# Not `using` anahtar sözcüğü etkili bir şekilde işler de dahil olmak üzere nesnelerin dispose için kullanılabilir.  
  
 Rağmen <xref:System.AppDomain> geri dönüştürülüyor temiz sonlandırıcıyı iş parçacığı üzerinde kaynakları, kodu temizleme doğru yerleştirdiniz hala önem taşır.  Bir iş parçacığı bir zaman uyumsuz özel bir kilit tutmadan alırsa, CLR geri dönüşüm gerek kalmadan iş parçacığının kendi bitiş denemesi Not <xref:System.AppDomain>.  Kaynakları daha erken yerine sonraki yardımcı daha fazla kaynağı kullanılabilir hale getirme ve yaşam süresini daha iyi yönetme temizlendiğinden emin olma.  Bazı hata kodu yolda bir dosya için bir tanıtıcı açıkça kapatmazsanız sonra bekleyin <xref:System.Runtime.InteropServices.SafeHandle> ilk kez kodunuzu çalıştığında, temizlemek için sonlandırıcıyı Sonlandırıcı olmayan zaten çalıştırıldıysa tam aynı dosyaya erişmeye başarısız olabilir.  Bu nedenle, kodu temizleme var olduğundan ve doğru bir şekilde çalıştığından emin olduktan yardımcı olacak kesinlikle gerekli olmasa da hatalarından daha düzgün bir şekilde ve hızlı kurtarma.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Temizleme koddan sonra `catch` olması gereken bir `finally` bloğu. Aramayı içinde silmek için bir son engelleyin.  `catch`Bloklar içinde bir throw bitiş veya yeniden oluşturulması gerekir.  Özel durumlar olacaktır karşın, ağ bağlantı kurulamıyor algılama kodu gibi herhangi bir sayıda özel durumlar, normal koşullar altında özel durum sayısı yakalama gerektiren herhangi bir kod burada alabilirsiniz vermelidir bir kod olmalıdır göstergesi başarılı olur, görmek için test.  
  
### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Uygulama etki alanları arasında değişebilir paylaşılan durumu işlem genelinde ortadan veya kısıtlı yürütme bölge kullanın  
 Girişte açıklandığı gibi işlem genelinde paylaşılan durum uygulama etki alanları arasında güvenilir bir şekilde izler yönetilen kod yazmak oldukça zor olabilir.  İşlem genelinde paylaşılan durumu uygulama etki alanları arasında Win32 kod, CLR içinde ya da remoting kullanarak yönetilen kodda ya da paylaşılan veri yapısı herhangi bir tür değil.  Durum paylaşılmasını değişebilir doğru yönetilen kodda yazma çok zordur ve herhangi bir statik paylaşılan durum yalnızca çok dikkatli ile yapılabilir.  İşlem genelinde veya makine genelinde paylaşılan durum varsa, bunu kaldırın veya kısıtlanmış yürütme bölgesi (CER) kullanarak paylaşılan durumunu korumak için bazı yol bulun.  Tanımlanan düzeltildi değilse ve paylaşılan durumu ile herhangi bir kitaplığı temiz gerektiren SQL Server gibi bir konak sağlayabilir Not <xref:System.AppDomain> çökmesine kaldırma.  
  
 Kod bir COM nesnesi kullanıyorsa, bu COM nesnesinin uygulama etki alanları arasında paylaşımı kaçının.  
  
### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Kilitler işlem genelinde veya uygulama etki alanları arasında çalışmaz.  
 Geçmişte, <xref:System.Threading.Monitor.Enter%2A> ve [lock deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md) genel işlem kilitleri oluşturmak için kullanılır.  Örneğin, bu üzerinde kilitleme ortaya çıkar <xref:System.AppDomain> Çevik sınıflar gibi <xref:System.Type> paylaşılmayan derlemelerden örnekleri <xref:System.Threading.Thread> nesneleri, interned dizeler ve remoting kullanarak uygulama etki alanları arasında paylaşılan herhangi bir dize.  Bu kilit artık işlem kapsamındadır.  İşlem genelinde interapplication etki alanı kilit varlığı tanımlamak için kilit içindeki kod diske veya büyük olasılıkla bir veritabanı dosyası gibi herhangi bir dış, kalıcı kaynak kullanıp kullanmadığını belirleyin.  
  
 Bu içinde bir kilit almayı unutmayın bir <xref:System.AppDomain> korunan kod, dış kaynak kullanır, bu kod, aynı anda birden çok uygulama etki alanları arasında çalıştırabilir çünkü sorunlara neden olabilir.  Bu yazma sırasında bir sorun olabilir tek bir günlük dosyası veya tüm işlem için bir yuva için bağlama.  Bu değişiklikler, bir adlandırılmış kullanma dışındaki bir işlem genel kilit yönetilen kodu kullanarak hiçbir kolay bir yolu olmadığını anlamına geliyor <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore> örneği.  Olmayan iki uygulama etki alanında aynı anda çalıştırmak, veya kullanan kodu oluşturmak <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore> sınıfları.  Var olan kodu değiştirilemiyorsa mutex adlı bir Win32 fiber modunda çalışan işletim sistemi iş parçacığı edinmeli ve bir mutex yayın garanti edemez gösterdiğinden bu eşitleme elde etmek için kullanmayın.  Yönetilen kullanmalısınız <xref:System.Threading.Mutex> sınıfı veya bir adlandırılmış <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, veya bir <xref:System.Threading.Semaphore> CLR yönetilmeyen kod kullanarak kilit eşitleme yerine bilmektedir bir şekilde kod kilit eşitlenecek.  
  
#### <a name="avoid-locktypeofmytype"></a>Lock(typeof(MyType)) kaçının  
 Özel ve ortak <xref:System.Type> tüm uygulama etki alanları arasında paylaşılan kod yalnızca bir kopya ile paylaşılan derlemeler nesneleri sorunları de sunar.  Paylaşılan derlemeler için yalnızca bir örneği var. bir <xref:System.Type> her işlem, birden çok uygulama etki alanları tam aynı paylaşıma anlamına <xref:System.Type> örneği.  Kilit almayı bir <xref:System.Type> örneği alır, tüm işlem etkileyen değil kilit yalnızca <xref:System.AppDomain>.  Varsa <xref:System.AppDomain> kilit geçen bir <xref:System.Type> iş parçacığı aniden durduruldu, kilidi serbest değil nesne.  Bu kilit sonra kilitlenme diğer uygulama etki alanları neden olabilir.  
  
 Statik yöntemleri kilitleri olabilmesi için en iyi yolu, bir statik iç eşitleme nesnesi için kod ekleme içerir.  Bu sınıf oluşturucusunda varsa, ancak bunu şu şekilde başlatılamıyor başlatılamadı:  
  
```  
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
  
 Ardından bir kilit kullanım duruma getirirken `InternalSyncObject` kilitlemek için bir nesne almak için özellik.  İç eşitleme nesne sınıfı oluşturucuda başlatılmış durumunda özelliğinin kullanılması gerekmez.  Çift denetimi kilit başlatma kodu, bu örnekteki gibi görünmelidir:  
  
```  
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
  
#### <a name="a-note-about-lockthis"></a>Not Lock(this) hakkında  
 Genel olarak erişilebilir olan tek tek bir nesne üzerinde bir kilit etkinleştirilir genellikle kabul edilebilir.  Ancak, nesne kilitlenme için tüm bir alt neden olabilecek bir singleton nesneyse da yukarıdaki tasarım deseni kullanmayı düşünün.  Örneğin, bir kilit <xref:System.Security.SecurityManager> nesnesi içinde bir kilitlenme neden <xref:System.AppDomain> tüm yapma <xref:System.AppDomain> kullanılamaz. Bu tür genel olarak erişilebilir bir nesne üzerinde bir kilit olmayacağına iyi bir uygulamadır.  Ancak bir tek tek koleksiyonu veya dizisi üzerinde bir kilit genellikle bir sorun yoktur.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Kilitleri uygulama etki alanları arasında kullanılan ya da kimlik güçlü bir fikir yok türlerinde kazanmaz. Çağırmayın <xref:System.Threading.Monitor.Enter%2A> üzerinde bir <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>, veya türetilen herhangi bir nesne <xref:System.MarshalByRefObject>.  
  
### <a name="remove-gckeepalive-calls"></a>GC kaldırın. KeepAlive çağrıları  
 Var olan kodu önemli miktarda kullanmayan <xref:System.GC.KeepAlive%2A> zaman gerekir veya uygun değilse, bunu kullanır.  Dönüştürme sonra <xref:System.Runtime.InteropServices.SafeHandle>, sınıfları çağrı gerekmez <xref:System.GC.KeepAlive%2A>, bir sonlandırıcı yoksa ancak Bel varsayılarak <xref:System.Runtime.InteropServices.SafeHandle> işletim sistemi sonlandırmak için işler.  While yapılan bir çağrı korunuyor performans maliyeti <xref:System.GC.KeepAlive%2A> durum, göz ardı edilebilir algısına, çağrı <xref:System.GC.KeepAlive%2A> gerekli ya da artık mevcut olmayabilir sorunu kodu korumak daha zor yapar bir ömrü çözmek yeterli.  Ancak, COM birlikte çalışma CLR aranabilir sarmalayıcılar (RCWs) kullanırken <xref:System.GC.KeepAlive%2A> kod tarafından hala gereklidir.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Kaldırma <xref:System.GC.KeepAlive%2A>.  
  
### <a name="use-the-host-protection-attribute"></a>Ana bilgisayar koruması özniteliğini kullanın  
 <xref:System.Security.Permissions.HostProtectionAttribute> (HPA) gibibelirlianabilgisayariçinuygunolanbazıyöntemleriçağırmabiletamgüvenilirkodunengellemekanabilgisayarizinvererekkonakkorumagereksinimlerinibelirlemekiçinbildirimtemelligüvenlikeylemlerikullanımınısağlar<xref:System.Environment.Exit%2A>veya <xref:System.Windows.Forms.MessageBox.Show%2A> SQL Server için.  
  
 HPA barındıran ortak dil çalışma zamanı ve uygulama ana bilgisayar koruması, SQL Server gibi yalnızca yönetilmeyen uygulamaları etkiler. Uygulandığında, bağlantı isteği oluşturulmasına güvenlik eylem sonuçlarını sınıf veya yöntemin çıkarır konak kaynaklara bağlı. Kod bir istemci uygulamasında veya ana bilgisayar korumalı olmayan bir sunucuda çalıştırırsanız öznitelik "evaporates"; değil algılanır ve bu nedenle uygulanmaz.  
  
> [!IMPORTANT]
>  Ana bilgisayara özgü programlama modeli yönergeleri, güvenliği davranışını zorlamak için bu öznitelik amacı budur.  Model gereksinimleri programlama için uygunluk denetlemek için bir bağlantı isteği kullanılsa <xref:System.Security.Permissions.HostProtectionAttribute> bir güvenlik izni değil.  
  
 Ana, model gereksinimleri programlama yoksa bağlantı talepleri gerçekleşmez.  
  
 Bu öznitelik aşağıdakileri tanımlar:  
  
-   Yöntemleri veya programlama modeli, ana bilgisayar uymayan sınıfları ancak Aksi halde zararsız.  
  
-   Yöntemleri veya sınıflarda konak programlama modeli sığmayan ve sunucusu yönetilen kullanıcı kodu destabilizing için neden olabilir.  
  
-   Yöntemleri veya programlama konak uymayan sınıfları model ve bir sunucu işlemi destabilization için yol açabilir.  
  
> [!NOTE]
>  Bir korumalı konak ortamında yürütür uygulamalar tarafından çağrılacak olan bir sınıf kitaplığı oluşturuyorsanız, bu öznitelik kullanıma üyelerine uygulamalıdır <xref:System.Security.Permissions.HostProtectionResource> kaynak kategoriler. Bu öznitelik ile .NET Framework sınıf kitaplığı üyeleri denetlenmesi yalnızca ilk çağıran neden.  Kitaplık üyesini aynı şekilde anında arayanlar kontrol neden gerekir.  
  
 Lütfen HPA hakkında daha fazla bilgi bulmak <xref:System.Security.Permissions.HostProtectionAttribute>.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 SQL Server için eşitleme veya iş parçacığı oluşturma sunmak için kullanılan tüm yöntemleri gerekir tanımlanan HPA ile. Bu durum paylaşmak, eşitlenen ya da dış işlemlerini yönetmek yöntemleri içerir. <xref:System.Security.Permissions.HostProtectionResource> SQL Server etkisi değerler <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, ve <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Ancak, herhangi bir kullanıma sunan herhangi bir yöntemini <xref:System.Security.Permissions.HostProtectionResource> bir HPA tarafından yalnızca bu SQL etkileyen kaynakları kullanarak tanımlanmalıdır.  
  
### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Yönetilmeyen kod içinde süresiz olarak engellemez  
 Yönetilen kod yerine yönetilmeyen kodunda engelleme, CLR iş parçacığı abort mümkün olmadığı için bir hizmet reddi saldırısına neden olabilir.  Engellenen bir iş parçacığı CLR kaldırılmasını engeller <xref:System.AppDomain>, en az son derece güvenli olmayan bazı işlemler yapmak olmadan.  Win32 kullanarak engelleme eşitleme basit bir şey izin veremez Temizle bir örneği bulunmaktadır.  Çağrıda engelleme `ReadFile` bir yuvada mümkünse kaçınılmalıdır — ideal Win32 API şuna benzer bir işlem zaman aşımına için bir mekanizma sağlamanız gerekir.  
  
 Yerel çağırır herhangi bir yöntemini makul, sonlu zaman aşımı ile bir Win32 çağrı ideal olarak kullanmanız gerekir.  Zaman aşımını belirlemek için kullanıcı izin veriliyorsa, kullanıcı sonsuz bir zaman aşımı bazı belirli güvenlik izni olmadan belirtmek için izin verilmelidir değil.  Bir kılavuz olarak ~ 10 saniyeden fazla için bir yöntem engeller, zaman aşımları destekleyen bir sürüm kullanıyor gerekir veya ek CLR destek gerekir.  
  
 Sorunlu API'nin bazı örnekleri aşağıda verilmiştir.  Kanallar (adsız ve adlandırılmış) zaman aşımı ile oluşturulabilir; Ancak, kodu, hiçbir zaman çağrıları emin olmalısınız `CreateNamedPipe` ya da `WaitNamedPipe` NMPWAIT_WAIT_FOREVER ile.  Ayrıca, olabilir bir zaman aşımı belirtilmiş olsa bile engelleme beklenmeyen.  Çağırma `WriteFile` arabellek varsa anlamı tüm baytlar yazılır kadar anonim bir kanalda engeller, okunmamış verilerde `WriteFile` çağrısı okuyucu kanal 's arabellek alanı serbest kadar engeller.  Yuva her zaman bir zaman aşımı mekanizması geliştirir bazı API kullanmanız gerekir.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Yönetilmeyen kod zaman aşımı olmadan engelleyen bir hizmet reddi saldırısına olur. Platform gerçekleştirmeyin çağrıları çağırma `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`, ve `MsgWaitForMultipleObjectsEx`.  NMPWAIT_WAIT_FOREVER kullanmayın.  
  
### <a name="identify-any-sta-dependent-features"></a>STA'ya bağımlı özellikler tanımlayın.  
 Tek iş parçacıklı COM grupların (STAs) kullanan herhangi bir kod tanımlayın.  STAs SQL Server işleminde devre dışı bırakılır.  Bağımlı Özellikler `CoInitialize`performans sayaçlarını veya Pano devre dışı bırakılmalıdır içinde SQL Server gibi.  
  
### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Sonlandırıcılar eşitleme sorunlarını boş olduğundan emin olun  
 Birden çok sonlandırıcıyı iş parçacığı gelecekte sonlandırıcılar için aynı anda çalışmasına aynı türde farklı örnekleri anlamına gelir, .NET Framework sürümleri bulunuyor olabilir.  Tamamen iş parçacığı içinde korumalı olması gerekmez; Çöp toplayıcı sonlandırıcıyı belirli nesne örneği için yalnızca bir iş parçacığı çalışacağını garanti eder.  Ancak, sonlandırıcılar yarış durumları ve kilitlenmeleri aynı anda birden çok farklı nesne örnekleri üzerinde çalışırken önlemek için kodlanmış olmalıdır.  İş parçacığı oluşturma sorunları, bir günlük dosyasında bir sonlandırıcı yazma gibi dış durumu kullanırken ele alınması gerekir.  İş parçacığı güvenliği sağlamak sonlandırma kullanmayın. İş parçacığı yerel depolaması, yönetilen veya yerel, sonlandırıcıyı iş parçacığı üzerinde durumunu depolamak için kullanmayın.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Sonlandırıcılar eşitleme sorunlarını boş olması gerekir. Bir statik değişebilir bir sonlandırıcı durumda kullanmayın.  
  
### <a name="avoid-unmanaged-memory-if-possible"></a>Yönetilmeyen bellek mümkünse kaçının  
 Yalnızca bir işletim sistemi tanıtıcısı gibi yönetilmeyen bellek sızabileceği.  Mümkünse, yığın kullanarak bellek kullanmaya çalıştığınızda [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) veya sabitlenmiş bir yönetilen nesne gibi [deyimi sabit](~/docs/csharp/language-reference/keywords/fixed-statement.md) veya <xref:System.Runtime.InteropServices.GCHandle> kullanarak byte [].  <xref:System.GC> Sonunda bunlar temizler.  Yönetilmeyen bellek gerekir, ancak türeyen bir sınıf kullanmayı <xref:System.Runtime.InteropServices.SafeHandle> bellek ayırma sarmalamak için.  
  
 En az bir harf olduğuna dikkat edin nerede <xref:System.Runtime.InteropServices.SafeHandle> yeterli değil.  Ayırma ya da boş bellek COM yöntem çağrıları için aracılığıyla bellek ayırmak bir DLL için ortak olan `CoTaskMemAlloc` bu belleğe sahip başka bir DLL boşaltır sonra `CoTaskMemFree`.  Kullanarak <xref:System.Runtime.InteropServices.SafeHandle> ömrü yönetilmeyen belleği ömrü bağlamanın deneyecek beri bu yerlerde uygunsuz olacaktır <xref:System.Runtime.InteropServices.SafeHandle> diğer DLL denetimi bellek ömrü izin vermek yerine.  
  
### <a name="review-all-uses-of-catchexception"></a>Catch(Exception) tüm kullanımlarını gözden geçirin  
 Catch blokları catch tüm özel durumları tek bir özel durum yerine zaman uyumsuz özel durumlar da şimdi yakalar.  Büyük olasılıkla yanlış davranışa catch bloğu kendisini işleme içinde yanı sıra atlanabilir hiçbir önemli kaynak serbest bırakma ya da geri çıkma kod arayan her catch(Exception) blok inceleyin bir <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, veya <xref:System.OutOfMemoryException>.  Bu kod oturum veya tek bir belirli nedenle başarısız oldu, bir özel durum olduğunda, yalnızca belirli özel durumları veya görebileceğiniz bazı varsayımlarda yapmadan mümkün olduğunu unutmayın.  Bu varsayımları içerecek şekilde güncelleştirilmesi gerekebilir <xref:System.Threading.ThreadAbortException>.  
  
 Tüm değiştirme yerleştirir beklediğiniz özel durumu belirli bir türdeki yakalama için tüm özel durum, bu catch gibi göz önünde bulundurun bir <xref:System.FormatException> dizeden biçimlendirme yöntemlerine.  Bu yakalama bloğunun beklenmeyen özel durumları çalışmasını engeller ve kod hataları beklenmeyen özel durumları yakalama tarafından gizlemez sağlamaya yardımcı olur.  Genel kural olarak hiçbir zaman kitaplık kodu bir özel durum işleme (bir özel durum catch gerektiren kod çağırdığınız kodda bir tasarım kusur gösterebilir).  Bazı durumlarda bir özel durum yakalamak ve daha fazla veri sağlamak için farklı bir özel durum türüne throw isteyebilirsiniz.  İç içe geçmiş özel durumlar, bu durumda, gerçek başarısızlığın nedenini depolamak kullanın <xref:System.Exception.InnerException%2A> yeni özel durum özelliği.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Yönetilen kod tüm catch blokları Bu catch tüm nesneleri veya catch tüm özel durumları gözden geçirin.  C# ' ta her ikisi de işaretlemesini yani `catch` {} ve `catch(Exception)` {}.  Özel durum türü belirli yapmayı düşünün veya beklenmeyen özel durum türü yakalar varsa, hatalı bir şekilde hareket değil emin olmak için kodu gözden geçirin.  
  
### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Varsayın değil yönetilen iş parçacığı bir Win32 iş parçacığı – bir Fiber olduğu  
 Yönetilen iş parçacığı yerel depolama çalışır ama, düzgün yönetilmeyen iş parçacığı yerel depolama kullanın veya kodu geçerli işletim sistemi iş parçacığı üzerinde yeniden çalıştıracak varsayın kullanarak.  İş parçacığı yerel ayarları gibi ayarları değiştirmeyin.  Çağırmayın `InitializeCriticalSection` veya `CreateMutex` kilit girer işletim sistemi iş parçacığına da kilidi çıkmak gerektirdiğinden platform çağırma.  Bu durum lifleri kullanırken değil olacağından, Win32 kritik bölümler ve zaman uyumu sağlayıcılar SQL doğrudan kullanılamaz.  Unutmayın yönetilen <xref:System.Threading.Mutex> sınıfı, bu iş parçacığı benzeşimini sorunları işlemez.  
  
 Güvenli bir şekilde durumu çoğunu yönetilen üzerinde kullanabilirsiniz <xref:System.Threading.Thread> yönetilen iş parçacığı yerel depolaması ve iş parçacığının geçerli UI kültürü içeren nesne.  Aynı zamanda <xref:System.ThreadStaticAttribute>, hangi yapar mevcut bir statik değişken değerini erişilebilir (Bu, yerel depolama CLR fiber yapmanın bir başka yolu) yalnızca geçerli yönetilen iş parçacığı tarafından.  Programlama modeli nedenleri, geçerli bir iş parçacığı kültürünü SQL'de çalıştırırken değiştirilemiyor.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 SQL Server fiber modunda çalışır; iş parçacığı yerel depolaması kullanmayın. Platform kaçının çağrıları çağırma `TlsAlloc`, `TlsFree`, `TlsGetValue`, ve`TlsSetValue.`  
  
### <a name="let-sql-server-handle-impersonation"></a>SQL Server tanıtıcı kimliğe bürünme sağlar  
 Kimliğe bürünme iş parçacığı düzeyinde çalışır ve SQL fiber modunda çalıştırmak için yönetilen kod kullanıcıların kimliğine bürüneceği değil ve değil çağırmalıdır `RevertToSelf`.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 SQL Server kimliğe bürünme işlemesine olanak sağlar. Kullanmayın `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`, veya `SetThreadToken`.  
  
### <a name="do-not-call-threadsuspend"></a>Thread::suspend çağırmayın  
 Bir iş parçacığı askıya alabilme basit bir işlemle görünebilir, ancak kilitlenmeleri neden olabilir.  Kilit ikinci bir iş parçacığı ve ardından ikinci bir iş parçacığı tarafından askıya bulunduran bir iş parçacığı aynı kilidi alma çalışırsa, bir kilitlenme oluşur.  <xref:System.Threading.Thread.Suspend%2A>Güvenlik, sınıf yükleme, remoting ve yansıma ile şu anda etkileyebilir.  
  
#### <a name="code-analysis-rule"></a>Kod Analizi kural  
 Çağırmayın <xref:System.Threading.Thread.Suspend%2A>. Gerçek bir eşitleme kullanmayı bunun yerine, gibi basit bir <xref:System.Threading.Semaphore> veya <xref:System.Threading.ManualResetEvent> .  
  
### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Kısıtlı yürütme bölgeleri ve güvenilirlik sözleşmeleri ile ilgili kritik işlemleri koruma  
 Karmaşık bir işlemi gerçekleştirirken paylaşılan durum güncelleştirmelerini veya belirleyici biçimde ya da tam olarak başarılı veya tamamen başarısız, kısıtlı yürütme bölge (CER) tarafından korunduğundan emin gerekiyor. Bu kodu her durumda, hatta bir ani iş parçacığı durdurma veya bir ani çalışır garanti <xref:System.AppDomain> kaldırın.  
  
 Belirli bir CER olan `try/finally` için yapılan bir çağrı tarafından hemen öncesinde blok <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
 Bunu yaptığınızda bu nedenle tüm kodda hazırlamak üzere tam zamanı derleyici bildirir çalıştırmadan önce finally bloğunda `try` bloğu. Bu, kodda garanti finally bloğu yerleşik olarak bulunur ve tüm durumlarda çalışır. Boş bir sağlamak için bir CER seyrek değil `try` bloğu. Bir CER kullanarak zaman uyumsuz iş parçacığı iptalleri ve bellek yetersiz özel durumları karşı korur. Bkz: <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> ayrıca tanıtıcıları yığın verebilmesine derin kodunu taşar CER formu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.ConstrainedExecution>  
 [SQL Server programlama ve konak koruması öznitelikleri](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
