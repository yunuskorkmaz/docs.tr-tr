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
ms.openlocfilehash: 53d7bbf214a71daff9372efcd5978f34c066c657
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320000"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="41bbc-103">.NET 'teki System. ıO. işlem hatları</span><span class="sxs-lookup"><span data-stu-id="41bbc-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="41bbc-104"><xref:System.IO.Pipelines>, .NET ortamında yüksek performanslı g/ç 'yi daha kolay hale getirmek için tasarlanan yeni bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="41bbc-105">Bu, tüm .NET uygulamalarında çalışacak .NET Standard hedefleme bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="41bbc-106">System. ıO. hatlarını çözme sorunu</span><span class="sxs-lookup"><span data-stu-id="41bbc-106">What problem does System.IO.Pipelines solve</span></span>
<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="41bbc-107">Akış verilerini ayrıştırmaya yönelik uygulamalar, çok sayıda özel ve olağandışı kod akışına sahip ortak koddan oluşur.</span><span class="sxs-lookup"><span data-stu-id="41bbc-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="41bbc-108">Ortak ve özel durum kodu karmaşık ve devam etmek zordur.</span><span class="sxs-lookup"><span data-stu-id="41bbc-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="41bbc-109">`System.IO.Pipelines` şu şekilde tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="41bbc-110">Akış verilerinin yüksek performans ayrıştırması vardır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="41bbc-111">Kod karmaşıklığını azaltın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-111">Reduce code complexity.</span></span>

<span data-ttu-id="41bbc-112">Aşağıdaki kod, bir istemciden satır sınırlı iletileri (`'\n'` ile sınırlandırılmış) alan bir TCP sunucusu için tipik bir noktadır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);
    
    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="41bbc-113">Yukarıdaki kodda birkaç sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="41bbc-114">Tüm ileti (satır sonu) `ReadAsync` ' a yapılan tek bir çağrıda alınmayabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="41bbc-115">@No__t-0 sonucu yok sayılıyor.</span><span class="sxs-lookup"><span data-stu-id="41bbc-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="41bbc-116">`stream.ReadAsync`, okunan veri miktarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="41bbc-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="41bbc-117">Tek bir `ReadAsync` çağrısında birden çok satırın okunduğu durumu işlemez.</span><span class="sxs-lookup"><span data-stu-id="41bbc-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="41bbc-118">Her okuma ile bir `byte` dizisi ayırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="41bbc-119">Yukarıdaki sorunları onarmak için aşağıdaki değişiklikler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="41bbc-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="41bbc-120">Yeni bir satır bulunana kadar gelen verileri arabelleğe koyun.</span><span class="sxs-lookup"><span data-stu-id="41bbc-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="41bbc-121">Arabellekte döndürülen tüm satırları ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="41bbc-122">Satır 1 KB 'den büyük (1024 bayt) olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="41bbc-123">Bu kodun, arabelleğin içindeki tamamlanma satırına sığması için sınırlayıcı bulunana kadar giriş arabelleğini yeniden boyutlandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="41bbc-124">Arabellek yeniden boyutlandırılırsa, girişte daha uzun çizgiler göründüğü sürece daha fazla arabellek kopyası yapılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="41bbc-125">Harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="41bbc-126">Belleği sürekli ayırmayı önlemek için arabellek havuzu kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="41bbc-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="41bbc-127">Aşağıdaki kod bu sorunlardan bazılarını ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="41bbc-128">Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez.</span><span class="sxs-lookup"><span data-stu-id="41bbc-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="41bbc-129">Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="41bbc-130">`System.IO.Pipelines`, bu tür kodu daha kolay yazmayı kolaylaştırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

## <a name="pipe"></a><span data-ttu-id="41bbc-131">Kapatıldığı</span><span class="sxs-lookup"><span data-stu-id="41bbc-131">Pipe</span></span>

<span data-ttu-id="41bbc-132">@No__t-0 sınıfı bir `PipeWriter/PipeReader` çifti oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="41bbc-133">@No__t-0 ' a yazılan tüm veriler `PipeReader` ' de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="41bbc-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="41bbc-134">Kanal temel kullanımı</span><span class="sxs-lookup"><span data-stu-id="41bbc-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="41bbc-135">İki döngü vardır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-135">There are two loops:</span></span>

* <span data-ttu-id="41bbc-136">`FillPipeAsync` `Socket` ' den okur ve `PipeWriter` ' ye yazar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="41bbc-137">`ReadPipeAsync` `PipeReader` ' den okur ve gelen satırları ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="41bbc-138">Ayrılmış açık arabellek yok.</span><span class="sxs-lookup"><span data-stu-id="41bbc-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="41bbc-139">Tüm arabellek yönetimi, `PipeReader` ve `PipeWriter` uygulamalarına devredildi.</span><span class="sxs-lookup"><span data-stu-id="41bbc-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="41bbc-140">Arabellek yönetimi için temsilci seçme, kodun yalnızca iş mantığına odaklanılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="41bbc-141">İlk döngüde:</span><span class="sxs-lookup"><span data-stu-id="41bbc-141">In the first loop:</span></span>

* <span data-ttu-id="41bbc-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>, temel kümeden belleği almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="41bbc-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>, arabelleğe ne kadar veri yazıldığını @no__t söylemek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="41bbc-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>, verileri `PipeReader` ' e kullanılabilir hale getirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="41bbc-145">İkinci döngüde `PipeReader` `PipeWriter` tarafından yazılan arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="41bbc-146">Arabellekler yuvadan gelir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-146">The buffers come from the socket.</span></span> <span data-ttu-id="41bbc-147">@No__t-0 ' a çağrı:</span><span class="sxs-lookup"><span data-stu-id="41bbc-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="41bbc-148">İki önemli bilgi parçasını içeren <xref:System.IO.Pipelines.ReadResult> döndürür:</span><span class="sxs-lookup"><span data-stu-id="41bbc-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="41bbc-149">@No__t-0 biçiminde okunan veriler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="41bbc-150">Verilerin sonuna (EOF) ulaşıldığını belirten bir Boole `IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="41bbc-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span> 

<span data-ttu-id="41bbc-151">Satır sonu (EOL) sınırlayıcısı bulduktan ve satırı ayrıştırdıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="41bbc-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="41bbc-152">Mantık, zaten işlenmiş olan öğeleri atlamak için arabelleği işler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="41bbc-153">`PipeReader.AdvanceTo` ' a, ne kadar veri tüketildiğini ve inceleyeceğinizi @no__t söylemek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="41bbc-154">Okuyucu ve yazıcı döngüleri `Complete` çağırarak biter.</span><span class="sxs-lookup"><span data-stu-id="41bbc-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="41bbc-155">`Complete`, temeldeki kanalın ayrılan belleği serbest bırakmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="41bbc-156">Arka basınç ve akış denetimi</span><span class="sxs-lookup"><span data-stu-id="41bbc-156">Backpressure and flow control</span></span>

<span data-ttu-id="41bbc-157">İdeal olarak, birlikte iş okuma ve ayrıştırma:</span><span class="sxs-lookup"><span data-stu-id="41bbc-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="41bbc-158">Yazma iş parçacığı ağdan verileri tüketir ve arabelleğe koyar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="41bbc-159">Ayrıştırma iş parçacığı, uygun veri yapılarını oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="41bbc-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="41bbc-160">Genellikle, ayrıştırma yalnızca ağdan veri bloklarını kopyalamaya kıyasla daha fazla zaman alır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="41bbc-161">Okuma iş parçacığı ayrıştırma iş parçacığının önüne alınır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="41bbc-162">Okuma iş parçacığı, ayrıştırma iş parçacığı için verileri depolamak üzere yavaşlıyor veya daha fazla bellek ayırmıştır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="41bbc-163">En iyi performans için, sık duraklamalar ve daha fazla bellek ayırma arasında bir denge vardır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="41bbc-164">Önceki sorunu çözmek için, `Pipe` ' ın veri akışını denetlemek için iki ayarı vardır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="41bbc-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> duraklatmaya çağrı yapmadan önce ne kadar verinin arabelleğe alınacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="41bbc-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: okuyucunun `PipeWriter.FlushAsync` sürdürülmesine geçmeden önce ne kadar veri gözlemleyecek olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![ResumeWriterThreshold ve PauseWriterThreshold ile diyagram](./media/pipelines/resume-pause.png)

<span data-ttu-id="41bbc-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="41bbc-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="41bbc-169">@No__t-1 ' deki veri miktarı `PauseWriterThreshold` ' den kesişse, tamamlanmamış `ValueTask<FlushResult>` döndürür.</span><span class="sxs-lookup"><span data-stu-id="41bbc-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="41bbc-170">@No__t, `ResumeWriterThreshold` ' den daha düşük hale geldiğinde 0 ' a tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="41bbc-171">Tek bir değer kullanılırsa oluşabilecek hızlı döngüyü engellemek için iki değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="41bbc-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="41bbc-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="41bbc-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="41bbc-173">PipeScheduler</span></span>

<span data-ttu-id="41bbc-174">Genellikle `async` ve `await` kullanılırken, zaman uyumsuz kod <xref:System.Threading.Tasks.TaskScheduler> üzerinde veya geçerli <xref:System.Threading.SynchronizationContext> üzerinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="41bbc-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="41bbc-175">G/ç yaparken, g/ç 'nin gerçekleştirildiği noktada ayrıntılı denetime sahip olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="41bbc-176">Bu denetim, CPU önbelleklerinin etkin bir şekilde yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="41bbc-177">Verimli önbelleğe alma, Web sunucuları gibi yüksek performanslı uygulamalar için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="41bbc-178"><xref:System.IO.Pipelines.PipeScheduler>, zaman uyumsuz geri çağırmaların çalıştığı konum üzerinde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="41bbc-179">Varsayılan olarak:</span><span class="sxs-lookup"><span data-stu-id="41bbc-179">By default:</span></span>

* <span data-ttu-id="41bbc-180">Geçerli <xref:System.Threading.SynchronizationContext> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="41bbc-181">@No__t-0 yoksa, geri çağırmaları çalıştırmak için iş parçacığı havuzunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="41bbc-182">[Pipescheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) , geri çağırmaları iş parçacığı havuzuna sıraya alan <xref:System.IO.Pipelines.PipeScheduler> uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="41bbc-183">`PipeScheduler.ThreadPool` varsayılandır ve genellikle en iyi seçimdir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="41bbc-184">[Pipescheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) , kilitlenme gibi istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="41bbc-185">Kanal sıfırlama</span><span class="sxs-lookup"><span data-stu-id="41bbc-185">Pipe reset</span></span>

<span data-ttu-id="41bbc-186">@No__t-0 nesnesini yeniden kullanmak sıklıkla etkilidir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="41bbc-187">Kanalı sıfırlamak için, hem `PipeReader` hem de `PipeWriter` tamamlandığında <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="41bbc-188">Piypereader</span><span class="sxs-lookup"><span data-stu-id="41bbc-188">PipeReader</span></span>

<span data-ttu-id="41bbc-189"><xref:System.IO.Pipelines.PipeReader>, arayanın adına belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="41bbc-190">@No__t-2 çağrıldıktan sonra **her zaman** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41bbc-191">Bu, `PipeReader` ' ın, Arayıcı bellekle izlenebilmesi için ne zaman yapıldığını bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="41bbc-192">@No__t-1 ' den döndürülen `ReadOnlySequence<byte>` yalnızca `PipeReader.AdvanceTo` ' a çağrı yapana kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="41bbc-193">@No__t-1 çağrıldıktan sonra `ReadOnlySequence<byte>` kullanmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="41bbc-194">`PipeReader.AdvanceTo` iki <xref:System.SequencePosition> bağımsız değişkeni alır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="41bbc-195">İlk bağımsız değişken, ne kadar bellek tüketildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="41bbc-196">İkinci bağımsız değişken, arabelleğin ne kadarının gözlemlendiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="41bbc-197">Verileri tüketilen olarak işaretlemek, kanalın belleği temel alınan arabellek havuzuna döndürebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="41bbc-198">Verileri gözlemlenen olarak işaretlemek, `PipeReader.ReadAsync` ' a yapılan bir sonraki çağrının ne olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="41bbc-199">Her şeyi gözlemlenen olarak işaretlemek, kanala daha fazla veri yazılıncaya kadar `PipeReader.ReadAsync` ' a yapılan bir sonraki çağrının dönemeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="41bbc-200">Diğer herhangi bir değer, `PipeReader.ReadAsync` ' a bir sonraki çağrının, gözlemlenen *ve* gözlemlenen verilerle hemen geri dönmesini sağlar, ancak daha önce tüketilen veriler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="41bbc-201">Akış verilerini okuma senaryoları</span><span class="sxs-lookup"><span data-stu-id="41bbc-201">Read streaming data scenarios</span></span>

<span data-ttu-id="41bbc-202">Akış verilerini okumaya çalışırken ortaya çıktı olan birkaç tipik desen vardır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="41bbc-203">Veri akışı verildiğinde, tek bir iletiyi ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="41bbc-204">Veri akışı verildiğinde, tüm kullanılabilir iletileri ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="41bbc-205">Aşağıdaki örneklerde, bir `ReadOnlySequence<byte>` ' den iletileri ayrıştırmak için `TryParseMessage` yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="41bbc-206">`TryParseMessage` tek bir iletiyi ayrıştırır ve ayrıştırılmış iletiyi arabelleğin kırpıldığı için giriş arabelleğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="41bbc-207">`TryParseMessage` .NET kapsamında değildir, bu, aşağıdaki bölümlerde kullanılan bir kullanıcı yazılmış yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="41bbc-208">Tek bir iletiyi okuyun</span><span class="sxs-lookup"><span data-stu-id="41bbc-208">Read a single message</span></span>

<span data-ttu-id="41bbc-209">Aşağıdaki kod `PipeReader` ' dan tek bir ileti okur ve bunu çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="41bbc-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="41bbc-210">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="41bbc-210">The preceding code:</span></span>

* <span data-ttu-id="41bbc-211">Tek bir ileti ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-211">Parses a single message.</span></span>
* <span data-ttu-id="41bbc-212">Tüketilen `SequencePosition` ' ı güncelleştirir ve kırpılan giriş arabelleğinin başlangıcına işaret etmek için `SequencePosition` ' i inceledi.</span><span class="sxs-lookup"><span data-stu-id="41bbc-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="41bbc-213">İki `SequencePosition` bağımsız değişkeni güncelleştirilir çünkü `TryParseMessage` ayrıştırılmış iletiyi giriş arabelleğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="41bbc-214">Genellikle, arabellekteki tek bir ileti ayrıştırılırken, incelenen konum aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="41bbc-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="41bbc-215">İletinin sonu.</span><span class="sxs-lookup"><span data-stu-id="41bbc-215">The end of the message.</span></span>
* <span data-ttu-id="41bbc-216">İleti bulunmazsa alınan arabelleğin sonu.</span><span class="sxs-lookup"><span data-stu-id="41bbc-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="41bbc-217">Tek ileti durumunun hata için en olası olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="41bbc-218">Yanlış değerleri *incelenmeye* geçirmek, yetersiz bellek özel durumu veya sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="41bbc-219">Daha fazla bilgi için bu makaledeki [Pıpereader ortak sorunlar](#gotchas) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="41bbc-220">Birden çok ileti okunuyor</span><span class="sxs-lookup"><span data-stu-id="41bbc-220">Reading multiple messages</span></span>

<span data-ttu-id="41bbc-221">Aşağıdaki kod `PipeReader` ' dan gelen tüm iletileri okur ve her biri üzerinde `ProcessMessageAsync` ' i çağırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="41bbc-222">İptal Etme</span><span class="sxs-lookup"><span data-stu-id="41bbc-222">Cancellation</span></span>

<span data-ttu-id="41bbc-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="41bbc-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="41bbc-224">@No__t geçirmeyi destekler-0.</span><span class="sxs-lookup"><span data-stu-id="41bbc-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="41bbc-225">Bir okuma beklemede olduğunda, `CancellationToken` iptal edilirse bir <xref:System.OperationCanceledException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41bbc-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="41bbc-226">, Bir özel durumun çıkarılmasını önleyen <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> aracılığıyla geçerli okuma işlemini iptal etmenin bir yolunu destekler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="41bbc-227">@No__t-0 ' a çağırmak, geçerli veya sonraki `PipeReader.ReadAsync` çağrısının `IsCanceled` ' i `true` ' e ayarlı <xref:System.IO.Pipelines.ReadResult> ' i döndürmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="41bbc-228">Bu, var olan okuma döngüsünü bozucu olmayan ve olağanüstü olmayan bir şekilde sonlandırmanız için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="41bbc-229">Piypereader yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="41bbc-229">PipeReader common problems</span></span>

* <span data-ttu-id="41bbc-230">@No__t-0 veya `examined` ' e yanlış değerler geçirmek, zaten okunan verileri okumaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="41bbc-231">@No__t-0 ' ın incelenmesiyle geçirilmesi şu sonucu verebilir:</span><span class="sxs-lookup"><span data-stu-id="41bbc-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="41bbc-232">Durdurulmuş veriler</span><span class="sxs-lookup"><span data-stu-id="41bbc-232">Stalled data</span></span>
  * <span data-ttu-id="41bbc-233">Veriler tüketilmemişse, büyük olasılıkla yetersiz bellek (OOM) özel durumu.</span><span class="sxs-lookup"><span data-stu-id="41bbc-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="41bbc-234">Örneğin, her seferinde tek bir ileti işlenirken `PipeReader.AdvanceTo(position, buffer.End)`.</span><span class="sxs-lookup"><span data-stu-id="41bbc-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="41bbc-235">@No__t-0 veya `examined` ' e yanlış değerler geçirilme sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="41bbc-236">Örneğin, @no__t `buffer.Start` ' i değişmemişse, yeni veriler alınmadan hemen önce `PipeReader.ReadAsync` ' ye yapılan bir sonraki çağrının geri dönmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="41bbc-237">@No__t-0 veya `examined` ' e yanlış değerler geçirilmesi sonsuz arabelleğe alma (nihai OOM) ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="41bbc-238">@No__t-0 ' i çağırdıktan sonra, `PipeReader.AdvanceTo` ' in kullanılması bellek bozulmasına yol açabilir (ücretsiz olarak kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="41bbc-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="41bbc-239">@No__t-0 çağrlamaması, bellek sızıntısına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="41bbc-240">Veri kaybına neden olan arabellek sonuçlarını işlemeden önce <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> denetleniyor ve okuma mantığını çıkıyor.</span><span class="sxs-lookup"><span data-stu-id="41bbc-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="41bbc-241">Döngü çıkış koşulunun `ReadResult.Buffer.IsEmpty` ve `ReadResult.IsCompleted` temelinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="41bbc-242">Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="41bbc-243">Sorunlu kod</span><span class="sxs-lookup"><span data-stu-id="41bbc-243">Problematic code</span></span>

<span data-ttu-id="41bbc-244">❌ **veri kaybı**</span><span class="sxs-lookup"><span data-stu-id="41bbc-244">❌ **Data loss**</span></span>

<span data-ttu-id="41bbc-245">@No__t-0, `IsCompleted` `true` olarak ayarlandığında verilerin son segmentini döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="41bbc-246">Okuma döngüsünden çıkmadan önce bu verilerin okunmamasından dolayı veri kaybı olur.</span><span class="sxs-lookup"><span data-stu-id="41bbc-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="41bbc-247">❌ **sonsuz döngü**</span><span class="sxs-lookup"><span data-stu-id="41bbc-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="41bbc-248">@No__t-0 `true` ise ve arabellekte hiç tam ileti yoksa, aşağıdaki mantık sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="41bbc-249">Aynı sorunu içeren başka bir kod parçası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="41bbc-250">@No__t-0 denetlemeden önce boş olmayan bir arabellek denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="41bbc-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="41bbc-251">@No__t-0 olduğundan, arabellekte hiç tam ileti yoksa sonsuza kadar döngüye alınır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="41bbc-252">❌ **beklenmeyen askı**</span><span class="sxs-lookup"><span data-stu-id="41bbc-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="41bbc-253">@No__t-2 konumunda `buffer.End` ile @no__t koşulsuz olarak çağırmanın tek bir ileti ayrıştırılırken askıda kalmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="41bbc-254">@No__t-0 ' a yapılan bir sonraki çağrı şu kadar döndürmez:</span><span class="sxs-lookup"><span data-stu-id="41bbc-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="41bbc-255">Kanala yazılan daha fazla veri var.</span><span class="sxs-lookup"><span data-stu-id="41bbc-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="41bbc-256">Ve yeni veriler daha önce incelendi.</span><span class="sxs-lookup"><span data-stu-id="41bbc-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="41bbc-257">❌ **yetersiz bellek (OOM)**</span><span class="sxs-lookup"><span data-stu-id="41bbc-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="41bbc-258">Aşağıdaki koşullara göre aşağıdaki kod <xref:System.OutOfMemoryException> gerçekleşene kadar arabelleğe almayı sürdürür:</span><span class="sxs-lookup"><span data-stu-id="41bbc-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="41bbc-259">En büyük ileti boyutu yok.</span><span class="sxs-lookup"><span data-stu-id="41bbc-259">There's no maximum message size.</span></span>
* <span data-ttu-id="41bbc-260">@No__t-0 ' dan döndürülen veriler tam bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="41bbc-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="41bbc-261">Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB bir ileti) yazıldığı için, bu tam bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="41bbc-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="41bbc-262">❌ **bellek bozulması**</span><span class="sxs-lookup"><span data-stu-id="41bbc-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="41bbc-263">Arabelleği okuyan yardımcıları yazarken, `Advance` çağrılmadan önce döndürülen yükün kopyalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="41bbc-264">Aşağıdaki örnek, `Pipe` ' ın atılacağını ve bir sonraki işlem (okuma/yazma) için onu yeniden kullanabildiğinden belleği döndürür.</span><span class="sxs-lookup"><span data-stu-id="41bbc-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="41bbc-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="41bbc-265">PipeWriter</span></span>

<span data-ttu-id="41bbc-266">@No__t-0, arayanın adına yazma arabelleğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="41bbc-267">`PipeWriter` [@no__t uygular-2](xref:System.Buffers.IBufferWriter`1).</span><span class="sxs-lookup"><span data-stu-id="41bbc-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1).</span></span> <span data-ttu-id="41bbc-268">`IBufferWriter<byte>`, ek arabellek kopyaları olmadan yazma işlemleri gerçekleştirmek için arabelleklere erişim sağlamak mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="41bbc-269">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="41bbc-269">The previous code:</span></span>

* <span data-ttu-id="41bbc-270">@No__t-1 kullanarak `PipeWriter` ' dan en az 5 baytlık bir arabellek ister.</span><span class="sxs-lookup"><span data-stu-id="41bbc-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.</span></span>
* <span data-ttu-id="41bbc-271">ASCII dizesi için bayt `"Hello"` ' yı döndürülen `Span<byte>` öğesine yazar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-271">Writes bytes for the ASCII string `"Hello"` to the returned `Span<byte>`.</span></span>
* <span data-ttu-id="41bbc-272">Arabelleğe kaç bayt yazıldığını belirten <xref:System.IO.Pipelines.PipeWriter.Advance%2A> ' ı çağırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="41bbc-273">Temel cihaza bayt gönderen `PipeWriter` ' ı boşaltır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="41bbc-274">Önceki yazma yöntemi `PipeWriter` tarafından sağlanmış arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="41bbc-275">Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="41bbc-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="41bbc-276">Mevcut arabelleği `PipeWriter` ' a kopyalar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="41bbc-277">@No__t-0, `Advance` ' i uygun şekilde çağırır ve <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> ' i çağırır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="41bbc-278">İptal Etme</span><span class="sxs-lookup"><span data-stu-id="41bbc-278">Cancellation</span></span>

<span data-ttu-id="41bbc-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> <xref:System.Threading.CancellationToken> geçirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="41bbc-280">@No__t-0 ' ın geçirilmesi, bir temizleme işlemi sırasında belirteç iptal edildiğinde, bir `OperationCanceledException` ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="41bbc-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="41bbc-281">`PipeWriter.FlushAsync`, bir özel durum oluşturmadan geçerli temizleme işlemini <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> aracılığıyla iptal etmenin bir yolunu destekler.</span><span class="sxs-lookup"><span data-stu-id="41bbc-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="41bbc-282">@No__t-0 ' a çağırmak, geçerli veya sonraki `PipeWriter.FlushAsync` veya `PipeWriter.WriteAsync` çağrısının `IsCanceled` ile `true` olarak ayarlanmış bir <xref:System.IO.Pipelines.FlushResult> döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="41bbc-283">Bu, bozucu olmayan ve olağanüstü olmayan bir şekilde boşaltmayı Temizleme için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="41bbc-284">PipeWriter ortak sorunları</span><span class="sxs-lookup"><span data-stu-id="41bbc-284">PipeWriter common problems</span></span>

* <span data-ttu-id="41bbc-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>, en az istenen bellek miktarına sahip bir arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="41bbc-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="41bbc-286">Tam arabellek boyutlarını kabul **etmeyin** .</span><span class="sxs-lookup"><span data-stu-id="41bbc-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="41bbc-287">Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="41bbc-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="41bbc-288">Daha fazla veri yazmaya devam etmek için <xref:System.IO.Pipelines.PipeWriter.Advance%2A> çağrıldıktan sonra yeni bir arabelleğin istenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="41bbc-289">Daha önce edinilen arabelleğin üzerine yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="41bbc-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="41bbc-290">@No__t-0 veya `GetSpan` ' i çağırmak, `FlushAsync` ' ye yönelik tamamlanmamış bir çağrı olması durumunda güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="41bbc-291">@No__t-0 veya `CompleteAsync` ' i çağırmak, verilerin temizlenme sırasında bellek bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="41bbc-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="41bbc-292">IDuplexPipe</span></span>

<span data-ttu-id="41bbc-293">@No__t-0, hem okumayı hem de yazmayı destekleyen türler için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="41bbc-294">Örneğin, bir ağ bağlantısı `IDuplexPipe` ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="41bbc-295">@No__t-1 ve bir `PipeWriter` içeren `Pipe` ' dan farklı olarak, `IDuplexPipe` tam çift yönlü bağlantının tek tarafını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41bbc-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="41bbc-296">Bu, @no__t yazılmış olan ve `PipeReader` ' den okunmayacak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="41bbc-297">Akışlar</span><span class="sxs-lookup"><span data-stu-id="41bbc-297">Streams</span></span>

<span data-ttu-id="41bbc-298">Akış verilerini okurken veya yazarken genellikle seri hale getirici kullanarak verileri okur ve serileştirici kullanarak verileri yazın.</span><span class="sxs-lookup"><span data-stu-id="41bbc-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="41bbc-299">Bu okuma ve yazma akışı API 'Lerinin çoğu `Stream` parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="41bbc-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="41bbc-300">Bu mevcut API 'lerle tümleştirmeyi kolaylaştırmak için `PipeReader` ve `PipeWriter` <xref:System.IO.Pipelines.PipeReader.AsStream%2A> ' yi kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="41bbc-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="41bbc-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> `PipeReader` veya `PipeWriter` etrafında `Stream` uygulamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="41bbc-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
