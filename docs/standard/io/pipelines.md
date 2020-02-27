---
title: G/ç işlem hatları-.NET
description: .NET ' te ı/O işlem hatlarını verimli bir şekilde kullanmayı ve kodunuzda sorunlardan kaçınmak hakkında bilgi edinin.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: b18b2bf31787fa58e614cd4f057fba9037fe8ad8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627558"
---
# <a name="systemiopipelines-in-net"></a>.NET 'teki System. ıO. işlem hatları

<xref:System.IO.Pipelines>, .NET ortamında yüksek performanslı g/ç 'yi daha kolay hale getirmek için tasarlanan yeni bir kitaplıktır. Bu, tüm .NET uygulamalarında çalışacak .NET Standard hedefleme bir kitaplıktır.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>System. ıO. hatlarını çözme sorunu

<!-- corner case doesn't MT (machine translate)   -->
Akış verilerini ayrıştırmaya yönelik uygulamalar, çok sayıda özel ve olağandışı kod akışına sahip ortak koddan oluşur. Ortak ve özel durum kodu karmaşık ve devam etmek zordur.

`System.IO.Pipelines` şu şekilde tasarlanmıştır:

* Akış verilerinin yüksek performans ayrıştırması vardır.
* Kod karmaşıklığını azaltın.

Aşağıdaki kod, bir istemciden satır sınırlı iletileri (`'\n'`ile ayrılmış) alan bir TCP sunucusu için tipik bir noktadır:

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Yukarıdaki kodda birkaç sorun vardır:

* Tüm ileti (satır sonu) `ReadAsync`tek bir çağrıda alınmayabilir.
* `stream.ReadAsync`sonucunu yok sayıyor. `stream.ReadAsync`, ne kadar verinin okunduğunu döndürür.
* Tek bir `ReadAsync` çağrısında birden çok satırın okunduğu durumu işlemez.
* Her okuma ile bir `byte` dizisi ayırır.

Yukarıdaki sorunları onarmak için aşağıdaki değişiklikler gereklidir:

* Yeni bir satır bulunana kadar gelen verileri arabelleğe koyun.
* Arabellekte döndürülen tüm satırları ayrıştırın.
* Satır 1 KB 'den büyük (1024 bayt) olabilir. Bu kodun, arabelleğin içindeki tamamlanma satırına sığması için sınırlayıcı bulunana kadar giriş arabelleğini yeniden boyutlandırması gerekir.

  * Arabellek yeniden boyutlandırılırsa, girişte daha uzun çizgiler göründüğü sürece daha fazla arabellek kopyası yapılır.
  * Harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.

* Belleği sürekli ayırmayı önlemek için arabellek havuzu kullanmayı düşünün.
* Aşağıdaki kod bu sorunlardan bazılarını ele alınmaktadır:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez. Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir. `System.IO.Pipelines`, bu tür bir kodu daha kolay yazmayı kolaylaştırmak için tasarlanmıştır.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Kapatıldığı

<xref:System.IO.Pipelines.Pipe> sınıfı bir `PipeWriter/PipeReader` çifti oluşturmak için kullanılabilir. `PipeWriter` yazılan tüm veriler `PipeReader`kullanılabilir:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Kanal temel kullanımı

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

İki döngü vardır:

* `FillPipeAsync` `Socket` okur ve `PipeWriter`yazar.
* `ReadPipeAsync` `PipeReader` okur ve gelen satırları ayrıştırır.

Ayrılmış açık arabellek yok. Tüm arabellek yönetimi, `PipeReader` ve `PipeWriter` uygulamalarına devredildi. Arabellek yönetimi için temsilci seçme, kodun yalnızca iş mantığına odaklanılmasını kolaylaştırır.

İlk döngüde:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>, temel alınan yazıcıya bellek almak için çağrılır.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>, arabelleğe ne kadar veri yazıldığını `PipeWriter` söylemek için çağırılır.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>, verileri `PipeReader`kullanılabilir hale getirmek için çağrılır.

İkinci döngüde, `PipeReader` `PipeWriter`tarafından yazılan arabellekleri tüketir. Arabellekler yuvadan gelir. `PipeReader.ReadAsync`çağrısı:

* İki önemli bilgi parçasını içeren bir <xref:System.IO.Pipelines.ReadResult> döndürür:

  * `ReadOnlySequence<byte>`biçiminde okunan veriler.
  * Verilerin sonuna (EOF) ulaşıldığını belirten bir Boole `IsCompleted`.

Satır sonu (EOL) sınırlayıcısı bulduktan ve satırı ayrıştırdıktan sonra:

* Mantık, zaten işlenmiş olan öğeleri atlamak için arabelleği işler.
* `PipeReader.AdvanceTo`, ne kadar veri tüketiğini ve incelendiğini `PipeReader` söylemek için çağırılır.

Okuyucu ve yazıcı döngüleri `Complete`çağırarak biter. `Complete`, temeldeki kanalın ayrılan belleği serbest bırakmasına olanak tanır.

### <a name="backpressure-and-flow-control"></a>Arka basınç ve akış denetimi

İdeal olarak, birlikte iş okuma ve ayrıştırma:

* Yazma iş parçacığı ağdan verileri tüketir ve arabelleğe koyar.
* Ayrıştırma iş parçacığı, uygun veri yapılarını oluşturmaktan sorumludur.

Genellikle, ayrıştırma yalnızca ağdan veri bloklarını kopyalamaya kıyasla daha fazla zaman alır:

* Okuma iş parçacığı ayrıştırma iş parçacığının önüne alınır.
* Okuma iş parçacığı, ayrıştırma iş parçacığı için verileri depolamak üzere yavaşlıyor veya daha fazla bellek ayırmıştır.

En iyi performans için, sık duraklamalar ve daha fazla bellek ayırma arasında bir denge vardır.

Önceki sorunu çözmek için, `Pipe` veri akışını denetlemek üzere iki ayarı vardır:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> duraklatma çağrısı yapmadan önce ne kadar veri ara belleğe alınacağını belirler.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: okuyucunun `PipeWriter.FlushAsync` sürdürülmeye yönelik çağrılardan önce ne kadar veri gözlemleyecek olduğunu belirler.

![ResumeWriterThreshold ve PauseWriterThreshold ile diyagram](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* `Pipe` veri miktarı `PauseWriterThreshold`kesiştiği zaman tamamlanmamış bir `ValueTask<FlushResult>` döndürür.
* `ResumeWriterThreshold`daha düşük hale geldiğinde `ValueTask<FlushResult>` tamamlar.

Tek bir değer kullanılırsa oluşabilecek hızlı döngüyü engellemek için iki değer kullanılır.

### <a name="examples"></a>Örnekler

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Genellikle `async` ve `await`kullanılırken, zaman uyumsuz kod <xref:System.Threading.Tasks.TaskScheduler> ya da geçerli <xref:System.Threading.SynchronizationContext>üzerinde devam eder.

G/ç yaparken, g/ç 'nin gerçekleştirildiği noktada ayrıntılı denetime sahip olmak önemlidir. Bu denetim, CPU önbelleklerinin etkin bir şekilde yararlanmasını sağlar. Verimli önbelleğe alma, Web sunucuları gibi yüksek performanslı uygulamalar için kritik öneme sahiptir. <xref:System.IO.Pipelines.PipeScheduler>, zaman uyumsuz geri çağırmaların çalıştığı yerde denetim sağlar. Varsayılan olarak:

* Geçerli <xref:System.Threading.SynchronizationContext> kullanılır.
* `SynchronizationContext`yoksa, geri çağırmaları çalıştırmak için iş parçacığı havuzunu kullanır.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[Pipescheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) , iş parçacığı havuzuna geri çağırmaları sıraya alan <xref:System.IO.Pipelines.PipeScheduler> uygulamasıdır. `PipeScheduler.ThreadPool` varsayılandır ve genellikle en iyi seçenektir. [Pipescheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) , kilitlenme gibi istenmeyen sonuçlara neden olabilir.

### <a name="pipe-reset"></a>Kanal sıfırlama

`Pipe` nesnesini yeniden kullanmak sıklıkla etkilidir. Kanalı sıfırlamak için, hem `PipeReader` hem de `PipeWriter` tamamlandığında <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> çağırın.

## <a name="pipereader"></a>Piypereader

<xref:System.IO.Pipelines.PipeReader>, arayanın adına belleği yönetir. <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>çağrıldıktan sonra **her zaman** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> çağırın. Bu, `PipeReader` izlenebilecek şekilde çağıranın bellekle ne zaman yapıldığını bilmesini sağlar. `PipeReader.ReadAsync` döndürülen `ReadOnlySequence<byte>` yalnızca `PipeReader.AdvanceTo`çağrısı yapılıncaya kadar geçerlidir. `PipeReader.AdvanceTo`çağrıldıktan sonra `ReadOnlySequence<byte>` kullanımı geçersizdir.

`PipeReader.AdvanceTo` iki <xref:System.SequencePosition> bağımsız değişkeni alır:

* İlk bağımsız değişken, ne kadar bellek tüketildiğini belirler.
* İkinci bağımsız değişken, arabelleğin ne kadarının gözlemlendiğini belirler.

Verileri tüketilen olarak işaretlemek, kanalın belleği temel alınan arabellek havuzuna döndürebileceği anlamına gelir. Verileri gözlemlenen olarak işaretlemek `PipeReader.ReadAsync` sonraki çağrının ne yaptığını denetler. Her şeyi gözlemlenen olarak işaretlemek, kanala daha fazla veri yazılıncaya kadar `PipeReader.ReadAsync` bir sonraki çağrının dönemeyeceği anlamına gelir. Diğer herhangi bir değer, bir sonraki çağrının `PipeReader.ReadAsync` gözlemlenen *ve* gözlemlenen verilerle hemen döndürülmesini sağlar, ancak daha önce tüketilen veriler.

### <a name="read-streaming-data-scenarios"></a>Akış verilerini okuma senaryoları

Akış verilerini okumaya çalışırken ortaya çıktı olan birkaç tipik desen vardır:

* Veri akışı verildiğinde, tek bir iletiyi ayrıştırır.
* Veri akışı verildiğinde, tüm kullanılabilir iletileri ayrıştırır.

Aşağıdaki örneklerde, bir `ReadOnlySequence<byte>`iletileri ayrıştırmak için `TryParseMessage` yöntemi kullanılmaktadır. `TryParseMessage` tek bir iletiyi ayrıştırır ve ayrıştırılmış iletiyi arabellekten kırpmak için giriş arabelleğini güncelleştirir. `TryParseMessage` .NET 'in bir parçası değildir, bu, aşağıdaki bölümlerde kullanılan bir kullanıcı yazılmış yöntemidir.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Tek bir iletiyi okuyun

Aşağıdaki kod `PipeReader` tek bir ileti okur ve bunu çağırana döndürür.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Yukarıdaki kod:

* Tek bir ileti ayrıştırır.
* Tüketilen `SequencePosition` güncelleştirir ve kırpılan giriş arabelleğinin başlangıcına işaret etmek için `SequencePosition` incelenir.

İki `SequencePosition` bağımsız değişkeni güncelleştirilir çünkü `TryParseMessage` ayrıştırılmış iletiyi giriş arabelleğinden kaldırır. Genellikle, arabellekteki tek bir ileti ayrıştırılırken, incelenen konum aşağıdakilerden biri olmalıdır:

* İletinin sonu.
* İleti bulunmazsa alınan arabelleğin sonu.

Tek ileti durumunun hata için en olası olasılığı vardır. Yanlış değerleri *incelenmeye* geçirmek, yetersiz bellek özel durumu veya sonsuz bir döngüye neden olabilir. Daha fazla bilgi için bu makaledeki [Pıpereader ortak sorunlar](#gotchas) bölümüne bakın.

### <a name="reading-multiple-messages"></a>Birden çok ileti okunuyor

Aşağıdaki kod bir `PipeReader` tüm iletileri okur ve her bir `ProcessMessageAsync` çağırır.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>İptal

`PipeReader.ReadAsync`:

* <xref:System.Threading.CancellationToken>geçirmeyi destekler.
* Bir okuma beklemede olduğunda `CancellationToken` iptal edilirse bir <xref:System.OperationCanceledException> oluşturur.
* , Geçerli okuma işlemini <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>aracılığıyla iptal etmek için bir yol destekler, bu da bir özel durumun çıkarılmasını önler. `PipeReader.CancelPendingRead` çağırmak, geçerli veya sonraki `PipeReader.ReadAsync` çağrının `IsCanceled` <xref:System.IO.Pipelines.ReadResult> ile `true`döndürmesine neden olur. Bu, var olan okuma döngüsünü bozucu olmayan ve olağanüstü olmayan bir şekilde sonlandırmanız için yararlı olabilir.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Piypereader yaygın sorunlar

* Yanlış değerleri `consumed` veya `examined` geçirmek, zaten okuma verilerinin okunmasına neden olabilir.
* `buffer.End` İncelenme olarak geçirilmesiyle sonuçlanabilir:

  * Durdurulmuş veriler
  * Veriler tüketilmemişse, büyük olasılıkla yetersiz bellek (OOM) özel durumu. Örneğin, her seferinde tek bir ileti işlenirken `PipeReader.AdvanceTo(position, buffer.End)`.

* Yanlış değerleri `consumed` veya `examined` geçirmek sonsuz bir döngüye neden olabilir. Örneğin, `buffer.Start` değiştirilmemişse `PipeReader.AdvanceTo(buffer.Start)`, yeni veri alınmadan hemen önce `PipeReader.ReadAsync` bir sonraki çağrının dönmesini sağlar.
* Yanlış değerleri `consumed` veya `examined` geçirmek sonsuz arabelleğe alma (nihai OOM) ile sonuçlanabilir.
* `PipeReader.AdvanceTo` çağrıldıktan sonra `ReadOnlySequence<byte>` kullanmak bellek bozulmasına neden olabilir (ücretsiz olarak kullanabilirsiniz).
* `PipeReader.Complete/CompleteAsync` çağıramayan bellek sızıntısına neden olabilir.
* Veri kaybına neden olan arabellek sonuçlarını işlemeden önce <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> denetleniyor ve okuma mantığı çıkıyor. Döngü çıkış koşulunun `ReadResult.Buffer.IsEmpty` ve `ReadResult.IsCompleted`temel almalıdır. Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.

#### <a name="problematic-code"></a>Sorunlu kod

❌ **veri kaybı**

`ReadResult`, `IsCompleted` `true`olarak ayarlandığında son veri segmentini döndürebilir. Okuma döngüsünden çıkmadan önce bu verilerin okunmamasından dolayı veri kaybı olur.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **sonsuz döngü**

Aşağıdaki mantık, `Result.IsCompleted` `true`, ancak arabellekte hiç tamamlanmamış bir ileti varsa sonsuz döngüye neden olabilir.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Aynı sorunu içeren başka bir kod parçası aşağıda verilmiştir. `ReadResult.IsCompleted`denetlemeden önce boş olmayan bir arabellek denetleniyor. Bir `else if`olduğundan, arabellekte hiç bir ileti yoksa, süresiz olarak döngü yapılır.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**beklenmeyen ❌ askıda**

`examined` konumundaki `buffer.End` ile `PipeReader.AdvanceTo` koşulsuz olarak çağırmanın tek bir ileti ayrıştırılırken askıda kalmasına neden olabilir. `PipeReader.AdvanceTo` sonraki çağrısı şu kadar döndürmez:

* Kanala yazılan daha fazla veri var.
* Ve yeni veriler daha önce incelendi.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**yetersiz bellek (OOM)** ❌

Aşağıdaki koşullara göre aşağıdaki kod, <xref:System.OutOfMemoryException> gerçekleşene kadar arabelleğe almayı sürdürür:

* En büyük ileti boyutu yok.
* `PipeReader` döndürülen veriler, tüm iletileri yapmaz. Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB bir ileti) yazıldığı için, bu tam bir ileti yapmaz.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **belleği bozulması**

Arabelleği okuyan yardımcıları yazarken, `Advance`çağrılmadan önce döndürülen yükün kopyalanması gerekir. Aşağıdaki örnek, `Pipe` atılan belleği döndürür ve bir sonraki işlem (okuma/yazma) için onu yeniden kullanabilir.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

<xref:System.IO.Pipelines.PipeWriter>, arayan adına yazma arabelleğini yönetir. `PipeWriter` [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)uygular. `IBufferWriter<byte>` ek arabellek kopyaları olmadan yazma işlemleri gerçekleştirmek için arabelleklere erişim sağlamak mümkün hale gelir.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Önceki kod:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>kullanarak `PipeWriter` en az 5 baytlık bir arabellek ister.
* `"Hello"` ASCII dizesinin bayt sayısını döndürülen `Memory<byte>`yazar.
* Arabelleğe kaç bayt yazıldığını belirten <xref:System.IO.Pipelines.PipeWriter.Advance%2A> çağırır.
* , Baytları temel alınan cihaza gönderen `PipeWriter`boşaltır.

Önceki yazma yöntemi, `PipeWriter`tarafından belirtilen arabellekleri kullanır. Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Mevcut arabelleği `PipeWriter`kopyalar.
* `GetSpan`çağırır `Advance` ve <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>çağırır.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>İptal

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> <xref:System.Threading.CancellationToken>geçirmeyi destekler. Bir `CancellationToken` geçirme işlemi, belirteç bekleyen bir temizleme işlemi sırasında iptal edilirse bir `OperationCanceledException` sonuçlanır. `PipeWriter.FlushAsync`, özel durum oluşturmadan <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> aracılığıyla geçerli temizleme işlemini iptal etmek için bir yol destekler. `PipeWriter.CancelPendingFlush` çağırmak, geçerli veya sonraki `PipeWriter.FlushAsync` veya `PipeWriter.WriteAsync` çağrının `IsCanceled` ayarlanmış `true`bir <xref:System.IO.Pipelines.FlushResult> döndürmesini sağlar. Bu, bozucu olmayan ve olağanüstü olmayan bir şekilde boşaltmayı Temizleme için yararlı olabilir.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter ortak sorunları

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> en az istenen bellek miktarına sahip bir arabellek döndürür. Tam arabellek boyutlarını kabul **etmeyin** .
* Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.
* Daha fazla veri yazmaya devam etmek için <xref:System.IO.Pipelines.PipeWriter.Advance%2A> çağrıldıktan sonra yeni bir arabellek istenmesi gerekir. Daha önce edinilen arabelleğin üzerine yazılamaz.
* `FlushAsync` tamamlanmamış bir çağrı olduğundan `GetMemory` veya `GetSpan` çağırma.
* Verilerin temizlenme sırasında `Complete` veya `CompleteAsync` çağırmak bellek bozulmasına yol açabilir.

## <a name="iduplexpipe"></a>IDuplexPipe

<xref:System.IO.Pipelines.IDuplexPipe>, hem okumayı hem de yazmayı destekleyen türler için bir sözleşmedir. Örneğin, bir ağ bağlantısı bir `IDuplexPipe`tarafından temsil edilir.

 Bir `PipeReader` ve `PipeWriter`içeren `Pipe` aksine, `IDuplexPipe` tam çift yönlü bağlantının tek tarafını temsil eder. Bu, `PipeWriter` yazılan ve `PipeReader`okunmayacak anlamına gelir.

## <a name="streams"></a>Akışlar

Akış verilerini okurken veya yazarken genellikle seri hale getirici kullanarak verileri okur ve serileştirici kullanarak verileri yazın. Bu okuma ve yazma akışı API 'Lerinin çoğu bir `Stream` parametresine sahiptir. Bu mevcut API 'lerle tümleştirmeyi kolaylaştırmak için `PipeReader` ve `PipeWriter` <xref:System.IO.Pipelines.PipeReader.AsStream%2A>kullanıma sunun.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>, `PipeReader` veya `PipeWriter`etrafında `Stream` bir uygulama döndürür.
