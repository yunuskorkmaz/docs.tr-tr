---
title: Eşitleme Temellerine Genel Bakış
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37abcb6b3a8fdf4ef91d5e946a97db7ca1428ce8
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529577"
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme Temellerine Genel Bakış
<a name="top"></a> .NET Framework eşitleme temellerine çeşitli iş parçacıklarının etkileşimler denetleme ve yarış durumları önleme sağlar. Bu kabaca üç kategoriye ayrılabilir: kilitleme, sinyal ve birbirine kenetlenmiş işlemler.  
  
 Kategorileri derleyin veya açıkça tanımlanmış değildir: Bazı eşitleme mekanizmaları birden çok kategori; özelliklerine sahip bir kerede tek bir iş parçacığı yayın olayları gibi işlevsel olarak kilitleri; herhangi bir kilidi sürümü, bir sinyal düşünülebilir; ve birbirine kenetlenmiş işlemler kilit oluşturmak için kullanılabilir. Ancak, kategorileri hala faydalıdır.  
  
 İş parçacığı eşitleme işbirlikçi olduğunu unutmamak önemlidir. Tek iş parçacığı eşitleme mekanizması atlar ve doğrudan korumalı kaynağa erişir, bu eşitleme mekanizması etkin olamaz.  
  
 Bu genel bakış aşağıdaki bölümleri içerir:  
  
-   [Kilitleme](#locking)  
  
-   [Sinyal](#signaling)  
  
-   [Hafif eşitleme türleri](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Birbirine Kenetlenmiş İşlemler](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Kilitleme  
 Kilitleri, aynı anda tek bir iş parçacığı veya belirtilen bir iş parçacığı sayısı için bir kaynak denetim verir. Kilit olduğunda, özel bir kilit isteyen bir iş parçacığı kilit kullanılabilir oluncaya kadar blokları kullanın.  
  
### <a name="exclusive-locks"></a>Özel kilit  
 Kilitleme en basit biçimidir `lock` C# deyimi ve `SyncLock` deyimi Visual Basic'te, bir kod bloğu erişimi denetler. Böyle bir blok, genellikle önemli bir bölümü da bilinir. `lock` Deyimi kullanılarak gerçekleştirilen <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> yöntemleri ve onu kullanan bir `try…finally` kilidi serbest bırakılır emin olmak için blok.  
  
 Genel olarak, kullanarak `lock` veya `SyncLock` deyimi küçük kod, hiçbir zaman kapsayan birden fazla tek bir yöntem bloklarını korumak için kullanılacak en iyi yolu <xref:System.Threading.Monitor> sınıfı. Güçlü ancak <xref:System.Threading.Monitor> sınıftır sahipsiz kilit ve kilitlenmeleri eğilimlidir.  
  
#### <a name="monitor-class"></a>İzleme sınıfı  
 <xref:System.Threading.Monitor> Sınıfı ile birlikte kullanılan ek işlevsellik sağlar `lock` deyimi:  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> Yöntemi için belirtilen bir süre sonra vermek kaynak bekleyerek engellenen bir iş parçacığı sağlar. Başarı veya başarısızlık, algılamak ve olası kilitlenmeleri önlemek için kullanılabilecek gösteren bir Boole değeri döndürür.  
  
-   <xref:System.Threading.Monitor.Wait%2A> Yöntemi bir iş parçacığı, kritik bölüm tarafından çağrılır. Kaynağı yeniden kullanılabilir olana kadar blokları ve kaynak denetimi sağlar.  
  
-   <xref:System.Threading.Monitor.Pulse%2A> Ve <xref:System.Threading.Monitor.PulseAll%2A> yöntemleri hakkında kilidi veya çağırmak için bir iş parçacığı izin <xref:System.Threading.Monitor.Wait%2A> kilidi almak hazır kuyruğa bir veya daha fazla iş parçacığı yerleştirmek için.  
  
 Zaman aşımlarını <xref:System.Threading.Monitor.Wait%2A> yöntemi aşırı yüklemeleri hazır kuyruğa atlamak bekleyen iş parçacıklarının izin verin.  
  
 <xref:System.Threading.Monitor> Sınıfı, birden çok uygulama etki alanlarında kilit için kullanılan nesne öğesinden türer, kilitleme sağlayabilir <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> iş parçacığı benzeşimini sahiptir. Diğer bir deyişle, İzleyici girilen bir iş parçacığı çağırarak çıkmalı <xref:System.Threading.Monitor.Exit%2A> veya <xref:System.Threading.Monitor.Wait%2A>.  
  
 <xref:System.Threading.Monitor> Sınıf instantiable değil. Yöntemleri statik (`Shared` Visual Basic'te) ve instantiable kilit nesne üzerinde işlem yapma.  
  
 Kavramsal bir genel bakış için bkz. [izleyiciler](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Mutex Sınıfı  
 İş parçacıkları isteği bir <xref:System.Threading.Mutex> bir aşırı yüklemesini çağırarak kendi <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Aşırı yüklemeler zaman aşımı ile bekleme vermek iş parçacığı olanak sağlanır. Farklı <xref:System.Threading.Monitor> sınıfı, bir mutex yerel veya genel olabilir. Adlandırılmış mutex'leri olarak da bilinen genel mutex'leri boyunca işletim sistemi tarafından görülebilir ve birden çok uygulama etki alanları veya işlem iş parçacıklarının eşitlemek için kullanılabilir. Yerel mutex'leri türetilen <xref:System.MarshalByRefObject>ve uygulama etki alanı sınırlarında kullanılabilir.  
  
 Ayrıca, <xref:System.Threading.Mutex> türetildiği <xref:System.Threading.WaitHandle>, yani bu sinyal tarafından sağlanan mekanizmaları ile kullanılabilir <xref:System.Threading.WaitHandle>, gibi <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, ve <xref:System.Threading.WaitHandle.SignalAndWait%2A> yöntemleri.  
  
 Gibi <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> iş parçacığı benzeşimini sahiptir. Farklı <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> instantiable bir nesnedir.  
  
 Kavramsal bir genel bakış için bkz. [mutex'ler](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>SpinLock sınıfı  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.SpinLock> sınıf ek yükü tarafından istendiğinde <xref:System.Threading.Monitor> performansı düşürür. Zaman <xref:System.Threading.SpinLock> kilitli kritik bölümü karşılaştığında kilit kullanılabilir oluncaya kadar yalnızca bir döngüde döner. Kilit çok kısa bir süre tutulursa, dönen engelleme daha iyi performans sağlar. Ancak, döngü, fazla sayıda onlarca kilidi açık tutulduğu <xref:System.Threading.SpinLock> ekleyebiliyorsa gerçekleştirir olarak <xref:System.Threading.Monitor>, ancak daha fazla CPU döngüsü kullanır ve bu nedenle diğer iş parçacıkları veya işlemlerdeki performansını düşürebilir.  
  
### <a name="other-locks"></a>Diğer kilitleri  
 Kilitleri özel olması gerekmez. Genellikle, sınırlı sayıda iş parçacığının bir kaynağa eş zamanlı erişim izni vermek kullanışlıdır. Semafor ve Okuyucu-Yazıcı kilitleri, bu tür bir havuza alınmış kaynak erişimi denetlemek için tasarlanmıştır.  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock Sınıfı  
 <xref:System.Threading.ReaderWriterLockSlim> Sınıfı adresleri veri yazıcısı değiştiren bir iş parçacığı gerekir sahip olduğu bir kaynağa özel erişim durumu. Yazıcı etkin değilken okuyucular herhangi bir sayıda kaynağa erişmek için (örneğin, arama tarafından <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> yöntemi). Bir iş parçacığı özel erişim istediğinde (çağırarak gibi <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> yöntemi), tüm mevcut okuyucular kilit çıkılana ve yazıcı girdi ve çıktı kilit kadar sonraki okuyucu istekleri blok.  
  
 <xref:System.Threading.ReaderWriterLockSlim> iş parçacığı benzeşimini sahiptir.  
  
 Kavramsal bir genel bakış için bkz. [Okuyucu-Yazıcı kilitleri](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Semafor Sınıfı  
 <xref:System.Threading.Semaphore> Sınıfı, belirtilen sayıda iş parçacığı bir kaynağa erişmeye olanak tanır. Bir iş parçacığı semafor serbest kadar kaynak blok isteyen ek iş parçacıkları.  
  
 Gibi <xref:System.Threading.Mutex> sınıfı <xref:System.Threading.Semaphore> türetildiği <xref:System.Threading.WaitHandle>. Ayrıca <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> yerel veya genel olabilir. Uygulama etki alanı sınırlarında kullanılabilir.  
  
 Farklı <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, ve <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> iş parçacığı benzeşimini sahip değil. Başka bir deyişle, burada tek bir iş parçacığı semafor devralır ve başka bir serbest senaryolarda kullanılabilir.  
  
 Kavramsal bir genel bakış için bkz. [semafor ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> tek bir işlem sınırları içinde eşitleme için basit bir semafor olur.  
  
 [Başa dön](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Sinyal  
 Çağırmak için başka bir iş parçacığından bir sinyal için beklenecek en basit yolu <xref:System.Threading.Thread.Join%2A> başka bir iş parçacığı tamamlanıncaya kadar engeller yöntemi. <xref:System.Threading.Thread.Join%2A> Belirtilen bir zaman aralığı geçtikten sonra dışı beklemeyi ayırmak engellenen iş parçacığına izin veren iki aşırı yüklemesi vardır.  
  
 Bekleme tanıtıcıları bekleyen ve özellikleri sinyal çok daha zengin sağlar.  
  
### <a name="wait-handles"></a>Bekleme Tanıtıcıları  
 Bekleme tanıtıcıları türetilen <xref:System.Threading.WaitHandle> sırayla türetilen sınıf <xref:System.MarshalByRefObject>. Bu nedenle, bekleme tanıtıcıları, uygulama etki alanı sınırları arasında iş parçacıklarının etkinlikleri eşitlemek için kullanılabilir.  
  
 İş parçacıklarını bekleme blok işleme örnek yöntemini çağırarak <xref:System.Threading.WaitHandle.WaitOne%2A> veya statik yöntemleri <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, veya <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Nasıl yayımlanan hangi yöntemi çağrıldı ve bekleme tanıtıcıları türüne bağlıdır.  
  
 Kavramsal bir genel bakış için bkz. [bekleyin işler](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Olay bekleme tanıtıcıları  
 Olay bekleme tanıtıcıları içeren <xref:System.Threading.EventWaitHandle> sınıfı ve türetilmiş sınıflarının <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent>. Olay bekleme tanıtıcısı çağırarak sinyal olduğunda bir olay bekleme tanıtıcısı iş parçacığı yayımlandığında, <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi kullanarak veya <xref:System.Threading.WaitHandle.SignalAndWait%2A> yöntemi.  
  
 Olay ya da kendilerini otomatik olarak yalnızca tek bir iş parçacığı aracılığıyla işareti verilen veya el ile sıfırlama sinyal ve birisi kapatana kadar açın kadar kapalı bir ağ geçidi gibi her zaman izin veren bir Turnike gibi sıfırlama tanıtıcıları bekleyin. Adlarını da ifade ettiği şekilde <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> eski ve ikinci olarak, sırasıyla temsil eder. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> tek bir işlem sınırları içinde eşitleme için basit bir olaydır.  
  
 Bir <xref:System.Threading.EventWaitHandle> ya da olay türünü temsil edebilir ve yerel veya genel olabilir. Türetilen sınıfların <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> her zaman yereldir.  
  
 Olay bekleme tanıtıcıları iş parçacığı benzeşimini yok. Herhangi bir iş parçacığı, bir olay bekleme tanıtıcısının sinyal verebilirsiniz.  
  
 Kavramsal bir genel bakış için bkz. [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Mutex ve semafor sınıfları  
 Çünkü <xref:System.Threading.Mutex> ve <xref:System.Threading.Semaphore> sınıflar türetilen <xref:System.Threading.WaitHandle>, statik yöntemleriyle kullanılabilir <xref:System.Threading.WaitHandle>. Örneğin, bir iş parçacığı kullanabilirsiniz <xref:System.Threading.WaitHandle.WaitAll%2A> Aşağıdakilerden üçü true olana kadar beklenecek yöntemi: bir <xref:System.Threading.EventWaitHandle> işareti verilen bir <xref:System.Threading.Mutex> yayımlandığı ve <xref:System.Threading.Semaphore> serbest bırakılır. Benzer şekilde, bir iş parçacığı kullanabilirsiniz <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemi Bu koşullardan herhangi biri true olana kadar bekleyin.  
  
 İçin bir <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore>, sinyal yayımlanan anlamına gelir. Her iki türü ilk bağımsız değişken olarak kullanılıp kullanılmadığını <xref:System.Threading.WaitHandle.SignalAndWait%2A> yöntemi serbest kalır. Durumunda, bir <xref:System.Threading.Mutex>, iş parçacığı benzeşimini olan, çağıran iş parçacığını mutex sahip değilse bir özel durum oluşturulur. Daha önce belirtildiği gibi iş parçacığı benzeşimini parçacıklarıyla yok.  
  
#### <a name="barrier"></a>Engel  
 <xref:System.Threading.Barrier> Sınıfı, böylece bunlar aynı anda tüm blok gelin ve tamamlamak tüm diğer iş parçacıkları için bekleyin periyodik olarak birden çok iş parçacığı eşitlemek için bir yol sağlar. Bir engel bir algoritma sonraki aşamaya devam etmeden önce bir veya daha fazla iş parçacığı başka bir iş parçacığı sonuçlarını gerektiğinde yararlıdır. Daha fazla bilgi için [engel](../../../docs/standard/threading/barrier.md).  
  
 [Başa dön](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Hafif eşitleme türleri  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Win32 çekirdek pahalı güvenme önleme hızlı performansı bekleme tanıtıcıları mümkün olduğunca gibi nesneleri sağlayan eşitleme temellerine kullanabilirsiniz. Genel olarak, bu tür bekleme süresini kısa olduğunda ve yalnızca özgün eşitleme türleri çalıştı ve yetersiz olduğu tespit kullanmanız gerekir. Basit türler çapraz proses haberleşmesi gerektiren senaryolar içinde kullanılamaz.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> hafif bir sürümüdür <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> hafif bir sürümüdür <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> kendi sayısı sıfır olduğunda, sinyal haline gelir bir olayı temsil eder.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> Ana iş parçacığı tarafından denetim gerektirmeden birbirleriyle eşitlemek birden çok iş parçacığı sağlar. Tüm iş parçacıklarının belirli bir noktaya ulaşıncaya kadar bir engel her iş parçacığı devam etmesini engeller.  
  
 [Başa dön](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kullanabileceğiniz <xref:System.Threading.SpinWait?displayProperty=nameWithType> sinyal bir olay ya da karşılanması gereken bir koşul için beklenecek bir iş parçacığı sahip olduğunda, ancak gerçek bir bekleme süresi bir bekleme tanıtıcısı kullanarak veya otherwi gereken bekleme süresi değerinden küçük olması bekleniyorsa yapısı Geçerli iş parçacığını engelleyip se. Kullanarak <xref:System.Threading.SpinWait>, bekleme sırasında çalıştırın ve koşul belirtilen süre içinde yalnızca aşıldığı değil durumunda (örneğin, bekleyen veya uyku) verim için kısa bir süre belirtebilirsiniz.  
  
 [Başa dön](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Birbirine Kenetlenmiş İşlemler  
 Birbirine kenetlenmiş işlemler olan bir bellek konumuna statik yöntemleri tarafından gerçekleştirilen basit atomik işlemler <xref:System.Threading.Interlocked> sınıfı. Atomik işlemleri ekleme dahil, artırmak ve azaltma, exchange, bir karşılaştırma bağlı olarak koşullu exchange okuma işlemleri ve 64-bit değerleri için 32-bit platformlarda.  
  
> [!NOTE]
>  Kararlılık garanti tek işlemler için sınırlıdır; bir birim olarak birden çok işlemi gerçekleştirilmesi gerekir, daha parçalı bir eşitleme mekanizması kullanılması gerekir.  
  
 Bu işlemlerin hiçbiri kilitler veya sinyalleri olmasına rağmen kilitler ve sinyaller oluşturmak için kullanılabilir. Birbirine kenetlenmiş işlemler, Windows işletim sisteminde yerel oldukları için son derece hızlı.  
  
 Birbirine kenetlenmiş işlemler, güçlü engelleyici olmayan eşzamanlılık sergileyen uygulamalar yazmak üzere geçici bir bellek Garantisi ile kullanılabilir. Ancak, bunlar ciddi bir şekilde daha iyi bir seçenek birçok amaç için basit kilit şekilde karmaşık, düşük düzeydeki programlama, gerektirir.  
  
 Kavramsal bir genel bakış için bkz. [birbirine geçmiş Operations](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [İzleyiciler](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
- [Karşılıklı dışlamalar](../../../docs/standard/threading/mutexes.md)  
- [Semaphore ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Bekleme tanıtıcıları](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
- [Birbirine Kenetlenmiş İşlemler](../../../docs/standard/threading/interlocked-operations.md)  
- [Okuyucu-Yazıcı Kilitleri](../../../docs/standard/threading/reader-writer-locks.md)  
- [Engel](../../../docs/standard/threading/barrier.md)  
- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [SpinLock](../../../docs/standard/threading/spinlock.md)
