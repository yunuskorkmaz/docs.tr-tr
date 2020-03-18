---
title: G/Ç boru hatları - .NET
description: .NET'te G/Ç ardışık hatlarını verimli bir şekilde nasıl kullanacağınızı ve kodunuzdaki sorunları nasıl önleyeceğimiz öğrenin.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: b18b2bf31787fa58e614cd4f057fba9037fe8ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627558"
---
# <a name="systemiopipelines-in-net"></a>System.IO.Pipelines in .NET

<xref:System.IO.Pipelines>.NET'te yüksek performanslı G/Ç yapmayı kolaylaştırmak için tasarlanmış yeni bir kitaplıktır. Tüm .NET uygulamalarında çalışan .NET Standard'ı hedefleyen bir kitaplık.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>System.IO.Pipelines hangi sorunu çözer?

<!-- corner case doesn't MT (machine translate)   -->
Akış verilerini ayrıştıran uygulamalar, birçok özel ve sıradışı kod akışına sahip ortak kodlardan oluşur. Ortak plaka ve özel servis kodu karmaşıktır ve bakımı zordur.

`System.IO.Pipelines`için mimar oldu:

* Akış verisi için yüksek performanslı ayrışma vardır.
* Kod karmaşıklığını azaltın.

Aşağıdaki kod, istemciden satır sınırlandırAn `'\n'`(sınırlandırılabilen) iletileri alan bir TCP sunucusu için tipiktir:

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Önceki kodun çeşitli sorunları vardır:

* İletinin tamamı (satır sonu) `ReadAsync`tek bir aramada alınmayabilir.
* Sonucu görmezden `stream.ReadAsync`geliyor. `stream.ReadAsync`ne kadar veri okundugünü döndürür.
* Tek `ReadAsync` bir aramada birden çok satırın okunduğu durumu işlemez.
* Her okuma `byte` ile bir dizi ayırır.

Önceki sorunları gidermek için aşağıdaki değişiklikler gereklidir:

* Yeni bir satır bulunana kadar gelen verileri arabelleğe alan.
* Arabellekte döndürülen tüm satırları ayrıştırın.
* Bu satır 1 KB (1024 bayt) daha büyük olması mümkündür. Kodun, arabellek içindeki tam satırı sığdırmak için sınır dışı layıcı bulunana kadar giriş arabelleği yeniden boyutlandırılması gerekir.

  * Arabellek yeniden boyutlandırılırsa, girişte daha uzun satırlar göründükçe daha fazla arabellek kopyası yapılır.
  * Boşa harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.

* Belleği tekrar tekrar ayırmamak için arabellek birleştirme yi kullanmayı düşünün.
* Aşağıdaki kod, bu sorunlardan bazılarını giderer:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez. Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir. `System.IO.Pipelines`bu tür kod yazmayı kolaylaştırmak için tasarlanmıştır.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Boru

Sınıf <xref:System.IO.Pipelines.Pipe> bir `PipeWriter/PipeReader` çift oluşturmak için kullanılabilir. Tüm veriler içinde `PipeWriter` mevcuttur: `PipeReader`

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Boru temel kullanımı

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

İki döngü vardır:

* `FillPipeAsync`dan okur `Socket` ve yazıyor `PipeWriter`.
* `ReadPipeAsync``PipeReader` ve gelen satırları parses okur.

Ayrılmış açık arabellek yok. Tüm arabellek yönetimi ve `PipeReader` `PipeWriter` uygulamalara devredilir. Arabellek yönetimini adeleyen, kod tüketen lerin yalnızca iş mantığına odaklanmasını kolaylaştırır.

İlk döngüde:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>altta yatan yazardan bellek almak için çağrılır.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>arabelleğe `PipeWriter` ne kadar veri yazıldığını söylemek için çağrılır.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>verileri kullanılabilir hale getirmek için `PipeReader`denir.

İkinci döngüde, `PipeReader` `PipeWriter`'' tarafından yazılan arabellekleri tüketir. Arabellekler yuvadan geliyor. Çağrı: `PipeReader.ReadAsync`

* İki <xref:System.IO.Pipelines.ReadResult> önemli bilgi parçasını içeren bir verir:

  * Şeklinde okunan veriler `ReadOnlySequence<byte>`.
  * Verilerin sonuna `IsCompleted` (EOF) ulaşılıp ulaşıldığını gösteren bir boolean.

Satır sonu (EOL) delimiter bulma ve çizgi ayrıştırma sonra:

* Mantık, arabelleği zaten işlenmiş olanı atlamak için işler.
* `PipeReader.AdvanceTo``PipeReader` ne kadar veri tüketildiğini ve incelendiğini söylemek için çağrılır.

Okuyucu ve yazar döngüleri `Complete`arayarak sona erer. `Complete`altta yatan Boru'nun ayırdEttiği belleği serbest bırakmasına olanak tanır.

### <a name="backpressure-and-flow-control"></a>Geri basınç ve akış kontrolü

İdeal olarak, okuma ve ayrıştma birlikte çalışır:

* Yazma iş parçacığı ağdan gelen verileri tüketir ve arabelleklere koyar.
* Ayrıştırma iş parçacığı, uygun veri yapılarının oluşturulmasından sorumludur.

Genellikle, ayrıştma, ağdaki veri bloklarını kopyalamaktan daha fazla zaman alır:

* Okuma iş parçacığı ayrışma iş parçacığının önüne geçer.
* Okuma iş parçacığı, ayrıştma iş parçacığı için verileri depolamak için daha fazla bellek ayırmak veya yavaşlatmak zorundadır.

En iyi performans için, sık duraklar ve daha fazla bellek ayırma arasında bir denge vardır.

Önceki sorunu çözmek için, `Pipe` veri akışını denetlemek için iki ayarı vardır:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> Duraklatma çağrıları ndan önce ne kadar veri arabelleğe alınması gerektiğini belirler.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Okuyucunun devam etmek için `PipeWriter.FlushAsync` yapılan aramadan önce ne kadar veri gözlemlemeyi gerektiğini belirler.

![ResumeWriterThreshold ve PauseWriterThreshold ile Diyagram](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* `Pipe` Haçlar `PauseWriterThreshold`veri miktarı tamamlanmamış `ValueTask<FlushResult>` bir verir.
* 'den `ValueTask<FlushResult>` daha `ResumeWriterThreshold`düşük olduğunda tamamlar.

Bir değer kullanıldığında oluşabilir hızlı bisiklet, önlemek için iki değer kullanılır.

### <a name="examples"></a>Örnekler

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Genellikle kullanırken `async` `await`ve , asynchronous kodu bir <xref:System.Threading.Tasks.TaskScheduler> veya geçerli <xref:System.Threading.SynchronizationContext>üzerinde devam eder.

G/Ç yaparken, G/Ç'nin nerede gerçekleştirildiği üzerinde ince taneli denetime sahip olmak önemlidir. Bu denetim, CPU önbelleklerinden etkin bir şekilde yararlanmanızı sağlar. Verimli önbelleğe alma, web sunucuları gibi yüksek performanslı uygulamalar için çok önemlidir. <xref:System.IO.Pipelines.PipeScheduler>eşzamanlı geri aramaların nerede çalıştığı üzerinde denetim sağlar. Varsayılan olarak:

* Akım <xref:System.Threading.SynchronizationContext> kullanılır.
* Yoksa, `SynchronizationContext`geri aramaları çalıştırmak için iş parçacığı havuzunu kullanır.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) iş <xref:System.IO.Pipelines.PipeScheduler> parçacığı havuzuna geri aramaları sıralayan bir uygulamadır. `PipeScheduler.ThreadPool`varsayılan ve genellikle en iyi seçimdir. [PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) kilitlenmeler gibi istenmeyen sonuçlara neden olabilir.

### <a name="pipe-reset"></a>Boru sıfırlama

Nesneyi `Pipe` yeniden kullanmak genellikle etkilidir. Boruyu sıfırlamak için, hem `PipeReader` `PipeWriter` boru hem de tam olduğunda arayın. <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A>

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader>arayan adına belleği yönetir. **Her** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> zaman <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>aradıktan sonra arayın. Bu, `PipeReader` arayanın bellekle ne zaman işlenirse izlenebileceğini bilmesini sağlar. İade `ReadOnlySequence<byte>` edilen `PipeReader.ReadAsync` den yalnızca arama `PipeReader.AdvanceTo`gelene kadar geçerlidir. Aradıktan `PipeReader.AdvanceTo`sonra kullanmak `ReadOnlySequence<byte>` yasak.

`PipeReader.AdvanceTo`iki <xref:System.SequencePosition> bağımsız değişken alır:

* İlk bağımsız değişken ne kadar bellek tüketilmeyi belirler.
* İkinci bağımsız değişken, arabelleğe ne kadarının gözlendiğini belirler.

Verileri tüketilen olarak işaretleme, borunun belleği alttaki arabellek havuzuna döndürebileceği anlamına gelir. Verileri gözlenen olarak işaretleme, `PipeReader.ReadAsync` bir sonraki çağrının ne işe yaradığı yla ilgili denetimleri yapar. Her şeyi gözlenen şekilde işaretlemek, bir sonraki çağrının boruya `PipeReader.ReadAsync` daha fazla veri yazılana kadar geri dönmeyeceği anlamına gelir. Başka bir değer, gözlenen `PipeReader.ReadAsync` *ve* gözlenmeyen verilerle hemen dönmek için bir sonraki çağrıyı yapar, ancak zaten tüketilen veriler.

### <a name="read-streaming-data-scenarios"></a>Akış veri senaryolarını okuma

Akış verilerini okumaya çalışırken ortaya çıkan birkaç tipik desen vardır:

* Veri akışı göz önüne alındığında, tek bir iletiyi ayrıştın.
* Bir veri akışı göz önüne alındığında, kullanılabilir tüm iletileri ayrıştın.

Aşağıdaki örnekler, `TryParseMessage` bir `ReadOnlySequence<byte>`. `TryParseMessage`tek bir iletiyi ayrıştırır ve arabellekten ayrıştırılan iletiyi kırpmak için giriş arabelleği güncelleştirin. `TryParseMessage`.NET'in bir parçası değildir, aşağıdaki bölümlerde kullanılan kullanıcı yazılı bir yöntemdir.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Tek bir iletiyi okuma

Aşağıdaki kod a'dan `PipeReader` tek bir ileti okur ve arayana döndürür.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Yukarıdaki kod:

* Tek bir iletiyi ayrışdırır.
* Kırpılan giriş arabelleği başlangıcına işaret etmek için tüketilen `SequencePosition` ve incelenen `SequencePosition` güncelleştirmeler.

Ayrıştırılmış iletiyi giriş arabelleğinden `SequencePosition` `TryParseMessage` kaldırdığından, iki bağımsız değişken güncelleştirilir. Genellikle, arabellekten tek bir ileti ayrıştırırken, incelenen konum aşağıdakilerden biri olmalıdır:

* İletinin sonu.
* İleti bulunamadıysa alınan arabelleğe son.

Tek ileti örneği en fazla hata potansiyeline sahiptir. Yanlış değerlerin *incelenmesi,* bellek dışı bir özel durum veya sonsuz bir döngüyle sonuçlanabilir. Daha fazla bilgi için bu makaledeki [PipeReader ortak sorunlar](#gotchas) bölümüne bakın.

### <a name="reading-multiple-messages"></a>Birden çok ileti okuma

Aşağıdaki kod a'dan `PipeReader` gelen tüm `ProcessMessageAsync` iletileri okur ve her birinde çağrılar.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>İptal

`PipeReader.ReadAsync`:

* Bir <xref:System.Threading.CancellationToken>.
* Bekleyen bir <xref:System.OperationCanceledException> okuma `CancellationToken` varken iptal edilirse atar.
* Bir özel durum yükseltmeyi önleyen <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>geçerli okuma işlemini iptal etmenin bir yolunu destekler. `PipeReader.CancelPendingRead` Arama, geçerli veya bir `PipeReader.ReadAsync` sonraki <xref:System.IO.Pipelines.ReadResult> çağrının bir 'e `IsCanceled` ayarlanmış bir 'e döndürülmeye neden `true`olur. Bu, varolan okuma döngüsünün yıkıcı olmayan ve istisnai olmayan bir şekilde durdurulması için yararlı olabilir.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader yaygın sorunlar

* Yanlış değerlerin okunması `consumed` `examined` veya okunmasıyla sonuçlanabilir.
* İncelendiği gibi geçmek `buffer.End` şu neden olabilir:

  * Durmuş veriler
  * Veriler tüketilmezse, büyük olasılıkla bellek dışı (OOM) özel durumu. Örneğin, `PipeReader.AdvanceTo(position, buffer.End)` arabellekten bir seferde tek bir ileti işlenirken.

* Yanlış değerlerin sonsuz `consumed` `examined` bir döngüye geçirilmesi veya bunun sonucu olabilir. Örneğin, `PipeReader.AdvanceTo(buffer.Start)` değişmediyse, `buffer.Start` bir sonraki aramanın `PipeReader.ReadAsync` yeni veriler gelmeden hemen önce geri dönmesine neden olur.
* Yanlış değerlerin geçirilmesi `consumed` `examined` veya sonsuz arabelleğe alma (nihai OOM) neden olabilir.
* Aramadan `ReadOnlySequence<byte>` `PipeReader.AdvanceTo` sonra kullanmak bellek bozulmasına neden olabilir (ücretsiz sonra kullanın).
* Aramanın `PipeReader.Complete/CompleteAsync` başarısız olması bellek sızıntısına neden olabilir.
* Arabelleği işlemeden önce okuma mantığını denetlemek <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> ve çıkmak veri kaybına neden olabilir. Döngü çıkış durumu temel `ReadResult.Buffer.IsEmpty` alınmalıdır ve `ReadResult.IsCompleted`. Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.

#### <a name="problematic-code"></a>Sorunlu kod

❌**Veri kaybı**

Son `ReadResult` veri kesimi ayarlandığında' `IsCompleted` `true` Okuma döngüsünden çıkmadan önce bu verilerin okunmaması veri kaybına neden olur.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Sonsuz döngü**

Aşağıdaki mantık sonsuz bir döngü ile `Result.IsCompleted` `true` sonuçlanabilir, ancak arabellekte hiçbir zaman tam bir ileti yoktur.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Burada aynı sorun ile kod başka bir parçası. Kontrol etmeden önce boş olmayan bir arabelleği kontrol `ReadResult.IsCompleted`ediyor. Çünkü bir `else if`, tampon tam bir mesaj yoksa sonsuza kadar döngü olacaktır.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Beklenmeyen Hang**

Pozisyonda koşulsuz `PipeReader.AdvanceTo` `buffer.End` arama, tek bir iletiyi ayrıştururken askıda kalmasına neden olabilir. `examined` Bir sonraki `PipeReader.AdvanceTo` arama şu zamana kadar geri dönmeyecek:

* Boruya daha fazla veri yazılmış.
* Ve yeni veriler daha önce incelenmedi.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Bellek Dışı (OOM)**

Aşağıdaki koşullarla, aşağıdaki kod bir <xref:System.OutOfMemoryException> oluştukadar arabelleğe alma tutar:

* Maksimum ileti boyutu yok.
* Döndürülen `PipeReader` veriler tam bir ileti yapmaz. Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB'lık ileti) yazdığından tam bir ileti yapmaz.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Bellek Bozulması**

Arabelleği okuyan yardımcıları yazarken, döndürülen herhangi bir yük `Advance`aramadan önce kopyalanmalıdır. Aşağıdaki örnek, atanbellin `Pipe` attığı belleği döndürür ve bir sonraki işlem için yeniden kullanabilir (okuma/yazma).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

Arayan <xref:System.IO.Pipelines.PipeWriter> adına yazmak için arabellekleri yönetir. `PipeWriter`[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)uygular. `IBufferWriter<byte>`ek arabellek kopyaları olmadan yazma yapmak için arabelleklere erişim elde etmek mümkün kılar.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Önceki kod:

* `PipeWriter` Kullanarak <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>en az 5 bayt lık bir arabellek ister.
* Döndürülen `Memory<byte>`ASCII dizesi `"Hello"` için bayt yazar.
* Arabelleğe kaç bayt yazıldığını gösteren çağrılar. <xref:System.IO.Pipelines.PipeWriter.Advance%2A>
* Baytları `PipeWriter`alttaki aygıta gönderen floşlar.

Önceki yazma yöntemi, `PipeWriter`.. Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Varolan arabelleği `PipeWriter`' ne kopyalar.
* Aramalar `GetSpan` `Advance` , uygun <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>olarak ve aramalar .

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>İptal

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>bir <xref:System.Threading.CancellationToken>. Bekleyen `CancellationToken` bir floş varken belirteç iptal edilirse bir `OperationCanceledException` sonuç geçirme. `PipeWriter.FlushAsync`bir özel durum <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> yükseltmeden geçerli floş işlemini iptal etmenin bir yolunu destekler. Arama, `PipeWriter.CancelPendingFlush` geçerli veya bir `PipeWriter.FlushAsync` `PipeWriter.WriteAsync` sonraki çağrıya neden olur veya bir <xref:System.IO.Pipelines.FlushResult> 'e `IsCanceled` ayarlanmış bir ile `true`döndürün. Bu, zarar vermeyen ve istisnai olmayan bir şekilde verimli floş durdurmak için yararlı olabilir.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter sık karşılaşılan sorunlar

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> en az istenen bellek miktarı ile bir arabellek döndürün. Tam arabellek boyutları **varsayma.**
* Ardışık aramaların aynı arabelleği veya aynı boyuttaara bellek döndüreceğinin garantisi yoktur.
* Daha fazla veri yazmaya devam <xref:System.IO.Pipelines.PipeWriter.Advance%2A> etmek için çağrıda bulunduktan sonra yeni bir arabellek istenmelidir. Daha önce edinilen arabellek için yazılamaz.
* Arama `GetMemory` `GetSpan` ya da eksik bir arama `FlushAsync` güvenli değil.
* Arama `Complete` `CompleteAsync` veya sifonlanmamış veri varken bellek bozulmasına neden olabilir.

## <a name="iduplexpipe"></a>IDuplexPipe

Hem <xref:System.IO.Pipelines.IDuplexPipe> okuma yı hem de yazmayı destekleyen türler için bir sözleşmedir. Örneğin, bir ağ bağlantısı bir `IDuplexPipe`.

 Bir `Pipe` ve `PipeReader` a `PipeWriter`içeren `IDuplexPipe` aksine, tam çift yönlü bağlantının tek bir tarafını temsil eder. Yani yazılanlar `PipeWriter` `PipeReader`okunmayacak.

## <a name="streams"></a>Akışlar

Akış verilerini okurken veya yazarken, genellikle bir de-serializer kullanarak verileri okur ve bir serializer kullanarak veri yazarsınız. Bu okuma ve yazma akışı API'lerinin çoğunun bir `Stream` parametresi var. Bu varolan API'lerle tümleştirmeyi `PipeReader` `PipeWriter` kolaylaştırmak <xref:System.IO.Pipelines.PipeReader.AsStream%2A>ve bir .  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>etrafında `Stream` `PipeReader` bir uygulama `PipeWriter`döndürür.
