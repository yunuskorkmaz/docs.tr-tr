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
ms.openlocfilehash: 8822e731ae805e83d4072c5bd78dff3fcf9a31a1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81462518"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="057af-103">System.IO.Pipelines in .NET</span><span class="sxs-lookup"><span data-stu-id="057af-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="057af-104"><xref:System.IO.Pipelines>.NET'te yüksek performanslı G/Ç yapmayı kolaylaştırmak için tasarlanmış yeni bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="057af-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="057af-105">Tüm .NET uygulamalarında çalışan .NET Standard'ı hedefleyen bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="057af-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="057af-106">System.IO.Pipelines hangi sorunu çözer?</span><span class="sxs-lookup"><span data-stu-id="057af-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="057af-107">Akış verilerini ayrıştıran uygulamalar, birçok özel ve sıradışı kod akışına sahip ortak kodlardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="057af-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="057af-108">Ortak plaka ve özel servis kodu karmaşıktır ve bakımı zordur.</span><span class="sxs-lookup"><span data-stu-id="057af-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="057af-109">`System.IO.Pipelines`için mimar oldu:</span><span class="sxs-lookup"><span data-stu-id="057af-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="057af-110">Akış verisi için yüksek performanslı ayrışma vardır.</span><span class="sxs-lookup"><span data-stu-id="057af-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="057af-111">Kod karmaşıklığını azaltın.</span><span class="sxs-lookup"><span data-stu-id="057af-111">Reduce code complexity.</span></span>

<span data-ttu-id="057af-112">Aşağıdaki kod, istemciden satır sınırlandırAn `'\n'`(sınırlandırılabilen) iletileri alan bir TCP sunucusu için tipiktir:</span><span class="sxs-lookup"><span data-stu-id="057af-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="057af-113">Önceki kodun çeşitli sorunları vardır:</span><span class="sxs-lookup"><span data-stu-id="057af-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="057af-114">İletinin tamamı (satır sonu) `ReadAsync`tek bir aramada alınmayabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="057af-115">Sonucu görmezden `stream.ReadAsync`geliyor.</span><span class="sxs-lookup"><span data-stu-id="057af-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="057af-116">`stream.ReadAsync`ne kadar veri okundugünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="057af-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="057af-117">Tek `ReadAsync` bir aramada birden çok satırın okunduğu durumu işlemez.</span><span class="sxs-lookup"><span data-stu-id="057af-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="057af-118">Her okuma `byte` ile bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="057af-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="057af-119">Önceki sorunları gidermek için aşağıdaki değişiklikler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="057af-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="057af-120">Yeni bir satır bulunana kadar gelen verileri arabelleğe alan.</span><span class="sxs-lookup"><span data-stu-id="057af-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="057af-121">Arabellekte döndürülen tüm satırları ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="057af-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="057af-122">Bu satır 1 KB (1024 bayt) daha büyük olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="057af-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="057af-123">Kodun, arabellek içindeki tam satırı sığdırmak için sınır dışı layıcı bulunana kadar giriş arabelleği yeniden boyutlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="057af-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="057af-124">Arabellek yeniden boyutlandırılırsa, girişte daha uzun satırlar göründükçe daha fazla arabellek kopyası yapılır.</span><span class="sxs-lookup"><span data-stu-id="057af-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="057af-125">Boşa harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="057af-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="057af-126">Belleği tekrar tekrar ayırmamak için arabellek birleştirme yi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="057af-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="057af-127">Aşağıdaki kod, bu sorunlardan bazılarını giderer:</span><span class="sxs-lookup"><span data-stu-id="057af-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="057af-128">Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez.</span><span class="sxs-lookup"><span data-stu-id="057af-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="057af-129">Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="057af-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="057af-130">`System.IO.Pipelines`bu tür kod yazmayı kolaylaştırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="057af-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="057af-131">Boru</span><span class="sxs-lookup"><span data-stu-id="057af-131">Pipe</span></span>

<span data-ttu-id="057af-132">Sınıf <xref:System.IO.Pipelines.Pipe> bir `PipeWriter/PipeReader` çift oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="057af-133">Tüm veriler içinde `PipeWriter` mevcuttur: `PipeReader`</span><span class="sxs-lookup"><span data-stu-id="057af-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="057af-134">Boru temel kullanımı</span><span class="sxs-lookup"><span data-stu-id="057af-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="057af-135">İki döngü vardır:</span><span class="sxs-lookup"><span data-stu-id="057af-135">There are two loops:</span></span>

* <span data-ttu-id="057af-136">`FillPipeAsync`dan okur `Socket` ve yazıyor `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="057af-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="057af-137">`ReadPipeAsync``PipeReader` ve gelen satırları parses okur.</span><span class="sxs-lookup"><span data-stu-id="057af-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="057af-138">Ayrılmış açık arabellek yok.</span><span class="sxs-lookup"><span data-stu-id="057af-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="057af-139">Tüm arabellek yönetimi ve `PipeReader` `PipeWriter` uygulamalara devredilir.</span><span class="sxs-lookup"><span data-stu-id="057af-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="057af-140">Arabellek yönetimini adeleyen, kod tüketen lerin yalnızca iş mantığına odaklanmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="057af-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="057af-141">İlk döngüde:</span><span class="sxs-lookup"><span data-stu-id="057af-141">In the first loop:</span></span>

* <span data-ttu-id="057af-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>altta yatan yazardan bellek almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="057af-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="057af-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>arabelleğe `PipeWriter` ne kadar veri yazıldığını söylemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="057af-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="057af-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>verileri kullanılabilir hale getirmek için `PipeReader`denir.</span><span class="sxs-lookup"><span data-stu-id="057af-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="057af-145">İkinci döngüde, `PipeReader` `PipeWriter`'' tarafından yazılan arabellekleri tüketir.</span><span class="sxs-lookup"><span data-stu-id="057af-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="057af-146">Arabellekler yuvadan geliyor.</span><span class="sxs-lookup"><span data-stu-id="057af-146">The buffers come from the socket.</span></span> <span data-ttu-id="057af-147">Çağrı: `PipeReader.ReadAsync`</span><span class="sxs-lookup"><span data-stu-id="057af-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="057af-148">İki <xref:System.IO.Pipelines.ReadResult> önemli bilgi parçasını içeren bir verir:</span><span class="sxs-lookup"><span data-stu-id="057af-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="057af-149">Şeklinde okunan veriler `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="057af-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="057af-150">Verilerin sonuna `IsCompleted` (EOF) ulaşılıp ulaşıldığını gösteren bir boolean.</span><span class="sxs-lookup"><span data-stu-id="057af-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="057af-151">Satır sonu (EOL) delimiter bulma ve çizgi ayrıştırma sonra:</span><span class="sxs-lookup"><span data-stu-id="057af-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="057af-152">Mantık, arabelleği zaten işlenmiş olanı atlamak için işler.</span><span class="sxs-lookup"><span data-stu-id="057af-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="057af-153">`PipeReader.AdvanceTo``PipeReader` ne kadar veri tüketildiğini ve incelendiğini söylemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="057af-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="057af-154">Okuyucu ve yazar döngüleri `Complete`arayarak sona erer.</span><span class="sxs-lookup"><span data-stu-id="057af-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="057af-155">`Complete`altta yatan Boru'nun ayırdEttiği belleği serbest bırakmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="057af-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="057af-156">Geri basınç ve akış kontrolü</span><span class="sxs-lookup"><span data-stu-id="057af-156">Backpressure and flow control</span></span>

<span data-ttu-id="057af-157">İdeal olarak, okuma ve ayrıştma birlikte çalışır:</span><span class="sxs-lookup"><span data-stu-id="057af-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="057af-158">Yazma iş parçacığı ağdan gelen verileri tüketir ve arabelleklere koyar.</span><span class="sxs-lookup"><span data-stu-id="057af-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="057af-159">Ayrıştırma iş parçacığı, uygun veri yapılarının oluşturulmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="057af-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="057af-160">Genellikle, ayrıştma, ağdaki veri bloklarını kopyalamaktan daha fazla zaman alır:</span><span class="sxs-lookup"><span data-stu-id="057af-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="057af-161">Okuma iş parçacığı ayrışma iş parçacığının önüne geçer.</span><span class="sxs-lookup"><span data-stu-id="057af-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="057af-162">Okuma iş parçacığı, ayrıştma iş parçacığı için verileri depolamak için daha fazla bellek ayırmak veya yavaşlatmak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="057af-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="057af-163">En iyi performans için, sık duraklar ve daha fazla bellek ayırma arasında bir denge vardır.</span><span class="sxs-lookup"><span data-stu-id="057af-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="057af-164">Önceki sorunu çözmek için, `Pipe` veri akışını denetlemek için iki ayarı vardır:</span><span class="sxs-lookup"><span data-stu-id="057af-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="057af-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> Duraklatma çağrıları ndan önce ne kadar veri arabelleğe alınması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="057af-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="057af-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Okuyucunun devam etmek için `PipeWriter.FlushAsync` yapılan aramadan önce ne kadar veri gözlemlemeyi gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="057af-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![ResumeWriterThreshold ve PauseWriterThreshold ile Diyagram](./media/pipelines/resume-pause.png)

<span data-ttu-id="057af-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="057af-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="057af-169">`Pipe` Haçlar `PauseWriterThreshold`veri miktarı tamamlanmamış `ValueTask<FlushResult>` bir verir.</span><span class="sxs-lookup"><span data-stu-id="057af-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="057af-170">'den `ValueTask<FlushResult>` daha `ResumeWriterThreshold`düşük olduğunda tamamlar.</span><span class="sxs-lookup"><span data-stu-id="057af-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="057af-171">Bir değer kullanıldığında oluşabilir hızlı bisiklet, önlemek için iki değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="057af-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="057af-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="057af-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="057af-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="057af-173">PipeScheduler</span></span>

<span data-ttu-id="057af-174">Genellikle kullanırken `async` `await`ve , asynchronous kodu bir <xref:System.Threading.Tasks.TaskScheduler> veya geçerli <xref:System.Threading.SynchronizationContext>üzerinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="057af-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="057af-175">G/Ç yaparken, G/Ç'nin nerede gerçekleştirildiği üzerinde ince taneli denetime sahip olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="057af-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="057af-176">Bu denetim, CPU önbelleklerinden etkin bir şekilde yararlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="057af-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="057af-177">Verimli önbelleğe alma, web sunucuları gibi yüksek performanslı uygulamalar için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="057af-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="057af-178"><xref:System.IO.Pipelines.PipeScheduler>eşzamanlı geri aramaların nerede çalıştığı üzerinde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="057af-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="057af-179">Varsayılan olarak:</span><span class="sxs-lookup"><span data-stu-id="057af-179">By default:</span></span>

* <span data-ttu-id="057af-180">Akım <xref:System.Threading.SynchronizationContext> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="057af-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="057af-181">Yoksa, `SynchronizationContext`geri aramaları çalıştırmak için iş parçacığı havuzunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="057af-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="057af-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) iş <xref:System.IO.Pipelines.PipeScheduler> parçacığı havuzuna geri aramaları sıralayan bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="057af-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="057af-183">`PipeScheduler.ThreadPool`varsayılan ve genellikle en iyi seçimdir.</span><span class="sxs-lookup"><span data-stu-id="057af-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="057af-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) kilitlenmeler gibi istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="057af-185">Boru sıfırlama</span><span class="sxs-lookup"><span data-stu-id="057af-185">Pipe reset</span></span>

<span data-ttu-id="057af-186">Nesneyi `Pipe` yeniden kullanmak genellikle etkilidir.</span><span class="sxs-lookup"><span data-stu-id="057af-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="057af-187">Boruyu sıfırlamak için, hem `PipeReader` `PipeWriter` boru hem de tam olduğunda arayın. <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A></span><span class="sxs-lookup"><span data-stu-id="057af-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="057af-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="057af-188">PipeReader</span></span>

<span data-ttu-id="057af-189"><xref:System.IO.Pipelines.PipeReader>arayan adına belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="057af-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="057af-190">**Her** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> zaman <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>aradıktan sonra arayın.</span><span class="sxs-lookup"><span data-stu-id="057af-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="057af-191">Bu, `PipeReader` arayanın bellekle ne zaman işlenirse izlenebileceğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="057af-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="057af-192">İade `ReadOnlySequence<byte>` edilen `PipeReader.ReadAsync` den yalnızca arama `PipeReader.AdvanceTo`gelene kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="057af-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="057af-193">Aradıktan `PipeReader.AdvanceTo`sonra kullanmak `ReadOnlySequence<byte>` yasak.</span><span class="sxs-lookup"><span data-stu-id="057af-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="057af-194">`PipeReader.AdvanceTo`iki <xref:System.SequencePosition> bağımsız değişken alır:</span><span class="sxs-lookup"><span data-stu-id="057af-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="057af-195">İlk bağımsız değişken ne kadar bellek tüketilmeyi belirler.</span><span class="sxs-lookup"><span data-stu-id="057af-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="057af-196">İkinci bağımsız değişken, arabelleğe ne kadarının gözlendiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="057af-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="057af-197">Verileri tüketilen olarak işaretleme, borunun belleği alttaki arabellek havuzuna döndürebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="057af-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="057af-198">Verileri gözlenen olarak işaretleme, `PipeReader.ReadAsync` bir sonraki çağrının ne işe yaradığı yla ilgili denetimleri yapar.</span><span class="sxs-lookup"><span data-stu-id="057af-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="057af-199">Her şeyi gözlenen şekilde işaretlemek, bir sonraki çağrının boruya `PipeReader.ReadAsync` daha fazla veri yazılana kadar geri dönmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="057af-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="057af-200">Başka bir değer, gözlenen `PipeReader.ReadAsync` *ve* gözlenmeyen verilerle hemen dönmek için bir sonraki çağrıyı yapar, ancak zaten tüketilen verileri yapmaz.</span><span class="sxs-lookup"><span data-stu-id="057af-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="057af-201">Akış veri senaryolarını okuma</span><span class="sxs-lookup"><span data-stu-id="057af-201">Read streaming data scenarios</span></span>

<span data-ttu-id="057af-202">Akış verilerini okumaya çalışırken ortaya çıkan birkaç tipik desen vardır:</span><span class="sxs-lookup"><span data-stu-id="057af-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="057af-203">Veri akışı göz önüne alındığında, tek bir iletiyi ayrıştın.</span><span class="sxs-lookup"><span data-stu-id="057af-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="057af-204">Bir veri akışı göz önüne alındığında, kullanılabilir tüm iletileri ayrıştın.</span><span class="sxs-lookup"><span data-stu-id="057af-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="057af-205">Aşağıdaki örnekler, `TryParseMessage` bir `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="057af-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="057af-206">`TryParseMessage`tek bir iletiyi ayrıştırır ve arabellekten ayrıştırılan iletiyi kırpmak için giriş arabelleği güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="057af-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="057af-207">`TryParseMessage`.NET'in bir parçası değildir, aşağıdaki bölümlerde kullanılan kullanıcı yazılı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="057af-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="057af-208">Tek bir iletiyi okuma</span><span class="sxs-lookup"><span data-stu-id="057af-208">Read a single message</span></span>

<span data-ttu-id="057af-209">Aşağıdaki kod a'dan `PipeReader` tek bir ileti okur ve arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="057af-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="057af-210">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="057af-210">The preceding code:</span></span>

* <span data-ttu-id="057af-211">Tek bir iletiyi ayrışdırır.</span><span class="sxs-lookup"><span data-stu-id="057af-211">Parses a single message.</span></span>
* <span data-ttu-id="057af-212">Kırpılan giriş arabelleği başlangıcına işaret etmek için tüketilen `SequencePosition` ve incelenen `SequencePosition` güncelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="057af-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="057af-213">Ayrıştırılmış iletiyi giriş arabelleğinden `SequencePosition` `TryParseMessage` kaldırdığından, iki bağımsız değişken güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="057af-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="057af-214">Genellikle, arabellekten tek bir ileti ayrıştırırken, incelenen konum aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="057af-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="057af-215">İletinin sonu.</span><span class="sxs-lookup"><span data-stu-id="057af-215">The end of the message.</span></span>
* <span data-ttu-id="057af-216">İleti bulunamadıysa alınan arabelleğe son.</span><span class="sxs-lookup"><span data-stu-id="057af-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="057af-217">Tek ileti örneği en fazla hata potansiyeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="057af-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="057af-218">Yanlış değerlerin *incelenmesi,* bellek dışı bir özel durum veya sonsuz bir döngüyle sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="057af-219">Daha fazla bilgi için bu makaledeki [PipeReader ortak sorunlar](#gotchas) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="057af-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="057af-220">Birden çok ileti okuma</span><span class="sxs-lookup"><span data-stu-id="057af-220">Reading multiple messages</span></span>

<span data-ttu-id="057af-221">Aşağıdaki kod a'dan `PipeReader` gelen tüm `ProcessMessageAsync` iletileri okur ve her birinde çağrılar.</span><span class="sxs-lookup"><span data-stu-id="057af-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="057af-222">İptal</span><span class="sxs-lookup"><span data-stu-id="057af-222">Cancellation</span></span>

<span data-ttu-id="057af-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="057af-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="057af-224">Bir <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="057af-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="057af-225">Bekleyen bir <xref:System.OperationCanceledException> okuma `CancellationToken` varken iptal edilirse atar.</span><span class="sxs-lookup"><span data-stu-id="057af-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="057af-226">Bir özel durum yükseltmeyi önleyen <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>geçerli okuma işlemini iptal etmenin bir yolunu destekler.</span><span class="sxs-lookup"><span data-stu-id="057af-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="057af-227">`PipeReader.CancelPendingRead` Arama, geçerli veya bir `PipeReader.ReadAsync` sonraki <xref:System.IO.Pipelines.ReadResult> çağrının bir 'e `IsCanceled` ayarlanmış bir 'e döndürülmeye neden `true`olur.</span><span class="sxs-lookup"><span data-stu-id="057af-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="057af-228">Bu, varolan okuma döngüsünün yıkıcı olmayan ve istisnai olmayan bir şekilde durdurulması için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="057af-229">PipeReader yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="057af-229">PipeReader common problems</span></span>

* <span data-ttu-id="057af-230">Yanlış değerlerin okunması `consumed` `examined` veya okunmasıyla sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="057af-231">İncelendiği gibi geçmek `buffer.End` şu neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="057af-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="057af-232">Durmuş veriler</span><span class="sxs-lookup"><span data-stu-id="057af-232">Stalled data</span></span>
  * <span data-ttu-id="057af-233">Veriler tüketilmezse, büyük olasılıkla bellek dışı (OOM) özel durumu.</span><span class="sxs-lookup"><span data-stu-id="057af-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="057af-234">Örneğin, `PipeReader.AdvanceTo(position, buffer.End)` arabellekten bir seferde tek bir ileti işlenirken.</span><span class="sxs-lookup"><span data-stu-id="057af-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="057af-235">Yanlış değerlerin sonsuz `consumed` `examined` bir döngüye geçirilmesi veya bunun sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="057af-236">Örneğin, `PipeReader.AdvanceTo(buffer.Start)` değişmediyse, `buffer.Start` bir sonraki aramanın `PipeReader.ReadAsync` yeni veriler gelmeden hemen önce geri dönmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="057af-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="057af-237">Yanlış değerlerin geçirilmesi `consumed` `examined` veya sonsuz arabelleğe alma (nihai OOM) neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="057af-238">Aramadan `ReadOnlySequence<byte>` `PipeReader.AdvanceTo` sonra kullanmak bellek bozulmasına neden olabilir (ücretsiz sonra kullanın).</span><span class="sxs-lookup"><span data-stu-id="057af-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="057af-239">Aramanın `PipeReader.Complete/CompleteAsync` başarısız olması bellek sızıntısına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="057af-240">Arabelleği işlemeden önce okuma mantığını denetlemek <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> ve çıkmak veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="057af-241">Döngü çıkış durumu temel `ReadResult.Buffer.IsEmpty` alınmalıdır ve `ReadResult.IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="057af-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="057af-242">Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="057af-243">Sorunlu kod</span><span class="sxs-lookup"><span data-stu-id="057af-243">Problematic code</span></span>

<span data-ttu-id="057af-244">❌**Veri kaybı**</span><span class="sxs-lookup"><span data-stu-id="057af-244">❌ **Data loss**</span></span>

<span data-ttu-id="057af-245">Son `ReadResult` veri kesimi ayarlandığında' `IsCompleted` `true`</span><span class="sxs-lookup"><span data-stu-id="057af-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="057af-246">Okuma döngüsünden çıkmadan önce bu verilerin okunmaması veri kaybına neden olur.</span><span class="sxs-lookup"><span data-stu-id="057af-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="057af-247">❌**Sonsuz döngü**</span><span class="sxs-lookup"><span data-stu-id="057af-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="057af-248">Aşağıdaki mantık sonsuz bir döngü ile `Result.IsCompleted` `true` sonuçlanabilir, ancak arabellekte hiçbir zaman tam bir ileti yoktur.</span><span class="sxs-lookup"><span data-stu-id="057af-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="057af-249">Burada aynı sorun ile kod başka bir parçası.</span><span class="sxs-lookup"><span data-stu-id="057af-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="057af-250">Kontrol etmeden önce boş olmayan bir arabelleği kontrol `ReadResult.IsCompleted`ediyor.</span><span class="sxs-lookup"><span data-stu-id="057af-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="057af-251">Çünkü bir `else if`, tampon tam bir mesaj yoksa sonsuza kadar döngü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="057af-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="057af-252">❌**Beklenmeyen Hang**</span><span class="sxs-lookup"><span data-stu-id="057af-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="057af-253">Pozisyonda koşulsuz `PipeReader.AdvanceTo` `buffer.End` arama, tek bir iletiyi ayrıştururken askıda kalmasına neden olabilir. `examined`</span><span class="sxs-lookup"><span data-stu-id="057af-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="057af-254">Bir sonraki `PipeReader.AdvanceTo` arama şu zamana kadar geri dönmeyecek:</span><span class="sxs-lookup"><span data-stu-id="057af-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="057af-255">Boruya daha fazla veri yazılmış.</span><span class="sxs-lookup"><span data-stu-id="057af-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="057af-256">Ve yeni veriler daha önce incelenmedi.</span><span class="sxs-lookup"><span data-stu-id="057af-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="057af-257">❌**Bellek Dışı (OOM)**</span><span class="sxs-lookup"><span data-stu-id="057af-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="057af-258">Aşağıdaki koşullarla, aşağıdaki kod bir <xref:System.OutOfMemoryException> oluştukadar arabelleğe alma tutar:</span><span class="sxs-lookup"><span data-stu-id="057af-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="057af-259">Maksimum ileti boyutu yok.</span><span class="sxs-lookup"><span data-stu-id="057af-259">There's no maximum message size.</span></span>
* <span data-ttu-id="057af-260">Döndürülen `PipeReader` veriler tam bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="057af-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="057af-261">Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB'lık ileti) yazdığından tam bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="057af-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="057af-262">❌**Bellek Bozulması**</span><span class="sxs-lookup"><span data-stu-id="057af-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="057af-263">Arabelleği okuyan yardımcıları yazarken, döndürülen herhangi bir yük `Advance`aramadan önce kopyalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="057af-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="057af-264">Aşağıdaki örnek, atanbellin `Pipe` attığı belleği döndürür ve bir sonraki işlem için yeniden kullanabilir (okuma/yazma).</span><span class="sxs-lookup"><span data-stu-id="057af-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="057af-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="057af-265">PipeWriter</span></span>

<span data-ttu-id="057af-266">Arayan <xref:System.IO.Pipelines.PipeWriter> adına yazmak için arabellekleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="057af-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="057af-267">`PipeWriter`[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)uygular.</span><span class="sxs-lookup"><span data-stu-id="057af-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="057af-268">`IBufferWriter<byte>`ek arabellek kopyaları olmadan yazma yapmak için arabelleklere erişim elde etmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="057af-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="057af-269">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="057af-269">The previous code:</span></span>

* <span data-ttu-id="057af-270">`PipeWriter` Kullanarak <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>en az 5 bayt lık bir arabellek ister.</span><span class="sxs-lookup"><span data-stu-id="057af-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="057af-271">Döndürülen `Memory<byte>`ASCII dizesi `"Hello"` için bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="057af-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="057af-272">Arabelleğe kaç bayt yazıldığını gösteren çağrılar. <xref:System.IO.Pipelines.PipeWriter.Advance%2A></span><span class="sxs-lookup"><span data-stu-id="057af-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="057af-273">Baytları `PipeWriter`alttaki aygıta gönderen floşlar.</span><span class="sxs-lookup"><span data-stu-id="057af-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="057af-274">Önceki yazma yöntemi, `PipeWriter`..</span><span class="sxs-lookup"><span data-stu-id="057af-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="057af-275">Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="057af-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="057af-276">Varolan arabelleği `PipeWriter`' ne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="057af-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="057af-277">Aramalar `GetSpan` `Advance` , uygun <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>olarak ve aramalar .</span><span class="sxs-lookup"><span data-stu-id="057af-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="057af-278">İptal</span><span class="sxs-lookup"><span data-stu-id="057af-278">Cancellation</span></span>

<span data-ttu-id="057af-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>bir <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="057af-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="057af-280">Bekleyen `CancellationToken` bir floş varken belirteç iptal edilirse bir `OperationCanceledException` sonuç geçirme.</span><span class="sxs-lookup"><span data-stu-id="057af-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="057af-281">`PipeWriter.FlushAsync`bir özel durum <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> yükseltmeden geçerli floş işlemini iptal etmenin bir yolunu destekler.</span><span class="sxs-lookup"><span data-stu-id="057af-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="057af-282">Arama, `PipeWriter.CancelPendingFlush` geçerli veya bir `PipeWriter.FlushAsync` `PipeWriter.WriteAsync` sonraki çağrıya neden olur veya bir <xref:System.IO.Pipelines.FlushResult> 'e `IsCanceled` ayarlanmış bir ile `true`döndürün.</span><span class="sxs-lookup"><span data-stu-id="057af-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="057af-283">Bu, zarar vermeyen ve istisnai olmayan bir şekilde verimli floş durdurmak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="057af-284">PipeWriter sık karşılaşılan sorunlar</span><span class="sxs-lookup"><span data-stu-id="057af-284">PipeWriter common problems</span></span>

* <span data-ttu-id="057af-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> en az istenen bellek miktarı ile bir arabellek döndürün.</span><span class="sxs-lookup"><span data-stu-id="057af-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="057af-286">Tam arabellek boyutları **varsayma.**</span><span class="sxs-lookup"><span data-stu-id="057af-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="057af-287">Ardışık aramaların aynı arabelleği veya aynı boyuttaara bellek döndüreceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="057af-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="057af-288">Daha fazla veri yazmaya devam <xref:System.IO.Pipelines.PipeWriter.Advance%2A> etmek için çağrıda bulunduktan sonra yeni bir arabellek istenmelidir.</span><span class="sxs-lookup"><span data-stu-id="057af-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="057af-289">Daha önce edinilen arabellek için yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="057af-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="057af-290">Arama `GetMemory` `GetSpan` ya da eksik bir arama `FlushAsync` güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="057af-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="057af-291">Arama `Complete` `CompleteAsync` veya sifonlanmamış veri varken bellek bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="057af-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="057af-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="057af-292">IDuplexPipe</span></span>

<span data-ttu-id="057af-293">Hem <xref:System.IO.Pipelines.IDuplexPipe> okuma yı hem de yazmayı destekleyen türler için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="057af-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="057af-294">Örneğin, bir ağ bağlantısı bir `IDuplexPipe`.</span><span class="sxs-lookup"><span data-stu-id="057af-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="057af-295">Bir `Pipe` ve `PipeReader` a `PipeWriter`içeren `IDuplexPipe` aksine, tam çift yönlü bağlantının tek bir tarafını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="057af-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="057af-296">Yani yazılanlar `PipeWriter` `PipeReader`okunmayacak.</span><span class="sxs-lookup"><span data-stu-id="057af-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="057af-297">Akışlar</span><span class="sxs-lookup"><span data-stu-id="057af-297">Streams</span></span>

<span data-ttu-id="057af-298">Akış verilerini okurken veya yazarken, genellikle bir de-serializer kullanarak verileri okur ve bir serializer kullanarak veri yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="057af-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="057af-299">Bu okuma ve yazma akışı API'lerinin çoğunun bir `Stream` parametresi var.</span><span class="sxs-lookup"><span data-stu-id="057af-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="057af-300">Bu varolan API'lerle tümleştirmeyi `PipeReader` `PipeWriter` kolaylaştırmak <xref:System.IO.Pipelines.PipeReader.AsStream%2A>ve bir .</span><span class="sxs-lookup"><span data-stu-id="057af-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="057af-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>etrafında `Stream` `PipeReader` bir uygulama `PipeWriter`döndürür.</span><span class="sxs-lookup"><span data-stu-id="057af-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
