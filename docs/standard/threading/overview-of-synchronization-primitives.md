---
title: "Eşitleme Temellerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 79d6e384458e289c4da8587eae66486a054aad08
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme Temellerine Genel Bakış
<a name="top"></a>.NET Framework eşitleme temelleri çeşitli iş parçacığı etkileşimlerinin denetleme ve yarış durumları önleme sağlar. Bunlar kabaca üç kategoriye ayrılabilir: kilitleme, sinyal ve ınterlocked işlemleri.  
  
 Kategoriler derleyin veya açıkça tanımlanmış değildir: birden çok kategori; özelliklerini bazı eşitleme mekanizmaları sahip bir kerede tek bir iş parçacığı yayın işlevsel olarak kilitler gibi olaylardır; Tüm kilidi sürümü, bir sinyal düşünülebilir; ve birbirine kenetlenmiş işlemler kilitleri oluşturmak için kullanılabilir. Ancak, kategoriler hala faydalıdır.  
  
 İş parçacığı eşitleme işbirlikçi olduğunu unutmamak önemlidir. Tek iş parçacığı eşitleme mekanizması atlar ve doğrudan korunan bir kaynağa erişir, bu eşitleme mekanizması etkin olamaz.  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [Kilitleme](#locking)  
  
-   [Sinyal](#signaling)  
  
-   [Basit eşitleme türleri](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Birbirine Kenetlenmiş İşlemler](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Kilitleme  
 Kilitleri kaynak denetimi aynı anda tek bir iş parçacığı ya da belirtilen bir iş parçacığı sayısını verin. Kilit olduğunda, özel bir kilit isteyen bir iş parçacığı kilit kullanılabilir oluncaya kadar blokları kullanın.  
  
### <a name="exclusive-locks"></a>Özel kilit  
 Kilitleme en basit biçimidir `lock` deyimi C# ve `SyncLock` kod bloğu için erişim denetimleri Visual Basic deyimi. Bu tür bir blok, sık önemli bir bölümü da adlandırılır. `lock` Deyimi kullanarak gerçekleştirilir <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> yöntemleri ve onu kullanan `try…catch…finally` blok kilidi serbest emin olun.  
  
 Genel olarak, kullanarak `lock` veya `SyncLock` kodu, hiçbir zaman yayılan birden fazla tek bir yöntem küçük bloklarını korumak için açıklamadır kullanmak için en iyi yolu <xref:System.Threading.Monitor> sınıfı. Güçlü rağmen <xref:System.Threading.Monitor> sınıftır artık kilitler ve kilitlenmeleri yatkın.  
  
#### <a name="monitor-class"></a>İzleme sınıfı  
 <xref:System.Threading.Monitor> Sınıfı ile birlikte kullanılan ek işlevsellik sağlar `lock` deyimi:  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> Yöntemi belirtilen bir zaman aralığından sonra vermek kaynağı için bekleyen engellenmiş iş parçacığı sağlar. Başarısını veya başarısızlığını algılamak ve olası kilitlenmeleri önlemek için kullanılan gösteren bir Boole değeri döndürür.  
  
-   <xref:System.Threading.Monitor.Wait%2A> Yöntemi, bir iş parçacığı önemli bir bölümü tarafından çağrılır. Kaynak yeniden kullanılabilir hale gelene kadar blokları ve kaynak denetim olanağı verir.  
  
-   <xref:System.Threading.Monitor.Pulse%2A> Ve <xref:System.Threading.Monitor.PulseAll%2A> yöntemlere izin hakkında kilidi veya çağırmak için bir iş parçacığı <xref:System.Threading.Monitor.Wait%2A> kilidi elde edebilirsiniz hazır sıraya bir veya daha fazla iş parçacığı yerleştirmek için.  
  
 Zaman aşımlarını <xref:System.Threading.Monitor.Wait%2A> yöntemi aşırı hazır kuyruğuna kaçınmak, bekleyen iş parçacıkları izin verin.  
  
 <xref:System.Threading.Monitor> Sınıfı, kilitleme için kullanılan nesne türetilen durumunda birden çok uygulama etki alanlarında kilitleme sağlayabilir <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor>iş parçacığı benzeşimini sahiptir. Diğer bir deyişle, İzleyici girilen bir iş parçacığı çağırarak çıkmalı <xref:System.Threading.Monitor.Exit%2A> veya <xref:System.Threading.Monitor.Wait%2A>.  
  
 <xref:System.Threading.Monitor> Sınıf instantiable değil. Yöntemlerinin statik (`Shared` Visual Basic'te) ve hareket instantiable kilit nesne.  
  
 Kavramsal genel bakış için bkz: [izleyicileri](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Mutex Sınıfı  
 İş parçacığı isteği bir <xref:System.Threading.Mutex> bir aşırı yüklemesini çağırarak kendi <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Aşırı zaman aşımları ile bekleme vermek iş parçacığı olanak sağlanır. Farklı <xref:System.Threading.Monitor> sınıfı, bir mutex yerel veya genel olabilir. Genel zaman uyumu sağlayıcılar adlandırılmış zaman uyumu sağlayıcılar, olarak da adlandırılan, işletim sistemi görünür durumda ve birden çok uygulama etki alanları veya işlemler iş parçacıklarında eşitlemek için kullanılır. Yerel zaman uyumu sağlayıcılar türetilen <xref:System.MarshalByRefObject>ve uygulama etki alanı sınırlarında kullanılabilir.  
  
 Ayrıca, <xref:System.Threading.Mutex> türetilen <xref:System.Threading.WaitHandle>, yani bu tarafından sağlanan sinyal mekanizmaları ile kullanılabilir <xref:System.Threading.WaitHandle>, gibi <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, ve <xref:System.Threading.WaitHandle.SignalAndWait%2A> yöntemleri.  
  
 Gibi <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> iş parçacığı benzeşimini sahiptir. Farklı <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> instantiable bir nesnedir.  
  
 Kavramsal genel bakış için bkz: [zaman uyumu sağlayıcılar](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>SpinLock sınıfı  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.SpinLock> sınıfı tarafından yükü gerekli olduğunda <xref:System.Threading.Monitor> performansı düşürür. Zaman <xref:System.Threading.SpinLock> kilitli kritik bir bölüme karşılaştığında kilit kullanılabilir oluncaya kadar bu yalnızca bir döngüde döner. Kilit çok kısa bir süre tutulursa dönen engelleme daha iyi performans sağlayabilirsiniz. Ancak, kilit döngüleri, birden fazla birkaç onlarca tutulursa <xref:System.Threading.SpinLock> da gerçekleştirir olarak <xref:System.Threading.Monitor>, ancak daha fazla CPU döngüsü kullanır ve bu nedenle diğer iş parçacıkları veya işlemler performansını düşürebilir.  
  
### <a name="other-locks"></a>Diğer kilitleri  
 Kilitleri özel olması gerekmez. Genellikle, iş parçacıkları, sınırlı sayıda eşzamanlı bir kaynağa erişmesine izin vermek kullanışlıdır. Semafor ve Okuyucu-Yazıcı kilitleri, bu tür bir havuza alınmış kaynak erişimi denetlemek için tasarlanmıştır.  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock Sınıfı  
 <xref:System.Threading.ReaderWriterLockSlim> Sınıfı adresleri verileri, yazıcı değiştiren bir iş parçacığı gerekir sahip olduğu bir kaynağa özel erişim durumu. Yazıcı etkin değilken, herhangi bir sayıda okuyucular kaynağa erişebilir (örneğin, çağıran tarafından <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> yöntemi). Bir iş parçacığı özel erişim istediğinde (örneğin, çağıran tarafından <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> yöntemi), tüm mevcut okuyucular kilit çıkış ve yazıcı girilen ve kilidi çıkıldı kadar sonraki okuyucu istekleri bloğu.  
  
 <xref:System.Threading.ReaderWriterLockSlim>iş parçacığı benzeşimini sahiptir.  
  
 Kavramsal genel bakış için bkz: [Okuyucu-Yazıcı kilitleri](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Semafor Sınıfı  
 <xref:System.Threading.Semaphore> Sınıfı, bir kaynağa erişmek için iş parçacığı belirtilen sayıda olanak tanır. Bir iş parçacığı semafor yayımları kadar kaynak blok isteyen ek iş parçacığı.  
  
 Gibi <xref:System.Threading.Mutex> sınıfı, <xref:System.Threading.Semaphore> türetilen <xref:System.Threading.WaitHandle>. Ayrıca ister <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> yerel veya genel olabilir. Uygulama etki alanı sınırlarında kullanılabilir.  
  
 Farklı <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, ve <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> iş parçacığı benzeşimini yok. Bu, burada bir iş parçacığı semafor edinir ve başka yayımları senaryolarda kullanılabileceği anlamına gelir.  
  
 Kavramsal genel bakış için bkz: [semafor ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>tek bir işlem sınırında eşitleme için basit bir semafor olur.  
  
 [Başa dön](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Sinyal  
 Başka bir iş parçacığından sinyal çağırmak için beklenecek en basit yolu <xref:System.Threading.Thread.Join%2A> başka bir iş parçacığı tamamlanana kadar engeller yöntemi. <xref:System.Threading.Thread.Join%2A>Belirtilen bir zaman aralığı geçtikten sonra dışında bekleme bölüneceği engellenmiş iş parçacığı izin iki aşırı yüklemeye sahip.  
  
 Bekleme tanıtıcıları bekleyen ve yetenekleri sinyal çok daha zengin kümesi sağlar.  
  
### <a name="wait-handles"></a>Bekleme Tanıtıcıları  
 Bekleme tanıtıcıları türetilen <xref:System.Threading.WaitHandle> sırayla türeyen sınıf <xref:System.MarshalByRefObject>. Bu nedenle, bekleme tanıtıcıları iş parçacığı etkinliklerini uygulama etki alanı sınırlarında eşitlemek için kullanılabilir.  
  
 İş parçacığı bloğu bekleme üzerinde işler örneği yöntemini çağırarak <xref:System.Threading.WaitHandle.WaitOne%2A> veya statik yöntemler <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, veya <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Nasıl yayımlanan hangi yöntemi çağrıldı ve bekleme tanıtıcıları türüne bağlıdır.  
  
 Kavramsal genel bakış için bkz: [bekleyin işleme](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Olay bekleme tanıtıcıları  
 Olay bekleme tanıtıcıları içeren <xref:System.Threading.EventWaitHandle> sınıf ve türetilmiş sınıflarının, <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent>. İş parçacığı, bir olay bekleme tanıtıcısı yayımlandığında, olay bekleme tanıtıcısı çağırarak işaret zaman kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi kullanarak veya <xref:System.Threading.WaitHandle.SignalAndWait%2A> yöntemi.  
  
 Olay tanıtıcıları ya da kendilerini otomatik olarak yalnızca bir iş parçacığı aracılığıyla işareti veya el ile sıfırlama işaret ve birisi kapatana kadar açın kadar kapalı bir ağ geçidi gibi her zaman izin veren bir Turnike gibi Sıfırla bekleyin. Adları kapsıyor gibi <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> önceki ve sonraki, sırasıyla temsil eder. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>tek bir işlem sınırında eşitleme için basit bir olaydır.  
  
 Bir <xref:System.Threading.EventWaitHandle> iki tür olay gösterebilir ve yerel veya genel olabilir. Türetilen sınıflar <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> her zaman yerel olarak.  
  
 Olay bekleme tanıtıcıları iş parçacığı benzeşimini gerekmez. Tüm iş parçacığı bir olay bekleme tanıtıcısı işaret.  
  
 Kavramsal genel bakış için bkz: [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Mutex ve semafor sınıfları  
 Çünkü <xref:System.Threading.Mutex> ve <xref:System.Threading.Semaphore> sınıfları türetilen <xref:System.Threading.WaitHandle>, statik yöntemleriyle kullanılan <xref:System.Threading.WaitHandle>. Örneğin, bir iş parçacığı kullanabilir <xref:System.Threading.WaitHandle.WaitAll%2A> Aşağıdakilerden üçü true olana kadar beklenecek yöntemi: bir <xref:System.Threading.EventWaitHandle> işareti verilen bir <xref:System.Threading.Mutex> yayımlandığı ve <xref:System.Threading.Semaphore> yayımlanır. Benzer şekilde, bir iş parçacığı kullanabilir <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemi Bu koşullardan herhangi biri true olana kadar bekleyin.  
  
 İçin bir <xref:System.Threading.Mutex> veya <xref:System.Threading.Semaphore>, işaret yayımlanan anlamına gelir. Her iki türü ilk bağımsız değişken olarak kullanılıyorsa, <xref:System.Threading.WaitHandle.SignalAndWait%2A> yöntemi, serbest bırakılır. Durumunda bir <xref:System.Threading.Mutex>, iş parçacığı benzeşimini olan, çağıran iş parçacığı mutex kendisine değil, özel durum oluşur. Daha önce belirtildiği gibi semafor iş parçacığı benzeşimini sahip değilsiniz.  
  
#### <a name="barrier"></a>Engel  
 <xref:System.Threading.Barrier> Sınıfı, böylece bunlar aynı tüm bloğundaki noktası ve tamamlamak tüm diğer iş parçacığı için bekleyin birden çok iş parçacığı cyclically eşitlemenize olanak sağlar. Bir veya daha fazla iş parçacığı bir algoritma sonraki aşamasına devam etmeden önce başka bir iş parçacığı sonuçlarını gerektirdiğinde bir engel yararlıdır. Daha fazla bilgi için bkz: [engel](../../../docs/standard/threading/barrier.md).  
  
 [Başa dön](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Basit eşitleme türleri  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Win32 çekirdek pahalı bağımlılık önleme tarafından hızlı performans bekleme tanıtıcıları mümkün olduğunca gibi nesneleri sağlamak eşitleme temelleri kullanabilirsiniz. Genel olarak, bu tür bekleme süresini kısa olduğunda ve yalnızca özgün eşitleme türleri denedi ve yetersiz olduğu tespit ne zaman kullanmanız gerekir. Basit türler, işlem içi iletişimi gerektiren senaryolar içinde kullanılamaz.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>hafif bir sürümüdür <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>hafif bir sürümüdür <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>sayımına sıfır olduğunda işaret hale bir olayı temsil eder.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType>bir ana iş parçacığı tarafından denetim gerektirmeden birbirleriyle eşitlemek birden çok iş parçacığı sağlar. Tüm iş parçacıklarının belirli bir noktaya ulaştınız kadar bir engel her iş parçacığı devam etmesini engelliyor.  
  
 [Başa dön](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kullanabileceğiniz <xref:System.Threading.SpinWait?displayProperty=nameWithType> bildirilmesini bir olay ya da karşılanması gereken bir koşul için beklenecek bir iş parçacığı vardır, ancak gerçek bekleme süresi değerinden küçük bir bekleme tanıtıcısı kullanarak veya otherwi gerekli bekleme süresi olması beklenir yapısı Geçerli iş parçacığının engelleme kullan. Kullanarak <xref:System.Threading.SpinWait>, bekleme sırasında Döndür ve ardından yalnızca belirtilen sürede koşul değil, (örneğin, bekleyen veya uyku) elde etmek için kısa bir süre belirtebilirsiniz.  
  
 [Başa dön](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Birbirine Kenetlenmiş İşlemler  
 Birbirine kenetlenmiş işlemler olan bir bellek konumuna statik yöntemleri tarafından gerçekleştirilen basit atomik işlemleri <xref:System.Threading.Interlocked> sınıfı. Bu atomik işlemleri toplama dahil, Artır azaltma, exchange, bir karşılaştırma bağlı olarak koşullu exchange ve okuma işlemlerini 64-bit değerleri için 32-bit platformlarda.  
  
> [!NOTE]
>  Kararlılık garanti tek tek işlemleri sınırlıdır; bir birim olarak birden çok işlemi gerçekleştirilmesi gerekir, daha parçalı bir eşitleme mekanizması kullanılması gerekir.  
  
 Bu işlemlerin hiçbiri kilitleri ya da sinyalleri olsa da, kilitler ve sinyalleri oluşturmak için kullanılabilir. Windows işletim sisteminin yerel olduklarından, birbirine kenetlenmiş işlemler son derece hızlı.  
  
 Birbirine kenetlenmiş işlemler geçici bellek garanti ile güçlü engellemeyen eşzamanlılık sergilemesine uygulamaları yazmak için kullanılabilir. Bununla birlikte, çoğu amaç için basit kilitleri daha uygun bir seçenektir; bu nedenle Gelişmiş, alt düzey programlama, duyarlar.  
  
 Kavramsal genel bakış için bkz: [Interlocked Operations](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [İzleyicileri](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Karşılıklı dışlamalar](../../../docs/standard/threading/mutexes.md)  
 [Semaphore ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Bekleme tanıtıcıları](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [Birbirine Kenetlenmiş İşlemler](../../../docs/standard/threading/interlocked-operations.md)  
 [Okuyucu-Yazıcı Kilitleri](../../../docs/standard/threading/reader-writer-locks.md)  
 [Engel](../../../docs/standard/threading/barrier.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
