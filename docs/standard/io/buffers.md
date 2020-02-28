---
title: System. buffers-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: f939164cd56b2fb2feeeb171236b0e1171327e19
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160124"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="cd315-102">.NET 'teki arabelleklerle çalışma</span><span class="sxs-lookup"><span data-stu-id="cd315-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="cd315-103">Bu makalede, birden çok arabelleğe çalışan verileri okumaya yardımcı olan türlere genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd315-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="cd315-104">Bunlar öncelikle <xref:System.IO.Pipelines.PipeReader> nesneleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd315-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="cd315-105">Ibufferwriter\<T\></span><span class="sxs-lookup"><span data-stu-id="cd315-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="cd315-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>, zaman uyumlu arabelleğe alınmış yazma için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="cd315-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="cd315-107">En düşük düzeyde, arabirimi:</span><span class="sxs-lookup"><span data-stu-id="cd315-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="cd315-108">Temel ve kullanılması zor değildir.</span><span class="sxs-lookup"><span data-stu-id="cd315-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="cd315-109"><xref:System.Memory%601> veya <xref:System.Span%601>erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cd315-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="cd315-110">`Memory<T>` veya `Span<T>` üzerine yazılabilir ve kaç `T` öğe yazıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd315-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="cd315-111">Önceki Yöntem:</span><span class="sxs-lookup"><span data-stu-id="cd315-111">The preceding method:</span></span>

- <span data-ttu-id="cd315-112">`GetSpan(5)`kullanarak `IBufferWriter<byte>` en az 5 baytlık bir arabellek ister.</span><span class="sxs-lookup"><span data-stu-id="cd315-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="cd315-113">"Hello" ASCII dizesi için döndürülen `Span<byte>`bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="cd315-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="cd315-114">Arabelleğe kaç bayt yazıldığını belirten <xref:System.Buffers.IBufferWriter%601> çağırır.</span><span class="sxs-lookup"><span data-stu-id="cd315-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="cd315-115">Bu yazma yöntemi, `IBufferWriter<T>`tarafından sunulan `Memory<T>`/`Span<T>` arabelleğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd315-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="cd315-116">Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> uzantısı yöntemi mevcut bir arabelleği `IBufferWriter<T>`kopyalamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd315-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="cd315-117">`Write`, `GetSpan`/`Advance` uygun şekilde çağırmada çalışır; bu nedenle, yazdıktan sonra `Advance` çağrısına gerek yoktur:</span><span class="sxs-lookup"><span data-stu-id="cd315-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="cd315-118"><xref:System.Buffers.ArrayBufferWriter%601>, yedekleme deposu tek bir bitişik dizi olan `IBufferWriter<T>` uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="cd315-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="cd315-119">Ibufferwriter yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="cd315-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="cd315-120">`GetSpan` ve `GetMemory` en az istenen bellek miktarına sahip bir arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd315-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="cd315-121">Tam arabellek boyutlarını kabul etmeyin.</span><span class="sxs-lookup"><span data-stu-id="cd315-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="cd315-122">Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd315-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="cd315-123">Daha fazla veri yazmaya devam etmek için `Advance` çağrıldıktan sonra yeni bir arabellek istenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd315-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="cd315-124">Daha önce elde edilen bir arabellek `Advance` çağrıldıktan sonra yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="cd315-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="cd315-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="cd315-125">ReadOnlySequence\<T\></span></span>

![Salt okunan belleğin sıra konumunun kanalda ve altında belleği gösteren ReadOnlySequence](media/buffers/ro-sequence.png)

<span data-ttu-id="cd315-127"><xref:System.Buffers.ReadOnlySequence%601>, bitişik veya bitişik olmayan bir `T`dizisini temsil eden bir struct.</span><span class="sxs-lookup"><span data-stu-id="cd315-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="cd315-128">Oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="cd315-128">It can be constructed from:</span></span>

1. <span data-ttu-id="cd315-129">Bir `T[]`</span><span class="sxs-lookup"><span data-stu-id="cd315-129">A `T[]`</span></span>
1. <span data-ttu-id="cd315-130">Bir `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="cd315-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="cd315-131">Dizinin başlangıç ve bitiş konumunu temsil etmek için bir çift bağlantılı liste düğümü <xref:System.Buffers.ReadOnlySequenceSegment%601> ve dizini.</span><span class="sxs-lookup"><span data-stu-id="cd315-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="cd315-132">Üçüncü Gösterim, `ReadOnlySequence<T>`çeşitli işlemlerde performans etkilerine sahip olduğu için en ilginç bir gösterimidir:</span><span class="sxs-lookup"><span data-stu-id="cd315-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="cd315-133">İmle</span><span class="sxs-lookup"><span data-stu-id="cd315-133">Representation</span></span>|<span data-ttu-id="cd315-134">İşlem</span><span class="sxs-lookup"><span data-stu-id="cd315-134">Operation</span></span>|<span data-ttu-id="cd315-135">Karmaşıklık</span><span class="sxs-lookup"><span data-stu-id="cd315-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="cd315-136">Bu karışık Gösterim nedeniyle `ReadOnlySequence<T>` dizinleri bir tamsayı yerine `SequencePosition` olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cd315-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="cd315-137">`SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="cd315-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="cd315-138">, `ReadOnlySequence<T>` kaynaklandığı bir dizini temsil eden donuk bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="cd315-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="cd315-139">İki bölümden oluşur, bir tamsayı ve bir nesne.</span><span class="sxs-lookup"><span data-stu-id="cd315-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="cd315-140">Bu iki değerin ne gösterdiği, `ReadOnlySequence<T>`uygulamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cd315-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="cd315-141">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="cd315-141">Access data</span></span>

<span data-ttu-id="cd315-142">`ReadOnlySequence<T>`, verileri sıralanabilir bir `ReadOnlyMemory<T>`olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cd315-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="cd315-143">Parçaların her birini numaralandırma, temel bir foreach kullanılarak yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="cd315-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="cd315-144">Yukarıdaki yöntem, her segmenti belirli bir bayt arar.</span><span class="sxs-lookup"><span data-stu-id="cd315-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="cd315-145">Her bir segmentin `SequencePosition`izlemeniz gerekiyorsa <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="cd315-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="cd315-146">Sonraki örnek, önceki kodu bir tamsayı yerine bir `SequencePosition` döndürecek şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cd315-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="cd315-147">`SequencePosition` döndürmek, çağıranın belirli bir dizindeki verileri almak için ikinci bir taramayı önlemenize izin vermenin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd315-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="cd315-148">`SequencePosition` ve `TryGet` birleşimi bir Numaralandırıcı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="cd315-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="cd315-149">Konum alanı her bir yinelemenin başlangıcında, `ReadOnlySequence<T>`içindeki her bir segmentin başlaması için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="cd315-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="cd315-150">Önceki yöntem `ReadOnlySequence<T>`bir genişletme yöntemi olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd315-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="cd315-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>, önceki kodu basitleştirmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cd315-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="cd315-152">ReadOnlySequence\<T\> işleme</span><span class="sxs-lookup"><span data-stu-id="cd315-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="cd315-153">Verilerin dizideki birden çok parçaya bölünmesi gerektiğinden, bir `ReadOnlySequence<T>` işleme zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd315-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="cd315-154">En iyi performansı elde etmek için kodu iki yola ayırın:</span><span class="sxs-lookup"><span data-stu-id="cd315-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="cd315-155">Tek kesimli büyük/küçük harf ile ilgilenen hızlı bir yol.</span><span class="sxs-lookup"><span data-stu-id="cd315-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="cd315-156">Bölümler arasında bölünen verilerle ilgilenen yavaş bir yol.</span><span class="sxs-lookup"><span data-stu-id="cd315-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="cd315-157">Verileri çok kesimli dizilerden işlemek için kullanılabilecek birkaç yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="cd315-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="cd315-158">[`SequenceReader<T>`](#sequencereadert)kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd315-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="cd315-159">Segmenti segmente göre ayrıştırır, `SequencePosition` ve dizinin içindeki dizini ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="cd315-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="cd315-160">Bu, gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd315-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="cd315-161">`ReadOnlySequence<T>` bitişik bir diziye kopyalayın ve tek bir arabellek gibi değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="cd315-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="cd315-162">`ReadOnlySequence<T>` boyutu küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanılarak verileri yığına ayrılan bir arabelleğe kopyalamak makul olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd315-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="cd315-163"><xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>kullanarak `ReadOnlySequence<T>` havuza alınmış bir diziye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cd315-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="cd315-164">[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd315-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="cd315-165">Bu, yığın üzerinde yeni bir `T[]` ayırdığı için etkin yollarda önerilmez.</span><span class="sxs-lookup"><span data-stu-id="cd315-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="cd315-166">Aşağıdaki örneklerde `ReadOnlySequence<byte>`işlemeye yönelik bazı genel durumlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cd315-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="cd315-167">İkili verileri işle</span><span class="sxs-lookup"><span data-stu-id="cd315-167">Process binary data</span></span>

<span data-ttu-id="cd315-168">Aşağıdaki örnek, `ReadOnlySequence<byte>`başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="cd315-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="cd315-169">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="cd315-169">Process text data</span></span>

<span data-ttu-id="cd315-170">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="cd315-170">The following example:</span></span>

- <span data-ttu-id="cd315-171">`ReadOnlySequence<byte>` ilk yeni satırı (`\r\n`) bulur ve out ' Line ' parametresi aracılığıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd315-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="cd315-172">Giriş arabelleğindeki `\r\n` hariç bırakarak bu satırı kırpar.</span><span class="sxs-lookup"><span data-stu-id="cd315-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="cd315-173">Boş segmentler</span><span class="sxs-lookup"><span data-stu-id="cd315-173">Empty segments</span></span>

<span data-ttu-id="cd315-174">Boş kesimleri bir `ReadOnlySequence<T>`içinde depolamak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cd315-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="cd315-175">Kesimleri açıkça Numaralandırırken boş kesimler meydana gelebilir:</span><span class="sxs-lookup"><span data-stu-id="cd315-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="cd315-176">Yukarıdaki kod, boş kesimleri olan bir `ReadOnlySequence<byte>` oluşturur ve bu boş segmentlerin çeşitli API 'Leri nasıl etkilediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="cd315-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="cd315-177">boş bir kesime işaret eden bir `SequencePosition` `ReadOnlySequence<T>.Slice`, bu segmenti korur.</span><span class="sxs-lookup"><span data-stu-id="cd315-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="cd315-178">bir int ile `ReadOnlySequence<T>.Slice` boş kesimleri atlar.</span><span class="sxs-lookup"><span data-stu-id="cd315-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="cd315-179">`ReadOnlySequence<T>` numaralandırılırken boş segmentler numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="cd315-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="cd315-180">ReadOnlySequence\<T > ve SequencePosition ile ilgili olası sorunlar</span><span class="sxs-lookup"><span data-stu-id="cd315-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="cd315-181">Bir `ReadOnlySequence<T>`/ile ilgilenirken olağan dışı sonuçlar vardır `SequencePosition` vs `ReadOnlySpan<T>`. /`ReadOnlyMemory<T>`/`T[]`/`int`:</span><span class="sxs-lookup"><span data-stu-id="cd315-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="cd315-182">`SequencePosition`, mutlak bir konum değil, belirli bir `ReadOnlySequence<T>`için konum işaretleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="cd315-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="cd315-183">Belirli bir `ReadOnlySequence<T>`göreli olduğundan, kaynaklandığı `ReadOnlySequence<T>` dışında kullanılırsa anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd315-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="cd315-184">Aritmetik, `ReadOnlySequence<T>`olmadan `SequencePosition` gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="cd315-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="cd315-185">Bu, `position++` gibi temel nesnelerin `ReadOnlySequence<T>.GetPosition(position, 1)`yazıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cd315-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="cd315-186">`GetPosition(long)` negatif **dizinleri desteklemez.**</span><span class="sxs-lookup"><span data-stu-id="cd315-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="cd315-187">Diğer bir deyişle, tüm kesimleri yürümeden ikinciden son karaktere ulaşmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="cd315-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="cd315-188">İki `SequencePosition` karşılaştırılamaz ve şunları yapmayı zorlaştırıyor:</span><span class="sxs-lookup"><span data-stu-id="cd315-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="cd315-189">Bir konumun başka bir konumdan büyük veya küçük olup olmadığını öğrenin.</span><span class="sxs-lookup"><span data-stu-id="cd315-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="cd315-190">Bazı ayrıştırma algoritmaları yazın.</span><span class="sxs-lookup"><span data-stu-id="cd315-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="cd315-191">`ReadOnlySequence<T>` bir nesne başvurusundan daha büyük ve [içinde](../../csharp/language-reference/keywords/in-parameter-modifier.md) ya da mümkün olduğunda [başvuru](../../csharp/language-reference/keywords/ref.md) olarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd315-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="cd315-192">`in` veya `ref` tarafından `ReadOnlySequence<T>` geçirme [yapının](../../csharp/language-reference/builtin-types/struct.md)kopyalarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="cd315-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="cd315-193">Boş segmentler:</span><span class="sxs-lookup"><span data-stu-id="cd315-193">Empty segments:</span></span>
  - <span data-ttu-id="cd315-194">`ReadOnlySequence<T>`içinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cd315-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="cd315-195">`ReadOnlySequence<T>.TryGet` yöntemi kullanılarak yinelenirken görünebilirler.</span><span class="sxs-lookup"><span data-stu-id="cd315-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="cd315-196">`SequencePosition` nesneleri ile `ReadOnlySequence<T>.Slice()` yöntemi kullanılarak diziyi Dilimleme görünebilir.</span><span class="sxs-lookup"><span data-stu-id="cd315-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="cd315-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="cd315-197">SequenceReader\<T\></span></span>

<span data-ttu-id="cd315-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="cd315-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="cd315-199">, Bir `ReadOnlySequence<T>`işlenmesini basitleştirmek için .NET Core 3,0 ' de tanıtılan yeni bir türdür.</span><span class="sxs-lookup"><span data-stu-id="cd315-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="cd315-200">Tek bir kesim `ReadOnlySequence<T>` ve çok kesimli `ReadOnlySequence<T>`arasındaki farkları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd315-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="cd315-201">Bölümler arasında bölünecek veya bölünmemiş olabilecek ikili ve metin verilerini (`byte` ve `char`) okumak için yardımcılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd315-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="cd315-202">Hem ikili hem de sınırlandırılmış verilerin işlenmesiyle ilgili yerleşik yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="cd315-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="cd315-203">Aşağıdaki bölümde, bu yöntemlerin `SequenceReader<T>`nasıl göründüğünü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cd315-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="cd315-204">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="cd315-204">Access data</span></span>

<span data-ttu-id="cd315-205">`SequenceReader<T>`, `ReadOnlySequence<T>` içindeki verileri doğrudan numaralandırma yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd315-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="cd315-206">Aşağıdaki kod, bir `ReadOnlySequence<byte>` `byte` bir anda işleme örneğidir:</span><span class="sxs-lookup"><span data-stu-id="cd315-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="cd315-207">`CurrentSpan`, geçerli segmentin `Span`, yöntemde yapılan yönteme benzer şekilde kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cd315-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="cd315-208">Kullanım konumu</span><span class="sxs-lookup"><span data-stu-id="cd315-208">Use position</span></span>

<span data-ttu-id="cd315-209">Aşağıdaki kod, `SequenceReader<T>`kullanarak `FindIndexOf` örnek bir uygulamasıdır:</span><span class="sxs-lookup"><span data-stu-id="cd315-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="cd315-210">İkili verileri işle</span><span class="sxs-lookup"><span data-stu-id="cd315-210">Process binary data</span></span>

<span data-ttu-id="cd315-211">Aşağıdaki örnek, `ReadOnlySequence<byte>`başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="cd315-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="cd315-212">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="cd315-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="cd315-213">SequenceReader\<T\> genel sorunlar</span><span class="sxs-lookup"><span data-stu-id="cd315-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="cd315-214">`SequenceReader<T>` kesilebilir bir struct olduğundan, her zaman [başvuruya](../../csharp/language-reference/keywords/ref.md)göre geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd315-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="cd315-215">`SequenceReader<T>`, yalnızca zaman uyumlu metotlarda kullanılabilmesi ve alanlarda depolanabilmesi için [başvuru yapısı](../../csharp/language-reference/keywords/ref.md#ref-struct-types) .</span><span class="sxs-lookup"><span data-stu-id="cd315-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/keywords/ref.md#ref-struct-types) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="cd315-216">Daha fazla bilgi için bkz. [yazma güvenli ve C# verimli kod](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="cd315-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="cd315-217">`SequenceReader<T>` yalnızca ileri bir okuyucu olarak kullanılmak üzere iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd315-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="cd315-218">`Rewind`, diğer `Read`, `Peek`ve `IsNext` API 'Lerini kullanarak değinilmemiş küçük yedeklemeler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd315-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
