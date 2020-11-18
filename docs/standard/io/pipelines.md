---
title: G/ç işlem hatları-.NET
description: .NET ' te ı/O işlem hatlarını verimli bir şekilde kullanmayı ve kodunuzda sorunlardan kaçınmak hakkında bilgi edinin.
ms.date: 08/27/2020
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 508ae0e2b854f81ee639a63063a8f6d73ae84863
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830642"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="9cab7-103">.NET 'teki System. ıO. işlem hatları</span><span class="sxs-lookup"><span data-stu-id="9cab7-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="9cab7-104"><xref:System.IO.Pipelines> , .NET ortamında yüksek performanslı g/ç 'yi daha kolay hale getirmek için tasarlanan yeni bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="9cab7-105">Bu, tüm .NET uygulamalarında çalışacak .NET Standard hedefleme bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-105">It's a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="9cab7-106">System. ıO. hatlarını çözme sorunu</span><span class="sxs-lookup"><span data-stu-id="9cab7-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="9cab7-107">Akış verilerini ayrıştırmaya yönelik uygulamalar, çok sayıda özel ve olağandışı kod akışına sahip ortak koddan oluşur.</span><span class="sxs-lookup"><span data-stu-id="9cab7-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="9cab7-108">Ortak ve özel durum kodu karmaşık ve devam etmek zordur.</span><span class="sxs-lookup"><span data-stu-id="9cab7-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="9cab7-109">`System.IO.Pipelines` Şu şekilde tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="9cab7-110">Akış verilerinin yüksek performans ayrıştırması vardır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="9cab7-111">Kod karmaşıklığını azaltın.</span><span class="sxs-lookup"><span data-stu-id="9cab7-111">Reduce code complexity.</span></span>

<span data-ttu-id="9cab7-112">Aşağıdaki kod, bir istemciden satır sınırlı iletileri (ile ayrılmış) alan bir TCP sunucusu için tipik bir noktadır `'\n'` :</span><span class="sxs-lookup"><span data-stu-id="9cab7-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="9cab7-113">Yukarıdaki kodda birkaç sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="9cab7-114">Tüm ileti (satır sonu), için tek bir çağrıda alınmayabilir `ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="9cab7-115">Sonucu yok sayılıyor `stream.ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="9cab7-116">`stream.ReadAsync` ne kadar veri okunduğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cab7-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="9cab7-117">Birden çok satırın tek bir çağrıda okunduğu durumu işlemez `ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="9cab7-118">`byte`Her okunan bir diziyi ayırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="9cab7-119">Yukarıdaki sorunları onarmak için aşağıdaki değişiklikler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="9cab7-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="9cab7-120">Yeni bir satır bulunana kadar gelen verileri arabelleğe koyun.</span><span class="sxs-lookup"><span data-stu-id="9cab7-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="9cab7-121">Arabellekte döndürülen tüm satırları ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="9cab7-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="9cab7-122">Satır 1 KB 'den büyük (1024 bayt) olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="9cab7-123">Bu kodun, arabelleğin içindeki tamamlanma satırına sığması için sınırlayıcı bulunana kadar giriş arabelleğini yeniden boyutlandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="9cab7-124">Arabellek yeniden boyutlandırılırsa, girişte daha uzun çizgiler göründüğü sürece daha fazla arabellek kopyası yapılır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="9cab7-125">Harcanan alanı azaltmak için, satırları okumak için kullanılan arabelleği sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="9cab7-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="9cab7-126">Belleği sürekli ayırmayı önlemek için arabellek havuzu kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9cab7-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="9cab7-127">Aşağıdaki kod bu sorunlardan bazılarını ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-127">The following code addresses some of these problems:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

<span data-ttu-id="9cab7-128">Önceki kod karmaşıktır ve tanımlanan tüm sorunları gidermez.</span><span class="sxs-lookup"><span data-stu-id="9cab7-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="9cab7-129">Yüksek performanslı ağ genellikle performansı en üst düzeye çıkarmak için çok karmaşık kod yazmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="9cab7-130">`System.IO.Pipelines` Bu tür bir kodu daha kolay yazmak için tasarlandı.</span><span class="sxs-lookup"><span data-stu-id="9cab7-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="9cab7-131">Kapatıldığı</span><span class="sxs-lookup"><span data-stu-id="9cab7-131">Pipe</span></span>

<span data-ttu-id="9cab7-132"><xref:System.IO.Pipelines.Pipe>Sınıf, bir çift oluşturmak için kullanılabilir `PipeWriter/PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="9cab7-133">İçine yazılan tüm veriler `PipeWriter` ' de kullanılabilir `PipeReader` :</span><span class="sxs-lookup"><span data-stu-id="9cab7-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="9cab7-134">Kanal temel kullanımı</span><span class="sxs-lookup"><span data-stu-id="9cab7-134">Pipe basic usage</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

<span data-ttu-id="9cab7-135">İki döngü vardır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-135">There are two loops:</span></span>

* <span data-ttu-id="9cab7-136">`FillPipeAsync` öğesinden okur `Socket` ve öğesine yazar `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="9cab7-137">`ReadPipeAsync` öğesinden okur `PipeReader` ve gelen satırları ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="9cab7-138">Ayrılmış açık arabellek yok.</span><span class="sxs-lookup"><span data-stu-id="9cab7-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="9cab7-139">Tüm arabellek yönetimi, `PipeReader` ve uygulamalarına Temsilcili `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="9cab7-140">Arabellek yönetimi için temsilci seçme, kodun yalnızca iş mantığına odaklanılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="9cab7-141">İlk döngüde:</span><span class="sxs-lookup"><span data-stu-id="9cab7-141">In the first loop:</span></span>

* <span data-ttu-id="9cab7-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> , temel alınan yazıcıya bellek almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="9cab7-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> , `PipeWriter` arabelleğe ne kadar veri yazıldığını bildirmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="9cab7-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> , verileri için kullanılabilir hale getirmek üzere çağırılır `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="9cab7-145">İkinci döngüde, `PipeReader` tarafından yazılan arabellekleri kullanır `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="9cab7-146">Arabellekler yuvadan gelir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-146">The buffers come from the socket.</span></span> <span data-ttu-id="9cab7-147">Çağrısı `PipeReader.ReadAsync` :</span><span class="sxs-lookup"><span data-stu-id="9cab7-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="9cab7-148"><xref:System.IO.Pipelines.ReadResult>İki önemli bilgi parçasını içeren bir döndürür:</span><span class="sxs-lookup"><span data-stu-id="9cab7-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="9cab7-149">Biçiminde okunan veriler `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="9cab7-150">`IsCompleted`Verilerin sonuna (EOF) ulaşıldığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9cab7-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="9cab7-151">Satır sonu (EOL) sınırlayıcısı bulduktan ve satırı ayrıştırdıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="9cab7-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="9cab7-152">Mantık, zaten işlenmiş olan öğeleri atlamak için arabelleği işler.</span><span class="sxs-lookup"><span data-stu-id="9cab7-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="9cab7-153">`PipeReader.AdvanceTo` ne `PipeReader` kadar veri tüketiğini ve incelendiğini söylemek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="9cab7-154">Okuyucu ve yazıcı döngüleri, çağırarak biter `Complete` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="9cab7-155">`Complete` temeldeki kanalın ayrılan belleği serbest bırakmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="9cab7-156">Arka basınç ve akış denetimi</span><span class="sxs-lookup"><span data-stu-id="9cab7-156">Backpressure and flow control</span></span>

<span data-ttu-id="9cab7-157">İdeal olarak, birlikte iş okuma ve ayrıştırma:</span><span class="sxs-lookup"><span data-stu-id="9cab7-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="9cab7-158">Yazma iş parçacığı ağdan verileri tüketir ve arabelleğe koyar.</span><span class="sxs-lookup"><span data-stu-id="9cab7-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="9cab7-159">Ayrıştırma iş parçacığı, uygun veri yapılarını oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="9cab7-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="9cab7-160">Genellikle, ayrıştırma yalnızca ağdan veri bloklarını kopyalamaya kıyasla daha fazla zaman alır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="9cab7-161">Okuma iş parçacığı ayrıştırma iş parçacığının önüne alınır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="9cab7-162">Okuma iş parçacığı, ayrıştırma iş parçacığı için verileri depolamak üzere yavaşlıyor veya daha fazla bellek ayırmıştır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="9cab7-163">En iyi performans için, sık duraklamalar ve daha fazla bellek ayırma arasında bir denge vardır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="9cab7-164">Önceki sorunu çözmek için, `Pipe` veri akışını denetlemek üzere iki ayarı vardır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="9cab7-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Duraklatma çağrılarına önce ne kadar veri ara belleğe alınacağını belirler <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="9cab7-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Okuyucunun sürdürülmeye yönelik çağrılardan önce ne kadar veri gözlemleyecek olduğunu belirler `PipeWriter.FlushAsync` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![ResumeWriterThreshold ve PauseWriterThreshold ile diyagram](media/pipelines/resume-pause.png)

<span data-ttu-id="9cab7-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9cab7-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="9cab7-169">`ValueTask<FlushResult>`Kesiştiği içindeki veri miktarı için bir tamamlanmamış döndürür `Pipe` `PauseWriterThreshold` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="9cab7-170">Daha `ValueTask<FlushResult>` düşük hale geldiğinde tamamlanır `ResumeWriterThreshold` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="9cab7-171">Tek bir değer kullanılırsa oluşabilecek hızlı döngüyü engellemek için iki değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="9cab7-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9cab7-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="9cab7-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="9cab7-173">PipeScheduler</span></span>

<span data-ttu-id="9cab7-174">Genellikle ve kullanılırken `async` `await` , zaman uyumsuz kod, ya da geçerli bir üzerinde devam eder <xref:System.Threading.Tasks.TaskScheduler> <xref:System.Threading.SynchronizationContext> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="9cab7-175">G/ç yaparken, g/ç 'nin gerçekleştirildiği noktada ayrıntılı denetime sahip olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="9cab7-176">Bu denetim, CPU önbelleklerinin etkin bir şekilde yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cab7-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="9cab7-177">Verimli önbelleğe alma, Web sunucuları gibi yüksek performanslı uygulamalar için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="9cab7-178"><xref:System.IO.Pipelines.PipeScheduler> zaman uyumsuz geri çağırmaların çalıştığı konum üzerinde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cab7-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="9cab7-179">Varsayılan olarak:</span><span class="sxs-lookup"><span data-stu-id="9cab7-179">By default:</span></span>

* <span data-ttu-id="9cab7-180">Geçerli, <xref:System.Threading.SynchronizationContext> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="9cab7-181">Hayır ise `SynchronizationContext` , geri çağırmaları çalıştırmak için iş parçacığı havuzunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

<span data-ttu-id="9cab7-182">[Pipescheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) , <xref:System.IO.Pipelines.PipeScheduler> iş parçacığı havuzuna geri çağırmaları sıraya alan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="9cab7-183">`PipeScheduler.ThreadPool` Varsayılan ve genellikle en iyi seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="9cab7-184">[Pipescheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) , kilitlenme gibi istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="9cab7-185">Kanal sıfırlama</span><span class="sxs-lookup"><span data-stu-id="9cab7-185">Pipe reset</span></span>

<span data-ttu-id="9cab7-186">Nesneyi yeniden kullanmak sıklıkla etkilidir `Pipe` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="9cab7-187">Kanalı sıfırlamak için <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> hem hem de `PipeReader` tamamlandığında çağırın `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="9cab7-188">Piypereader</span><span class="sxs-lookup"><span data-stu-id="9cab7-188">PipeReader</span></span>

<span data-ttu-id="9cab7-189"><xref:System.IO.Pipelines.PipeReader> arayan adına belleği yönetir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="9cab7-190">Çağrıldıktan sonra **her zaman** çağırın <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9cab7-191">Bu, `PipeReader` çağıranın bellek ile ne zaman yapıldığını, böylece izlenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cab7-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="9cab7-192">`ReadOnlySequence<byte>`Döndürülen öğesinden `PipeReader.ReadAsync` yalnızca öğesine çağrı yapılıncaya kadar geçerlidir `PipeReader.AdvanceTo` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="9cab7-193">Çağrıldıktan sonra kullanım geçersizdir `ReadOnlySequence<byte>` `PipeReader.AdvanceTo` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="9cab7-194">`PipeReader.AdvanceTo` iki <xref:System.SequencePosition> bağımsız değişken alır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="9cab7-195">İlk bağımsız değişken, ne kadar bellek tüketildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="9cab7-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="9cab7-196">İkinci bağımsız değişken, arabelleğin ne kadarının gözlemlendiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="9cab7-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="9cab7-197">Verileri tüketilen olarak işaretlemek, kanalın belleği temel alınan arabellek havuzuna döndürebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="9cab7-198">Verileri gözlemlenen olarak işaretlemek, sonraki çağrının ne olduğunu denetler `PipeReader.ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="9cab7-199">Her şeyi gözlemlenen olarak işaretlemek, bir sonraki çağrının `PipeReader.ReadAsync` kanala yazılmış daha fazla veri olana kadar dönemeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="9cab7-200">Diğer herhangi bir değer, sonraki çağrının `PipeReader.ReadAsync` gözlemlenen *ve* gözlemlenen verilerle hemen döndürülmesini sağlar, ancak daha önce tüketilen verileri değil.</span><span class="sxs-lookup"><span data-stu-id="9cab7-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="9cab7-201">Akış verilerini okuma senaryoları</span><span class="sxs-lookup"><span data-stu-id="9cab7-201">Read streaming data scenarios</span></span>

<span data-ttu-id="9cab7-202">Akış verilerini okumaya çalışırken ortaya çıktı olan birkaç tipik desen vardır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="9cab7-203">Veri akışı verildiğinde, tek bir iletiyi ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="9cab7-204">Veri akışı verildiğinde, tüm kullanılabilir iletileri ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="9cab7-205">Aşağıdaki örneklerde, ' `TryParseMessage` dan ileti ayrıştırma yöntemi kullanılmaktadır `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="9cab7-206">`TryParseMessage` tek bir iletiyi ayrıştırır ve ayrıştırılmış iletiyi arabellekten kırpmak için giriş arabelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="9cab7-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="9cab7-207">`TryParseMessage` , .NET 'in bir parçası değildir, aşağıdaki bölümlerde kullanılan bir kullanıcı yazılmış yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="9cab7-208">Tek bir iletiyi okuyun</span><span class="sxs-lookup"><span data-stu-id="9cab7-208">Read a single message</span></span>

<span data-ttu-id="9cab7-209">Aşağıdaki kod, bir öğesinden tek bir ileti okur `PipeReader` ve bunu çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cab7-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

<span data-ttu-id="9cab7-210">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="9cab7-210">The preceding code:</span></span>

* <span data-ttu-id="9cab7-211">Tek bir ileti ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-211">Parses a single message.</span></span>
* <span data-ttu-id="9cab7-212">Tüketilen `SequencePosition` ve incelenen, `SequencePosition` kırpılan giriş arabelleğinin başlangıcını işaret eden şekilde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="9cab7-213">İki `SequencePosition` bağımsız değişken güncelleştirilir çünkü bu, `TryParseMessage` ayrıştırılmış iletiyi giriş arabelleğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="9cab7-214">Genellikle, arabellekteki tek bir ileti ayrıştırılırken, incelenen konum aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9cab7-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="9cab7-215">İletinin sonu.</span><span class="sxs-lookup"><span data-stu-id="9cab7-215">The end of the message.</span></span>
* <span data-ttu-id="9cab7-216">İleti bulunmazsa alınan arabelleğin sonu.</span><span class="sxs-lookup"><span data-stu-id="9cab7-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="9cab7-217">Tek ileti durumunun hata için en olası olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="9cab7-218">Yanlış değerleri *incelenmeye* geçirmek, yetersiz bellek özel durumu veya sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="9cab7-219">Daha fazla bilgi için bu makaledeki [Pıpereader ortak sorunlar](#gotchas) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9cab7-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="9cab7-220">Birden çok ileti okunuyor</span><span class="sxs-lookup"><span data-stu-id="9cab7-220">Reading multiple messages</span></span>

<span data-ttu-id="9cab7-221">Aşağıdaki kod, `PipeReader` her bir üzerinde ve çağrılarındaki tüm iletileri okur `ProcessMessageAsync` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a><span data-ttu-id="9cab7-222">İptal Etme</span><span class="sxs-lookup"><span data-stu-id="9cab7-222">Cancellation</span></span>

<span data-ttu-id="9cab7-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="9cab7-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="9cab7-224">, Geçişini destekler <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="9cab7-225">Bir okuma beklemede olduğunda, bir iptal edilirse bir oluşturur <xref:System.OperationCanceledException> `CancellationToken` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="9cab7-226"><xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, Bir özel durumun çıkarılmasını engelleyen geçerli okuma işlemini iptal etmek için bir yol destekler.</span><span class="sxs-lookup"><span data-stu-id="9cab7-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="9cab7-227">Çağırma `PipeReader.CancelPendingRead` , geçerli veya sonraki çağrısının ' `PipeReader.ReadAsync` a ayarlanmış olarak dönüşmesine neden olur <xref:System.IO.Pipelines.ReadResult> `IsCanceled` `true` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="9cab7-228">Bu, var olan okuma döngüsünü bozucu olmayan ve olağanüstü olmayan bir şekilde sonlandırmanız için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="9cab7-229">Piypereader yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="9cab7-229">PipeReader common problems</span></span>

* <span data-ttu-id="9cab7-230">Yanlış değerleri veya ' a geçirmek, `consumed` `examined` zaten okuma verilerinin okunmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="9cab7-231">`buffer.End`İncelenen şekilde geçirme şu şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="9cab7-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="9cab7-232">Durdurulmuş veriler</span><span class="sxs-lookup"><span data-stu-id="9cab7-232">Stalled data</span></span>
  * <span data-ttu-id="9cab7-233">Veriler tüketilmemişse, büyük olasılıkla yetersiz bellek (OOM) özel durumu.</span><span class="sxs-lookup"><span data-stu-id="9cab7-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="9cab7-234">Örneğin, `PipeReader.AdvanceTo(position, buffer.End)` arabellekteki bir anda tek bir ileti işlenirken.</span><span class="sxs-lookup"><span data-stu-id="9cab7-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="9cab7-235">Yanlış değerleri ' a geçirme `consumed` veya `examined` sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="9cab7-236">Örneğin, `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` henüz değiştirilmediyse, `PipeReader.ReadAsync` Yeni veri ulaşmadan hemen önce geri dönmesi için bir sonraki çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="9cab7-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="9cab7-237">Yanlış değerleri ' a geçirme `consumed` veya `examined` sonsuz arabelleğe alma (NIHAI OOM) ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="9cab7-238">Çağrıldıktan `ReadOnlySequence<byte>` sonra kullanılması, `PipeReader.AdvanceTo` bellek bozulmasına yol açabilir (ücretsiz olarak kullanabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="9cab7-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="9cab7-239">Çağrı başarısız `PipeReader.Complete/CompleteAsync` olabilir ve bellek sızıntısına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="9cab7-240"><xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType>Veri kaybına neden olan arabellek sonuçlarını işlemeden önce okuma mantığı denetleniyor ve çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="9cab7-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="9cab7-241">Döngü çıkış koşulunun ve tabanlı olması gerekir `ReadResult.Buffer.IsEmpty` `ReadResult.IsCompleted` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="9cab7-242">Bunu yanlış yapmak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="9cab7-243">Sorunlu kod</span><span class="sxs-lookup"><span data-stu-id="9cab7-243">Problematic code</span></span>

<span data-ttu-id="9cab7-244">❌ **Veri kaybı**</span><span class="sxs-lookup"><span data-stu-id="9cab7-244">❌ **Data loss**</span></span>

<span data-ttu-id="9cab7-245">, `ReadResult` Olarak ayarlandığında verilerin son segmentini döndürebilir `IsCompleted` `true` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="9cab7-246">Okuma döngüsünden çıkmadan önce bu verilerin okunmamasından dolayı veri kaybı olur.</span><span class="sxs-lookup"><span data-stu-id="9cab7-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9cab7-247">❌**Sonsuz döngü**</span><span class="sxs-lookup"><span data-stu-id="9cab7-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="9cab7-248">Aşağıdaki mantık,, `Result.IsCompleted` `true` ancak arabellekte hiç tamamlanmamış bir ileti varsa sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9cab7-249">Aynı sorunu içeren başka bir kod parçası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="9cab7-250">Denetlemeden önce boş olmayan bir arabellek denetleniyor `ReadResult.IsCompleted` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="9cab7-251">Bir içinde olduğu için `else if` , arabellekte hiç bir ileti yoksa sonsuza kadar döngüye alınır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9cab7-252">❌**Beklenmeyen askı**</span><span class="sxs-lookup"><span data-stu-id="9cab7-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="9cab7-253">Konumda koşullu olarak `PipeReader.AdvanceTo` çağırmanın `buffer.End` `examined` tek bir ileti ayrıştırılırken askıda kalmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="9cab7-254">Sonraki çağrısı şu `PipeReader.AdvanceTo` kadar geri dönemeyecek:</span><span class="sxs-lookup"><span data-stu-id="9cab7-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="9cab7-255">Kanala yazılan daha fazla veri var.</span><span class="sxs-lookup"><span data-stu-id="9cab7-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="9cab7-256">Ve yeni veriler daha önce incelendi.</span><span class="sxs-lookup"><span data-stu-id="9cab7-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9cab7-257">❌**Yetersiz bellek (OOM)**</span><span class="sxs-lookup"><span data-stu-id="9cab7-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="9cab7-258">Aşağıdaki koşullara göre aşağıdaki kod arabelleğe alma işlemi gerçekleşene kadar devam eder <xref:System.OutOfMemoryException> :</span><span class="sxs-lookup"><span data-stu-id="9cab7-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="9cab7-259">En büyük ileti boyutu yok.</span><span class="sxs-lookup"><span data-stu-id="9cab7-259">There's no maximum message size.</span></span>
* <span data-ttu-id="9cab7-260">Öğesinden döndürülen veriler, `PipeReader` bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="9cab7-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="9cab7-261">Örneğin, diğer taraf büyük bir ileti (örneğin, 4 GB bir ileti) yazıldığı için, bu tam bir ileti yapmaz.</span><span class="sxs-lookup"><span data-stu-id="9cab7-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9cab7-262">❌**Bellek bozulması**</span><span class="sxs-lookup"><span data-stu-id="9cab7-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="9cab7-263">Arabelleği okuyan yardımcıları yazarken, çağrılmadan önce döndürülen tüm yükün kopyalanması gerekir `Advance` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="9cab7-264">Aşağıdaki örnek, atılan belleği döndürür ve bir `Pipe` sonraki işlem (okuma/yazma) için onu tekrar kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="9cab7-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="9cab7-265">PipeWriter</span></span>

<span data-ttu-id="9cab7-266"><xref:System.IO.Pipelines.PipeWriter>Arayan adına yazmak için arabellekleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="9cab7-267">`PipeWriter` uygular [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) .</span><span class="sxs-lookup"><span data-stu-id="9cab7-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="9cab7-268">`IBufferWriter<byte>` ek arabellek kopyaları olmadan yazma işlemleri gerçekleştirmek için arabelleklere erişim sağlamak mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

<span data-ttu-id="9cab7-269">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="9cab7-269">The previous code:</span></span>

* <span data-ttu-id="9cab7-270">Kullanarak en az 5 baytlık bir arabellek ister `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="9cab7-271">ASCII dizesinin bayt sayısını `"Hello"` döndürülen öğesine yazar `Memory<byte>` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="9cab7-272"><xref:System.IO.Pipelines.PipeWriter.Advance%2A>Arabelleğe kaç bayt yazıldığını belirten çağrılar.</span><span class="sxs-lookup"><span data-stu-id="9cab7-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="9cab7-273">, `PipeWriter` Baytları temeldeki cihaza gönderen öğesini temizler.</span><span class="sxs-lookup"><span data-stu-id="9cab7-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="9cab7-274">Önceki yazma yöntemi, tarafından sağlanmış arabellekleri kullanır `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="9cab7-275">Alternatif olarak, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="9cab7-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="9cab7-276">Varolan arabelleği öğesine kopyalar `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="9cab7-277">`GetSpan` `Advance` Uygun ve çağrılar için çağrılar <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a><span data-ttu-id="9cab7-278">İptal Etme</span><span class="sxs-lookup"><span data-stu-id="9cab7-278">Cancellation</span></span>

<span data-ttu-id="9cab7-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> , geçişini destekler <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="9cab7-280">Bekleyen bir `CancellationToken` `OperationCanceledException` Temizleme işlemi varken belirteç iptal edilirse bir sonuçları bir ile geçirme.</span><span class="sxs-lookup"><span data-stu-id="9cab7-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="9cab7-281">`PipeWriter.FlushAsync` , özel durum oluşturmadan geçerli temizleme işlemini iptal etmenin bir yolunu destekler <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="9cab7-282">Çağırma `PipeWriter.CancelPendingFlush` , geçerli veya sonraki çağrıya, `PipeWriter.FlushAsync` veya olarak `PipeWriter.WriteAsync` ayarlanmış olarak dönüşmesine neden olur <xref:System.IO.Pipelines.FlushResult> `IsCanceled` `true` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="9cab7-283">Bu, bozucu olmayan ve olağanüstü olmayan bir şekilde boşaltmayı Temizleme için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="9cab7-284">PipeWriter ortak sorunları</span><span class="sxs-lookup"><span data-stu-id="9cab7-284">PipeWriter common problems</span></span>

* <span data-ttu-id="9cab7-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> ve <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> en az istenen bellek miktarına sahip bir arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cab7-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="9cab7-286">Tam arabellek boyutlarını kabul **etmeyin** .</span><span class="sxs-lookup"><span data-stu-id="9cab7-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="9cab7-287">Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9cab7-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="9cab7-288"><xref:System.IO.Pipelines.PipeWriter.Advance%2A>Daha fazla veri yazmaya devam etmek için çağrıldıktan sonra yeni bir arabellek istenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="9cab7-289">Daha önce edinilen arabelleğin üzerine yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="9cab7-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="9cab7-290">`GetMemory` `GetSpan` Eksik bir çağrı olduğu için veya çağrısı sırasında `FlushAsync` güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="9cab7-291">`Complete` `CompleteAsync` Verilerin temizlenme sırasında veya boşaltılmasından sonra bellek bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="9cab7-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="9cab7-292">IDuplexPipe</span></span>

<span data-ttu-id="9cab7-293">, <xref:System.IO.Pipelines.IDuplexPipe> Hem okumayı hem de yazmayı destekleyen türler için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="9cab7-294">Örneğin, bir ağ bağlantısı bir tarafından temsil edilir `IDuplexPipe` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="9cab7-295">`Pipe`Ve içeren öğelerinden farklı olarak `PipeReader` `PipeWriter` , `IDuplexPipe` tam çift yönlü bağlantının tek tarafını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9cab7-295">Unlike `Pipe`, which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="9cab7-296">Bu, üzerine yazılan ve ' `PipeWriter` den okunmayacağı anlamına gelir `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="9cab7-297">Akışlar</span><span class="sxs-lookup"><span data-stu-id="9cab7-297">Streams</span></span>

<span data-ttu-id="9cab7-298">Akış verilerini okurken veya yazarken genellikle seri hale getirici kullanarak verileri okur ve serileştirici kullanarak verileri yazın.</span><span class="sxs-lookup"><span data-stu-id="9cab7-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="9cab7-299">Bu okuma ve yazma akışı API 'Lerinin çoğu bir `Stream` parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="9cab7-300">Bu var olan API 'lerle tümleştirmeyi kolaylaştırmak `PipeReader` ve `PipeWriter` bir yöntemi ortaya çıkarmak için <xref:System.IO.Pipelines.PipeReader.AsStream%2A> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A> method.</span></span> <span data-ttu-id="9cab7-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>`Stream`veya etrafında bir uygulama döndürür `PipeReader` `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>

### <a name="stream-example"></a><span data-ttu-id="9cab7-302">Akış örneği</span><span class="sxs-lookup"><span data-stu-id="9cab7-302">Stream example</span></span>

<span data-ttu-id="9cab7-303">`PipeReader` ve `PipeWriter` örnekleri `Create` bir nesne verilen statik yöntemler <xref:System.IO.Stream> ve isteğe bağlı olarak ilgili oluşturma seçenekleri kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="9cab7-303">`PipeReader` and `PipeWriter` instances can be created using the static `Create` methods given a <xref:System.IO.Stream> object and optional corresponding creation options.</span></span>

<span data-ttu-id="9cab7-304"><xref:System.IO.Pipelines.StreamPipeReaderOptions>Aşağıdaki parametrelerle örnek oluşturma üzerinde denetime izin ver `PipeReader` :</span><span class="sxs-lookup"><span data-stu-id="9cab7-304">The <xref:System.IO.Pipelines.StreamPipeReaderOptions> allow for control over the creation of the `PipeReader` instance with the following parameters:</span></span>

- <span data-ttu-id="9cab7-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> , havuzdan belleği yeniden boyutlandırdığınızda kullanılan bayt cinsinden en düşük arabellek boyutu ve varsayılan değer olarak kullanılır `4096` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> is the minimum buffer size in bytes used when renting memory from the pool, and defaults to `4096`.</span></span>
- <span data-ttu-id="9cab7-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> bayrak, işlem tamamlandıktan sonra temeldeki akışın açık bırakılıp başlatılmayacağını belirler `PipeReader` ve varsayılan olarak öğesine ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeReader` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="9cab7-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> Yeni bir arabelleğin ayrılmadan önce arabellekteki kalan baytların eşiğini temsil eder ve varsayılan olarak değerine ayarlanır `1024` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> represents the threshold of remaining bytes in the buffer before a new buffer is allocated, and defaults to `1024`.</span></span>
- <span data-ttu-id="9cab7-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType>`MemoryPool<byte>`bellek ayrılırken kullanılır ve varsayılan olarak öğesine ayarlanır `null` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

<span data-ttu-id="9cab7-309"><xref:System.IO.Pipelines.StreamPipeWriterOptions>Aşağıdaki parametrelerle örnek oluşturma üzerinde denetime izin ver `PipeWriter` :</span><span class="sxs-lookup"><span data-stu-id="9cab7-309">The <xref:System.IO.Pipelines.StreamPipeWriterOptions> allow for control over the creation of the `PipeWriter` instance with the following parameters:</span></span>

- <span data-ttu-id="9cab7-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> bayrak, işlem tamamlandıktan sonra temeldeki akışın açık bırakılıp başlatılmayacağını belirler `PipeWriter` ve varsayılan olarak öğesine ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeWriter` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="9cab7-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> , bellekten bellek oluştururken kullanılacak en düşük arabellek boyutunu temsil eder <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> `4096` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> represents the minimum buffer size to use when renting memory from the <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool>, and defaults to `4096`.</span></span>
- <span data-ttu-id="9cab7-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType>`MemoryPool<byte>`bellek ayrılırken kullanılır ve varsayılan olarak öğesine ayarlanır `null` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9cab7-313">`PipeReader` `PipeWriter` Yöntemlerini kullanarak ve örnekleri kullanırken `Create` , nesne ömrünü göz önünde bulundurmanız gerekir `Stream` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-313">When creating `PipeReader` and `PipeWriter` instances using the `Create` methods, you need to consider the `Stream` object lifetime.</span></span> <span data-ttu-id="9cab7-314">Okuyucu veya yazıcı ile işiniz bittiğinde akışa erişmeniz gerekiyorsa, `LeaveOpen` oluşturma seçeneklerinde bayrağını olarak ayarlamanız gerekir `true` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-314">If you need access to the stream after the reader or writer is done with it, you'll need to set the `LeaveOpen` flag to `true` on the creation options.</span></span> <span data-ttu-id="9cab7-315">Aksi takdirde, akış kapatılacak.</span><span class="sxs-lookup"><span data-stu-id="9cab7-315">Otherwise, the stream will be closed.</span></span>

<span data-ttu-id="9cab7-316">Aşağıdaki kod, `PipeReader` `PipeWriter` bir akıştan yöntemleri kullanarak ve örneklerinin oluşturulmasını gösterir `Create` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-316">The following code demonstrates the creation of `PipeReader` and `PipeWriter` instances using the `Create` methods from a stream.</span></span>

:::code language="csharp" source="snippets/pipelines/Program.cs":::

<span data-ttu-id="9cab7-317">Uygulama bir <xref:System.IO.StreamReader> akış olarak *lorem-ipsum.txt* dosyayı okumak için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cab7-317">The application uses a <xref:System.IO.StreamReader> to read the *lorem-ipsum.txt* file as a stream.</span></span> <span data-ttu-id="9cab7-318">, <xref:System.IO.FileStream> <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> Bir nesneyi örnekleyen öğesine geçirilir `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="9cab7-318">The <xref:System.IO.FileStream> is passed to <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>, which instantiates a `PipeReader` object.</span></span> <span data-ttu-id="9cab7-319">Konsol uygulaması daha sonra kendi standart çıkış akışını kullanarak geçirir <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9cab7-319">The console application then passes its standard output stream to <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> using <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9cab7-320">Örnek [iptali](#cancellation)destekler.</span><span class="sxs-lookup"><span data-stu-id="9cab7-320">The example supports [cancellation](#cancellation).</span></span>
