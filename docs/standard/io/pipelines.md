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
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="773fe-103">.NET 'teki System. ıO. işlem hatları</span><span class="sxs-lookup"><span data-stu-id="773fe-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="773fe-104"><xref:System.IO.Pipelines>, .NET ortamında yüksek performanslı g/ç 'yi daha kolay hale getirmek için tasarlanan yeni bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="773fe-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="773fe-105">Bu, tüm .NET uygulamalarında çalışacak .NET Standard hedefleme bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="773fe-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="773fe-106">System. ıO. hatlarını çözme sorunu</span><span class="sxs-lookup"><span data-stu-id="773fe-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="773fe-107">Akış verilerini ayrıştırmaya yönelik uygulamalar, çok sayıda özel ve olağandışı kod akışına sahip ortak koddan oluşur.</span><span class="sxs-lookup"><span data-stu-id="773fe-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="773fe-108">Ortak ve özel durum kodu karmaşık ve devam etmek zordur.</span><span class="sxs-lookup"><span data-stu-id="773fe-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="773fe-109">`System.IO.Pipelines` şu şekilde tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="773fe-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="773fe-110">Akış verilerinin yüksek performans ayrıştırması vardır.</span><span class="sxs-lookup"><span data-stu-id="773fe-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="773fe-111">Kod karmaşıklığını azaltın.</span><span class="sxs-lookup"><span data-stu-id="773fe-111">Reduce code complexity.</span></span>

<span data-ttu-id="773fe-112">Aşağıdaki kod, bir istemciden satır sınırlı iletileri (`'\n'`ile ayrılmış) alan bir TCP sunucusu için tipik bir noktadır:</span><span class="sxs-lookup"><span data-stu-id="773fe-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="773fe-113">Yukarıdaki kodda birkaç sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="773fe-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="773fe-114">Tüm ileti (satır sonu) `ReadAsync`tek bir çağrıda alınmayabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="773fe-115">`stream.ReadAsync`sonucunu yok sayıyor.</span><span class="sxs-lookup"><span data-stu-id="773fe-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="773fe-116">`stream.ReadAsync`, ne kadar verinin okunduğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="773fe-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="773fe-117">Tek bir `ReadAsync` çağrısında birden çok satırın okunduğu durumu işlemez.</span><span class="sxs-lookup"><span data-stu-id="773fe-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="773fe-118">Her okuma ile bir `byte` dizisi ayırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="773fe-119">Yukarıdaki sorunları onarmak için aşağıdaki değişiklikler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="773fe-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="773fe-120">Yeni bir satır bulunana kadar gelen verileri arabelleğe koyun.</span><span class="sxs-lookup"><span data-stu-id="773fe-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="773fe-121">Arabellekte döndürülen tüm satırları ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="773fe-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="773fe-122">Satır 1 KB 'den büyük (1024 bayt) olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="773fe-123">Bu kodun, arabelleğin içindeki tamamlanma satırına sığması için sınırlayıcı bulunana kadar giriş arabelleğini yeniden boyutlandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="773fe-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="773fe-124">Arabellek yeniden boyutlandırılırsa, girişte daha uzun çizgiler göründüğü sürece daha fazla arabellek kopyası yapılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="773fe-125">Harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="773fe-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="773fe-126">Belleği sürekli ayırmayı önlemek için arabellek havuzu kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="773fe-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="773fe-127">Aşağıdaki kod bu sorunlardan bazılarını ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="773fe-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="773fe-128">Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez.</span><span class="sxs-lookup"><span data-stu-id="773fe-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="773fe-129">Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="773fe-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="773fe-130">`System.IO.Pipelines`, bu tür bir kodu daha kolay yazmayı kolaylaştırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="773fe-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="773fe-131">Kapatıldığı</span><span class="sxs-lookup"><span data-stu-id="773fe-131">Pipe</span></span>

<span data-ttu-id="773fe-132"><xref:System.IO.Pipelines.Pipe> sınıfı bir `PipeWriter/PipeReader` çifti oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="773fe-133">`PipeWriter` yazılan tüm veriler `PipeReader`kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="773fe-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="773fe-134">Kanal temel kullanımı</span><span class="sxs-lookup"><span data-stu-id="773fe-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="773fe-135">İki döngü vardır:</span><span class="sxs-lookup"><span data-stu-id="773fe-135">There are two loops:</span></span>

* <span data-ttu-id="773fe-136">`FillPipeAsync` `Socket` okur ve `PipeWriter`yazar.</span><span class="sxs-lookup"><span data-stu-id="773fe-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="773fe-137">`ReadPipeAsync` `PipeReader` okur ve gelen satırları ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="773fe-138">Ayrılmış açık arabellek yok.</span><span class="sxs-lookup"><span data-stu-id="773fe-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="773fe-139">Tüm arabellek yönetimi, `PipeReader` ve `PipeWriter` uygulamalarına devredildi.</span><span class="sxs-lookup"><span data-stu-id="773fe-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="773fe-140">Arabellek yönetimi için temsilci seçme, kodun yalnızca iş mantığına odaklanılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="773fe-141">İlk döngüde:</span><span class="sxs-lookup"><span data-stu-id="773fe-141">In the first loop:</span></span>

* <span data-ttu-id="773fe-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>, temel alınan yazıcıya bellek almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="773fe-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>, arabelleğe ne kadar veri yazıldığını `PipeWriter` söylemek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="773fe-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>, verileri `PipeReader`kullanılabilir hale getirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="773fe-145">İkinci döngüde, `PipeReader` `PipeWriter`tarafından yazılan arabellekleri tüketir.</span><span class="sxs-lookup"><span data-stu-id="773fe-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="773fe-146">Arabellekler yuvadan gelir.</span><span class="sxs-lookup"><span data-stu-id="773fe-146">The buffers come from the socket.</span></span> <span data-ttu-id="773fe-147">`PipeReader.ReadAsync`çağrısı:</span><span class="sxs-lookup"><span data-stu-id="773fe-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="773fe-148">İki önemli bilgi parçasını içeren bir <xref:System.IO.Pipelines.ReadResult> döndürür:</span><span class="sxs-lookup"><span data-stu-id="773fe-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="773fe-149">`ReadOnlySequence<byte>`biçiminde okunan veriler.</span><span class="sxs-lookup"><span data-stu-id="773fe-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="773fe-150">Verilerin sonuna (EOF) ulaşıldığını belirten bir Boole `IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="773fe-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="773fe-151">Satır sonu (EOL) sınırlayıcısı bulduktan ve satırı ayrıştırdıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="773fe-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="773fe-152">Mantık, zaten işlenmiş olan öğeleri atlamak için arabelleği işler.</span><span class="sxs-lookup"><span data-stu-id="773fe-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="773fe-153">`PipeReader.AdvanceTo`, ne kadar veri tüketiğini ve incelendiğini `PipeReader` söylemek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="773fe-154">Okuyucu ve yazıcı döngüleri `Complete`çağırarak biter.</span><span class="sxs-lookup"><span data-stu-id="773fe-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="773fe-155">`Complete`, temeldeki kanalın ayrılan belleği serbest bırakmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="773fe-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="773fe-156">Arka basınç ve akış denetimi</span><span class="sxs-lookup"><span data-stu-id="773fe-156">Backpressure and flow control</span></span>

<span data-ttu-id="773fe-157">İdeal olarak, birlikte iş okuma ve ayrıştırma:</span><span class="sxs-lookup"><span data-stu-id="773fe-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="773fe-158">Yazma iş parçacığı ağdan verileri tüketir ve arabelleğe koyar.</span><span class="sxs-lookup"><span data-stu-id="773fe-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="773fe-159">Ayrıştırma iş parçacığı, uygun veri yapılarını oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="773fe-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="773fe-160">Genellikle, ayrıştırma yalnızca ağdan veri bloklarını kopyalamaya kıyasla daha fazla zaman alır:</span><span class="sxs-lookup"><span data-stu-id="773fe-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="773fe-161">Okuma iş parçacığı ayrıştırma iş parçacığının önüne alınır.</span><span class="sxs-lookup"><span data-stu-id="773fe-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="773fe-162">Okuma iş parçacığı, ayrıştırma iş parçacığı için verileri depolamak üzere yavaşlıyor veya daha fazla bellek ayırmıştır.</span><span class="sxs-lookup"><span data-stu-id="773fe-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="773fe-163">En iyi performans için, sık duraklamalar ve daha fazla bellek ayırma arasında bir denge vardır.</span><span class="sxs-lookup"><span data-stu-id="773fe-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="773fe-164">Önceki sorunu çözmek için, `Pipe` veri akışını denetlemek üzere iki ayarı vardır:</span><span class="sxs-lookup"><span data-stu-id="773fe-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="773fe-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> duraklatma çağrısı yapmadan önce ne kadar veri ara belleğe alınacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="773fe-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="773fe-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: okuyucunun `PipeWriter.FlushAsync` sürdürülmeye yönelik çağrılardan önce ne kadar veri gözlemleyecek olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="773fe-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![ResumeWriterThreshold ve PauseWriterThreshold ile diyagram](./media/pipelines/resume-pause.png)

<span data-ttu-id="773fe-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="773fe-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="773fe-169">`Pipe` veri miktarı `PauseWriterThreshold`kesiştiği zaman tamamlanmamış bir `ValueTask<FlushResult>` döndürür.</span><span class="sxs-lookup"><span data-stu-id="773fe-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="773fe-170">`ResumeWriterThreshold`daha düşük hale geldiğinde `ValueTask<FlushResult>` tamamlar.</span><span class="sxs-lookup"><span data-stu-id="773fe-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="773fe-171">Tek bir değer kullanılırsa oluşabilecek hızlı döngüyü engellemek için iki değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="773fe-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="773fe-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="773fe-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="773fe-173">PipeScheduler</span></span>

<span data-ttu-id="773fe-174">Genellikle `async` ve `await`kullanılırken, zaman uyumsuz kod <xref:System.Threading.Tasks.TaskScheduler> ya da geçerli <xref:System.Threading.SynchronizationContext>üzerinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="773fe-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="773fe-175">G/ç yaparken, g/ç 'nin gerçekleştirildiği noktada ayrıntılı denetime sahip olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="773fe-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="773fe-176">Bu denetim, CPU önbelleklerinin etkin bir şekilde yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="773fe-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="773fe-177">Verimli önbelleğe alma, Web sunucuları gibi yüksek performanslı uygulamalar için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="773fe-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="773fe-178"><xref:System.IO.Pipelines.PipeScheduler>, zaman uyumsuz geri çağırmaların çalıştığı yerde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="773fe-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="773fe-179">Varsayılan olarak:</span><span class="sxs-lookup"><span data-stu-id="773fe-179">By default:</span></span>

* <span data-ttu-id="773fe-180">Geçerli <xref:System.Threading.SynchronizationContext> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="773fe-181">`SynchronizationContext`yoksa, geri çağırmaları çalıştırmak için iş parçacığı havuzunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="773fe-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="773fe-182">[Pipescheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) , iş parçacığı havuzuna geri çağırmaları sıraya alan <xref:System.IO.Pipelines.PipeScheduler> uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="773fe-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="773fe-183">`PipeScheduler.ThreadPool` varsayılandır ve genellikle en iyi seçenektir.</span><span class="sxs-lookup"><span data-stu-id="773fe-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="773fe-184">[Pipescheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) , kilitlenme gibi istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="773fe-185">Kanal sıfırlama</span><span class="sxs-lookup"><span data-stu-id="773fe-185">Pipe reset</span></span>

<span data-ttu-id="773fe-186">`Pipe` nesnesini yeniden kullanmak sıklıkla etkilidir.</span><span class="sxs-lookup"><span data-stu-id="773fe-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="773fe-187">Kanalı sıfırlamak için, hem `PipeReader` hem de `PipeWriter` tamamlandığında <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="773fe-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="773fe-188">Piypereader</span><span class="sxs-lookup"><span data-stu-id="773fe-188">PipeReader</span></span>

<span data-ttu-id="773fe-189"><xref:System.IO.Pipelines.PipeReader>, arayanın adına belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="773fe-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="773fe-190"><xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>çağrıldıktan sonra **her zaman** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="773fe-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="773fe-191">Bu, `PipeReader` izlenebilecek şekilde çağıranın bellekle ne zaman yapıldığını bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="773fe-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="773fe-192">`PipeReader.ReadAsync` döndürülen `ReadOnlySequence<byte>` yalnızca `PipeReader.AdvanceTo`çağrısı yapılıncaya kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="773fe-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="773fe-193">`PipeReader.AdvanceTo`çağrıldıktan sonra `ReadOnlySequence<byte>` kullanımı geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="773fe-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="773fe-194">`PipeReader.AdvanceTo` iki <xref:System.SequencePosition> bağımsız değişkeni alır:</span><span class="sxs-lookup"><span data-stu-id="773fe-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="773fe-195">İlk bağımsız değişken, ne kadar bellek tüketildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="773fe-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="773fe-196">İkinci bağımsız değişken, arabelleğin ne kadarının gözlemlendiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="773fe-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="773fe-197">Verileri tüketilen olarak işaretlemek, kanalın belleği temel alınan arabellek havuzuna döndürebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="773fe-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="773fe-198">Verileri gözlemlenen olarak işaretlemek `PipeReader.ReadAsync` sonraki çağrının ne yaptığını denetler.</span><span class="sxs-lookup"><span data-stu-id="773fe-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="773fe-199">Her şeyi gözlemlenen olarak işaretlemek, kanala daha fazla veri yazılıncaya kadar `PipeReader.ReadAsync` bir sonraki çağrının dönemeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="773fe-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="773fe-200">Diğer herhangi bir değer, bir sonraki çağrının `PipeReader.ReadAsync` gözlemlenen *ve* gözlemlenen verilerle hemen döndürülmesini sağlar, ancak daha önce tüketilen veriler.</span><span class="sxs-lookup"><span data-stu-id="773fe-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="773fe-201">Akış verilerini okuma senaryoları</span><span class="sxs-lookup"><span data-stu-id="773fe-201">Read streaming data scenarios</span></span>

<span data-ttu-id="773fe-202">Akış verilerini okumaya çalışırken ortaya çıktı olan birkaç tipik desen vardır:</span><span class="sxs-lookup"><span data-stu-id="773fe-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="773fe-203">Veri akışı verildiğinde, tek bir iletiyi ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="773fe-204">Veri akışı verildiğinde, tüm kullanılabilir iletileri ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="773fe-205">Aşağıdaki örneklerde, bir `ReadOnlySequence<byte>`iletileri ayrıştırmak için `TryParseMessage` yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="773fe-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="773fe-206">`TryParseMessage` tek bir iletiyi ayrıştırır ve ayrıştırılmış iletiyi arabellekten kırpmak için giriş arabelleğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="773fe-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="773fe-207">`TryParseMessage` .NET 'in bir parçası değildir, bu, aşağıdaki bölümlerde kullanılan bir kullanıcı yazılmış yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="773fe-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="773fe-208">Tek bir iletiyi okuyun</span><span class="sxs-lookup"><span data-stu-id="773fe-208">Read a single message</span></span>

<span data-ttu-id="773fe-209">Aşağıdaki kod `PipeReader` tek bir ileti okur ve bunu çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="773fe-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="773fe-210">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="773fe-210">The preceding code:</span></span>

* <span data-ttu-id="773fe-211">Tek bir ileti ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-211">Parses a single message.</span></span>
* <span data-ttu-id="773fe-212">Tüketilen `SequencePosition` güncelleştirir ve kırpılan giriş arabelleğinin başlangıcına işaret etmek için `SequencePosition` incelenir.</span><span class="sxs-lookup"><span data-stu-id="773fe-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="773fe-213">İki `SequencePosition` bağımsız değişkeni güncelleştirilir çünkü `TryParseMessage` ayrıştırılmış iletiyi giriş arabelleğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="773fe-214">Genellikle, arabellekteki tek bir ileti ayrıştırılırken, incelenen konum aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="773fe-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="773fe-215">İletinin sonu.</span><span class="sxs-lookup"><span data-stu-id="773fe-215">The end of the message.</span></span>
* <span data-ttu-id="773fe-216">İleti bulunmazsa alınan arabelleğin sonu.</span><span class="sxs-lookup"><span data-stu-id="773fe-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="773fe-217">Tek ileti durumunun hata için en olası olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="773fe-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="773fe-218">Yanlış değerleri *incelenmeye* geçirmek, yetersiz bellek özel durumu veya sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="773fe-219">Daha fazla bilgi için bu makaledeki [Pıpereader ortak sorunlar](#gotchas) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="773fe-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="773fe-220">Birden çok ileti okunuyor</span><span class="sxs-lookup"><span data-stu-id="773fe-220">Reading multiple messages</span></span>

<span data-ttu-id="773fe-221">Aşağıdaki kod bir `PipeReader` tüm iletileri okur ve her bir `ProcessMessageAsync` çağırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="773fe-222">İptal</span><span class="sxs-lookup"><span data-stu-id="773fe-222">Cancellation</span></span>

<span data-ttu-id="773fe-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="773fe-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="773fe-224"><xref:System.Threading.CancellationToken>geçirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="773fe-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="773fe-225">Bir okuma beklemede olduğunda `CancellationToken` iptal edilirse bir <xref:System.OperationCanceledException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="773fe-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="773fe-226">, Geçerli okuma işlemini <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>aracılığıyla iptal etmek için bir yol destekler, bu da bir özel durumun çıkarılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="773fe-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="773fe-227">`PipeReader.CancelPendingRead` çağırmak, geçerli veya sonraki `PipeReader.ReadAsync` çağrının `IsCanceled` <xref:System.IO.Pipelines.ReadResult> ile `true`döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="773fe-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="773fe-228">Bu, var olan okuma döngüsünü bozucu olmayan ve olağanüstü olmayan bir şekilde sonlandırmanız için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="773fe-229">Piypereader yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="773fe-229">PipeReader common problems</span></span>

* <span data-ttu-id="773fe-230">Yanlış değerleri `consumed` veya `examined` geçirmek, zaten okuma verilerinin okunmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="773fe-231">`buffer.End` İncelenme olarak geçirilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="773fe-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="773fe-232">Durdurulmuş veriler</span><span class="sxs-lookup"><span data-stu-id="773fe-232">Stalled data</span></span>
  * <span data-ttu-id="773fe-233">Veriler tüketilmemişse, büyük olasılıkla yetersiz bellek (OOM) özel durumu.</span><span class="sxs-lookup"><span data-stu-id="773fe-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="773fe-234">Örneğin, her seferinde tek bir ileti işlenirken `PipeReader.AdvanceTo(position, buffer.End)`.</span><span class="sxs-lookup"><span data-stu-id="773fe-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="773fe-235">Yanlış değerleri `consumed` veya `examined` geçirmek sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="773fe-236">Örneğin, `buffer.Start` değiştirilmemişse `PipeReader.AdvanceTo(buffer.Start)`, yeni veri alınmadan hemen önce `PipeReader.ReadAsync` bir sonraki çağrının dönmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="773fe-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="773fe-237">Yanlış değerleri `consumed` veya `examined` geçirmek sonsuz arabelleğe alma (nihai OOM) ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="773fe-238">`PipeReader.AdvanceTo` çağrıldıktan sonra `ReadOnlySequence<byte>` kullanmak bellek bozulmasına neden olabilir (ücretsiz olarak kullanabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="773fe-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="773fe-239">`PipeReader.Complete/CompleteAsync` çağıramayan bellek sızıntısına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="773fe-240">Veri kaybına neden olan arabellek sonuçlarını işlemeden önce <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> denetleniyor ve okuma mantığı çıkıyor.</span><span class="sxs-lookup"><span data-stu-id="773fe-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="773fe-241">Döngü çıkış koşulunun `ReadResult.Buffer.IsEmpty` ve `ReadResult.IsCompleted`temel almalıdır.</span><span class="sxs-lookup"><span data-stu-id="773fe-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="773fe-242">Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="773fe-243">Sorunlu kod</span><span class="sxs-lookup"><span data-stu-id="773fe-243">Problematic code</span></span>

<span data-ttu-id="773fe-244">❌ **veri kaybı**</span><span class="sxs-lookup"><span data-stu-id="773fe-244">❌ **Data loss**</span></span>

<span data-ttu-id="773fe-245">`ReadResult`, `IsCompleted` `true`olarak ayarlandığında son veri segmentini döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="773fe-246">Okuma döngüsünden çıkmadan önce bu verilerin okunmamasından dolayı veri kaybı olur.</span><span class="sxs-lookup"><span data-stu-id="773fe-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="773fe-247">❌ **sonsuz döngü**</span><span class="sxs-lookup"><span data-stu-id="773fe-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="773fe-248">Aşağıdaki mantık, `Result.IsCompleted` `true`, ancak arabellekte hiç tamamlanmamış bir ileti varsa sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="773fe-249">Aynı sorunu içeren başka bir kod parçası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="773fe-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="773fe-250">`ReadResult.IsCompleted`denetlemeden önce boş olmayan bir arabellek denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="773fe-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="773fe-251">Bir `else if`olduğundan, arabellekte hiç bir ileti yoksa, süresiz olarak döngü yapılır.</span><span class="sxs-lookup"><span data-stu-id="773fe-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="773fe-252">**beklenmeyen ❌ askıda**</span><span class="sxs-lookup"><span data-stu-id="773fe-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="773fe-253">`examined` konumundaki `buffer.End` ile `PipeReader.AdvanceTo` koşulsuz olarak çağırmanın tek bir ileti ayrıştırılırken askıda kalmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="773fe-254">`PipeReader.AdvanceTo` sonraki çağrısı şu kadar döndürmez:</span><span class="sxs-lookup"><span data-stu-id="773fe-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="773fe-255">Kanala yazılan daha fazla veri var.</span><span class="sxs-lookup"><span data-stu-id="773fe-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="773fe-256">Ve yeni veriler daha önce incelendi.</span><span class="sxs-lookup"><span data-stu-id="773fe-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="773fe-257">**yetersiz bellek (OOM)** ❌</span><span class="sxs-lookup"><span data-stu-id="773fe-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="773fe-258">Aşağıdaki koşullara göre aşağıdaki kod, <xref:System.OutOfMemoryException> gerçekleşene kadar arabelleğe almayı sürdürür:</span><span class="sxs-lookup"><span data-stu-id="773fe-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="773fe-259">En büyük ileti boyutu yok.</span><span class="sxs-lookup"><span data-stu-id="773fe-259">There's no maximum message size.</span></span>
* <span data-ttu-id="773fe-260">`PipeReader` döndürülen veriler, tüm iletileri yapmaz.</span><span class="sxs-lookup"><span data-stu-id="773fe-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="773fe-261">Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB bir ileti) yazıldığı için, bu tam bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="773fe-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="773fe-262">❌ **belleği bozulması**</span><span class="sxs-lookup"><span data-stu-id="773fe-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="773fe-263">Arabelleği okuyan yardımcıları yazarken, `Advance`çağrılmadan önce döndürülen yükün kopyalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="773fe-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="773fe-264">Aşağıdaki örnek, `Pipe` atılan belleği döndürür ve bir sonraki işlem (okuma/yazma) için onu yeniden kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="773fe-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="773fe-265">PipeWriter</span></span>

<span data-ttu-id="773fe-266"><xref:System.IO.Pipelines.PipeWriter>, arayan adına yazma arabelleğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="773fe-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="773fe-267">`PipeWriter` [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)uygular.</span><span class="sxs-lookup"><span data-stu-id="773fe-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="773fe-268">`IBufferWriter<byte>` ek arabellek kopyaları olmadan yazma işlemleri gerçekleştirmek için arabelleklere erişim sağlamak mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="773fe-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="773fe-269">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="773fe-269">The previous code:</span></span>

* <span data-ttu-id="773fe-270"><xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>kullanarak `PipeWriter` en az 5 baytlık bir arabellek ister.</span><span class="sxs-lookup"><span data-stu-id="773fe-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="773fe-271">`"Hello"` ASCII dizesinin bayt sayısını döndürülen `Memory<byte>`yazar.</span><span class="sxs-lookup"><span data-stu-id="773fe-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="773fe-272">Arabelleğe kaç bayt yazıldığını belirten <xref:System.IO.Pipelines.PipeWriter.Advance%2A> çağırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="773fe-273">, Baytları temel alınan cihaza gönderen `PipeWriter`boşaltır.</span><span class="sxs-lookup"><span data-stu-id="773fe-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="773fe-274">Önceki yazma yöntemi, `PipeWriter`tarafından belirtilen arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="773fe-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="773fe-275">Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="773fe-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="773fe-276">Mevcut arabelleği `PipeWriter`kopyalar.</span><span class="sxs-lookup"><span data-stu-id="773fe-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="773fe-277">`GetSpan`çağırır `Advance` ve <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>çağırır.</span><span class="sxs-lookup"><span data-stu-id="773fe-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="773fe-278">İptal</span><span class="sxs-lookup"><span data-stu-id="773fe-278">Cancellation</span></span>

<span data-ttu-id="773fe-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> <xref:System.Threading.CancellationToken>geçirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="773fe-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="773fe-280">Bir `CancellationToken` geçirme işlemi, belirteç bekleyen bir temizleme işlemi sırasında iptal edilirse bir `OperationCanceledException` sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="773fe-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="773fe-281">`PipeWriter.FlushAsync`, özel durum oluşturmadan <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> aracılığıyla geçerli temizleme işlemini iptal etmek için bir yol destekler.</span><span class="sxs-lookup"><span data-stu-id="773fe-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="773fe-282">`PipeWriter.CancelPendingFlush` çağırmak, geçerli veya sonraki `PipeWriter.FlushAsync` veya `PipeWriter.WriteAsync` çağrının `IsCanceled` ayarlanmış `true`bir <xref:System.IO.Pipelines.FlushResult> döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="773fe-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="773fe-283">Bu, bozucu olmayan ve olağanüstü olmayan bir şekilde boşaltmayı Temizleme için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="773fe-284">PipeWriter ortak sorunları</span><span class="sxs-lookup"><span data-stu-id="773fe-284">PipeWriter common problems</span></span>

* <span data-ttu-id="773fe-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> en az istenen bellek miktarına sahip bir arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="773fe-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="773fe-286">Tam arabellek boyutlarını kabul **etmeyin** .</span><span class="sxs-lookup"><span data-stu-id="773fe-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="773fe-287">Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="773fe-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="773fe-288">Daha fazla veri yazmaya devam etmek için <xref:System.IO.Pipelines.PipeWriter.Advance%2A> çağrıldıktan sonra yeni bir arabellek istenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="773fe-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="773fe-289">Daha önce edinilen arabelleğin üzerine yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="773fe-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="773fe-290">`FlushAsync` tamamlanmamış bir çağrı olduğundan `GetMemory` veya `GetSpan` çağırma.</span><span class="sxs-lookup"><span data-stu-id="773fe-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="773fe-291">Verilerin temizlenme sırasında `Complete` veya `CompleteAsync` çağırmak bellek bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="773fe-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="773fe-292">IDuplexPipe</span></span>

<span data-ttu-id="773fe-293"><xref:System.IO.Pipelines.IDuplexPipe>, hem okumayı hem de yazmayı destekleyen türler için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="773fe-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="773fe-294">Örneğin, bir ağ bağlantısı bir `IDuplexPipe`tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="773fe-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="773fe-295">Bir `PipeReader` ve `PipeWriter`içeren `Pipe` aksine, `IDuplexPipe` tam çift yönlü bağlantının tek tarafını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="773fe-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="773fe-296">Bu, `PipeWriter` yazılan ve `PipeReader`okunmayacak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="773fe-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="773fe-297">Akışlar</span><span class="sxs-lookup"><span data-stu-id="773fe-297">Streams</span></span>

<span data-ttu-id="773fe-298">Akış verilerini okurken veya yazarken genellikle seri hale getirici kullanarak verileri okur ve serileştirici kullanarak verileri yazın.</span><span class="sxs-lookup"><span data-stu-id="773fe-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="773fe-299">Bu okuma ve yazma akışı API 'Lerinin çoğu bir `Stream` parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="773fe-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="773fe-300">Bu mevcut API 'lerle tümleştirmeyi kolaylaştırmak için `PipeReader` ve `PipeWriter` <xref:System.IO.Pipelines.PipeReader.AsStream%2A>kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="773fe-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="773fe-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>, `PipeReader` veya `PipeWriter`etrafında `Stream` bir uygulama döndürür.</span><span class="sxs-lookup"><span data-stu-id="773fe-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
