---
title: System.Buffers - .NET
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
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="b2bb8-102">.NET'te Arabelleklerle Çalışın</span><span class="sxs-lookup"><span data-stu-id="b2bb8-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="b2bb8-103">Bu makalede, birden çok arabellek te çalışan verilerin okunmasına yardımcı olan türlerin genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="b2bb8-104">Öncelikle nesneleri desteklemek <xref:System.IO.Pipelines.PipeReader> için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="b2bb8-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="b2bb8-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="b2bb8-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>senkron arabellekli yazı için bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="b2bb8-107">En düşük düzeyde, arabirim:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="b2bb8-108">Temel ve kullanımı zor değildir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="b2bb8-109">Bir <xref:System.Memory%601> veya <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="b2bb8-110">Veya `Memory<T>` `Span<T>` yazılabilir ve kaç `T` öğe nin yazıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="b2bb8-111">Önceki yöntem:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-111">The preceding method:</span></span>

- <span data-ttu-id="b2bb8-112">`IBufferWriter<byte>` Kullanarak `GetSpan(5)`en az 5 bayt lık bir arabellek ister.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="b2bb8-113">Döndürülen `Span<byte>`ASCII dizesi "Hello" için bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="b2bb8-114">Arabelleğe kaç bayt yazıldığını gösteren çağrılar. <xref:System.Buffers.IBufferWriter%601></span><span class="sxs-lookup"><span data-stu-id="b2bb8-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="b2bb8-115">Bu `Memory<T>` / `Span<T>` yazma yöntemi, `IBufferWriter<T>`..</span><span class="sxs-lookup"><span data-stu-id="b2bb8-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="b2bb8-116">Alternatif olarak, <xref:System.Buffers.BuffersExtensions.Write%2A> uzantı yöntemi varolan bir arabelleği kopyalamak için `IBufferWriter<T>`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="b2bb8-117">`Write`uygun olarak arama `GetSpan` / `Advance` işi yapar, bu nedenle yazdıktan sonra aramaya `Advance` gerek yoktur:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="b2bb8-118"><xref:System.Buffers.ArrayBufferWriter%601>`IBufferWriter<T>` olan destek deposu tek bir bitişik dizi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="b2bb8-119">IBufferWriter sık karşılaşılan sorunlar</span><span class="sxs-lookup"><span data-stu-id="b2bb8-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="b2bb8-120">`GetSpan`ve `GetMemory` en az istenen bellek miktarı ile bir arabellek döndürün.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="b2bb8-121">Tam arabellek boyutları varsayma.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="b2bb8-122">Ardışık aramaların aynı arabelleği veya aynı boyuttaara bellek döndüreceğinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="b2bb8-123">Daha fazla veri yazmaya devam `Advance` etmek için çağrıda bulunduktan sonra yeni bir arabellek istenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="b2bb8-124">Daha önce edinilen bir arabellek `Advance` sonra çağrılmıştır yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="b2bb8-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="b2bb8-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence, belleği pipe'de ve salt okunur belleğin sıra konumunun altında gösteren](media/buffers/ro-sequence.png)

<span data-ttu-id="b2bb8-127"><xref:System.Buffers.ReadOnlySequence%601>'nin bitişik veya bitişik olmayan sırasını temsil eden bir `T`yapıdır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="b2bb8-128">Bu inşa edilebilir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-128">It can be constructed from:</span></span>

1. <span data-ttu-id="b2bb8-129">Bir `T[]`</span><span class="sxs-lookup"><span data-stu-id="b2bb8-129">A `T[]`</span></span>
1. <span data-ttu-id="b2bb8-130">Bir `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="b2bb8-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="b2bb8-131">Dizinin başlangıç <xref:System.Buffers.ReadOnlySequenceSegment%601> ve bitiş konumunu temsil eden bağlantılı liste düğümü ve dizin çifti.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="b2bb8-132">Üçüncü temsil en ilginç olan ın üzerinde çeşitli operasyonlar üzerinde `ReadOnlySequence<T>`performans etkileri vardır:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="b2bb8-133">Gösterimi</span><span class="sxs-lookup"><span data-stu-id="b2bb8-133">Representation</span></span>|<span data-ttu-id="b2bb8-134">İşlem</span><span class="sxs-lookup"><span data-stu-id="b2bb8-134">Operation</span></span>|<span data-ttu-id="b2bb8-135">Karmaşıklık</span><span class="sxs-lookup"><span data-stu-id="b2bb8-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="b2bb8-136">Bu karışık gösterim nedeniyle, dizinleri `SequencePosition` tamsayı yerine ortaya `ReadOnlySequence<T>` çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="b2bb8-137">A `SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="b2bb8-138">Geldiği `ReadOnlySequence<T>` yere bir dizin temsil eden opak bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="b2bb8-139">İki bölümden oluşur, bir sasayı ve bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="b2bb8-140">Bu iki değerin temsil iå `ReadOnlySequence<T>`lemi nin uygulanmasına bağlı olanı</span><span class="sxs-lookup"><span data-stu-id="b2bb8-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="b2bb8-141">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="b2bb8-141">Access data</span></span>

<span data-ttu-id="b2bb8-142">Verileri `ReadOnlySequence<T>` bir yılbme olarak ortaya `ReadOnlyMemory<T>`çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="b2bb8-143">Segmentlerin her biri sayısallama temel bir foreach kullanılarak yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="b2bb8-144">Önceki yöntem, her kesimi belirli bir bayt için arar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="b2bb8-145">Her segmentin takip etmek `SequencePosition`gerekiyorsa, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="b2bb8-146">Sonraki örnek, bir tamsayı yerine `SequencePosition` bir döndürmek için önceki kodu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="b2bb8-147">A'yı `SequencePosition` döndürme, arayanın belirli bir dizindeki verileri almak için ikinci bir tazından kaçınmasına izin verme avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="b2bb8-148">Kombinasyonu `SequencePosition` ve `TryGet` bir sayısalatör gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="b2bb8-149">Konum alanı, her yinelemenin başında, `ReadOnlySequence<T>`içindeki her kesimin başlangıcı olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="b2bb8-150">Önceki yöntem üzerinde `ReadOnlySequence<T>`bir uzantı yöntemi olarak var.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="b2bb8-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>önceki kodu basitleştirmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="b2bb8-152">Bir ReadOnlySequence\<T'yi İşleme\></span><span class="sxs-lookup"><span data-stu-id="b2bb8-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="b2bb8-153">Veriler `ReadOnlySequence<T>` dizi içinde birden çok segmente bölünebildiği için a'yı işlemek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="b2bb8-154">En iyi performans için kodu iki eşite bölün:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="b2bb8-155">Tek segmentli durumla ilgilenen hızlı bir yol.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="b2bb8-156">Segmentler arasında bölünmüş verilerle ilgilenen yavaş bir yol.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="b2bb8-157">Verileri çok parçalı dizilerde işlemek için kullanılabilecek birkaç yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="b2bb8-158">[`SequenceReader<T>`](#sequencereadert)Kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="b2bb8-159">Ayrışdırılmış segment içindeki `SequencePosition` ve dizin izleme, segmente göre ayrışt.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="b2bb8-160">Bu gereksiz ayırmaları önler, ancak özellikle küçük arabellekler için verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="b2bb8-161">Bitişik `ReadOnlySequence<T>` bir diziye kopyalayın ve tek bir arabellek gibi davranın:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="b2bb8-162">Boyutu `ReadOnlySequence<T>` küçükse, [stackalloc](../../csharp/language-reference/operators/stackalloc.md) işleci kullanarak verileri yığınayrılmış bir arabelleğe kopyalamak makul olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="b2bb8-163">Kullanarak `ReadOnlySequence<T>` birleştirilmiş diziye <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="b2bb8-164">[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="b2bb8-165">Bu yığın üzerinde yeni `T[]` bir ayırır gibi sıcak yollarda tavsiye edilmez.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="b2bb8-166">Aşağıdaki örnekler, işleme `ReadOnlySequence<byte>`için bazı yaygın durumlarda göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="b2bb8-167">İkili verileri işleme</span><span class="sxs-lookup"><span data-stu-id="b2bb8-167">Process binary data</span></span>

<span data-ttu-id="b2bb8-168">Aşağıdaki örnek, 4 baytlık bir büyük endian tamsayı uzunluğunu `ReadOnlySequence<byte>`başından itibaren ayrışdırır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="b2bb8-169">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="b2bb8-169">Process text data</span></span>

<span data-ttu-id="b2bb8-170">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-170">The following example:</span></span>

- <span data-ttu-id="b2bb8-171">İlk yeni hattı`\r\n`bulur ( `ReadOnlySequence<byte>` ) ve çıkış 'çizgi' parametresi ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="b2bb8-172">Giriş arabelleği `\r\n` hariç, bu satırı kırpar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="b2bb8-173">Boş segmentler</span><span class="sxs-lookup"><span data-stu-id="b2bb8-173">Empty segments</span></span>

<span data-ttu-id="b2bb8-174">Boş segmentleri bir `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="b2bb8-175">Boş segmentler, segmentleri açıkça sayısalarken oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="b2bb8-176">Önceki kod boş segmentleri ile bir `ReadOnlySequence<byte>` oluşturur ve bu boş segmentleri çeşitli API'ler nasıl etkilediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="b2bb8-177">`ReadOnlySequence<T>.Slice`boş `SequencePosition` bir segmente işaret ile bu kesimi korur.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="b2bb8-178">`ReadOnlySequence<T>.Slice`boş segmentler üzerinden atlar bir int ile.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="b2bb8-179">Boş segmentleri `ReadOnlySequence<T>` sayısallaştırıyor.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="b2bb8-180">ReadOnlySequence\<T> ve SequencePosition ile olası sorunlar</span><span class="sxs-lookup"><span data-stu-id="b2bb8-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="b2bb8-181">`ReadOnlySequence<T>` / Bir `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>`vs /normal `T[]`ile uğraşırken birkaç olağandışı sonuçları vardır: / `int`</span><span class="sxs-lookup"><span data-stu-id="b2bb8-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="b2bb8-182">`SequencePosition`belirli `ReadOnlySequence<T>`bir pozisyon için bir konum işaretçisi, mutlak bir konum değil.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="b2bb8-183">Belirli bir göreceli olduğu `ReadOnlySequence<T>`için, geldiği `ReadOnlySequence<T>` yerin dışında kullanıldığında bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="b2bb8-184">Aritmetik `SequencePosition` olmadan `ReadOnlySequence<T>`yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="b2bb8-185">Bu, yazıldığı `ReadOnlySequence<T>.GetPosition(position, 1)`gibi `position++` temel şeyler yapmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="b2bb8-186">`GetPosition(long)`negatif dizinleri **desteklemez.**</span><span class="sxs-lookup"><span data-stu-id="b2bb8-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="b2bb8-187">Bu da demek oluyor ki, tüm bölümlerde yürümeden ikinciden son karaktere ulaşmak imkansız.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="b2bb8-188">İki `SequencePosition` karşılaştırılamaz, bu da zorlaştırır:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="b2bb8-189">Bir konumun başka bir konumdan daha büyük mü yoksa daha az mı olduğunu bilin.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="b2bb8-190">Bazı ayrışma algoritmaları yazın.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="b2bb8-191">`ReadOnlySequence<T>`bir nesne referansından daha büyüktür ve mümkünse içinde [veya](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../csharp/language-reference/keywords/ref.md) tarafından geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="b2bb8-192">Geçen `ReadOnlySequence<T>` `in` veya `ref` [yapıkopyalarını](../../csharp/language-reference/builtin-types/struct.md)azaltır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="b2bb8-193">Boş segmentler:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-193">Empty segments:</span></span>
  - <span data-ttu-id="b2bb8-194">Bir `ReadOnlySequence<T>`içinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="b2bb8-195">`ReadOnlySequence<T>.TryGet` Yöntemi kullanarak yinelediğinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="b2bb8-196">Nesnelerle `ReadOnlySequence<T>.Slice()` `SequencePosition` yöntemi kullanarak dizi dilimleme görünebilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="b2bb8-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="b2bb8-197">SequenceReader\<T\></span></span>

<span data-ttu-id="b2bb8-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="b2bb8-199">.NET Core 3.0'da bir işlemin basitleştirilmesini kolaylaştırmak `ReadOnlySequence<T>`için tanıtılan yeni bir türdür.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="b2bb8-200">Tek bir segment `ReadOnlySequence<T>` ve çok segment `ReadOnlySequence<T>`arasındaki farkları birleşdirir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="b2bb8-201">Bölümlere bölünebilen veya bölünmeyen ikili ve metin verilerini (ve)`byte` `char`okumak için yardımcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="b2bb8-202">Hem ikili hem de sınırlı verilerin işlenmesiyle başa çıkmak için yerleşik yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="b2bb8-203">Aşağıdaki bölümde bu aynı yöntemlerin `SequenceReader<T>`nasıl göründüğünü göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="b2bb8-204">Verilere erişme</span><span class="sxs-lookup"><span data-stu-id="b2bb8-204">Access data</span></span>

<span data-ttu-id="b2bb8-205">`SequenceReader<T>``ReadOnlySequence<T>` doğrudan içinde veri sayısallama yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="b2bb8-206">Aşağıdaki kod, bir defada `ReadOnlySequence<byte>` `byte` a işleme örneğidir:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="b2bb8-207">Geçerli `CurrentSpan` segmentin `Span`, yöntemde el ile yapılana benzer bir şekilde ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="b2bb8-208">Pozisyon kullanın</span><span class="sxs-lookup"><span data-stu-id="b2bb8-208">Use position</span></span>

<span data-ttu-id="b2bb8-209">Aşağıdaki kod `FindIndexOf` kullanarak bir örnek `SequenceReader<T>`uygulamadır:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="b2bb8-210">İkili verileri işleme</span><span class="sxs-lookup"><span data-stu-id="b2bb8-210">Process binary data</span></span>

<span data-ttu-id="b2bb8-211">Aşağıdaki örnek, 4 baytlık bir büyük endian tamsayı uzunluğunu `ReadOnlySequence<byte>`başından itibaren ayrışdırır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="b2bb8-212">Metin verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="b2bb8-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="b2bb8-213">SequenceReader\<\> T sık karşılaşılan sorunlar</span><span class="sxs-lookup"><span data-stu-id="b2bb8-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="b2bb8-214">Mutable bir yapı `SequenceReader<T>` olduğundan, her zaman [başvuru](../../csharp/language-reference/keywords/ref.md)ile geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="b2bb8-215">`SequenceReader<T>`bir [ref struct'dur,](../../csharp/language-reference/builtin-types/struct.md#ref-struct) bu nedenle yalnızca senkron yöntemlerle kullanılabilir ve alanlarda depolanamamaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="b2bb8-216">Daha fazla bilgi için bkz: [Güvenli ve verimli C# kodu yaz.](../../csharp/write-safe-efficient-code.md)</span><span class="sxs-lookup"><span data-stu-id="b2bb8-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="b2bb8-217">`SequenceReader<T>`yalnızca ileri okuyucu olarak kullanılmak üzere optimize edilsin.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="b2bb8-218">`Rewind`diğer `Read`ve `Peek` `IsNext` API'ler kullanılarak ele alınamaz küçük yedeklemeler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
