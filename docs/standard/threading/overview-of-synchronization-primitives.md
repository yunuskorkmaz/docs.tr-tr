---
title: Eşitleme temellerine genel bakış
description: Paylaşılan bir kaynağa erişimi eşitlemek veya iş parçacığı etkileşimini kontrol etmek için kullanılan .NET iş parçacığı eşitleme ilkelleri hakkında bilgi edinin
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 43f78c914b7cb01f9b0de4c258d5882548e52790
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106589"
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme temellerine genel bakış

.NET, paylaşılan bir kaynağa erişimi eşitlemek veya iş parçacığı etkileşimini koordine etmek için kullanabileceğiniz bir dizi tür sağlar.

> [!IMPORTANT]
> Paylaşılan bir kaynağın erişimini korumak için aynı eşitleme ilkel örneğini kullanın. Aynı kaynağı korumak için farklı eşitleme ilkel örnekleri kullanırsanız, eşitleme ilkel tarafından sağlanan korumayı atlatacaksınız.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle sınıfı ve hafif eşitleme türleri

Çoklu .NET senkronizasyon ilkel <xref:System.Threading.WaitHandle?displayProperty=nameWithType> sınıf, bir yerel işletim sistemi senkronizasyon kolu kapsüller ve iş parçacığı etkileşimi için bir sinyal mekanizması kullanır türetilmiştir. Bu sınıflar şunlardır:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, paylaşılan bir kaynağa özel erişim sağlayan. Bir mutex durumu hiçbir iş parçacığı sahibi ise sinyal verilir.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, paylaşılan kaynağa veya aynı anda bir kaynak havuzuna erişebilen iş parçacığı sayısını sınırlar. Bir semaforun durumu, sayısı sıfırdan büyük olduğunda ve sayısı sıfır olduğunda sinyal verilmeyen sinyal olarak ayarlanır.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, iş parçacığı eşitleme olayını temsil eder ve sinyalverilen veya sinyalverilmemiş durumda olabilir.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, sinyal <xref:System.Threading.EventWaitHandle> verildiğinde, tek bir bekleme iş parçacığı serbest bıraktıktan sonra otomatik olarak sinyalsiz duruma sıfırlar.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, hangi türetilir <xref:System.Threading.EventWaitHandle> ve, sinyal verildiğinde, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntem çağrılana kadar sinyalli durumda kalır.

.NET Framework'de, <xref:System.Threading.WaitHandle> bu tür <xref:System.MarshalByRefObject?displayProperty=nameWithType>lerden türediği için, iş parçacıklarının etkinliklerini uygulama etki alanı sınırları arasında eşitlemek için kullanılabilir.

.NET Framework ve .NET Core'da, bu türlerden bazıları, işletim sistemi boyunca görülebilen ve süreçler arası senkronizasyon için kullanılabilen adlandırılmış sistem eşitleme tutamaçlarını temsil edebilir:

- <xref:System.Threading.Mutex>(.NET Çerçeve ve .NET Çekirdek),
- <xref:System.Threading.Semaphore>(.NET Framework ve .NET Core Windows üzerinde),
- <xref:System.Threading.EventWaitHandle>(.NET Framework ve .NET Core Windows'da).

Daha fazla bilgi <xref:System.Threading.WaitHandle> için API başvurusuna bakın.

Hafif eşitleme türleri altta yatan işletim sistemi tutamaçlarına güvenmez ve genellikle daha iyi performans sağlar. Ancak, bunlar inter-process eşitleme için kullanılamaz. Tek bir uygulama içinde iş parçacığı eşitleme için bu türleri kullanın.

Bu türlerden bazıları türetilen türlere <xref:System.Threading.WaitHandle>alternatiflerdir. Örneğin, <xref:System.Threading.SemaphoreSlim> <xref:System.Threading.Semaphore>hafif bir alternatiftir.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Paylaşılan kaynağa erişimin eşitlenmesi

.NET, paylaşılan bir kaynağa birden çok iş parçacığı tarafından erişimi denetlemek için bir dizi eşitleme ilkelsağlar.

### <a name="monitor-class"></a>İzleme sınıfı

Sınıf, <xref:System.Threading.Monitor?displayProperty=nameWithType> kaynağı tanımlayan nesneye kilit alarak veya serbest bırakarak paylaşılan kaynağa birbirini dışlayan erişimi verir. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Başka bir iş parçacığı kilidi edinme engellenir ve <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> yöntem kilit serbest bırakılınyana kadar bekler. Yöntem, <xref:System.Threading.Monitor.Enter%2A> serbest bırakılmış bir kilit edinir. İş parçacığının <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> kilit elde etmeye çalıştığı süreyi belirtmek için de yöntemi kullanabilirsiniz. <xref:System.Threading.Monitor> Sınıfın iş parçacığı afiyeti olduğundan, kilit alan iş parçacığı <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> yöntemi çağırarak kilidi serbest bırakmalıdır.

Aynı nesneye kilit alan iş parçacıklarının etkileşimini <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, , <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>ve <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> yöntemleri kullanarak koordine edebilirsiniz.

Daha fazla bilgi <xref:System.Threading.Monitor> için API başvurusuna bakın.

> [!NOTE]
> Sınıfı doğrudan kullanmak yerine paylaşılan bir kaynağa erişimi eşitlemek için C#'daki <xref:System.Threading.Monitor> [kilit](../../csharp/language-reference/keywords/lock-statement.md) deyimini ve Visual Basic'teki [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimini kullanın. Bu ifadeler, edinilen kilidin <xref:System.Threading.Monitor.Exit%2A> her `try…finally` zaman serbest bırakılmasını sağlamak için yöntem <xref:System.Threading.Monitor.Enter%2A> ve yöntemler ve blok kullanılarak uygulanır.

### <a name="mutex-class"></a>Mutex sınıfı

Sınıf, <xref:System.Threading.Mutex?displayProperty=nameWithType> örneğin, <xref:System.Threading.Monitor>paylaşılan bir kaynağa özel erişim verir. [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) yönteminden birini kullanarak bir mutex'in sahipliğini talep edin. Gibi <xref:System.Threading.Monitor> <xref:System.Threading.Mutex> , iş parçacığı afiniteve bir mutex edinilen iş <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> parçacığı yöntemi çağırarak serbest bırakmak gerekir.

Aksine, <xref:System.Threading.Monitor> <xref:System.Threading.Mutex> sınıf inter-process senkronizasyon için kullanılabilir. Bunu yapmak için, işletim sistemi boyunca görülebilir adlı bir mutex kullanın. Adlandırılmış bir mutex örneği oluşturmak için, bir ad belirten bir [Mutex oluşturucu](<xref:System.Threading.Mutex.%23ctor%2A>) kullanın. Ayrıca, varolan <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> bir sistem mutex açmak için yöntemi arayabilirsiniz.
  
Daha fazla bilgi için [Mutexes](mutexes.md) <xref:System.Threading.Mutex> makalesine ve API başvurusuna bakın.

### <a name="spinlock-structure"></a>SpinLock yapısı

Yapı, <xref:System.Threading.SpinLock?displayProperty=nameWithType> örneğin, <xref:System.Threading.Monitor>bir kilidin kullanılabilirliğine bağlı olarak paylaşılan bir kaynağa özel erişim sağlar. Kullanılamayan bir kilit elde etmeye <xref:System.Threading.SpinLock> çalıştığında, kilit kullanılabilir olana kadar tekrar tekrar denetler, bir döngü içinde bekler.

Spin kilidi kullanmanın yararları ve dezavantajları hakkında daha fazla bilgi <xref:System.Threading.SpinLock> için [SpinLock](spinlock.md) makalesine ve API başvurusuna bakın.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim sınıf

Sınıf, <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> yazmak için paylaşılan bir kaynağa özel erişim sağlar ve birden çok iş parçacığının okumak için kaynağa aynı anda erişmesine izin verir. İş parçacığı için <xref:System.Threading.ReaderWriterLockSlim> güvenli okuma işlemlerini destekleyen, ancak yazma işlemini gerçekleştirmek için özel erişim gerektiren paylaşılan bir veri yapısına erişimi eşitlemek için kullanmak isteyebilirsiniz. Bir iş parçacığı özel erişim istediğinde (örneğin, <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> yöntemi arayarak), tüm varolan okuyucular kilitten çıkana ve yazar kilidi girip çıkana kadar sonraki okuyucu ve yazar isteklerini engeller.
  
Daha fazla bilgi <xref:System.Threading.ReaderWriterLockSlim> için API başvurusuna bakın.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor ve SemaforZayıflama dersleri

Ve <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> sınıflar, paylaşılan kaynağa veya aynı anda bir kaynak havuzuna erişebilen iş parçacığı sayısını sınırlar. Kaynak isteyen ek iş parçacıkları herhangi bir iş parçacığı semaphore serbest bırakana kadar bekleyin. Semaforda iplik yakınlığı olmadığından, bir iplik semaforu elde edebilir ve diğeri onu serbest bırakabilir.

<xref:System.Threading.SemaphoreSlim>hafif bir alternatiftir <xref:System.Threading.Semaphore> ve yalnızca tek bir işlem sınırı içinde senkronizasyon için kullanılabilir.

Windows'da, süreçler <xref:System.Threading.Semaphore> arası eşitleme için kullanabilirsiniz. Bunu yapmak için, <xref:System.Threading.Semaphore> bir ad veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntem belirten [Semaphore yapıcılar](<xref:System.Threading.Semaphore.%23ctor%2A>) birini kullanarak adlı bir sistem semafor temsil eden bir örnek oluşturun. <xref:System.Threading.SemaphoreSlim>adlı sistem semaforlarını desteklemez.

Daha fazla bilgi için [Semaphore ve SemaphoreSlim](semaphore-and-semaphoreslim.md) makalesine ve VEYA <xref:System.Threading.Semaphore> <xref:System.Threading.SemaphoreSlim> API başvurusuna bakın.

## <a name="thread-interaction-or-signaling"></a>İş parçacığı etkileşimi veya sinyal

İş parçacığı etkileşimi (veya iş parçacığı sinyali), bir iş parçacığının ilerlemek için bir veya daha fazla iş parçacığından bildirim veya sinyal beklemesi gerektiği anlamına gelir. Örneğin, iş parçacığı A <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığı B yöntemini çağırırsa, iş parçacığı A iş parçacığı B tamamlanana kadar engellenir. Önceki bölümde açıklanan eşitleme ilkel sinyal için farklı bir mekanizma sağlar: bir kilit bırakarak, bir iş parçacığı kilidi edinerek devam edebilirsiniz başka bir iş parçacığı bildirimde.

Bu bölümde .NET tarafından sağlanan ek sinyal yapıları açıklanmaktadır.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, AutoResetEvent, ManualResetEvent ve ManualResetEventSlim sınıfları

Sınıf <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> bir iş parçacığı eşitleme olay temsil eder.

Bir eşitleme olayı sinyal verilmemiş veya sinyalli durumda olabilir. Bir olayın durumu sinyal verildiğinde, olay sinyali verilene kadar <xref:System.Threading.WaitHandle.WaitOne%2A?> olayın aşırı yüklenmesini çağıran bir iş parçacığı engellenir. Yöntem, <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> bir olayın durumunu sinyale ayarlar.

Sinyal verilen <xref:System.Threading.EventWaitHandle> bir sinyalin davranışı sıfırlama moduna bağlıdır:

- <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> Tek bir <xref:System.Threading.EventWaitHandle> bekleme iş parçacığı serbest bıraktıktan sonra bayrak ile oluşturulan bir otomatik olarak sıfırlanır. Her sinyal geldiğinde sadece bir iplik sağlayan bir turnike gibi. Bu <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> davranışı temsil eden <xref:System.Threading.EventWaitHandle>sınıf, bu davranışı temsil eder.
- Bayrakla oluşturulan bir <xref:System.Threading.EventWaitHandle> yöntem çağrılana <xref:System.Threading.EventWaitHandle.Reset%2A> <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> kadar sinyal kalır. Sinyal verilene kadar kapalı olan ve biri kapanana kadar açık kalan bir kapı gibi. Bu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> davranışı temsil eden <xref:System.Threading.EventWaitHandle>sınıf, bu davranışı temsil eder. Sınıf <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> için hafif bir <xref:System.Threading.ManualResetEvent>alternatiftir.

Windows'da, süreçler <xref:System.Threading.EventWaitHandle> arası eşitleme için kullanabilirsiniz. Bunu yapmak için, <xref:System.Threading.EventWaitHandle> bir ad veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> yöntem belirten [EventWaitHandle oluşturucularından](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem eşitleme olayını temsil eden bir örnek oluşturun.

Daha fazla bilgi için [EventWaitHandle](eventwaithandle.md) makalesine bakın. API başvurusu için <xref:System.Threading.EventWaitHandle> <xref:System.Threading.AutoResetEvent>bkz. <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim>

### <a name="countdownevent-class"></a>CountdownOlay sınıfı

Sınıf, <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sayısı sıfır olduğunda ayarlanan bir olayı temsil eder. Sıfırdan büyük olsa <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> da, <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> çağıran bir iş parçacığı engellenir. Bir <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> olayın sayısını ertelemek için arayın.

Bir iş <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim>parçacığından gelen bir sinyalle birden çok iş parçacığının engelini kaldırmak için kullanabileceğiniz veya bunun aksine, birden çok iş parçacığından gelen sinyalleriçeren bir veya daha fazla iş parçacığının engelini kaldırmak için kullanabilirsiniz. <xref:System.Threading.CountdownEvent>

Daha fazla bilgi için [CountdownEvent](countdownevent.md) <xref:System.Threading.CountdownEvent> makalesine ve API başvurusuna bakın.

### <a name="barrier-class"></a>Bariyer sınıfı

Sınıf <xref:System.Threading.Barrier?displayProperty=nameWithType> bir iş parçacığı yürütme engelini temsil eder. <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> Yöntemi çağıran bir iş parçacığı, bariyere ulaştığını bildirir ve diğer katılımcı iş parçacıkları bariyere ulaşana kadar bekler. Tüm katılımcı iş parçacıkları bariyere ulaştığında, devam ederler ve bariyer sıfırlanır ve tekrar kullanılabilir.

Bir veya <xref:System.Threading.Barrier> daha fazla iş parçacığı bir sonraki hesaplama aşamasına geçmeden önce diğer iş parçacıklarının sonuçlarını gerektirdiğinde kullanabilirsiniz.

Daha fazla bilgi için [Bariyer](barrier.md) <xref:System.Threading.Barrier> makalesine ve API başvurusuna bakın.

## <a name="interlocked-class"></a>Interlocked sınıfı

Sınıf, <xref:System.Threading.Interlocked?displayProperty=nameWithType> bir değişken üzerinde basit atomik işlemler gerçekleştiren statik yöntemler sağlar. Bu atomik işlemler, bir karşılaştırmaya bağlı olan ekleme, artış ve değer değiştirme, değişim ve koşullu değişimi ve 64 bit'lik bir tamsayı değerinin çalışmasını içerir.

Daha fazla bilgi <xref:System.Threading.Interlocked> için API başvurusuna bakın.

## <a name="spinwait-structure"></a>SpinWait yapısı

Yapı, <xref:System.Threading.SpinWait?displayProperty=nameWithType> spin tabanlı bekleme desteği sağlar. Bir iş parçacığının bir olayın sinyal verilmesini veya bir koşulun karşılanmasını beklemesi gerektiğinde, ancak gerçek bekleme süresinin bekleme tutamacı nı kullanarak veya iş parçacığının engellenmesi için gereken bekleme süresinden daha az olması beklendiğinde kullanmak isteyebilirsiniz. Kullanarak, <xref:System.Threading.SpinWait>beklerken döndürmek için kısa bir süre belirtebilir ve yalnızca koşul belirtilen süre içinde karşılanmamışsa verim (örneğin, bekleyerek veya uyuyarak) verebilirsiniz.

Daha fazla bilgi için [SpinWait](spinwait.md) <xref:System.Threading.SpinWait> makalesine ve API başvurusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli koleksiyonları](../collections/thread-safe/index.md)
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
