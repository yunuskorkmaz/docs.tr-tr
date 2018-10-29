---
title: Eşitleme temellerine genel bakış
description: .NET iş parçacığı eşitleme temellerine bir paylaşılan kaynağa veya denetimi iş parçacığı etkileşim erişimi eşitlemek için kullanılan hakkında bilgi edinin
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4d1010069e9d95488a99133f949ca112dc08f0e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201604"
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme temellerine genel bakış

.NET, bir dizi paylaşılan bir kaynağa erişimi eşitleme veya iş parçacığı etkileşim koordine etmek için kullanabileceğiniz türleri sağlar.

> [!IMPORTANT]
> Her paylaşılan bir kaynağa erişimi korumak için aynı eşitleme temel örneği kullanın. Birden çok iş parçacığı bir kaynağa erişimi korumak için farklı eşitleme ilkel örnekleri kullanın ya da bazı kod parçalarını doğrudan bir kaynağa erişmek bir kaynak aynı anda erişebilir.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle sınıfı ve hafif eşitleme türleri

Birden çok .NET eşitleme temellerine türetilmesi <xref:System.Threading.WaitHandle?displayProperty=nameWithType> sınıfı bir yerel işletim sistemi eşitleme tanıtıcısı kapsüller ve iş parçacığı etkileşim için bir sinyal mekanizması kullanır. Bu sınıfları şunlardır:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, paylaşılan bir kaynağa özel erişim verir. Bir mutex durumu, iş parçacığının sahip olduğu, sinyal.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, sınırlar paylaşılan bir kaynağa erişmek için iş parçacığı sayısını veya bir kaynak havuzu eşzamanlı olarak. Kendi sayısı sıfırdan büyük ve nonsignaled ne zaman olduğunda semafor durumu için sinyal ayarlanır sayımına sıfırdır.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, bir iş parçacığı eşitleme olayı temsil eder ve bir sinyal veya unsignaled durumda olabilir.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, öğesinden türetildiğini <xref:System.Threading.EventWaitHandle> ve sinyal, otomatik olarak bir unsignaled durumuna tek bir bekleyen iş parçacığı bırakılıyor sonra sıfırlanır.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, öğesinden türetildiğini <xref:System.Threading.EventWaitHandle> ve sinyal zaman içinde bir sinyal verilmiş duruma dönmesine kadar kalır <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır.

.NET Framework'teki çünkü <xref:System.Threading.WaitHandle> türetildiği <xref:System.MarshalByRefObject?displayProperty=nameWithType>, uygulama etki alanı sınırları arasında iş parçacıklarının etkinlikleri eşitlemek için bu türleri kullanılabilir.

.NET Framework ve .NET Core, bu tür bazı boyunca işletim sistemi tarafından görülebilir ve işlemler arası eşitleme için kullanılabilir adlandırılmış sistem eşitleme tanıtıcılarını temsil edebilir:

- <xref:System.Threading.Mutex> (.NET framework ve .NET Core)
- <xref:System.Threading.Semaphore> (.NET framework ve Windows üzerinde .NET Core)
- <xref:System.Threading.EventWaitHandle> (.NET framework ve Windows üzerinde .NET Core).

Daha fazla bilgi için <xref:System.Threading.WaitHandle> API Başvurusu.

Hafif eşitleme türleri üzerinde temel işletim sistemi işleyicilerini kullanan yok ve normalde daha iyi performans sağlar. Ancak, işlemler arası eşitleme için kullanılamaz. Bu tür bir uygulama içinde bir iş parçacığı eşitlemesi için kullanın.

Bu tür bazı alternatifler türetilmiş türlere, <xref:System.Threading.WaitHandle>. Örneğin, <xref:System.Threading.SemaphoreSlim> basit bir alternatifidir <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Paylaşılan bir kaynağa erişim eşitleme

Eşitleme temellerine birden çok iş parçacığı tarafından paylaşılan bir kaynağa erişimi denetlemek için bir dizi .NET sağlar.

### <a name="monitor-class"></a>İzleme sınıfı

<xref:System.Threading.Monitor?displayProperty=nameWithType> Sınıfı alınırken veya kaynağı tanımlayan bir nesne üzerinde bir kilidin serbest tarafından paylaşılan bir kaynağa karşılıklı olarak birbirini erişim verir. Kilidi açık tutulduğu sürece kilidi tutan iş parçacığı yeniden almak ve kilidi serbest bırakır. Kilit alınırken alanından başka bir iş parçacığı engellenir ve <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> yöntemi kilidi serbest bırakılıncaya kadar bekler. <xref:System.Threading.Monitor.Enter%2A> Yöntemi yayımlanmış bir kilidi alır. Ayrıca <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> bir kilidi almak bir iş parçacığı sırasında çalışır süreyi belirtmek için yöntemi. Çünkü <xref:System.Threading.Monitor> sınıfında iş parçacığı benzeşimini, çağırarak bir kilit alınmadığı iş parçacığı kilidi serbest bırakmalısınız <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> yöntemi.

Kullanarak kilit aynı nesne üzerinde iş parçacıkları etkileşimi koordine edebilir <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> yöntemleri.

Daha fazla bilgi için <xref:System.Threading.Monitor> API Başvurusu.

> [!NOTE]
> Kullanım [kilit](../../csharp/language-reference/keywords/lock-statement.md) C# deyimi ve [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimini kullanmak yerine paylaşılan bir kaynağa erişimi eşitlemek için Visual Basic'te <xref:System.Threading.Monitor> doğrudan sınıf. Bu ifadeleri kullanarak uygulanan <xref:System.Threading.Monitor.Enter%2A> ve <xref:System.Threading.Monitor.Exit%2A> yöntemleri ve `try…finally` alınan kilidi her zaman kullanıma sunduğunu emin olmak için blok.

### <a name="mutex-class"></a>Mutex sınıfı

<xref:System.Threading.Mutex?displayProperty=nameWithType> Gibi sınıf <xref:System.Threading.Monitor>, paylaşılan bir kaynağa özel erişim verir. Birini [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) bir mutex sahipliğini istemek için yöntem aşırı yüklemeleri. Gibi <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> iş parçacığı benzeşimini vardır ve bir mutex alınan iş parçacığı çağrı yaparak bunu serbest bırakmalısınız <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> yöntemi.

Farklı <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> sınıfı işlemler arası eşitleme için kullanılabilir. Bunu yapmak için adlandırılmış bir mutex boyunca işletim sistemi görünen kullanın. Bir adlandırılmış mutex örneği oluşturmak için bir [Mutex Oluşturucusu](<xref:System.Threading.Mutex.%23ctor%2A>) bir ad belirtir. Ayrıca, çağırabilirsiniz <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> sistem mutex adlı varolan bir açmak için yöntemi.
  
Daha fazla bilgi için [mutex'ler](mutexes.md) makale ve <xref:System.Threading.Mutex> API Başvurusu.

### <a name="spinlock-structure"></a>SpinLock yapısı

<xref:System.Threading.SpinLock?displayProperty=nameWithType> Gibi yapı <xref:System.Threading.Monitor>, özel bir kilit kullanılabilirliğine göre paylaşılan bir kaynağa erişim verir. Zaman <xref:System.Threading.SpinLock> kullanılamıyor, kilit dener kilit kullanılabilir olana kadar sürekli olarak denetimi bir döngüde bekler.

Avantajları ve dezavantajları döndürme kilit kullanarak hakkında daha fazla bilgi için bkz: [SpinLock](spinlock.md) makale ve <xref:System.Threading.SpinLock> API Başvurusu.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim sınıfı

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> Sınıfı yazma için paylaşılan bir kaynağa özel erişim verir ve birden çok iş parçacığının kaynağa aynı anda okuma için erişim sağlar. Kullanmak istediğiniz <xref:System.Threading.ReaderWriterLockSlim> , okuma işlemleri iş parçacığı açısından güvenli destekler, ancak yazma işlemi gerçekleştirmek için özel erişim gerektiren bir paylaşılan veri yapısı erişimi eşitlemek için. Bir iş parçacığı özel erişim istediğinde (çağırarak gibi <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> yöntemi), tüm mevcut okuyucular kilit çıkılana ve yazıcı girdi ve çıktı kilit kadar sonraki okuyucu istekleri blok.
  
Daha fazla bilgi için [Okuyucu-Yazıcı kilitleri](reader-writer-locks.md) makale ve <xref:System.Threading.ReaderWriterLockSlim> API Başvurusu.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor ve SemaphoreSlim sınıfları

<xref:System.Threading.Semaphore?displayProperty=nameWithType> Ve <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> sınıfları paylaşılan bir kaynağa erişmek için iş parçacığı sayısını veya bir kaynak havuzu eşzamanlı olarak sınırlayın. Kaynak istek ek iş parçacıkları, herhangi bir iş parçacığı semafor serbest kadar bekleyin. Semafor iş parçacığı benzeşimini olmadığı için bir iş parçacığı semafor elde edebilir ve başka bir serbest bırakabilirsiniz.

<xref:System.Threading.SemaphoreSlim> Basit bir alternatifidir <xref:System.Threading.Semaphore> ve yalnızca tek bir işlem sınırları içinde eşitleme için kullanılabilir.

Windows üzerinde kullanabileceğiniz <xref:System.Threading.Semaphore> işlemler arası eşitleme. Bunu yapmak için oluşturun bir <xref:System.Threading.Semaphore> birini kullanarak bir adlandırılmış sistem semaforu temsil eden örneği [semafor oluşturucular](<xref:System.Threading.Semaphore.%23ctor%2A>) bir ad belirtir veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemi. <xref:System.Threading.SemaphoreSlim> Adlandırılmış sistem semaforları desteklemiyor.

Daha fazla bilgi için [semafor ve SemaphoreSlim](semaphore-and-semaphoreslim.md) makale ve <xref:System.Threading.Semaphore> veya <xref:System.Threading.SemaphoreSlim> API Başvurusu.

## <a name="thread-interaction-or-signaling"></a>İş parçacığı etkileşimi veya sinyali

İş parçacığı etkileşimi (veya iş parçacığı sinyal) bir iş parçacığı bildirim ya da bir sinyalden devam edebilmek için bir veya daha fazla iş parçacığı için beklemesi anlamına gelir. Örneğin, bir iş parçacığı çağırırsa <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemi B, iş parçacığı bir iş parçacığının iş parçacığı B tamamlanıncaya kadar engellenir. Önceki bölümde açıklanan eşitleme temellerine sinyal farklı bir mekanizma sağlar: bir kilidi serbest bırakarak bir iş parçacığı kilit alınırken tarafından geçebilirsiniz başka bir iş parçacığı bildirir.

Bu bölüm .NET tarafından sağlanan ek sinyal yapıları açıklar.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, AutoResetEvent ManualResetEvent ve ManualResetEventSlim sınıfları

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Sınıfı, bir iş parçacığı eşitleme olayı temsil eder.

Eşitleme olayı unsignaled veya sinyal durumda olabilir. Bir iş parçacığı bir olayın durumu unsignaled olduğunda, olayın çağrılarının <xref:System.Threading.WaitHandle.WaitOne%2A?> aşırı yükleme, bir olayın sinyal kadar engellenir. <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> Yöntemi için bir olay durumu sinyal ayarlar.

Davranışını bir <xref:System.Threading.EventWaitHandle> , sinyal kendi sıfırlama moduna bağlıdır:

- Bir <xref:System.Threading.EventWaitHandle> ile oluşturulan <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> tek bir bekleyen iş parçacığı bırakılıyor sonra bayrağı otomatik olarak sıfırlar. Yalnızca bir iş parçacığı aracılığıyla işareti verilen her zaman izin veren bir Turnike gibidir. <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> Türetilen sınıf <xref:System.Threading.EventWaitHandle>, bu davranışı temsil eder.
- Bir <xref:System.Threading.EventWaitHandle> ile oluşturulan <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> bayrağı kalır kadar sinyal kendi <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır. Bu, birisinin kapatana kadar ardından açık kalır ve sinyal kadar kapalı bir ağ geçidi gibi olur. <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Türetilen sınıf <xref:System.Threading.EventWaitHandle>, bu davranışı temsil eder. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> Sınıfı, basit bir alternatif <xref:System.Threading.ManualResetEvent>.

Windows üzerinde kullanabileceğiniz <xref:System.Threading.EventWaitHandle> işlemler arası eşitleme. Bunu yapmak için oluşturun bir <xref:System.Threading.EventWaitHandle> birini kullanarak bir adlandırılmış sistem eşitleme olayı temsil eden örneği [EventWaitHandle oluşturucular](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) bir ad belirtir veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> yöntemi.

Daha fazla bilgi için [EventWaitHandle](eventwaithandle.md), [AutoResetEvent](autoresetevent.md), ve [ManualResetEvent ve ManualResetEventSlim](manualresetevent-and-manualreseteventslim.md) makaleler. API Başvurusu için bkz: <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.ManualResetEvent>, ve <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>CountdownEvent sınıfı

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Sınıf kendi sayısı sıfır olduğunda, ayarladığınız olur bir olayı temsil eder. Sırada <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> çağıran iş parçacığı sıfırdan büyük <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> engellenir. Çağrı <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> olay sayısını azaltmak için.

Tersine <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim>, bir iş parçacığından bir sinyal ile birden çok iş parçacığı engelini kaldırmak için kullanabileceğiniz, kullanabileceğiniz <xref:System.Threading.CountdownEvent> birden çok iş parçacığından sinyallerle bir veya daha fazla iş parçacıklarının engellemesini kaldırmak için.

Daha fazla bilgi için [CountdownEvent](countdownevent.md) makale ve <xref:System.Threading.CountdownEvent> API Başvurusu.

### <a name="barrier-class"></a>Engel sınıfı

<xref:System.Threading.Barrier?displayProperty=nameWithType> Sınıfı, bir iş parçacığı yürütme engeli temsil eder. Çağıran iş parçacığı <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> yöntemi katılımcı başka iş parçacıklarının engeli ulaşana kadar bu bekler ve süreçlerinin önündeki engelleri ulaştığını bildirir. Katılımcı tüm iş parçacıklarının engeli ulaştığında, devam etmek ve süreçlerinin önündeki engelleri sıfırlanır ve yeniden kullanılabilir.

Kullanabileceğinize <xref:System.Threading.Barrier> ne zaman bir veya daha fazla iş parçacığı sonraki hesaplama aşamaya devam etmeden önce diğer iş parçacıklarını sonuçlarını gerektirir.

Daha fazla bilgi için [engel](barrier.md) makale ve <xref:System.Threading.Barrier> API Başvurusu.

## <a name="interlocked-class"></a>Interlocked sınıfı

<xref:System.Threading.Interlocked?displayProperty=nameWithType> Sınıfı bir değişken üzerinde basit atomik işlemleri gerçekleştiren statik yöntemler sağlar. Atomik işlemleri ek olarak, artırma ve azaltma, exchange ve bir karşılaştırmayı bağlıdır koşullu exchange eklemek ve okuma işlemi 64-bit tamsayı değeri.

Daha fazla bilgi için [birbirine geçmiş operations](interlocked-operations.md) makale ve <xref:System.Threading.Interlocked> API Başvurusu.

## <a name="spinwait-structure"></a>SpinWait yapısı

<xref:System.Threading.SpinWait?displayProperty=nameWithType> Yapısı döndürme tabanlı bekleme için destek sağlar. Sinyal bir olay ya da karşılanması gereken bir koşul için beklenecek bir iş parçacığı sahip olduğunda, ancak gerçek bir bekleme süresi bir bekleme tanıtıcısı kullanarak veya aksi halde iş parçacığının engellenmesi gereken bekleme süresi değerinden küçük olması bekleniyorsa kullanmak isteyebilirsiniz. Kullanarak <xref:System.Threading.SpinWait>, bekleme sırasında çalıştırın ve koşul belirtilen süre içinde yalnızca aşıldığı değil durumunda (örneğin, bekleyen veya uyku) verim için kısa bir süre belirtebilirsiniz.

Daha fazla bilgi için [SpinWait](spinwait.md) makale ve <xref:System.Threading.SpinWait> API Başvurusu.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı koleksiyonları](../collections/thread-safe/index.md)
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
