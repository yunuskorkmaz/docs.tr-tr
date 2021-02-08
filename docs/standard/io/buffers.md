---
description: "Hakkında daha fazla bilgi edinin: .NET 'te arabellekler ile çalışma"
title: System. buffers-.NET
ms.date: 12/05/2019
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 988ac5cae192b815ccac74f1bf15055538244bda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782435"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="d8cc0-103">.NET 'teki arabelleklerle çalışma</span><span class="sxs-lookup"><span data-stu-id="d8cc0-103">Work with Buffers in .NET</span></span>

<span data-ttu-id="d8cc0-104">Bu makalede, birden çok arabelleğe çalışan verileri okumaya yardımcı olan türlere genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-104">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="d8cc0-105">Bunlar öncelikle nesneleri desteklemek için kullanılır <xref:System.IO.Pipelines.PipeReader> .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-105">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="d8cc0-106">Ibufferwriter\<T\></span><span class="sxs-lookup"><span data-stu-id="d8cc0-106">IBufferWriter\<T\></span></span>

<span data-ttu-id="d8cc0-107"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> , zaman uyumlu arabelleğe alınmış yazma için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-107"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="d8cc0-108">En düşük düzeyde, arabirimi:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-108">At the lowest level, the interface:</span></span>

- <span data-ttu-id="d8cc0-109">Temel ve kullanılması zor değildir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-109">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="d8cc0-110">Veya erişimine izin verir <xref:System.Memory%601> <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-110">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="d8cc0-111">`Memory<T>`Veya `Span<T>` üzerine yazılabilir ve kaç `T` öğe yazıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-111">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="d8cc0-112">Önceki Yöntem:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-112">The preceding method:</span></span>

- <span data-ttu-id="d8cc0-113">Kullanarak en az 5 baytlık bir arabellek ister `IBufferWriter<byte>` `GetSpan(5)` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-113">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="d8cc0-114">"Hello" ASCII dizesi için verilen baytları döndürülen öğesine yazar `Span<byte>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-114">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="d8cc0-115"><xref:System.Buffers.IBufferWriter%601>Arabelleğe kaç bayt yazıldığını belirten çağrılar.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-115">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="d8cc0-116">Bu yazma yöntemi `Memory<T>` / `Span<T>` , tarafından sağlanmış olan arabelleği kullanır `IBufferWriter<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-116">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="d8cc0-117">Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> genişletme yöntemi var olan bir arabelleği öğesine kopyalamak için kullanılabilir `IBufferWriter<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-117">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="d8cc0-118">`Write`, doğru çağırma işini yapar `GetSpan` / `Advance` , bu nedenle `Advance` yazmadan sonra çağrı gerekmez:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-118">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="d8cc0-119"><xref:System.Buffers.ArrayBufferWriter%601> , `IBufferWriter<T>` yedekleme deposu tek bir bitişik dizi olan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-119"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="d8cc0-120">Ibufferwriter yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="d8cc0-120">IBufferWriter common problems</span></span>

- <span data-ttu-id="d8cc0-121">`GetSpan` ve `GetMemory` en az istenen bellek miktarına sahip bir arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-121">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="d8cc0-122">Tam arabellek boyutlarını kabul etmeyin.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-122">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="d8cc0-123">Art arda yapılan çağrıların aynı arabelleğe veya aynı boyutlu arabelleğe Döneceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-123">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="d8cc0-124">`Advance`Daha fazla veri yazmaya devam etmek için çağrıldıktan sonra yeni bir arabellek istenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-124">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="d8cc0-125">Daha önce elde edilen bir arabellek çağrıldıktan sonra üzerine yazılamaz `Advance` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-125">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="d8cc0-126">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="d8cc0-126">ReadOnlySequence\<T\></span></span>

![Salt okunan belleğin sıra konumunun kanalda ve altında belleği gösteren ReadOnlySequence](media/buffers/ro-sequence.png)

<span data-ttu-id="d8cc0-128"><xref:System.Buffers.ReadOnlySequence%601> , ardışık veya bitişik olmayan dizisini temsil eden bir struct `T` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-128"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="d8cc0-129">Oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-129">It can be constructed from:</span></span>

1. <span data-ttu-id="d8cc0-130">`T[]`</span><span class="sxs-lookup"><span data-stu-id="d8cc0-130">A `T[]`</span></span>
1. <span data-ttu-id="d8cc0-131">`ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="d8cc0-131">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="d8cc0-132"><xref:System.Buffers.ReadOnlySequenceSegment%601>Dizinin başlangıç ve bitiş konumunu temsil eden bağlantılı liste düğümü ve Dizin çifti.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-132">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="d8cc0-133">Üçüncü Gösterim, üzerinde çeşitli işlemlerde performans etkilerine sahip olduğu için en ilginç bir gösterimidir `ReadOnlySequence<T>` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-133">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="d8cc0-134">İmle</span><span class="sxs-lookup"><span data-stu-id="d8cc0-134">Representation</span></span>|<span data-ttu-id="d8cc0-135">İşlem</span><span class="sxs-lookup"><span data-stu-id="d8cc0-135">Operation</span></span>|<span data-ttu-id="d8cc0-136">Karmaşıklık</span><span class="sxs-lookup"><span data-stu-id="d8cc0-136">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="d8cc0-137">Bu karışık Gösterim nedeniyle `ReadOnlySequence<T>` dizinleri `SequencePosition` bir tamsayı yerine kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-137">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="d8cc0-138">Y `SequencePosition` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-138">A `SequencePosition`:</span></span>

- <span data-ttu-id="d8cc0-139">, Kaynaklandığı yere bir dizin temsil eden donuk bir değerdir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-139">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="d8cc0-140">İki bölümden oluşur, bir tamsayı ve bir nesne.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-140">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="d8cc0-141">Bu iki değerin uygulamasının uygulamasına bağlı olması `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-141">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="d8cc0-142">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="d8cc0-142">Access data</span></span>

<span data-ttu-id="d8cc0-143">`ReadOnlySequence<T>`Verileri numaralandırılabilir olarak gösterir `ReadOnlyMemory<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-143">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="d8cc0-144">Parçaların her birini numaralandırma, temel bir foreach kullanılarak yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-144">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="d8cc0-145">Yukarıdaki yöntem, her segmenti belirli bir bayt arar.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-145">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="d8cc0-146">Her bir parçayı takip etmeniz gerekiyorsa `SequencePosition` , <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-146">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="d8cc0-147">Sonraki örnek, önceki kodu bir tamsayı yerine döndürecek şekilde değiştirir `SequencePosition` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-147">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="d8cc0-148">Bir döndürmek `SequencePosition` , çağıranın belirli bir dizindeki verileri almak için ikinci bir taramayı önlemenize izin vermenin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-148">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="d8cc0-149">Birleşimi `SequencePosition` ve `TryGet` bir Numaralandırıcı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-149">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="d8cc0-150">Konum alanı her bir yinelemenin başlangıcında, içindeki her bir segmentin başlaması için değiştirilir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-150">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="d8cc0-151">Önceki yöntem üzerinde bir genişletme yöntemi olarak mevcuttur `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-151">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="d8cc0-152"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> , önceki kodu basitleştirmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-152"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="d8cc0-153">ReadOnlySequence işleme\<T\></span><span class="sxs-lookup"><span data-stu-id="d8cc0-153">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="d8cc0-154">`ReadOnlySequence<T>`Verilerin dizideki birden çok parçaya bölünmesi gerektiğinden, işleme bir işlem zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-154">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="d8cc0-155">En iyi performansı elde etmek için kodu iki yola ayırın:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-155">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="d8cc0-156">Tek kesimli büyük/küçük harf ile ilgilenen hızlı bir yol.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-156">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="d8cc0-157">Bölümler arasında bölünen verilerle ilgilenen yavaş bir yol.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-157">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="d8cc0-158">Verileri çok kesimli dizilerden işlemek için kullanılabilecek birkaç yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-158">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="d8cc0-159">Kullanın [`SequenceReader<T>`](#sequencereadert) .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-159">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="d8cc0-160">Segmenti segmente göre ayrıştırır, `SequencePosition` kesim içindeki ve dizininin izini saklayın.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-160">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="d8cc0-161">Bu, gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-161">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="d8cc0-162">Öğesini `ReadOnlySequence<T>` bitişik bir diziye kopyalayın ve tek bir arabellek gibi değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-162">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="d8cc0-163">Boyutu `ReadOnlySequence<T>` küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanılarak verileri yığına ayrılmış bir arabelleğe kopyalamanız makul olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-163">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="d8cc0-164">Öğesini `ReadOnlySequence<T>` kullanarak havuza alınmış bir diziye kopyalayın <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-164">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="d8cc0-165">[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-165">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="d8cc0-166">Bu, yığın üzerinde yeni bir ayırdığı için etkin yollarda önerilmez `T[]` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-166">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="d8cc0-167">Aşağıdaki örneklerde, işleme için bazı yaygın durumlar gösterilmektedir `ReadOnlySequence<byte>` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-167">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="d8cc0-168">İkili verileri işle</span><span class="sxs-lookup"><span data-stu-id="d8cc0-168">Process binary data</span></span>

<span data-ttu-id="d8cc0-169">Aşağıdaki örnek, öğesinin başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-169">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="d8cc0-170">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="d8cc0-170">Process text data</span></span>

<span data-ttu-id="d8cc0-171">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-171">The following example:</span></span>

- <span data-ttu-id="d8cc0-172">İçindeki ilk yeni satırı ( `\r\n` ) bulur `ReadOnlySequence<byte>` ve ' Line ' parametresi aracılığıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-172">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="d8cc0-173">Giriş arabelleğinden hariç bırakarak bu satırı kırpar `\r\n` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-173">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="d8cc0-174">Boş segmentler</span><span class="sxs-lookup"><span data-stu-id="d8cc0-174">Empty segments</span></span>

<span data-ttu-id="d8cc0-175">Boş kesimleri bir içinde depolamak için geçerlidir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-175">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="d8cc0-176">Kesimleri açıkça Numaralandırırken boş kesimler meydana gelebilir:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-176">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="d8cc0-177">Yukarıdaki kod, `ReadOnlySequence<byte>` boş kesimleri olan bir oluşturur ve bu boş segmentlerin çeşitli API 'leri nasıl etkilediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-177">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="d8cc0-178">`ReadOnlySequence<T>.Slice` boş bir `SequencePosition` kesime işaret eden, bu segmenti korur.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-178">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="d8cc0-179">`ReadOnlySequence<T>.Slice` bir int ile boş kesimleri atlar.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-179">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="d8cc0-180">Numaralandırma, `ReadOnlySequence<T>` boş kesimleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-180">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="d8cc0-181">ReadOnlySequence ve SequencePosition ile ilgili olası sorunlar \<T></span><span class="sxs-lookup"><span data-stu-id="d8cc0-181">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="d8cc0-182">Bir ile ve normal arasında işlem yaparken birkaç olağandışı sonuç vardır `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-182">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="d8cc0-183">`SequencePosition``ReadOnlySequence<T>`, mutlak bir konum değil, belirli bir konum işaretleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-183">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="d8cc0-184">Belirli bir göreli olduğundan `ReadOnlySequence<T>` , kaynaklandığı konum dışında kullanılırsa anlamı yoktur `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-184">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="d8cc0-185">Aritmetik, olmadan üzerinde gerçekleştirilemez `SequencePosition` `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-185">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="d8cc0-186">Bu, gibi temel nesnelerin `position++` yazıldığı anlamına gelir `ReadOnlySequence<T>.GetPosition(position, 1)` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-186">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="d8cc0-187">`GetPosition(long)`negatif **dizinleri desteklemez.**</span><span class="sxs-lookup"><span data-stu-id="d8cc0-187">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="d8cc0-188">Diğer bir deyişle, tüm kesimleri yürümeden ikinciden son karaktere ulaşmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-188">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="d8cc0-189">İkisi `SequencePosition` karşılaştırılamıyor, şunları yapmayı zorlaştırıyor:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-189">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="d8cc0-190">Bir konumun başka bir konumdan büyük veya küçük olup olmadığını öğrenin.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-190">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="d8cc0-191">Bazı ayrıştırma algoritmaları yazın.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-191">Write some parsing algorithms.</span></span>
- <span data-ttu-id="d8cc0-192">`ReadOnlySequence<T>` , bir nesne başvurusundan daha büyük ve [içinde](../../csharp/language-reference/keywords/in-parameter-modifier.md) ya da mümkün olduğunda [başvuru](../../csharp/language-reference/keywords/ref.md) olarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-192">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="d8cc0-193">`ReadOnlySequence<T>` `in` `ref` [Yapının](../../csharp/language-reference/builtin-types/struct.md)kopyalarını geçirerek veya azaltır.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-193">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="d8cc0-194">Boş segmentler:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-194">Empty segments:</span></span>
  - <span data-ttu-id="d8cc0-195">, Bir içinde geçerlidir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-195">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="d8cc0-196">Yöntemi kullanılarak yinelenirken görünebilirler `ReadOnlySequence<T>.TryGet` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-196">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="d8cc0-197">, Metodu nesneleriyle birlikte kullanarak diziyi Dilimleme gibi görünebilir `ReadOnlySequence<T>.Slice()` `SequencePosition` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-197">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="d8cc0-198">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="d8cc0-198">SequenceReader\<T\></span></span>

<span data-ttu-id="d8cc0-199"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="d8cc0-199"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="d8cc0-200">, .NET Core 3,0 ' de tanıtılan ve işlemesini basitleştirecek yeni bir türdür `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-200">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="d8cc0-201">Tek bir segment `ReadOnlySequence<T>` ve çok segment arasındaki farkları birleştirir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-201">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="d8cc0-202">`byte` `char` , Parçalar arasında bölünecek veya bölünemeyeceği ikili ve metin verilerini (ve) okumak için yardımcılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-202">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="d8cc0-203">Hem ikili hem de sınırlandırılmış verilerin işlenmesiyle ilgili yerleşik yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-203">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="d8cc0-204">Aşağıdaki bölümde, aynı yöntemlerin bu şekilde nasıl gösterdiği gösterilmektedir `SequenceReader<T>` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-204">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="d8cc0-205">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="d8cc0-205">Access data</span></span>

<span data-ttu-id="d8cc0-206">`SequenceReader<T>` , doğrudan içindeki verileri numaralandırma yöntemlerine sahiptir `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-206">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="d8cc0-207">Aşağıdaki kod, bir seferde bir işlem işleme örneğidir `ReadOnlySequence<byte>` `byte` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-207">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="d8cc0-208">, `CurrentSpan` `Span` Yönteminde el ile yapılan yönteme benzer şekilde, geçerli segmenti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-208">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="d8cc0-209">Kullanım konumu</span><span class="sxs-lookup"><span data-stu-id="d8cc0-209">Use position</span></span>

<span data-ttu-id="d8cc0-210">Aşağıdaki kod, şunu kullanmanın örnek bir uygulamasıdır `FindIndexOf` `SequenceReader<T>` :</span><span class="sxs-lookup"><span data-stu-id="d8cc0-210">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="d8cc0-211">İkili verileri işle</span><span class="sxs-lookup"><span data-stu-id="d8cc0-211">Process binary data</span></span>

<span data-ttu-id="d8cc0-212">Aşağıdaki örnek, öğesinin başlangıcından 4 baytlık büyük endian tamsayı uzunluğunu ayrıştırır `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-212">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="d8cc0-213">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="d8cc0-213">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="d8cc0-214">SequenceReader \<T\> genel sorunlar</span><span class="sxs-lookup"><span data-stu-id="d8cc0-214">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="d8cc0-215">`SequenceReader<T>`Değişebilir bir yapı olduğundan, her zaman [başvuruya](../../csharp/language-reference/keywords/ref.md)göre geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-215">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="d8cc0-216">`SequenceReader<T>` yalnızca zaman uyumlu metotlarda kullanılabilmesi ve alanlarda depolanabilmesi için [başvuru yapısı](../../csharp/language-reference/builtin-types/struct.md#ref-struct) .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-216">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="d8cc0-217">Daha fazla bilgi için bkz. [yazma güvenli ve verimli C# kodu](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="d8cc0-217">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="d8cc0-218">`SequenceReader<T>` yalnızca ileri bir okuyucu olarak kullanılmak üzere iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8cc0-218">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="d8cc0-219">`Rewind` , diğer `Read` , ve API 'lerden yararlanarak belirtilemeyilecek küçük yedeklemeler için tasarlanmıştır `Peek` `IsNext` .</span><span class="sxs-lookup"><span data-stu-id="d8cc0-219">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
