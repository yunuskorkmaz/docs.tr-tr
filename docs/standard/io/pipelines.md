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
ms.openlocfilehash: 9efd7a7581a1e8bd2cb5f544edd1b4c965aa1866
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395920"
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

Aşağıdaki kod, bir istemciden satır sınırlı iletileri (`'\n'` ile sınırlandırılmış) alan bir TCP sunucusu için tipik bir noktadır:

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

* Tüm ileti (satır sonu) `ReadAsync` ' a yapılan tek bir çağrıda alınmayabilir.
* @No__t-0 sonucu yok sayılıyor. `stream.ReadAsync`, okunan veri miktarını döndürür.
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

Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez. Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir. `System.IO.Pipelines`, bu tür kodu daha kolay yazmayı kolaylaştırmak için tasarlanmıştır.

## <a name="pipe"></a>Kapatıldığı

@No__t-0 sınıfı bir `PipeWriter/PipeReader` çifti oluşturmak için kullanılabilir. @No__t-0 ' a yazılan tüm veriler `PipeReader` ' de kullanılabilir:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Kanal temel kullanımı

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

İki döngü vardır:

* `FillPipeAsync` `Socket` ' den okur ve `PipeWriter` ' ye yazar.
* `ReadPipeAsync` `PipeReader` ' den okur ve gelen satırları ayrıştırır.

Ayrılmış açık arabellek yok. Tüm arabellek yönetimi, `PipeReader` ve `PipeWriter` uygulamalarına devredildi. Arabellek yönetimi için temsilci seçme, kodun yalnızca iş mantığına odaklanılmasını kolaylaştırır.

İlk döngüde:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>, temel kümeden belleği almak için çağrılır.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>, arabelleğe ne kadar veri yazıldığını @no__t söylemek için çağırılır.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>, verileri `PipeReader` ' e kullanılabilir hale getirmek için çağrılır.

İkinci döngüde `PipeReader` `PipeWriter` tarafından yazılan arabellekleri kullanır. Arabellekler yuvadan gelir. @No__t-0 ' a çağrı:

* İki önemli bilgi parçasını içeren <xref:System.IO.Pipelines.ReadResult> döndürür:

  * @No__t-0 biçiminde okunan veriler.
  * Verilerin sonuna (EOF) ulaşıldığını belirten bir Boole `IsCompleted`.

Satır sonu (EOL) sınırlayıcısı bulduktan ve satırı ayrıştırdıktan sonra:

* Mantık, zaten işlenmiş olan öğeleri atlamak için arabelleği işler.
* `PipeReader.AdvanceTo` ' a, ne kadar veri tüketildiğini ve inceleyeceğinizi @no__t söylemek için çağırılır.

Okuyucu ve yazıcı döngüleri `Complete` çağırarak biter. `Complete`, temeldeki kanalın ayrılan belleği serbest bırakmasına olanak tanır.

### <a name="backpressure-and-flow-control"></a>Arka basınç ve akış denetimi

İdeal olarak, birlikte iş okuma ve ayrıştırma:

* Yazma iş parçacığı ağdan verileri tüketir ve arabelleğe koyar.
* Ayrıştırma iş parçacığı, uygun veri yapılarını oluşturmaktan sorumludur.

Genellikle, ayrıştırma yalnızca ağdan veri bloklarını kopyalamaya kıyasla daha fazla zaman alır:

* Okuma iş parçacığı ayrıştırma iş parçacığının önüne alınır.
* Okuma iş parçacığı, ayrıştırma iş parçacığı için verileri depolamak üzere yavaşlıyor veya daha fazla bellek ayırmıştır.

En iyi performans için, sık duraklamalar ve daha fazla bellek ayırma arasında bir denge vardır.

Önceki sorunu çözmek için, `Pipe` ' ın veri akışını denetlemek için iki ayarı vardır:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> duraklatmaya çağrı yapmadan önce ne kadar verinin arabelleğe alınacağını belirler.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: okuyucunun `PipeWriter.FlushAsync` sürdürülmesine geçmeden önce ne kadar veri gözlemleyecek olduğunu belirler.

![ResumeWriterThreshold ve PauseWriterThreshold ile diyagram](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* @No__t-1 ' deki veri miktarı `PauseWriterThreshold` ' den kesişse, tamamlanmamış `ValueTask<FlushResult>` döndürür.
* @No__t, `ResumeWriterThreshold` ' den daha düşük hale geldiğinde 0 ' a tamamlanır.

Tek bir değer kullanılırsa oluşabilecek hızlı döngüyü engellemek için iki değer kullanılır.

### <a name="examples"></a>Örnekler

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Genellikle `async` ve `await` kullanılırken, zaman uyumsuz kod <xref:System.Threading.Tasks.TaskScheduler> üzerinde veya geçerli <xref:System.Threading.SynchronizationContext> üzerinde devam eder.

G/ç yaparken, g/ç 'nin gerçekleştirildiği noktada ayrıntılı denetime sahip olmak önemlidir. Bu denetim, CPU önbelleklerinin etkin bir şekilde yararlanmasını sağlar. Verimli önbelleğe alma, Web sunucuları gibi yüksek performanslı uygulamalar için kritik öneme sahiptir. <xref:System.IO.Pipelines.PipeScheduler>, zaman uyumsuz geri çağırmaların çalıştığı konum üzerinde denetim sağlar. Varsayılan olarak:

* Geçerli <xref:System.Threading.SynchronizationContext> kullanılır.
* @No__t-0 yoksa, geri çağırmaları çalıştırmak için iş parçacığı havuzunu kullanır.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[Pipescheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) , geri çağırmaları iş parçacığı havuzuna sıraya alan <xref:System.IO.Pipelines.PipeScheduler> uygulamasıdır. `PipeScheduler.ThreadPool` varsayılandır ve genellikle en iyi seçimdir. [Pipescheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) , kilitlenme gibi istenmeyen sonuçlara neden olabilir.

### <a name="pipe-reset"></a>Kanal sıfırlama

@No__t-0 nesnesini yeniden kullanmak sıklıkla etkilidir. Kanalı sıfırlamak için, hem `PipeReader` hem de `PipeWriter` tamamlandığında <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> ' i çağırın.

## <a name="pipereader"></a>Piypereader

<xref:System.IO.Pipelines.PipeReader>, arayanın adına belleği yönetir. @No__t-2 çağrıldıktan sonra **her zaman** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> ' i çağırın. Bu, `PipeReader` ' ın, Arayıcı bellekle izlenebilmesi için ne zaman yapıldığını bilmesini sağlar. @No__t-1 ' den döndürülen `ReadOnlySequence<byte>` yalnızca `PipeReader.AdvanceTo` ' a çağrı yapana kadar geçerlidir. @No__t-1 çağrıldıktan sonra `ReadOnlySequence<byte>` kullanmak geçersizdir.

`PipeReader.AdvanceTo` iki <xref:System.SequencePosition> bağımsız değişkeni alır:

* İlk bağımsız değişken, ne kadar bellek tüketildiğini belirler.
* İkinci bağımsız değişken, arabelleğin ne kadarının gözlemlendiğini belirler.

Verileri tüketilen olarak işaretlemek, kanalın belleği temel alınan arabellek havuzuna döndürebileceği anlamına gelir. Verileri gözlemlenen olarak işaretlemek, `PipeReader.ReadAsync` ' a yapılan bir sonraki çağrının ne olduğunu denetler. Her şeyi gözlemlenen olarak işaretlemek, kanala daha fazla veri yazılıncaya kadar `PipeReader.ReadAsync` ' a yapılan bir sonraki çağrının dönemeyeceği anlamına gelir. Diğer herhangi bir değer, `PipeReader.ReadAsync` ' a bir sonraki çağrının, gözlemlenen *ve* gözlemlenen verilerle hemen geri dönmesini sağlar, ancak daha önce tüketilen veriler.

### <a name="read-streaming-data-scenarios"></a>Akış verilerini okuma senaryoları

Akış verilerini okumaya çalışırken ortaya çıktı olan birkaç tipik desen vardır:

* Veri akışı verildiğinde, tek bir iletiyi ayrıştırır.
* Veri akışı verildiğinde, tüm kullanılabilir iletileri ayrıştırır.

Aşağıdaki örneklerde, bir `ReadOnlySequence<byte>` ' den iletileri ayrıştırmak için `TryParseMessage` yöntemi kullanılmaktadır. `TryParseMessage` tek bir iletiyi ayrıştırır ve ayrıştırılmış iletiyi arabelleğin kırpıldığı için giriş arabelleğini güncelleştirir. `TryParseMessage` .NET kapsamında değildir, bu, aşağıdaki bölümlerde kullanılan bir kullanıcı yazılmış yöntemidir.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Tek bir iletiyi okuyun

Aşağıdaki kod `PipeReader` ' dan tek bir ileti okur ve bunu çağırana döndürür.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Önceki kod:

* Tek bir ileti ayrıştırır.
* Tüketilen `SequencePosition` ' ı güncelleştirir ve kırpılan giriş arabelleğinin başlangıcına işaret etmek için `SequencePosition` ' i inceledi.

İki `SequencePosition` bağımsız değişkeni güncelleştirilir çünkü `TryParseMessage` ayrıştırılmış iletiyi giriş arabelleğinden kaldırır. Genellikle, arabellekteki tek bir ileti ayrıştırılırken, incelenen konum aşağıdakilerden biri olmalıdır:

* İletinin sonu.
* İleti bulunmazsa alınan arabelleğin sonu.

Tek ileti durumunun hata için en olası olasılığı vardır. Yanlış değerleri *incelenmeye* geçirmek, yetersiz bellek özel durumu veya sonsuz bir döngüye neden olabilir. Daha fazla bilgi için bu makaledeki [Pıpereader ortak sorunlar](#gotchas) bölümüne bakın.

### <a name="reading-multiple-messages"></a>Birden çok ileti okunuyor

Aşağıdaki kod `PipeReader` ' dan gelen tüm iletileri okur ve her biri üzerinde `ProcessMessageAsync` ' i çağırır.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>İptal Etme

`PipeReader.ReadAsync`:

* @No__t geçirmeyi destekler-0.
* Bir okuma beklemede olduğunda, `CancellationToken` iptal edilirse bir <xref:System.OperationCanceledException> oluşturur.
* , Bir özel durumun çıkarılmasını önleyen <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> aracılığıyla geçerli okuma işlemini iptal etmenin bir yolunu destekler. @No__t-0 ' a çağırmak, geçerli veya sonraki `PipeReader.ReadAsync` çağrısının `IsCanceled` ' i `true` ' e ayarlı <xref:System.IO.Pipelines.ReadResult> ' i döndürmesi sağlar. Bu, var olan okuma döngüsünü bozucu olmayan ve olağanüstü olmayan bir şekilde sonlandırmanız için yararlı olabilir.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Piypereader yaygın sorunlar

* @No__t-0 veya `examined` ' e yanlış değerler geçirmek, zaten okunan verileri okumaya neden olabilir.
* @No__t-0 ' ın incelenmesiyle geçirilmesi şu sonucu verebilir:

  * Durdurulmuş veriler
  * Veriler tüketilmemişse, büyük olasılıkla yetersiz bellek (OOM) özel durumu. Örneğin, her seferinde tek bir ileti işlenirken `PipeReader.AdvanceTo(position, buffer.End)`.

* @No__t-0 veya `examined` ' e yanlış değerler geçirilme sonsuz bir döngüye neden olabilir. Örneğin, @no__t `buffer.Start` ' i değişmemişse, yeni veriler alınmadan hemen önce `PipeReader.ReadAsync` ' ye yapılan bir sonraki çağrının geri dönmesini sağlar.
* @No__t-0 veya `examined` ' e yanlış değerler geçirilmesi sonsuz arabelleğe alma (nihai OOM) ile sonuçlanabilir.
* @No__t-0 ' i çağırdıktan sonra, `PipeReader.AdvanceTo` ' in kullanılması bellek bozulmasına yol açabilir (ücretsiz olarak kullanılabilir).
* @No__t-0 çağrlamaması, bellek sızıntısına yol açabilir.
* Veri kaybına neden olan arabellek sonuçlarını işlemeden önce <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> denetleniyor ve okuma mantığını çıkıyor. Döngü çıkış koşulunun `ReadResult.Buffer.IsEmpty` ve `ReadResult.IsCompleted` temelinde olması gerekir. Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.

#### <a name="problematic-code"></a>Sorunlu kod

❌ **veri kaybı**

@No__t-0, `IsCompleted` `true` olarak ayarlandığında verilerin son segmentini döndürebilir. Okuma döngüsünden çıkmadan önce bu verilerin okunmamasından dolayı veri kaybı olur.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **sonsuz döngü**

@No__t-0 `true` ise ve arabellekte hiç tam ileti yoksa, aşağıdaki mantık sonsuz döngüye neden olabilir.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Aynı sorunu içeren başka bir kod parçası aşağıda verilmiştir. @No__t-0 denetlemeden önce boş olmayan bir arabellek denetleniyor. @No__t-0 olduğundan, arabellekte hiç tam ileti yoksa sonsuza kadar döngüye alınır.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **beklenmeyen askı**

@No__t-2 konumunda `buffer.End` ile @no__t koşulsuz olarak çağırmanın tek bir ileti ayrıştırılırken askıda kalmasına neden olabilir. @No__t-0 ' a yapılan bir sonraki çağrı şu kadar döndürmez:

* Kanala yazılan daha fazla veri var.
* Ve yeni veriler daha önce incelendi.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **yetersiz bellek (OOM)**

Aşağıdaki koşullara göre aşağıdaki kod <xref:System.OutOfMemoryException> gerçekleşene kadar arabelleğe almayı sürdürür:

* En büyük ileti boyutu yok.
* @No__t-0 ' dan döndürülen veriler tam bir ileti yapmaz. Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB bir ileti) yazıldığı için, bu tam bir ileti yapmaz.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **bellek bozulması**

Arabelleği okuyan yardımcıları yazarken, `Advance` çağrılmadan önce döndürülen yükün kopyalanması gerekir. Aşağıdaki örnek, `Pipe` ' ın atılacağını ve bir sonraki işlem (okuma/yazma) için onu yeniden kullanabildiğinden belleği döndürür.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

@No__t-0, arayanın adına yazma arabelleğini yönetir. `PipeWriter` [@no__t uygular-2](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>`, ek arabellek kopyaları olmadan yazma işlemleri gerçekleştirmek için arabelleklere erişim sağlamak mümkün hale getirir.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Önceki kod:

* @No__t-1 kullanarak `PipeWriter` ' dan en az 5 baytlık bir arabellek ister.
* ASCII dizesi için bayt `"Hello"` ' yı döndürülen `Span<byte>` öğesine yazar.
* Arabelleğe kaç bayt yazıldığını belirten <xref:System.IO.Pipelines.PipeWriter.Advance%2A> ' ı çağırır.
* Temel cihaza bayt gönderen `PipeWriter` ' ı boşaltır.

Önceki yazma yöntemi `PipeWriter` tarafından sağlanmış arabellekleri kullanır. Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Mevcut arabelleği `PipeWriter` ' a kopyalar.
* @No__t-0, `Advance` ' i uygun şekilde çağırır ve <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> ' i çağırır.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>İptal Etme

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> <xref:System.Threading.CancellationToken> geçirmeyi destekler. @No__t-0 ' ın geçirilmesi, bir temizleme işlemi sırasında belirteç iptal edildiğinde, bir `OperationCanceledException` ile sonuçlanır. `PipeWriter.FlushAsync`, bir özel durum oluşturmadan geçerli temizleme işlemini <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> aracılığıyla iptal etmenin bir yolunu destekler. @No__t-0 ' a çağırmak, geçerli veya sonraki `PipeWriter.FlushAsync` veya `PipeWriter.WriteAsync` çağrısının `IsCanceled` ile `true` olarak ayarlanmış bir <xref:System.IO.Pipelines.FlushResult> döndürmesini sağlar. Bu, bozucu olmayan ve olağanüstü olmayan bir şekilde boşaltmayı Temizleme için yararlı olabilir.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter ortak sorunları

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>, en az istenen bellek miktarına sahip bir arabellek döndürür. Tam arabellek boyutlarını kabul **etmeyin** .
* Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.
* Daha fazla veri yazmaya devam etmek için <xref:System.IO.Pipelines.PipeWriter.Advance%2A> çağrıldıktan sonra yeni bir arabelleğin istenmesi gerekir. Daha önce edinilen arabelleğin üzerine yazılamaz.
* @No__t-0 veya `GetSpan` ' i çağırmak, `FlushAsync` ' ye yönelik tamamlanmamış bir çağrı olması durumunda güvenli değildir.
* @No__t-0 veya `CompleteAsync` ' i çağırmak, verilerin temizlenme sırasında bellek bozulmasına yol açabilir.

## <a name="iduplexpipe"></a>IDuplexPipe

@No__t-0, hem okumayı hem de yazmayı destekleyen türler için bir sözleşmedir. Örneğin, bir ağ bağlantısı `IDuplexPipe` ile temsil edilir.

 @No__t-1 ve bir `PipeWriter` içeren `Pipe` ' dan farklı olarak, `IDuplexPipe` tam çift yönlü bağlantının tek tarafını temsil eder. Bu, @no__t yazılmış olan ve `PipeReader` ' den okunmayacak anlamına gelir.

## <a name="streams"></a>Akışlar

Akış verilerini okurken veya yazarken genellikle seri hale getirici kullanarak verileri okur ve serileştirici kullanarak verileri yazın. Bu okuma ve yazma akışı API 'Lerinin çoğu `Stream` parametresine sahiptir. Bu mevcut API 'lerle tümleştirmeyi kolaylaştırmak için `PipeReader` ve `PipeWriter` <xref:System.IO.Pipelines.PipeReader.AsStream%2A> ' yi kullanıma sunar.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> `PipeReader` veya `PipeWriter` etrafında `Stream` uygulamasını döndürür.
