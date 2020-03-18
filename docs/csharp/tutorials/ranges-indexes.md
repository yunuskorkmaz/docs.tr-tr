---
title: Endeksleri ve aralıkları kullanarak veri aralıklarını keşfedin
description: Bu gelişmiş öğretici, sıralı veri kümesinin dilimlerini incelemek için endeksleri ve aralıkları kullanarak verileri keşfetmenizi öğretir.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156500"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="2036d-103">Endeksler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="2036d-103">Indices and ranges</span></span>

<span data-ttu-id="2036d-104">Aralıklar ve endeksler, bir dizideki tek öğelere veya aralıklara erişmek için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2036d-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="2036d-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2036d-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2036d-106">Aralıklar için sıralı sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2036d-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="2036d-107">Her dizinin başlangıç ve bitişi için tasarım kararlarını anlayın.</span><span class="sxs-lookup"><span data-stu-id="2036d-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="2036d-108">Senaryoları <xref:System.Index> ve <xref:System.Range> türleri öğrenin.</span><span class="sxs-lookup"><span data-stu-id="2036d-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="2036d-109">Endeksler ve aralıklar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="2036d-109">Language support for indices and ranges</span></span>

<span data-ttu-id="2036d-110">Bu dil desteği iki yeni türe ve iki yeni işleçe dayanır:</span><span class="sxs-lookup"><span data-stu-id="2036d-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="2036d-111"><xref:System.Index?displayProperty=nameWithType>diziye bir dizi içine bir dizi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2036d-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="2036d-112">Bir dizinin dizinin `^`sonuna göreolduğunu belirten son işleçten gelen dizin.</span><span class="sxs-lookup"><span data-stu-id="2036d-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="2036d-113"><xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2036d-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="2036d-114">Aralık işleci, `..`bir aralığın başlangıcını ve sonunu operands olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="2036d-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="2036d-115">Endekskurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="2036d-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="2036d-116">Bir dizi `sequence`düşünün.</span><span class="sxs-lookup"><span data-stu-id="2036d-116">Consider an array `sequence`.</span></span> <span data-ttu-id="2036d-117">Dizin `0` `sequence[0]`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2036d-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="2036d-118">Dizin `^0` `sequence[sequence.Length]`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2036d-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="2036d-119">İfade, `sequence[^0]` tıpkı olduğu gibi `sequence[sequence.Length]` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2036d-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="2036d-120">Herhangi bir `n`sayı `^n` için dizin `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="2036d-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="2036d-121">`^1` Dizinle son sözcüğü alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2036d-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="2036d-122">Başlatmanın altına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2036d-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="2036d-123">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="2036d-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="2036d-124">Aralıklar özeldir, yani *sonu* aralıkta dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="2036d-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="2036d-125">Aralık, `[0..^0]` tüm aralığı `[0..sequence.Length]` temsil eder gibi tüm aralığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2036d-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="2036d-126">Aşağıdaki kod ,"hızlı", "kahverengi" ve "tilki" sözcükleri içeren bir alt aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2036d-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="2036d-127">Bu `words[1]` aracılığıyla `words[3]`içerir.</span><span class="sxs-lookup"><span data-stu-id="2036d-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="2036d-128">Öğe `words[4]` aralıkta değil.</span><span class="sxs-lookup"><span data-stu-id="2036d-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="2036d-129">Aynı yönteme aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2036d-129">Add the following code to the same method.</span></span> <span data-ttu-id="2036d-130">Etkileşimli pencerenin altına kopyalayıp yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2036d-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="2036d-131">Aşağıdaki kod "tembel" ve "köpek" ile bir alt aralığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2036d-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="2036d-132">Bu `words[^2]` içerir `words[^1]`ve .</span><span class="sxs-lookup"><span data-stu-id="2036d-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="2036d-133">Bitiş dizini `words[^0]` dahil değil.</span><span class="sxs-lookup"><span data-stu-id="2036d-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="2036d-134">Aşağıdaki kodu da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2036d-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="2036d-135">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık uçlu aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2036d-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="2036d-136">Aralıkları veya endeksleri değişken olarak da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2036d-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="2036d-137">Değişken daha sonra `[` ve `]` karakterler içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2036d-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="2036d-138">Aşağıdaki örnek, bu seçimlerin birçok nedeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="2036d-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="2036d-139">`x`Değiştirin `y`ve `z` farklı kombinasyonları denemek için.</span><span class="sxs-lookup"><span data-stu-id="2036d-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="2036d-140">Deneme yaptığınızda, geçerli `x` kombinasyonlardan `y`daha `y` az `z` ve daha az olan değerleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2036d-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="2036d-141">Yeni bir yöntemde aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2036d-141">Add the following code in a new method.</span></span> <span data-ttu-id="2036d-142">Farklı kombinasyonları deneyin:</span><span class="sxs-lookup"><span data-stu-id="2036d-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="2036d-143">Endeksler ve aralıklar için tip desteği</span><span class="sxs-lookup"><span data-stu-id="2036d-143">Type support for indices and ranges</span></span>

<span data-ttu-id="2036d-144">Dizinler ve aralıklar, tek bir öğeye veya bir dizideki öğelerin bir alt aralığına erişmek için net, kısa sözdizimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2036d-144">Indexes and ranges provide clear, concise syntax to access a single element or a subrange of elements in a sequence.</span></span> <span data-ttu-id="2036d-145">Dizin ifadesi genellikle bir dizinin öğelerinin türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="2036d-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="2036d-146">Aralık ifadesi genellikle kaynak sırası ile aynı sıra türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="2036d-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="2036d-147">Bir [dizin leyiciye](../programming-guide/indexers/index.md) bir <xref:System.Index> <xref:System.Range> veya parametre içeren herhangi bir tür, sırasıyla endeksleri veya aralıkları açıkça destekler.</span><span class="sxs-lookup"><span data-stu-id="2036d-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="2036d-148">Tek <xref:System.Range> bir parametre alan bir dizinleyici, <xref:System.Span%601?displayProperty=nameWithType>', .</span><span class="sxs-lookup"><span data-stu-id="2036d-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2036d-149">Bir tür, adı verilen `Length` bir özelliği `Count` varsa veya erişilebilir bir getter ve bir dönüş türü ne varsa `int` **sayılabilir.**</span><span class="sxs-lookup"><span data-stu-id="2036d-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="2036d-150">Endeksleri veya aralıkları açıkça desteklemeyen sayılabilir bir tür, bunlar için örtülü bir destek sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2036d-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="2036d-151">Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [Örtük Dizini desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [Örtük Aralık destek](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="2036d-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="2036d-152">Örtük aralık desteği kullanan aralıklar, kaynak sırası ile aynı sıra türünü döndürer.</span><span class="sxs-lookup"><span data-stu-id="2036d-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="2036d-153">Örneğin, aşağıdaki .NET türleri hem endeksleri hem <xref:System.String>de <xref:System.Span%601>aralıkları destekler: , ve <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="2036d-153">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="2036d-154">Endeksleri <xref:System.Collections.Generic.List%601> destekler, ancak aralıkları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2036d-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="2036d-155"><xref:System.Array>daha nüanslı bir davranış almıştır.</span><span class="sxs-lookup"><span data-stu-id="2036d-155"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="2036d-156">Tek boyutlu diziler hem endeksleri hem de aralıkları destekler.</span><span class="sxs-lookup"><span data-stu-id="2036d-156">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="2036d-157">Çok boyutlu diziler yapmaz.</span><span class="sxs-lookup"><span data-stu-id="2036d-157">Multi-dimensional arrays don't.</span></span> <span data-ttu-id="2036d-158">Çok boyutlu bir dizi için dizinleyici, tek bir parametre değil, birden çok parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="2036d-158">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="2036d-159">Bir dizi dizi dizi olarak da adlandırılan pürüzlü diziler, hem aralıkları hem de dizinleyicileri destekler.</span><span class="sxs-lookup"><span data-stu-id="2036d-159">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="2036d-160">Aşağıdaki örnek, pürüzlü bir dizinin dikdörtgen alt kısmını nasıl yinelergösterilir.</span><span class="sxs-lookup"><span data-stu-id="2036d-160">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="2036d-161">İlk ve son üç satır hariç, merkezdeki bölümü ve seçilen her satırdan ilk ve son iki sütunu yineler:</span><span class="sxs-lookup"><span data-stu-id="2036d-161">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="2036d-162">Endeksler ve aralıklar için senaryolar</span><span class="sxs-lookup"><span data-stu-id="2036d-162">Scenarios for indices and ranges</span></span>

<span data-ttu-id="2036d-163">Daha büyük bir dizinin bir alt aralığını çözümlemek istediğinizde genellikle aralıkları ve endeksleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2036d-163">You'll often use ranges and indices when you want to analyze a subrange of a larger sequence.</span></span> <span data-ttu-id="2036d-164">Yeni sözdizimi tam olarak hangi alt aralığın dahil olduğunu okumada daha açıktır.</span><span class="sxs-lookup"><span data-stu-id="2036d-164">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="2036d-165">Yerel işlev `MovingAverage` bir <xref:System.Range> bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2036d-165">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="2036d-166">Yöntem daha sonra min, max ve ortalama hesaplanırken sadece bu aralığı sıralar.</span><span class="sxs-lookup"><span data-stu-id="2036d-166">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="2036d-167">Projenizde aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="2036d-167">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
