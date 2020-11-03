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
ms.openlocfilehash: d5ae0fe5813952742950582a4282cd1c6ab6a870
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188984"
---
# <a name="overview-of-synchronization-primitives"></a>Eşitleme temellerine genel bakış

.NET, paylaşılan bir kaynağa erişimi veya koordinat iş parçacığı etkileşimini eşleştirmek için kullanabileceğiniz bir dizi tür sağlar.

> [!IMPORTANT]
> Paylaşılan bir kaynağın erişimini korumak için aynı eşitleme temel örneğini kullanın. Aynı kaynağı korumak için farklı eşitleme temel örnekleri kullanıyorsanız, bir eşitleme temel tarafından sağlanmış olan korumayı atlacaksınız.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle sınıfı ve hafif eşitleme türleri

Çoklu .NET eşitleme temelleri <xref:System.Threading.WaitHandle?displayProperty=nameWithType> , yerel bir işletim sistemi eşitleme tanıtıcısını kapsülleyen ve iş parçacığı etkileşimi için bir sinyal mekanizması kullanan sınıfından türetilir. Bu sınıflar şunları içerir:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, paylaşılan bir kaynağa özel erişim izni veren. Bir mutex 'in durumu, kendisine ait bir iş parçacığı yoksa sinyal edilir.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlar. Bir semaforun durumu, sayısı sıfırdan büyük olduğunda ve sayısı sıfır olduğunda, sinyalsiz olarak ayarlanır.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, bir iş parçacığı eşitleme olayını temsil eden ve sinyal veya sinyal edilmemiş bir durumda olabilir.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>ve ' den türetilen, <xref:System.Threading.EventWaitHandle> sinyal edildiğinde, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra otomatik olarak sinyali verilmemiş bir duruma sıfırlar.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>ve ' den türetilen, <xref:System.Threading.EventWaitHandle> sinyal edildiğinde, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır.

.NET Framework ' de <xref:System.Threading.WaitHandle> , öğesinden türetildiğinden <xref:System.MarshalByRefObject?displayProperty=nameWithType> , bu türler uygulama etki alanı sınırları genelinde iş parçacığı etkinliklerinin eşitlenmesi için kullanılabilir.

.NET Framework, .NET Core ve .NET 5 + ' de, bu türlerden bazıları işletim sisteminde görünür olan ve işlemler arası eşitleme için kullanılabilen adlandırılmış sistem eşitleme tutamaçlarını temsil edebilir:

- <xref:System.Threading.Mutex>
- <xref:System.Threading.Semaphore> (Windows üzerinde)
- <xref:System.Threading.EventWaitHandle> (Windows üzerinde)

Daha fazla bilgi için bkz <xref:System.Threading.WaitHandle> . API başvurusu.

Hafif eşitleme türleri, temel işletim sistemi tanıtıcılarını içermez ve genellikle daha iyi performans sağlar. Ancak, işlemler arası eşitleme için kullanılamaz. Bir uygulama içinde iş parçacığı eşitlemesi için bu türleri kullanın.

Bu türlerden bazıları, öğesinden türetilmiş türler için alternatiflerdir <xref:System.Threading.WaitHandle> . Örneğin, <xref:System.Threading.SemaphoreSlim> için hafif bir alternatiftir <xref:System.Threading.Semaphore> .

## <a name="synchronization-of-access-to-a-shared-resource"></a>Paylaşılan kaynağa erişimin eşitlenmesi

.NET birden çok iş parçacığı tarafından paylaşılan bir kaynağa erişimi denetlemek için bir dizi eşitleme temel kümesi sağlar.

### <a name="monitor-class"></a>İzleme sınıfı

<xref:System.Threading.Monitor?displayProperty=nameWithType>Sınıfı, kaynağı tanımlayan nesne üzerinde bir kilit edinerek veya serbest bırakarak paylaşılan kaynağa birbirini dışlayan erişim verir. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Diğer herhangi bir iş parçacığının kilidi almak engellenir ve <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> Yöntem kilit serbest bırakılana kadar bekler. <xref:System.Threading.Monitor.Enter%2A>Yöntemi, serbest bırakıldı bir kilit alır. Yöntemini ayrıca, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> bir iş parçacığının kilit alma girişiminde bulunduğu süreyi belirtmek için de kullanabilirsiniz. <xref:System.Threading.Monitor>Sınıfta iş parçacığı benzeşimi bulunduğundan, bir kilit alan iş parçacığının yöntemi çağırarak kilidi serbest bırakmalıdır <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> .

<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> , Ve yöntemlerini kullanarak aynı nesne üzerinde bir kilit elde eden iş parçacıklarının etkileşimini koordine edebilirsiniz <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> .

Daha fazla bilgi için bkz <xref:System.Threading.Monitor> . API başvurusu.

> [!NOTE]
> Sınıfı doğrudan kullanmak yerine paylaşılan bir kaynağa erişimi eşleştirmek için, C# ' deki [Lock](../../csharp/language-reference/keywords/lock-statement.md) ifadesini ve Visual Basic içindeki [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ifadesini kullanın <xref:System.Threading.Monitor> . Bu deyimler, <xref:System.Threading.Monitor.Enter%2A> <xref:System.Threading.Monitor.Exit%2A> `try…finally` elde edilen kilidin her zaman serbest bırakılacağını sağlamak için ve yöntemleri ve bir bloğu kullanılarak uygulanır.

### <a name="mutex-class"></a>Mutex sınıfı

Gibi <xref:System.Threading.Mutex?displayProperty=nameWithType> sınıf, <xref:System.Threading.Monitor> paylaşılan bir kaynağa özel erişim izni verir. Mutex 'in sahipliğini istemek için [mutex. WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) yöntemi aşırı yüklerini kullanın. Benzer şekilde <xref:System.Threading.Monitor> , <xref:System.Threading.Mutex> iş parçacığı benzeşimine sahiptir ve bir mutex elde eden iş parçacığının yöntemini çağırarak onu serbest bırakmalıdır <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> .

Aksine <xref:System.Threading.Monitor> , <xref:System.Threading.Mutex> sınıfı işlemler arası eşitleme için kullanılabilir. Bunu yapmak için, işletim sisteminin tamamında görünür olan adlandırılmış bir mutex kullanın. Adlandırılmış bir mutex örneği oluşturmak için, bir adı belirten bir [mutex Oluşturucusu](<xref:System.Threading.Mutex.%23ctor%2A>) kullanın. Ayrıca, <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> var olan bir adlandırılmış sistem mutex 'i açmak için yöntemini çağırabilirsiniz.
  
Daha fazla bilgi için, [birbirini kapsamayan](mutexes.md) makaleye ve <xref:System.Threading.Mutex> API başvurusuna bakın.

### <a name="spinlock-structure"></a>SpinLock yapısı

<xref:System.Threading.SpinLock?displayProperty=nameWithType>Gibi yapı, <xref:System.Threading.Monitor> bir kilidin kullanılabilirliğine göre paylaşılan bir kaynağa özel erişim verir. <xref:System.Threading.SpinLock>Kullanılamayan bir kilit edinmeye çalıştığında, kilit kullanılabilir hale gelene kadar bir döngüde bekler, tekrar tekrar kontrol edilir.

Döndürme kilidi kullanmanın avantajları ve dezavantajları hakkında daha fazla bilgi için, bkz. [SpinLock](spinlock.md) makalesi ve <xref:System.Threading.SpinLock> API başvurusu.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim Class

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType>Sınıfı, yazmak üzere paylaşılan bir kaynağa özel erişim verir ve birden çok iş parçacığının okumak için aynı anda kaynağa erişmesini sağlar. <xref:System.Threading.ReaderWriterLockSlim>Erişimi, iş parçacığı güvenli okuma işlemlerini destekleyen bir paylaşılan veri yapısına eşitlemeniz, ancak yazma işlemini gerçekleştirmek için özel erişim gerektirir. Bir iş parçacığı özel erişim istediğinde (örneğin, <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> yöntemini çağırarak), sonraki okuyucu ve yazıcı istekleri, var olan tüm okuyucular kilitlenene kadar engeller ve yazıcı, kilitliyken ve kilide çıkış yaptı.
  
Daha fazla bilgi için bkz <xref:System.Threading.ReaderWriterLockSlim> . API başvurusu.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor ve SemaphoreSlim sınıfları

<xref:System.Threading.Semaphore?displayProperty=nameWithType>Ve <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> sınıfları, paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacıklarının sayısını sınırlar. Kaynak isteyen ek iş parçacıkları, herhangi bir iş parçacığı semaforu yayınlana kadar bekler. Semaforun iş parçacığı benzeşimi olmadığından, bir iş parçacığı semaforu alabilir ve başka bir tane onu serbest bırakabilir.

<xref:System.Threading.SemaphoreSlim> , için hafif bir alternatiftir <xref:System.Threading.Semaphore> ve yalnızca tek bir işlem sınırı içindeki eşitleme için kullanılabilir.

Windows 'ta, işlemler <xref:System.Threading.Semaphore> arası eşitleme için kullanabilirsiniz. Bunu yapmak için, <xref:System.Threading.Semaphore> bir ad veya yöntem belirten [semafor oluşturucularından](<xref:System.Threading.Semaphore.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem semaforu temsil eden bir örnek oluşturun <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> . <xref:System.Threading.SemaphoreSlim> adlandırılmış sistem semaforları desteklemez.

Daha fazla bilgi için [semafor ve SemaphoreSlim](semaphore-and-semaphoreslim.md) makalesine ve <xref:System.Threading.Semaphore> veya <xref:System.Threading.SemaphoreSlim> API başvurusuna bakın.

## <a name="thread-interaction-or-signaling"></a>İş parçacığı etkileşimi veya sinyal

İş parçacığı etkileşimi (veya iş parçacığı sinyali), bir iş parçacığının devam edebilmek için bir veya daha fazla iş parçacığından bildirim veya sinyal beklemesi gerektiği anlamına gelir. Örneğin, Thread A iş parçacığı <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> b iş parçacığı yöntemini çağırırsa, b iş parçacığı tamamlanana kadar bir iş parçacığı engellenir. Önceki bölümde açıklanan eşitleme temelleri, sinyal için farklı bir mekanizma sağlar: bir kilit serbest bırakarak, bir iş parçacığının kilidi alarak devam edemeyeceğini başka bir iş parçacığına bildirir.

Bu bölümde .NET tarafından sunulan ek sinyal yapıları açıklanmaktadır.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, oto ResetEvent, ManualResetEvent ve Manualreseteventince sınıflar

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>Sınıfı bir iş parçacığı eşitleme olayını temsil eder.

Eşitleme olayı, sinyal veya sinyal verilmemiş bir durumda olabilir. Bir olayın durumu işaret edildiğinde, <xref:System.Threading.WaitHandle.WaitOne%2A?> bir olay sinyallene kadar olayın aşırı yüklemesini çağıran bir iş parçacığı engellenir. <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType>Yöntemi, bir olayın durumunu sinyal olarak ayarlar.

Sinyal davranışı, <xref:System.Threading.EventWaitHandle> sıfırlama moduna bağlıdır:

- <xref:System.Threading.EventWaitHandle>Bayrağıyla oluşturulmuş bir, <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra otomatik olarak sıfırlanır. Her sinyalde yalnızca bir iş parçacığına izin veren bir turnike gibi. <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>Öğesinden türetilen sınıf, <xref:System.Threading.EventWaitHandle> Bu davranışı temsil eder.
- <xref:System.Threading.EventWaitHandle>Bayrağıyla oluşturulmuş bir, <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır. Bu, sinyal edilene kadar kapalı bir kapıdır ve bir kişi tarafından kapanana kadar açık kalır. <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>Öğesinden türetilen sınıf, <xref:System.Threading.EventWaitHandle> Bu davranışı temsil eder. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>Sınıfı, için hafif bir alternatiftir <xref:System.Threading.ManualResetEvent> .

Windows 'ta, işlemler <xref:System.Threading.EventWaitHandle> arası eşitleme için kullanabilirsiniz. Bunu yapmak için, <xref:System.Threading.EventWaitHandle> bir ad veya yöntem belirten [EventWaitHandle oluşturucularından](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) birini kullanarak adlandırılmış bir sistem eşitleme olayını temsil eden bir örnek oluşturun <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> .

Daha fazla bilgi için, [EventWaitHandle](eventwaithandle.md) makalesine bakın. API başvurusu için bkz., <xref:System.Threading.EventWaitHandle> , <xref:System.Threading.AutoResetEvent> <xref:System.Threading.ManualResetEvent> ve <xref:System.Threading.ManualResetEventSlim> .

### <a name="countdownevent-class"></a>CountdownEvent sınıfı

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>Sınıfı, sayısı sıfır olduğunda ayarlanan bir olayı temsil eder. <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType>Sıfırdan büyükse, çağıran bir iş parçacığı <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> engellenir. <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType>Bir olayın sayısını azaltmak için çağrısı yapın.

<xref:System.Threading.ManualResetEvent>Veya ' ın aksine <xref:System.Threading.ManualResetEventSlim> , bir iş parçacığından gelen bir sinyal ile birden çok iş parçacığının engellemesini kaldırmak için kullanabileceğiniz, <xref:System.Threading.CountdownEvent> birden çok iş parçacığının sinyalleriyle bir veya daha fazla iş parçacığının engellemesini kaldırmak için kullanabilirsiniz.

Daha fazla bilgi için bkz. [CountdownEvent](countdownevent.md) makalesi ve <xref:System.Threading.CountdownEvent> API başvurusu.

### <a name="barrier-class"></a>Bariyer sınıfı

<xref:System.Threading.Barrier?displayProperty=nameWithType>Sınıfı bir iş parçacığı yürütme engelini temsil eder. Yöntemi çağıran bir iş parçacığı <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> , engeli ne ulaştığına işaret eder ve diğer katılımcı iş parçacıkları engelye ulaşana kadar bekler. Tüm katılımcı iş parçacıkları engelye ulaştığında devam ederler ve engel sıfırlanır ve yeniden kullanılabilir.

<xref:System.Threading.Barrier>Bir veya daha fazla iş parçacığı, sonraki hesaplama aşamasına geçmeden önce diğer iş parçacıklarının sonuçlarını gerektirdiğinde kullanabilirsiniz.

Daha fazla bilgi için, bkz. [bariyer](barrier.md) makalesi ve <xref:System.Threading.Barrier> API başvurusu.

## <a name="interlocked-class"></a>Interlocked sınıfı

<xref:System.Threading.Interlocked?displayProperty=nameWithType>Sınıfı, bir değişkende basit Atomik işlemler gerçekleştiren statik yöntemler sağlar. Bu atomik işlemler, bir karşılaştırmaya ve 64 bitlik bir tamsayı değerinin okuma işlemine bağlı olan toplama, artırma ve azaltma, değişim ve koşullu değişim işlemlerini içerir.

Daha fazla bilgi için bkz <xref:System.Threading.Interlocked> . API başvurusu.

## <a name="spinwait-structure"></a>SpinWait yapısı

<xref:System.Threading.SpinWait?displayProperty=nameWithType>Yapı, döndürme tabanlı bekleme için destek sağlar. Bir iş parçacığının bir olayın sinyal vermesini veya bir koşulun karşılanmasını beklemek gerektiğinde, ancak gerçek bekleme süresinin bir bekleme tutamacı kullanılarak veya iş parçacığını engelleyerek gereken bekleme süresinden daha az olması beklendiğinde bunu kullanmak isteyebilirsiniz. Kullanarak <xref:System.Threading.SpinWait> , beklenirken dönebilmeniz için kısa bir süre belirtebilir ve sonra (örneğin, bekleme ya da uyuma) yalnızca koşulun belirtilen sürede karşılanmamış olması durumunda ödeme yapabilirsiniz.

Daha fazla bilgi için [SpinWait](spinwait.md) makalesine ve <xref:System.Threading.SpinWait> API başvurusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [İş parçacığı güvenli koleksiyonlar](../collections/thread-safe/index.md)
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
