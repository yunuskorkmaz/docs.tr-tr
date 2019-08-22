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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d5df6521b7c420943a7d3d0efcf6e4bee2d3a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666284"
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme temellerine genel bakış

.NET, paylaşılan bir kaynağa erişimi veya koordinat iş parçacığı etkileşimini eşleştirmek için kullanabileceğiniz bir dizi tür sağlar.

> [!IMPORTANT]
> Paylaşılan bir kaynağın erişimini korumak için aynı eşitleme temel örneğini kullanın. Aynı kaynağı korumak için farklı eşitleme temel örnekleri kullanıyorsanız, bir eşitleme temel tarafından sağlanmış olan korumayı atlacaksınız.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle sınıfı ve hafif eşitleme türleri

Çoklu .net eşitleme temelleri, yerel bir <xref:System.Threading.WaitHandle?displayProperty=nameWithType> işletim sistemi eşitleme tanıtıcısını kapsülleyen ve iş parçacığı etkileşimi için bir sinyal mekanizması kullanan sınıfından türetilir. Bu sınıflar şunları içerir:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, paylaşılan bir kaynağa özel erişim izni veren. Bir mutex 'in durumu, kendisine ait bir iş parçacığı yoksa sinyal edilir.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlar. Bir semaforun durumu, sayısı sıfırdan büyük olduğunda ve sayısı sıfır olduğunda, sinyalsiz olarak ayarlanır.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, bir iş parçacığı eşitleme olayını temsil eden ve sinyal veya sinyal edilmemiş bir durumda olabilir.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>ve ' den <xref:System.Threading.EventWaitHandle> türetilen, sinyal edildiğinde, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra otomatik olarak sinyali verilmemiş bir duruma sıfırlar.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>ve ' den <xref:System.Threading.EventWaitHandle> türetilen, sinyal edildiğinde, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır.

.NET Framework, öğesinden <xref:System.MarshalByRefObject?displayProperty=nameWithType>türetildiğinden <xref:System.Threading.WaitHandle> , bu türler uygulama etki alanı sınırları genelinde iş parçacığı etkinliklerini eşitlemeye yönelik olarak kullanılabilir.

.NET Framework ve .NET Core 'da, bu türlerden bazıları işletim sisteminin tamamında görülebilen adlandırılmış sistem eşitleme tutamaçlarını temsil edebilir ve işlemler arası eşitleme için kullanılabilir:

- <xref:System.Threading.Mutex>(.NET Framework ve .NET Core),
- <xref:System.Threading.Semaphore>(Windows üzerinde .NET Framework ve .NET Core),
- <xref:System.Threading.EventWaitHandle>(.NET Framework ve Windows üzerinde .NET Core).

Daha fazla bilgi için bkz <xref:System.Threading.WaitHandle> . API başvurusu.

Hafif eşitleme türleri, temel işletim sistemi tanıtıcılarını içermez ve genellikle daha iyi performans sağlar. Ancak, işlemler arası eşitleme için kullanılamaz. Bir uygulama içinde iş parçacığı eşitlemesi için bu türleri kullanın.

Bu türlerden bazıları, öğesinden <xref:System.Threading.WaitHandle>türetilmiş türler için alternatiflerdir. Örneğin, <xref:System.Threading.SemaphoreSlim> için <xref:System.Threading.Semaphore>hafif bir alternatiftir.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Paylaşılan kaynağa erişimin eşitlenmesi

.NET birden çok iş parçacığı tarafından paylaşılan bir kaynağa erişimi denetlemek için bir dizi eşitleme temel kümesi sağlar.

### <a name="monitor-class"></a>İzleme sınıfı

<xref:System.Threading.Monitor?displayProperty=nameWithType> Sınıfı, kaynağı tanımlayan nesne üzerinde bir kilit edinerek veya serbest bırakarak paylaşılan kaynağa birbirini dışlayan erişim verir. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Diğer herhangi bir iş parçacığının kilidi almak engellenir ve <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> Yöntem kilit serbest bırakılana kadar bekler. Yöntemi <xref:System.Threading.Monitor.Enter%2A> , serbest bırakıldı bir kilit alır. Yöntemini ayrıca, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> bir iş parçacığının kilit alma girişiminde bulunduğu süreyi belirtmek için de kullanabilirsiniz. Sınıfta iş parçacığı benzeşimi bulunduğundan, bir kilit alan iş parçacığının <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> yöntemi çağırarak kilidi serbest bırakmalıdır. <xref:System.Threading.Monitor>

<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> ,<xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, Ve<xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> yöntemlerini kullanarak aynı nesne üzerinde bir kilit elde eden iş parçacıklarının etkileşimini koordine edebilirsiniz.

Daha fazla bilgi için bkz <xref:System.Threading.Monitor> . API başvurusu.

> [!NOTE]
> Doğrudan <xref:System.Threading.Monitor> sınıfını kullanmak yerine, C# paylaşılan bir kaynağa erişimi eşleştirmek için, içindeki [Lock](../../csharp/language-reference/keywords/lock-statement.md) ifadesini ve Visual Basic içindeki [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ifadesini kullanın. Bu deyimler, <xref:System.Threading.Monitor.Enter%2A> elde edilen kilidin her zaman serbest bırakılacağını sağlamak `try…finally` için ve <xref:System.Threading.Monitor.Exit%2A> yöntemleri ve bir bloğu kullanılarak uygulanır.

### <a name="mutex-class"></a>Mutex sınıfı

Gibi <xref:System.Threading.Mutex?displayProperty=nameWithType> sınıf<xref:System.Threading.Monitor>, paylaşılan bir kaynağa özel erişim izni verir. Mutex 'in sahipliğini istemek için [mutex. WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) yöntemi aşırı yüklerini kullanın. Benzer <xref:System.Threading.Monitor>şekilde <xref:System.Threading.Mutex> , iş parçacığı benzeşimine sahiptir ve bir mutex elde eden iş parçacığının <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> yöntemini çağırarak onu serbest bırakmalıdır.

<xref:System.Threading.Monitor> Aksine<xref:System.Threading.Mutex> , sınıfı işlemler arası eşitleme için kullanılabilir. Bunu yapmak için, işletim sisteminin tamamında görünür olan adlandırılmış bir mutex kullanın. Adlandırılmış bir mutex örneği oluşturmak için, bir adı belirten bir [mutex Oluşturucusu](<xref:System.Threading.Mutex.%23ctor%2A>) kullanın. Ayrıca, <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> var olan bir adlandırılmış sistem mutex 'i açmak için yöntemini çağırabilirsiniz.
  
Daha fazla bilgi için, [birbirini kapsamayan](mutexes.md) makaleye ve <xref:System.Threading.Mutex> API başvurusuna bakın.

### <a name="spinlock-structure"></a>SpinLock yapısı

<xref:System.Threading.SpinLock?displayProperty=nameWithType> Gibi<xref:System.Threading.Monitor>yapı, bir kilidin kullanılabilirliğine göre paylaşılan bir kaynağa özel erişim verir. Kullanılamayan bir kilit edinmeye çalıştığında,kilitkullanılabilirhalegelenekadarbirdöngüdebekler,tekrartekrarkontroledilir.<xref:System.Threading.SpinLock>

Döndürme kilidi kullanmanın avantajları ve dezavantajları hakkında daha fazla bilgi için, bkz. [SpinLock](spinlock.md) makalesi ve <xref:System.Threading.SpinLock> API başvurusu.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim Class

Sınıfı <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> , yazmak üzere paylaşılan bir kaynağa özel erişim verir ve birden çok iş parçacığının okumak için aynı anda kaynağa erişmesini sağlar. <xref:System.Threading.ReaderWriterLockSlim> Erişimi, iş parçacığı güvenli okuma işlemlerini destekleyen bir paylaşılan veri yapısına eşitlemeniz, ancak yazma işlemini gerçekleştirmek için özel erişim gerektirir. Bir iş parçacığı özel erişim istediğinde (örneğin, <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> yöntemini çağırarak), sonraki okuyucu ve yazıcı istekleri, var olan tüm okuyucular kilitlenene kadar engeller ve yazıcı, kilitliyken ve kilide çıkış yaptı.
  
Daha fazla bilgi için bkz <xref:System.Threading.ReaderWriterLockSlim> . API başvurusu.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor ve SemaphoreSlim sınıfları

<xref:System.Threading.Semaphore?displayProperty=nameWithType> Ve<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> sınıfları, paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacıklarının sayısını sınırlar. Kaynak isteyen ek iş parçacıkları, herhangi bir iş parçacığı semaforu yayınlana kadar bekler. Semaforun iş parçacığı benzeşimi olmadığından, bir iş parçacığı semaforu alabilir ve başka bir tane onu serbest bırakabilir.

<xref:System.Threading.SemaphoreSlim>, için <xref:System.Threading.Semaphore> hafif bir alternatiftir ve yalnızca tek bir işlem sınırı içindeki eşitleme için kullanılabilir.

Windows 'ta, işlemler arası eşitleme <xref:System.Threading.Semaphore> için kullanabilirsiniz. Bunu yapmak için, <xref:System.Threading.Semaphore> <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> bir ad veya yöntem belirten [semafor oluşturucularından](<xref:System.Threading.Semaphore.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem semaforu temsil eden bir örnek oluşturun. <xref:System.Threading.SemaphoreSlim>adlandırılmış sistem semaforları desteklemez.

Daha fazla bilgi için [semafor ve SemaphoreSlim](semaphore-and-semaphoreslim.md) makalesine ve <xref:System.Threading.Semaphore> veya <xref:System.Threading.SemaphoreSlim> API başvurusuna bakın.

## <a name="thread-interaction-or-signaling"></a>İş parçacığı etkileşimi veya sinyal

İş parçacığı etkileşimi (veya iş parçacığı sinyali), bir iş parçacığının devam edebilmek için bir veya daha fazla iş parçacığından bildirim veya sinyal beklemesi gerektiği anlamına gelir. Örneğin, Thread a iş parçacığı b iş <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> parçacığı yöntemini çağırırsa, b iş parçacığı tamamlanana kadar bir iş parçacığı engellenir. Önceki bölümde açıklanan eşitleme temelleri, sinyal için farklı bir mekanizma sağlar: bir kilit serbest bırakarak, bir iş parçacığının kilidi alarak devam edemeyeceğini başka bir iş parçacığına bildirir.

Bu bölümde .NET tarafından sunulan ek sinyal yapıları açıklanmaktadır.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, oto ResetEvent, ManualResetEvent ve Manualreseteventince sınıflar

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Sınıfı bir iş parçacığı eşitleme olayını temsil eder.

Eşitleme olayı, sinyal veya sinyal verilmemiş bir durumda olabilir. Bir olayın durumu işaret edildiğinde, bir olay sinyallene kadar olayın <xref:System.Threading.WaitHandle.WaitOne%2A?> aşırı yüklemesini çağıran bir iş parçacığı engellenir. Yöntemi <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> , bir olayın durumunu sinyal olarak ayarlar.

Sinyal davranışı <xref:System.Threading.EventWaitHandle> , sıfırlama moduna bağlıdır:

- Bayrağıyla <xref:System.Threading.EventWaitHandle> oluşturulmuş bir, <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra otomatik olarak sıfırlanır. Her sinyalde yalnızca bir iş parçacığına izin veren bir turnike gibi. <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> Öğesinden<xref:System.Threading.EventWaitHandle>türetilen sınıf, bu davranışı temsil eder.
- Bayrağıyla oluşturulmuş bir <xref:System.Threading.EventWaitHandle> , <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> yöntemiçağrılanakadar<xref:System.Threading.EventWaitHandle.Reset%2A> sinyal olarak kalır. Bu, sinyal edilene kadar kapalı bir kapıdır ve bir kişi tarafından kapanana kadar açık kalır. <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Öğesinden<xref:System.Threading.EventWaitHandle>türetilen sınıf, bu davranışı temsil eder. Sınıfı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , için <xref:System.Threading.ManualResetEvent>hafif bir alternatiftir.

Windows 'ta, işlemler arası eşitleme <xref:System.Threading.EventWaitHandle> için kullanabilirsiniz. Bunu yapmak için, <xref:System.Threading.EventWaitHandle> <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> bir ad veya yöntem belirten [EventWaitHandle oluşturucularından](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem eşitleme olayını temsil eden bir örnek oluşturun.

Daha fazla bilgi için, [EventWaitHandle](eventwaithandle.md) makalesine bakın. <xref:System.Threading.EventWaitHandle>API başvurusu için bkz <xref:System.Threading.AutoResetEvent> <xref:System.Threading.ManualResetEvent>.,, ve <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>CountdownEvent sınıfı

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Sınıfı, sayısı sıfır olduğunda ayarlanan bir olayı temsil eder. Sıfırdan büyükse, çağıran <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> bir iş parçacığı engellenir. <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> Bir <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> olayın sayısını azaltmak için çağrısı yapın.

<xref:System.Threading.ManualResetEvent> Veya <xref:System.Threading.CountdownEvent> ' ın aksine, bir iş parçacığından gelen bir sinyal ile birden çok iş parçacığının engellemesini kaldırmak için kullanabileceğiniz, birden çok iş parçacığının sinyalleriyle bir veya daha fazla iş parçacığının engellemesini kaldırmak için kullanabilirsiniz. <xref:System.Threading.ManualResetEventSlim>

Daha fazla bilgi için bkz. [CountdownEvent](countdownevent.md) makalesi ve <xref:System.Threading.CountdownEvent> API başvurusu.

### <a name="barrier-class"></a>Bariyer sınıfı

<xref:System.Threading.Barrier?displayProperty=nameWithType> Sınıfı bir iş parçacığı yürütme engelini temsil eder. <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> Yöntemi çağıran bir iş parçacığı, engeli ne ulaştığına işaret eder ve diğer katılımcı iş parçacıkları engelye ulaşana kadar bekler. Tüm katılımcı iş parçacıkları engelye ulaştığında devam ederler ve engel sıfırlanır ve yeniden kullanılabilir.

Bir veya daha <xref:System.Threading.Barrier> fazla iş parçacığı, sonraki hesaplama aşamasına geçmeden önce diğer iş parçacıklarının sonuçlarını gerektirdiğinde kullanabilirsiniz.

Daha fazla bilgi için, bkz. [bariyer](barrier.md) makalesi <xref:System.Threading.Barrier> ve API başvurusu.

## <a name="interlocked-class"></a>Interlocked sınıfı

Sınıfı <xref:System.Threading.Interlocked?displayProperty=nameWithType> , bir değişkende basit Atomik işlemler gerçekleştiren statik yöntemler sağlar. Bu atomik işlemler, bir karşılaştırmaya ve 64 bitlik bir tamsayı değerinin okuma işlemine bağlı olan toplama, artırma ve azaltma, değişim ve koşullu değişim işlemlerini içerir.

Daha fazla bilgi için bkz <xref:System.Threading.Interlocked> . API başvurusu.

## <a name="spinwait-structure"></a>SpinWait yapısı

Yapı <xref:System.Threading.SpinWait?displayProperty=nameWithType> , döndürme tabanlı bekleme için destek sağlar. Bir iş parçacığının bir olayın sinyal vermesini veya bir koşulun karşılanmasını beklemek gerektiğinde, ancak gerçek bekleme süresinin bir bekleme tutamacı kullanılarak veya iş parçacığını engelleyerek gereken bekleme süresinden daha az olması beklendiğinde bunu kullanmak isteyebilirsiniz. Kullanarak <xref:System.Threading.SpinWait>, beklenirken dönebilmeniz için kısa bir süre belirtebilir ve sonra (örneğin, bekleme ya da uyuma) yalnızca koşulun belirtilen sürede karşılanmamış olması durumunda ödeme yapabilirsiniz.

Daha fazla bilgi için [SpinWait](spinwait.md) makalesine ve <xref:System.Threading.SpinWait> API başvurusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli Koleksiyonlar](../collections/thread-safe/index.md)
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
