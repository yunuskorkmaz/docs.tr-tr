---
title: System. buffers-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739615"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="22921-102">.NET 'teki arabelleklerle çalışma</span><span class="sxs-lookup"><span data-stu-id="22921-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="22921-103">Bu makalede, birden çok arabelleğe çalışan verileri okumaya yardımcı olan türlere genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22921-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="22921-104">Bunlar öncelikle nesneleri desteklemek için kullanılır <xref:System.IO.Pipelines.PipeReader> .</span><span class="sxs-lookup"><span data-stu-id="22921-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="22921-105">Ibufferwriter \< T\></span><span class="sxs-lookup"><span data-stu-id="22921-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="22921-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>, zaman uyumlu arabelleğe alınmış yazma için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="22921-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="22921-107">En düşük düzeyde, arabirimi:</span><span class="sxs-lookup"><span data-stu-id="22921-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="22921-108">Temel ve kullanılması zor değildir.</span><span class="sxs-lookup"><span data-stu-id="22921-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="22921-109">Veya erişimine izin verir <xref:System.Memory%601> <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="22921-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="22921-110">`Memory<T>`Veya `Span<T>` üzerine yazılabilir ve kaç `T` öğe yazıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22921-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="22921-111">Önceki Yöntem:</span><span class="sxs-lookup"><span data-stu-id="22921-111">The preceding method:</span></span>

- <span data-ttu-id="22921-112">Kullanarak en az 5 baytlık bir arabellek ister `IBufferWriter<byte>` `GetSpan(5)` .</span><span class="sxs-lookup"><span data-stu-id="22921-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="22921-113">"Hello" ASCII dizesi için verilen baytları döndürülen öğesine yazar `Span<byte>` .</span><span class="sxs-lookup"><span data-stu-id="22921-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="22921-114"><xref:System.Buffers.IBufferWriter%601>Arabelleğe kaç bayt yazıldığını belirten çağrılar.</span><span class="sxs-lookup"><span data-stu-id="22921-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="22921-115">Bu yazma yöntemi `Memory<T>` / `Span<T>` , tarafından sağlanmış olan arabelleği kullanır `IBufferWriter<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="22921-116">Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> genişletme yöntemi var olan bir arabelleği öğesine kopyalamak için kullanılabilir `IBufferWriter<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="22921-117">`Write`, doğru çağırma işini yapar `GetSpan` / `Advance` , bu nedenle `Advance` yazmadan sonra çağrı gerekmez:</span><span class="sxs-lookup"><span data-stu-id="22921-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="22921-118"><xref:System.Buffers.ArrayBufferWriter%601>, `IBufferWriter<T>` yedekleme deposu tek bir bitişik dizi olan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="22921-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="22921-119">Ibufferwriter yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="22921-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="22921-120">`GetSpan`ve `GetMemory` en az istenen bellek miktarına sahip bir arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="22921-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="22921-121">Tam arabellek boyutlarını kabul etmeyin.</span><span class="sxs-lookup"><span data-stu-id="22921-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="22921-122">Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="22921-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="22921-123">`Advance`Daha fazla veri yazmaya devam etmek için çağrıldıktan sonra yeni bir arabellek istenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="22921-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="22921-124">Daha önce elde edilen bir arabellek çağrıldıktan sonra üzerine yazılamaz `Advance` .</span><span class="sxs-lookup"><span data-stu-id="22921-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="22921-125">ReadOnlySequence \< T\></span><span class="sxs-lookup"><span data-stu-id="22921-125">ReadOnlySequence\<T\></span></span>

![Salt okunan belleğin sıra konumunun kanalda ve altında belleği gösteren ReadOnlySequence](media/buffers/ro-sequence.png)

<span data-ttu-id="22921-127"><xref:System.Buffers.ReadOnlySequence%601>, ardışık veya bitişik olmayan dizisini temsil eden bir struct `T` .</span><span class="sxs-lookup"><span data-stu-id="22921-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="22921-128">Oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="22921-128">It can be constructed from:</span></span>

1. <span data-ttu-id="22921-129">Bir `T[]`</span><span class="sxs-lookup"><span data-stu-id="22921-129">A `T[]`</span></span>
1. <span data-ttu-id="22921-130">Bir `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="22921-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="22921-131"><xref:System.Buffers.ReadOnlySequenceSegment%601>Dizinin başlangıç ve bitiş konumunu temsil eden bağlantılı liste düğümü ve Dizin çifti.</span><span class="sxs-lookup"><span data-stu-id="22921-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="22921-132">Üçüncü Gösterim, üzerinde çeşitli işlemlerde performans etkilerine sahip olduğu için en ilginç bir gösterimidir `ReadOnlySequence<T>` :</span><span class="sxs-lookup"><span data-stu-id="22921-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="22921-133">İmle</span><span class="sxs-lookup"><span data-stu-id="22921-133">Representation</span></span>|<span data-ttu-id="22921-134">Çalışma</span><span class="sxs-lookup"><span data-stu-id="22921-134">Operation</span></span>|<span data-ttu-id="22921-135">Karmaşıklık</span><span class="sxs-lookup"><span data-stu-id="22921-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="22921-136">Bu karışık Gösterim nedeniyle `ReadOnlySequence<T>` dizinleri `SequencePosition` bir tamsayı yerine kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="22921-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="22921-137">Y `SequencePosition` :</span><span class="sxs-lookup"><span data-stu-id="22921-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="22921-138">, Kaynaklandığı yere bir dizin temsil eden donuk bir değerdir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="22921-139">İki bölümden oluşur, bir tamsayı ve bir nesne.</span><span class="sxs-lookup"><span data-stu-id="22921-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="22921-140">Bu iki değerin uygulamasının uygulamasına bağlı olması `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="22921-141">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="22921-141">Access data</span></span>

<span data-ttu-id="22921-142">`ReadOnlySequence<T>`Verileri numaralandırılabilir olarak gösterir `ReadOnlyMemory<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="22921-143">Parçaların her birini numaralandırma, temel bir foreach kullanılarak yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="22921-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="22921-144">Yukarıdaki yöntem, her segmenti belirli bir bayt arar.</span><span class="sxs-lookup"><span data-stu-id="22921-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="22921-145">Her bir parçayı takip etmeniz gerekiyorsa `SequencePosition` , <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="22921-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="22921-146">Sonraki örnek, önceki kodu bir tamsayı yerine döndürecek şekilde değiştirir `SequencePosition` .</span><span class="sxs-lookup"><span data-stu-id="22921-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="22921-147">Bir döndürmek `SequencePosition` , çağıranın belirli bir dizindeki verileri almak için ikinci bir taramayı önlemenize izin vermenin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="22921-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="22921-148">Birleşimi `SequencePosition` ve `TryGet` bir Numaralandırıcı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="22921-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="22921-149">Konum alanı her bir yinelemenin başlangıcında, içindeki her bir segmentin başlaması için değiştirilir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="22921-150">Önceki yöntem üzerinde bir genişletme yöntemi olarak mevcuttur `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="22921-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>, önceki kodu basitleştirmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="22921-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="22921-152">ReadOnlySequence T işleme \<\></span><span class="sxs-lookup"><span data-stu-id="22921-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="22921-153">`ReadOnlySequence<T>`Verilerin dizideki birden çok parçaya bölünmesi gerektiğinden, işleme bir işlem zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="22921-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="22921-154">En iyi performansı elde etmek için kodu iki yola ayırın:</span><span class="sxs-lookup"><span data-stu-id="22921-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="22921-155">Tek kesimli büyük/küçük harf ile ilgilenen hızlı bir yol.</span><span class="sxs-lookup"><span data-stu-id="22921-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="22921-156">Bölümler arasında bölünen verilerle ilgilenen yavaş bir yol.</span><span class="sxs-lookup"><span data-stu-id="22921-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="22921-157">Verileri çok kesimli dizilerden işlemek için kullanılabilecek birkaç yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="22921-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="22921-158">Kullanın [`SequenceReader<T>`](#sequencereadert) .</span><span class="sxs-lookup"><span data-stu-id="22921-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="22921-159">Segmenti segmente göre ayrıştırır, `SequencePosition` kesim içindeki ve dizininin izini saklayın.</span><span class="sxs-lookup"><span data-stu-id="22921-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="22921-160">Bu, gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="22921-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="22921-161">Öğesini `ReadOnlySequence<T>` bitişik bir diziye kopyalayın ve tek bir arabellek gibi değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="22921-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="22921-162">Boyutu `ReadOnlySequence<T>` küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanılarak verileri yığına ayrılmış bir arabelleğe kopyalamanız makul olabilir.</span><span class="sxs-lookup"><span data-stu-id="22921-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="22921-163">Öğesini `ReadOnlySequence<T>` kullanarak havuza alınmış bir diziye kopyalayın <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="22921-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="22921-164">[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="22921-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="22921-165">Bu, yığın üzerinde yeni bir ayırdığı için etkin yollarda önerilmez `T[]` .</span><span class="sxs-lookup"><span data-stu-id="22921-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="22921-166">Aşağıdaki örneklerde, işleme için bazı yaygın durumlar gösterilmektedir `ReadOnlySequence<byte>` :</span><span class="sxs-lookup"><span data-stu-id="22921-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="22921-167">İkili verileri işle</span><span class="sxs-lookup"><span data-stu-id="22921-167">Process binary data</span></span>

<span data-ttu-id="22921-168">Aşağıdaki örnek, öğesinin başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="22921-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="22921-169">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="22921-169">Process text data</span></span>

<span data-ttu-id="22921-170">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="22921-170">The following example:</span></span>

- <span data-ttu-id="22921-171">İçindeki ilk yeni satırı ( `\r\n` ) bulur `ReadOnlySequence<byte>` ve ' Line ' parametresi aracılığıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="22921-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="22921-172">Giriş arabelleğinden hariç bırakarak bu satırı kırpar `\r\n` .</span><span class="sxs-lookup"><span data-stu-id="22921-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="22921-173">Boş segmentler</span><span class="sxs-lookup"><span data-stu-id="22921-173">Empty segments</span></span>

<span data-ttu-id="22921-174">Boş kesimleri bir içinde depolamak için geçerlidir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="22921-175">Kesimleri açıkça Numaralandırırken boş kesimler meydana gelebilir:</span><span class="sxs-lookup"><span data-stu-id="22921-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="22921-176">Yukarıdaki kod, `ReadOnlySequence<byte>` boş kesimleri olan bir oluşturur ve bu boş segmentlerin çeşitli API 'leri nasıl etkilediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="22921-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="22921-177">`ReadOnlySequence<T>.Slice`boş bir `SequencePosition` kesime işaret eden, bu segmenti korur.</span><span class="sxs-lookup"><span data-stu-id="22921-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="22921-178">`ReadOnlySequence<T>.Slice`bir int ile boş kesimleri atlar.</span><span class="sxs-lookup"><span data-stu-id="22921-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="22921-179">Numaralandırma, `ReadOnlySequence<T>` boş kesimleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="22921-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="22921-180">ReadOnlySequence \< T> ve SequencePosition ile ilgili olası sorunlar</span><span class="sxs-lookup"><span data-stu-id="22921-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="22921-181">Bir ile ve normal arasında işlem yaparken birkaç olağandışı sonuç vardır `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` :</span><span class="sxs-lookup"><span data-stu-id="22921-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="22921-182">`SequencePosition``ReadOnlySequence<T>`, mutlak bir konum değil, belirli bir konum işaretleyicisi.</span><span class="sxs-lookup"><span data-stu-id="22921-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="22921-183">Belirli bir göreli olduğundan `ReadOnlySequence<T>` , kaynaklandığı konum dışında kullanılırsa anlamı yoktur `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="22921-184">Aritmetik, olmadan üzerinde gerçekleştirilemez `SequencePosition` `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="22921-185">Bu, gibi temel nesnelerin `position++` yazıldığı anlamına gelir `ReadOnlySequence<T>.GetPosition(position, 1)` .</span><span class="sxs-lookup"><span data-stu-id="22921-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="22921-186">`GetPosition(long)`negatif **dizinleri desteklemez.**</span><span class="sxs-lookup"><span data-stu-id="22921-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="22921-187">Diğer bir deyişle, tüm kesimleri yürümeden ikinciden son karaktere ulaşmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="22921-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="22921-188">İkisi `SequencePosition` karşılaştırılamıyor, şunları yapmayı zorlaştırıyor:</span><span class="sxs-lookup"><span data-stu-id="22921-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="22921-189">Bir konumun başka bir konumdan büyük veya küçük olup olmadığını öğrenin.</span><span class="sxs-lookup"><span data-stu-id="22921-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="22921-190">Bazı ayrıştırma algoritmaları yazın.</span><span class="sxs-lookup"><span data-stu-id="22921-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="22921-191">`ReadOnlySequence<T>`, bir nesne başvurusundan daha büyük ve [içinde](../../csharp/language-reference/keywords/in-parameter-modifier.md) ya da mümkün olduğunda [başvuru](../../csharp/language-reference/keywords/ref.md) olarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="22921-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="22921-192">`ReadOnlySequence<T>` `in` `ref` [Yapının](../../csharp/language-reference/builtin-types/struct.md)kopyalarını geçirerek veya azaltır.</span><span class="sxs-lookup"><span data-stu-id="22921-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="22921-193">Boş segmentler:</span><span class="sxs-lookup"><span data-stu-id="22921-193">Empty segments:</span></span>
  - <span data-ttu-id="22921-194">, Bir içinde geçerlidir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="22921-195">Yöntemi kullanılarak yinelenirken görünebilirler `ReadOnlySequence<T>.TryGet` .</span><span class="sxs-lookup"><span data-stu-id="22921-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="22921-196">, Metodu nesneleriyle birlikte kullanarak diziyi Dilimleme gibi görünebilir `ReadOnlySequence<T>.Slice()` `SequencePosition` .</span><span class="sxs-lookup"><span data-stu-id="22921-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="22921-197">SequenceReader \< T\></span><span class="sxs-lookup"><span data-stu-id="22921-197">SequenceReader\<T\></span></span>

<span data-ttu-id="22921-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="22921-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="22921-199">, .NET Core 3,0 ' de tanıtılan ve işlemesini basitleştirecek yeni bir türdür `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="22921-200">Tek bir segment `ReadOnlySequence<T>` ve çok segment arasındaki farkları birleştirir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="22921-201">`byte` `char` , Parçalar arasında bölünecek veya bölünemeyeceği ikili ve metin verilerini (ve) okumak için yardımcılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="22921-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="22921-202">Hem ikili hem de sınırlandırılmış verilerin işlenmesiyle ilgili yerleşik yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="22921-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="22921-203">Aşağıdaki bölümde, aynı yöntemlerin bu şekilde nasıl gösterdiği gösterilmektedir `SequenceReader<T>` :</span><span class="sxs-lookup"><span data-stu-id="22921-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="22921-204">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="22921-204">Access data</span></span>

<span data-ttu-id="22921-205">`SequenceReader<T>`, doğrudan içindeki verileri numaralandırma yöntemlerine sahiptir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="22921-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="22921-206">Aşağıdaki kod, bir seferde bir işlem işleme örneğidir `ReadOnlySequence<byte>` `byte` :</span><span class="sxs-lookup"><span data-stu-id="22921-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="22921-207">, `CurrentSpan` `Span` Yönteminde el ile yapılan yönteme benzer şekilde, geçerli segmenti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="22921-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="22921-208">Kullanım konumu</span><span class="sxs-lookup"><span data-stu-id="22921-208">Use position</span></span>

<span data-ttu-id="22921-209">Aşağıdaki kod, şunu kullanmanın örnek bir uygulamasıdır `FindIndexOf` `SequenceReader<T>` :</span><span class="sxs-lookup"><span data-stu-id="22921-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="22921-210">İkili verileri işle</span><span class="sxs-lookup"><span data-stu-id="22921-210">Process binary data</span></span>

<span data-ttu-id="22921-211">Aşağıdaki örnek, öğesinin başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="22921-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="22921-212">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="22921-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="22921-213">SequenceReader \< T \> yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="22921-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="22921-214">`SequenceReader<T>`Değişebilir bir yapı olduğundan, her zaman [başvuruya](../../csharp/language-reference/keywords/ref.md)göre geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="22921-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="22921-215">`SequenceReader<T>`yalnızca zaman uyumlu metotlarda kullanılabilmesi ve alanlarda depolanabilmesi için [başvuru yapısı](../../csharp/language-reference/builtin-types/struct.md#ref-struct) .</span><span class="sxs-lookup"><span data-stu-id="22921-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="22921-216">Daha fazla bilgi için bkz. [yazma güvenli ve verimli C# kodu](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="22921-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="22921-217">`SequenceReader<T>`yalnızca ileri bir okuyucu olarak kullanılmak üzere iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22921-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="22921-218">`Rewind`, diğer `Read` , ve API 'lerden yararlanarak belirtilemeyilecek küçük yedeklemeler için tasarlanmıştır `Peek` `IsNext` .</span><span class="sxs-lookup"><span data-stu-id="22921-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
