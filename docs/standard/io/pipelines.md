---
title: G/ç işlem hatları-.NET
description: .NET ' te ı/O işlem hatlarını verimli bir şekilde kullanmayı ve kodunuzda sorunlardan kaçınmak hakkında bilgi edinin.
ms.date: 08/27/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: a24d7f5c22c936cd3fd3fdc51f0f3ace56386574
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271990"
---
# <a name="systemiopipelines-in-net"></a>.NET 'teki System. ıO. işlem hatları

<xref:System.IO.Pipelines> , .NET ortamında yüksek performanslı g/ç 'yi daha kolay hale getirmek için tasarlanan yeni bir kitaplıktır. Bu, tüm .NET uygulamalarında çalışacak .NET Standard hedefleme bir kitaplıktır.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>System. ıO. hatlarını çözme sorunu

<!-- corner case doesn't MT (machine translate)   -->
Akış verilerini ayrıştırmaya yönelik uygulamalar, çok sayıda özel ve olağandışı kod akışına sahip ortak koddan oluşur. Ortak ve özel durum kodu karmaşık ve devam etmek zordur.

`System.IO.Pipelines` Şu şekilde tasarlanmıştır:

* Akış verilerinin yüksek performans ayrıştırması vardır.
* Kod karmaşıklığını azaltın.

Aşağıdaki kod, bir istemciden satır sınırlı iletileri (ile ayrılmış) alan bir TCP sunucusu için tipik bir noktadır `'\n'` :

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

* Tüm ileti (satır sonu), için tek bir çağrıda alınmayabilir `ReadAsync` .
* Sonucu yok sayılıyor `stream.ReadAsync` . `stream.ReadAsync` ne kadar veri okunduğunu döndürür.
* Birden çok satırın tek bir çağrıda okunduğu durumu işlemez `ReadAsync` .
* `byte`Her okunan bir diziyi ayırır.

Yukarıdaki sorunları onarmak için aşağıdaki değişiklikler gereklidir:

* Yeni bir satır bulunana kadar gelen verileri arabelleğe koyun.
* Arabellekte döndürülen tüm satırları ayrıştırın.
* Satır 1 KB 'den büyük (1024 bayt) olabilir. Bu kodun, arabelleğin içindeki tamamlanma satırına sığması için sınırlayıcı bulunana kadar giriş arabelleğini yeniden boyutlandırması gerekir.

  * Arabellek yeniden boyutlandırılırsa, girişte daha uzun çizgiler göründüğü sürece daha fazla arabellek kopyası yapılır.
  * Harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.

* Belleği sürekli ayırmayı önlemek için arabellek havuzu kullanmayı düşünün.
* Aşağıdaki kod bu sorunlardan bazılarını ele alınmaktadır:

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez. Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir. `System.IO.Pipelines` Bu tür bir kodu daha kolay yazmak için tasarlandı.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Kapatıldığı

<xref:System.IO.Pipelines.Pipe>Sınıf, bir çift oluşturmak için kullanılabilir `PipeWriter/PipeReader` . İçine yazılan tüm veriler `PipeWriter` ' de kullanılabilir `PipeReader` :

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Kanal temel kullanımı

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

İki döngü vardır:

* `FillPipeAsync` öğesinden okur `Socket` ve öğesine yazar `PipeWriter` .
* `ReadPipeAsync` öğesinden okur `PipeReader` ve gelen satırları ayrıştırır.

Ayrılmış açık arabellek yok. Tüm arabellek yönetimi, `PipeReader` ve uygulamalarına Temsilcili `PipeWriter` . Arabellek yönetimi için temsilci seçme, kodun yalnızca iş mantığına odaklanılmasını kolaylaştırır.

İlk döngüde:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> , temel alınan yazıcıya bellek almak için çağrılır.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> , `PipeWriter` arabelleğe ne kadar veri yazıldığını bildirmek için çağırılır.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> , verileri için kullanılabilir hale getirmek üzere çağırılır `PipeReader` .

İkinci döngüde, `PipeReader` tarafından yazılan arabellekleri kullanır `PipeWriter` . Arabellekler yuvadan gelir. Çağrısı `PipeReader.ReadAsync` :

* <xref:System.IO.Pipelines.ReadResult>İki önemli bilgi parçasını içeren bir döndürür:

  * Biçiminde okunan veriler `ReadOnlySequence<byte>` .
  * `IsCompleted`Verilerin sonuna (EOF) ulaşıldığını gösteren bir Boole değeri.

Satır sonu (EOL) sınırlayıcısı bulduktan ve satırı ayrıştırdıktan sonra:

* Mantık, zaten işlenmiş olan öğeleri atlamak için arabelleği işler.
* `PipeReader.AdvanceTo` ne `PipeReader` kadar veri tüketiğini ve incelendiğini söylemek için çağırılır.

Okuyucu ve yazıcı döngüleri, çağırarak biter `Complete` . `Complete` temeldeki kanalın ayrılan belleği serbest bırakmasına olanak tanır.

### <a name="backpressure-and-flow-control"></a>Arka basınç ve akış denetimi

İdeal olarak, birlikte iş okuma ve ayrıştırma:

* Yazma iş parçacığı ağdan verileri tüketir ve arabelleğe koyar.
* Ayrıştırma iş parçacığı, uygun veri yapılarını oluşturmaktan sorumludur.

Genellikle, ayrıştırma yalnızca ağdan veri bloklarını kopyalamaya kıyasla daha fazla zaman alır:

* Okuma iş parçacığı ayrıştırma iş parçacığının önüne alınır.
* Okuma iş parçacığı, ayrıştırma iş parçacığı için verileri depolamak üzere yavaşlıyor veya daha fazla bellek ayırmıştır.

En iyi performans için, sık duraklamalar ve daha fazla bellek ayırma arasında bir denge vardır.

Önceki sorunu çözmek için, `Pipe` veri akışını denetlemek üzere iki ayarı vardır:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Duraklatma çağrılarına önce ne kadar veri ara belleğe alınacağını belirler <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Okuyucunun sürdürülmeye yönelik çağrılardan önce ne kadar veri gözlemleyecek olduğunu belirler `PipeWriter.FlushAsync` .

![ResumeWriterThreshold ve PauseWriterThreshold ile diyagram](media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* `ValueTask<FlushResult>`Kesiştiği içindeki veri miktarı için bir tamamlanmamış döndürür `Pipe` `PauseWriterThreshold` .
* Daha `ValueTask<FlushResult>` düşük hale geldiğinde tamamlanır `ResumeWriterThreshold` .

Tek bir değer kullanılırsa oluşabilecek hızlı döngüyü engellemek için iki değer kullanılır.

### <a name="examples"></a>Örnekler

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Genellikle ve kullanılırken `async` `await` , zaman uyumsuz kod, ya da geçerli bir üzerinde devam eder <xref:System.Threading.Tasks.TaskScheduler> <xref:System.Threading.SynchronizationContext> .

G/ç yaparken, g/ç 'nin gerçekleştirildiği noktada ayrıntılı denetime sahip olmak önemlidir. Bu denetim, CPU önbelleklerinin etkin bir şekilde yararlanmasını sağlar. Verimli önbelleğe alma, Web sunucuları gibi yüksek performanslı uygulamalar için kritik öneme sahiptir. <xref:System.IO.Pipelines.PipeScheduler> zaman uyumsuz geri çağırmaların çalıştığı konum üzerinde denetim sağlar. Varsayılan olarak:

* Geçerli, <xref:System.Threading.SynchronizationContext> kullanılır.
* Hayır ise `SynchronizationContext` , geri çağırmaları çalıştırmak için iş parçacığı havuzunu kullanır.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

[Pipescheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) , <xref:System.IO.Pipelines.PipeScheduler> iş parçacığı havuzuna geri çağırmaları sıraya alan uygulamasıdır. `PipeScheduler.ThreadPool` Varsayılan ve genellikle en iyi seçenektir. [Pipescheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) , kilitlenme gibi istenmeyen sonuçlara neden olabilir.

### <a name="pipe-reset"></a>Kanal sıfırlama

Nesneyi yeniden kullanmak sıklıkla etkilidir `Pipe` . Kanalı sıfırlamak için <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> hem hem de `PipeReader` tamamlandığında çağırın `PipeWriter` .

## <a name="pipereader"></a>Piypereader

<xref:System.IO.Pipelines.PipeReader> arayan adına belleği yönetir. Çağrıldıktan sonra **her zaman** çağırın <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> . Bu, `PipeReader` çağıranın bellek ile ne zaman yapıldığını, böylece izlenebilmesini sağlar. `ReadOnlySequence<byte>`Döndürülen öğesinden `PipeReader.ReadAsync` yalnızca öğesine çağrı yapılıncaya kadar geçerlidir `PipeReader.AdvanceTo` . Çağrıldıktan sonra kullanım geçersizdir `ReadOnlySequence<byte>` `PipeReader.AdvanceTo` .

`PipeReader.AdvanceTo` iki <xref:System.SequencePosition> bağımsız değişken alır:

* İlk bağımsız değişken, ne kadar bellek tüketildiğini belirler.
* İkinci bağımsız değişken, arabelleğin ne kadarının gözlemlendiğini belirler.

Verileri tüketilen olarak işaretlemek, kanalın belleği temel alınan arabellek havuzuna döndürebileceği anlamına gelir. Verileri gözlemlenen olarak işaretlemek, sonraki çağrının ne olduğunu denetler `PipeReader.ReadAsync` . Her şeyi gözlemlenen olarak işaretlemek, bir sonraki çağrının `PipeReader.ReadAsync` kanala yazılmış daha fazla veri olana kadar dönemeyeceği anlamına gelir. Diğer herhangi bir değer, sonraki çağrının `PipeReader.ReadAsync` gözlemlenen *ve* gözlemlenen verilerle hemen döndürülmesini sağlar, ancak daha önce tüketilen verileri değil.

### <a name="read-streaming-data-scenarios"></a>Akış verilerini okuma senaryoları

Akış verilerini okumaya çalışırken ortaya çıktı olan birkaç tipik desen vardır:

* Veri akışı verildiğinde, tek bir iletiyi ayrıştırır.
* Veri akışı verildiğinde, tüm kullanılabilir iletileri ayrıştırır.

Aşağıdaki örneklerde, ' `TryParseMessage` dan ileti ayrıştırma yöntemi kullanılmaktadır `ReadOnlySequence<byte>` . `TryParseMessage` tek bir iletiyi ayrıştırır ve ayrıştırılmış iletiyi arabellekten kırpmak için giriş arabelleğini güncelleştirin. `TryParseMessage` , .NET 'in bir parçası değildir, aşağıdaki bölümlerde kullanılan bir kullanıcı yazılmış yöntemidir.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Tek bir iletiyi okuyun

Aşağıdaki kod, bir öğesinden tek bir ileti okur `PipeReader` ve bunu çağırana döndürür.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

Yukarıdaki kod:

* Tek bir ileti ayrıştırır.
* Tüketilen `SequencePosition` ve incelenen, `SequencePosition` kırpılan giriş arabelleğinin başlangıcını işaret eden şekilde güncelleştirir.

İki `SequencePosition` bağımsız değişken güncelleştirilir çünkü bu, `TryParseMessage` ayrıştırılmış iletiyi giriş arabelleğinden kaldırır. Genellikle, arabellekteki tek bir ileti ayrıştırılırken, incelenen konum aşağıdakilerden biri olmalıdır:

* İletinin sonu.
* İleti bulunmazsa alınan arabelleğin sonu.

Tek ileti durumunun hata için en olası olasılığı vardır. Yanlış değerleri *incelenmeye* geçirmek, yetersiz bellek özel durumu veya sonsuz bir döngüye neden olabilir. Daha fazla bilgi için bu makaledeki [Pıpereader ortak sorunlar](#gotchas) bölümüne bakın.

### <a name="reading-multiple-messages"></a>Birden çok ileti okunuyor

Aşağıdaki kod, `PipeReader` her bir üzerinde ve çağrılarındaki tüm iletileri okur `ProcessMessageAsync` .

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a>İptal

`PipeReader.ReadAsync`:

* , Geçişini destekler <xref:System.Threading.CancellationToken> .
* Bir okuma beklemede olduğunda, bir iptal edilirse bir oluşturur <xref:System.OperationCanceledException> `CancellationToken` .
* <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, Bir özel durumun çıkarılmasını engelleyen geçerli okuma işlemini iptal etmek için bir yol destekler. Çağırma `PipeReader.CancelPendingRead` , geçerli veya sonraki çağrısının ' `PipeReader.ReadAsync` a ayarlanmış olarak dönüşmesine neden olur <xref:System.IO.Pipelines.ReadResult> `IsCanceled` `true` . Bu, var olan okuma döngüsünü bozucu olmayan ve olağanüstü olmayan bir şekilde sonlandırmanız için yararlı olabilir.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Piypereader yaygın sorunlar

* Yanlış değerleri veya ' a geçirmek, `consumed` `examined` zaten okuma verilerinin okunmasına neden olabilir.
* `buffer.End`İncelenen şekilde geçirme şu şekilde olabilir:

  * Durdurulmuş veriler
  * Veriler tüketilmemişse, büyük olasılıkla yetersiz bellek (OOM) özel durumu. Örneğin, `PipeReader.AdvanceTo(position, buffer.End)` arabellekteki bir anda tek bir ileti işlenirken.

* Yanlış değerleri ' a geçirme `consumed` veya `examined` sonsuz bir döngüye neden olabilir. Örneğin, `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` henüz değiştirilmediyse, `PipeReader.ReadAsync` Yeni veri ulaşmadan hemen önce geri dönmesi için bir sonraki çağrıya neden olur.
* Yanlış değerleri ' a geçirme `consumed` veya `examined` sonsuz arabelleğe alma (NIHAI OOM) ile sonuçlanabilir.
* Çağrıldıktan `ReadOnlySequence<byte>` sonra kullanılması, `PipeReader.AdvanceTo` bellek bozulmasına yol açabilir (ücretsiz olarak kullanabilirsiniz).
* Çağrı başarısız `PipeReader.Complete/CompleteAsync` olabilir ve bellek sızıntısına yol açabilir.
* <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType>Veri kaybına neden olan arabellek sonuçlarını işlemeden önce okuma mantığı denetleniyor ve çıkılıyor. Döngü çıkış koşulunun ve tabanlı olması gerekir `ReadResult.Buffer.IsEmpty` `ReadResult.IsCompleted` . Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.

#### <a name="problematic-code"></a>Sorunlu kod

❌**Veri kaybı**

, `ReadResult` Olarak ayarlandığında verilerin son segmentini döndürebilir `IsCompleted` `true` . Okuma döngüsünden çıkmadan önce bu verilerin okunmamasından dolayı veri kaybı olur.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Sonsuz döngü**

Aşağıdaki mantık,, `Result.IsCompleted` `true` ancak arabellekte hiç tamamlanmamış bir ileti varsa sonsuz döngüye neden olabilir.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Aynı sorunu içeren başka bir kod parçası aşağıda verilmiştir. Denetlemeden önce boş olmayan bir arabellek denetleniyor `ReadResult.IsCompleted` . Bir içinde olduğu için `else if` , arabellekte hiç bir ileti yoksa sonsuza kadar döngüye alınır.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Beklenmeyen askı**

Konumda koşullu olarak `PipeReader.AdvanceTo` çağırmanın `buffer.End` `examined` tek bir ileti ayrıştırılırken askıda kalmasına neden olabilir. Sonraki çağrısı şu `PipeReader.AdvanceTo` kadar geri dönemeyecek:

* Kanala yazılan daha fazla veri var.
* Ve yeni veriler daha önce incelendi.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Yetersiz bellek (OOM)**

Aşağıdaki koşullara göre aşağıdaki kod arabelleğe alma işlemi gerçekleşene kadar devam eder <xref:System.OutOfMemoryException> :

* En büyük ileti boyutu yok.
* Öğesinden döndürülen veriler, `PipeReader` bir ileti yapmaz. Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB bir ileti) yazıldığı için, bu tam bir ileti yapmaz.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Bellek bozulması**

Arabelleği okuyan yardımcıları yazarken, çağrılmadan önce döndürülen tüm yükün kopyalanması gerekir `Advance` . Aşağıdaki örnek, atılan belleği döndürür ve bir `Pipe` sonraki işlem (okuma/yazma) için onu tekrar kullanabilir.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

<xref:System.IO.Pipelines.PipeWriter>Arayan adına yazmak için arabellekleri yönetir. `PipeWriter` uygular [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) . `IBufferWriter<byte>` ek arabellek kopyaları olmadan yazma işlemleri gerçekleştirmek için arabelleklere erişim sağlamak mümkün hale gelir.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

Önceki kod:

* Kullanarak en az 5 baytlık bir arabellek ister `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> .
* ASCII dizesinin bayt sayısını `"Hello"` döndürülen öğesine yazar `Memory<byte>` .
* <xref:System.IO.Pipelines.PipeWriter.Advance%2A>Arabelleğe kaç bayt yazıldığını belirten çağrılar.
* , `PipeWriter` Baytları temeldeki cihaza gönderen öğesini temizler.

Önceki yazma yöntemi, tarafından sağlanmış arabellekleri kullanır `PipeWriter` . Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :

* Varolan arabelleği öğesine kopyalar `PipeWriter` .
* `GetSpan` `Advance` Uygun ve çağrılar için çağrılar <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a>İptal

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> , geçişini destekler <xref:System.Threading.CancellationToken> . Bekleyen bir `CancellationToken` `OperationCanceledException` Temizleme işlemi varken belirteç iptal edilirse bir sonuçları bir ile geçirme. `PipeWriter.FlushAsync` , özel durum oluşturmadan geçerli temizleme işlemini iptal etmenin bir yolunu destekler <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> . Çağırma `PipeWriter.CancelPendingFlush` , geçerli veya sonraki çağrıya, `PipeWriter.FlushAsync` veya olarak `PipeWriter.WriteAsync` ayarlanmış olarak dönüşmesine neden olur <xref:System.IO.Pipelines.FlushResult> `IsCanceled` `true` . Bu, bozucu olmayan ve olağanüstü olmayan bir şekilde boşaltmayı Temizleme için yararlı olabilir.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter ortak sorunları

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> en az istenen bellek miktarına sahip bir arabellek döndürür. Tam arabellek boyutlarını kabul **etmeyin** .
* Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.
* <xref:System.IO.Pipelines.PipeWriter.Advance%2A>Daha fazla veri yazmaya devam etmek için çağrıldıktan sonra yeni bir arabellek istenmesi gerekir. Daha önce edinilen arabelleğin üzerine yazılamaz.
* `GetMemory` `GetSpan` Eksik bir çağrı olduğu için veya çağrısı sırasında `FlushAsync` güvenli değildir.
* `Complete` `CompleteAsync` Verilerin temizlenme sırasında veya boşaltılmasından sonra bellek bozulmasına yol açabilir.

## <a name="iduplexpipe"></a>IDuplexPipe

, <xref:System.IO.Pipelines.IDuplexPipe> Hem okumayı hem de yazmayı destekleyen türler için bir sözleşmedir. Örneğin, bir ağ bağlantısı bir tarafından temsil edilir `IDuplexPipe` .

 `Pipe`Ve içeren öğelerinden farklı olarak `PipeReader` `PipeWriter` , `IDuplexPipe` tam çift yönlü bağlantının tek tarafını temsil eder. Bu, üzerine yazılan ve ' `PipeWriter` den okunmayacağı anlamına gelir `PipeReader` .

## <a name="streams"></a>Akışlar

Akış verilerini okurken veya yazarken genellikle seri hale getirici kullanarak verileri okur ve serileştirici kullanarak verileri yazın. Bu okuma ve yazma akışı API 'Lerinin çoğu bir `Stream` parametreye sahiptir. Bu var olan API 'lerle tümleştirmeyi kolaylaştırmak `PipeReader` ve `PipeWriter` bir yöntemi ortaya çıkarmak için <xref:System.IO.Pipelines.PipeReader.AsStream%2A> . <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>`Stream`veya etrafında bir uygulama döndürür `PipeReader` `PipeWriter` .

### <a name="stream-example"></a>Akış örneği

`PipeReader` ve `PipeWriter` örnekleri `Create` bir nesne verilen statik yöntemler <xref:System.IO.Stream> ve isteğe bağlı olarak ilgili oluşturma seçenekleri kullanılarak oluşturulabilir.

<xref:System.IO.Pipelines.StreamPipeReaderOptions>Aşağıdaki parametrelerle örnek oluşturma üzerinde denetime izin ver `PipeReader` :

- <xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> , havuzdan belleği yeniden boyutlandırdığınızda kullanılan bayt cinsinden en düşük arabellek boyutu ve varsayılan değer olarak kullanılır `4096` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> bayrak, işlem tamamlandıktan sonra temeldeki akışın açık bırakılıp başlatılmayacağını belirler `PipeReader` ve varsayılan olarak öğesine ayarlanır `false` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> Yeni bir arabelleğin ayrılmadan önce arabellekteki kalan baytların eşiğini temsil eder ve varsayılan olarak değerine ayarlanır `1024` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType>`MemoryPool<byte>`bellek ayrılırken kullanılır ve varsayılan olarak öğesine ayarlanır `null` .

<xref:System.IO.Pipelines.StreamPipeWriterOptions>Aşağıdaki parametrelerle örnek oluşturma üzerinde denetime izin ver `PipeWriter` :

- <xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> bayrak, işlem tamamlandıktan sonra temeldeki akışın açık bırakılıp başlatılmayacağını belirler `PipeWriter` ve varsayılan olarak öğesine ayarlanır `false` .
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> , bellekten bellek oluştururken kullanılacak en düşük arabellek boyutunu temsil eder <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> `4096` .
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType>`MemoryPool<byte>`bellek ayrılırken kullanılır ve varsayılan olarak öğesine ayarlanır `null` .

> [!IMPORTANT]
> `PipeReader` `PipeWriter` Yöntemlerini kullanarak ve örnekleri kullanırken `Create` , nesne ömrünü göz önünde bulundurmanız gerekir `Stream` . Okuyucu veya yazıcı ile işiniz bittiğinde akışa erişmeniz gerekiyorsa, `LeaveOpen` oluşturma seçeneklerinde bayrağını olarak ayarlamanız gerekir `true` . Aksi takdirde, akış kapatılacak.

Aşağıdaki kod, `PipeReader` `PipeWriter` bir akıştan yöntemleri kullanarak ve örneklerinin oluşturulmasını gösterir `Create` .

:::code language="csharp" source="snippets/pipelines/Program.cs":::

Uygulama bir <xref:System.IO.StreamReader> akış olarak *lorem-ipsum.txt* dosyayı okumak için bir kullanır. , <xref:System.IO.FileStream> <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> Bir nesneyi örnekleyen öğesine geçirilir `PipeReader` . Konsol uygulaması daha sonra kendi standart çıkış akışını kullanarak geçirir <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> . Örnek [iptali](#cancellation)destekler.
