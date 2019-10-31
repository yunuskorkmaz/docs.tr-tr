---
title: Eşitleme temellerine genel bakış
description: Paylaşılan bir kaynağa veya denetim iş parçacığı etkileşimine erişimi eşitlemek için kullanılan .NET iş parçacığı eşitleme temelleri hakkında bilgi edinin
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 43f78c914b7cb01f9b0de4c258d5882548e52790
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106589"
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme temellerine genel bakış

.NET, paylaşılan bir kaynağa erişimi veya koordinat iş parçacığı etkileşimini eşleştirmek için kullanabileceğiniz bir dizi tür sağlar.

> [!IMPORTANT]
> Paylaşılan bir kaynağın erişimini korumak için aynı eşitleme temel örneğini kullanın. Aynı kaynağı korumak için farklı eşitleme temel örnekleri kullanıyorsanız, bir eşitleme temel tarafından sağlanmış olan korumayı atlacaksınız.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle sınıfı ve hafif eşitleme türleri

Çoklu .NET eşitleme temelleri, yerel bir işletim sistemi eşitleme tanıtıcısını kapsülleyen ve iş parçacığı etkileşimi için bir sinyal mekanizması kullanan <xref:System.Threading.WaitHandle?displayProperty=nameWithType> sınıfından türetilir. Bu sınıflar şunları içerir:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, paylaşılan bir kaynağa özel erişim izni verir. Bir mutex 'in durumu, kendisine ait bir iş parçacığı yoksa sinyal edilir.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlar. Bir semaforun durumu, sayısı sıfırdan büyük olduğunda ve sayısı sıfır olduğunda, sinyalsiz olarak ayarlanır.
- bir iş parçacığı eşitleme olayını temsil eden ve sinyal veya sinyal verilmemiş durumunda olabilecek <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.
- <xref:System.Threading.EventWaitHandle> ondan türetilen <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>ve sinyal edildiğinde, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra otomatik olarak sinyali verilmemiş bir duruma sıfırlanır.
- <xref:System.Threading.EventWaitHandle> ondan türetilen <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>ve sinyal edildiğinde, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır.

.NET Framework, <xref:System.Threading.WaitHandle> <xref:System.MarshalByRefObject?displayProperty=nameWithType>türetildiğinden, bu türler uygulama etki alanı sınırları genelinde iş parçacığı etkinliklerinin eşitlenmesi için kullanılabilir.

.NET Framework ve .NET Core 'da, bu türlerden bazıları işletim sisteminin tamamında görülebilen adlandırılmış sistem eşitleme tutamaçlarını temsil edebilir ve işlemler arası eşitleme için kullanılabilir:

- <xref:System.Threading.Mutex> (.NET Framework ve .NET Core),
- <xref:System.Threading.Semaphore> (Windows üzerinde .NET Framework ve .NET Core),
- <xref:System.Threading.EventWaitHandle> (.NET Framework ve Windows üzerinde .NET Core).

Daha fazla bilgi için <xref:System.Threading.WaitHandle> API başvurusuna bakın.

Hafif eşitleme türleri, temel işletim sistemi tanıtıcılarını içermez ve genellikle daha iyi performans sağlar. Ancak, işlemler arası eşitleme için kullanılamaz. Bir uygulama içinde iş parçacığı eşitlemesi için bu türleri kullanın.

Bu türlerden bazıları <xref:System.Threading.WaitHandle>türetilen türlerin alternatifleri vardır. Örneğin, <xref:System.Threading.Semaphore><xref:System.Threading.SemaphoreSlim> hafif bir alternatiftir.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Paylaşılan kaynağa erişimin eşitlenmesi

.NET birden çok iş parçacığı tarafından paylaşılan bir kaynağa erişimi denetlemek için bir dizi eşitleme temel kümesi sağlar.

### <a name="monitor-class"></a>İzleme sınıfı

<xref:System.Threading.Monitor?displayProperty=nameWithType> sınıfı, kaynağı tanımlayan nesne üzerinde bir kilit edinerek veya serbest bırakarak paylaşılan kaynağa birbirini dışlayan erişim verir. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Başka herhangi bir iş parçacığının kilidi almak engellenir ve <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> yöntemi kilit serbest bırakılana kadar bekler. <xref:System.Threading.Monitor.Enter%2A> yöntemi, serbest bırakıldı bir kilit alır. Ayrıca, bir iş parçacığının kilit alma girişiminde bulunduğu süreyi belirtmek için <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemini de kullanabilirsiniz. <xref:System.Threading.Monitor> sınıfında iş parçacığı benzeşimi olduğundan, bir kilit elde eden iş parçacığı, <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metodunu çağırarak kilidi serbest bırakmalıdır.

<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>ve <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> yöntemlerini kullanarak aynı nesne üzerinde bir kilit elde eden iş parçacıklarının etkileşimini koordine edebilirsiniz.

Daha fazla bilgi için <xref:System.Threading.Monitor> API başvurusuna bakın.

> [!NOTE]
> <xref:System.Threading.Monitor> sınıfını [](../../csharp/language-reference/keywords/lock-statement.md) doğrudan kullanmak yerine C# , paylaşılan bir kaynağa erişimi eşleştirmek için, içindeki Lock Ifadesini ve Visual Basic içindeki [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ifadesini kullanın. Bu deyimler, alınan kilidin her zaman serbest bırakılacağını sağlamak için <xref:System.Threading.Monitor.Enter%2A> ve <xref:System.Threading.Monitor.Exit%2A> yöntemleri ve bir `try…finally` bloğu kullanılarak uygulanır.

### <a name="mutex-class"></a>Mutex sınıfı

<xref:System.Threading.Monitor>gibi <xref:System.Threading.Mutex?displayProperty=nameWithType> sınıfı, paylaşılan bir kaynağa özel erişim verir. Mutex 'in sahipliğini istemek için [mutex. WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) yöntemi aşırı yüklerini kullanın. <xref:System.Threading.Monitor>gibi, <xref:System.Threading.Mutex> iş parçacığı benzeşimi vardır ve bir mutex elde eden iş parçacığının <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> yöntemini çağırarak onu serbest bırakmalıdır.

<xref:System.Threading.Monitor>aksine <xref:System.Threading.Mutex> sınıfı işlemler arası eşitleme için kullanılabilir. Bunu yapmak için, işletim sisteminin tamamında görünür olan adlandırılmış bir mutex kullanın. Adlandırılmış bir mutex örneği oluşturmak için, bir adı belirten bir [mutex Oluşturucusu](<xref:System.Threading.Mutex.%23ctor%2A>) kullanın. Ayrıca, var olan bir adlandırılmış sistem mutex 'i açmak için <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz.
  
Daha fazla bilgi için bkz. zaman [uyumu](mutexes.md) sağlayıcılar makalesi ve <xref:System.Threading.Mutex> API başvurusu.

### <a name="spinlock-structure"></a>SpinLock yapısı

<xref:System.Threading.Monitor>gibi <xref:System.Threading.SpinLock?displayProperty=nameWithType> yapısı, bir kilit kullanılabilirliğine göre paylaşılan bir kaynağa özel erişim verir. <xref:System.Threading.SpinLock>, kullanılamayan bir kilit edinmeye çalıştığında, kilit kullanılabilir hale gelene kadar bir döngüde bekler, tekrar tekrar kontrol edilir.

Döndürme kilidi kullanmanın avantajları ve dezavantajları hakkında daha fazla bilgi için, bkz. [SpinLock](spinlock.md) makalesi ve <xref:System.Threading.SpinLock> API başvurusu.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim Class

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> sınıfı, yazmak üzere paylaşılan bir kaynağa özel erişim verir ve birden çok iş parçacığının okumak için aynı anda kaynağa erişmesini sağlar. İş parçacığı güvenli okuma işlemlerini destekleyen bir paylaşılan veri yapısına erişimi eşleştirmek için <xref:System.Threading.ReaderWriterLockSlim> kullanmak isteyebilirsiniz, ancak yazma işlemini gerçekleştirmek için özel erişim gerekir. Bir iş parçacığı özel erişim istediğinde (örneğin, <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> yöntemini çağırarak), sonraki okuyucu ve yazıcı istekleri, var olan tüm okuyucular kilitlenene çıkana kadar engeller ve yazıcı, kilitliyken ve kilide çıkış yaptı.
  
Daha fazla bilgi için <xref:System.Threading.ReaderWriterLockSlim> API başvurusuna bakın.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor ve SemaphoreSlim sınıfları

<xref:System.Threading.Semaphore?displayProperty=nameWithType> ve <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> sınıfları, paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacıklarının sayısını sınırlar. Kaynak isteyen ek iş parçacıkları, herhangi bir iş parçacığı semaforu yayınlana kadar bekler. Semaforun iş parçacığı benzeşimi olmadığından, bir iş parçacığı semaforu alabilir ve başka bir tane onu serbest bırakabilir.

<xref:System.Threading.SemaphoreSlim>, <xref:System.Threading.Semaphore> basit bir alternatiftir ve yalnızca tek bir işlem sınırı içindeki eşitleme için kullanılabilir.

Windows 'da, işlemler arası eşitleme için <xref:System.Threading.Semaphore> kullanabilirsiniz. Bunu yapmak için, bir ad veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemini belirten [semafor oluşturucularından](<xref:System.Threading.Semaphore.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem semaforu temsil eden bir <xref:System.Threading.Semaphore> örneği oluşturun. <xref:System.Threading.SemaphoreSlim>, adlandırılmış sistem semaforları desteklemez.

Daha fazla bilgi için [semafor ve SemaphoreSlim](semaphore-and-semaphoreslim.md) makalesine ve <xref:System.Threading.Semaphore> veya <xref:System.Threading.SemaphoreSlim> API başvurusuna bakın.

## <a name="thread-interaction-or-signaling"></a>İş parçacığı etkileşimi veya sinyal

İş parçacığı etkileşimi (veya iş parçacığı sinyali), bir iş parçacığının devam edebilmek için bir veya daha fazla iş parçacığından bildirim veya sinyal beklemesi gerektiği anlamına gelir. Örneğin, iş parçacığı A iş parçacığı B <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemini çağırırsa, iş parçacığı B tamamlanana kadar iş parçacığı A engellenir. Önceki bölümde açıklanan eşitleme temelleri, sinyal için farklı bir mekanizma sağlar: bir kilit serbest bırakarak, bir iş parçacığının kilidi alarak devam edemeyeceğini başka bir iş parçacığına bildirir.

Bu bölümde .NET tarafından sunulan ek sinyal yapıları açıklanmaktadır.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, oto ResetEvent, ManualResetEvent ve Manualreseteventince sınıflar

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> sınıfı bir iş parçacığı eşitleme olayını temsil eder.

Eşitleme olayı, sinyal veya sinyal verilmemiş bir durumda olabilir. Bir olayın durumu işaret edildiğinde, bir olay sinyallene kadar olayın <xref:System.Threading.WaitHandle.WaitOne%2A?> aşırı yüklemesini çağıran bir iş parçacığı engellenir. <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> yöntemi bir olayın durumunu sinyale ayarlar.

Sinyal edilen <xref:System.Threading.EventWaitHandle> davranışı, sıfırlama moduna bağlıdır:

- <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> bayrağıyla oluşturulan <xref:System.Threading.EventWaitHandle>, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra otomatik olarak sıfırlanır. Her sinyalde yalnızca bir iş parçacığına izin veren bir turnike gibi. <xref:System.Threading.EventWaitHandle>türetilen <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> sınıfı, bu davranışı temsil eder.
- <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> bayrağıyla oluşturulan <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır. Bu, sinyal edilene kadar kapalı bir kapıdır ve bir kişi tarafından kapanana kadar açık kalır. <xref:System.Threading.EventWaitHandle>türetilen <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıfı, bu davranışı temsil eder. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> sınıfı, <xref:System.Threading.ManualResetEvent>için hafif bir alternatiftir.

Windows 'da, işlemler arası eşitleme için <xref:System.Threading.EventWaitHandle> kullanabilirsiniz. Bunu yapmak için, bir ad veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> yöntemi belirten [EventWaitHandle oluşturucularından](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem eşitleme olayını temsil eden bir <xref:System.Threading.EventWaitHandle> örneği oluşturun.

Daha fazla bilgi için, [EventWaitHandle](eventwaithandle.md) makalesine bakın. API başvurusu için bkz. <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.ManualResetEvent>ve <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>CountdownEvent sınıfı

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sınıfı, sayısı sıfır olduğunda ayarlanan bir olayı temsil eder. <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> sıfırdan büyükse, <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> çağıran bir iş parçacığı engellenir. Bir olayın sayısını azaltmak için <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> çağırın.

Bir iş parçacığındaki sinyalle birden çok iş parçacığının engellemesini kaldırmak için kullanabileceğiniz <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim>aksine, birden çok iş parçacığının sinyalleriyle bir veya daha fazla iş parçacığının engellemesini kaldırmak için <xref:System.Threading.CountdownEvent> kullanabilirsiniz.

Daha fazla bilgi için bkz. [CountdownEvent](countdownevent.md) makalesi ve <xref:System.Threading.CountdownEvent> API başvurusu.

### <a name="barrier-class"></a>Bariyer sınıfı

<xref:System.Threading.Barrier?displayProperty=nameWithType> sınıfı bir iş parçacığı yürütme engelini temsil eder. <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> yöntemi çağıran bir iş parçacığı, engellere ulaştığı ve diğer katılımcı iş parçacıklarının engelye ulaşmasını beklene kadar bekler. Tüm katılımcı iş parçacıkları engelye ulaştığında devam ederler ve engel sıfırlanır ve yeniden kullanılabilir.

Bir veya daha fazla iş parçacığının sonraki hesaplama aşamasına geçmeden önce diğer iş parçacıklarının sonuçlarını gerektirmesi durumunda <xref:System.Threading.Barrier> kullanabilirsiniz.

Daha fazla bilgi için, bkz. [bariyer](barrier.md) makalesi ve <xref:System.Threading.Barrier> API başvurusu.

## <a name="interlocked-class"></a>Interlocked sınıfı

<xref:System.Threading.Interlocked?displayProperty=nameWithType> sınıfı, bir değişkende basit Atomik işlemler gerçekleştiren statik yöntemler sağlar. Bu atomik işlemler, bir karşılaştırmaya ve 64 bitlik bir tamsayı değerinin okuma işlemine bağlı olan toplama, artırma ve azaltma, değişim ve koşullu değişim işlemlerini içerir.

Daha fazla bilgi için <xref:System.Threading.Interlocked> API başvurusuna bakın.

## <a name="spinwait-structure"></a>SpinWait yapısı

<xref:System.Threading.SpinWait?displayProperty=nameWithType> yapısı, döndürme tabanlı bekleme için destek sağlar. Bir iş parçacığının bir olayın sinyal vermesini veya bir koşulun karşılanmasını beklemek gerektiğinde, ancak gerçek bekleme süresinin bir bekleme tutamacı kullanılarak veya iş parçacığını engelleyerek gereken bekleme süresinden daha az olması beklendiğinde bunu kullanmak isteyebilirsiniz. <xref:System.Threading.SpinWait>kullanarak, beklenirken dönebilmeniz için kısa bir süre belirtebilir ve sonra (örneğin, bekleme veya uyuma) yalnızca koşulun belirtilen sürede karşılanmamış olması durumunda ödeme yapın.

Daha fazla bilgi için [SpinWait](spinwait.md) makalesine ve <xref:System.Threading.SpinWait> API başvurusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli Koleksiyonlar](../collections/thread-safe/index.md)
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
