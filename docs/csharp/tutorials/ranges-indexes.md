---
title: Dizinler ve aralıklar kullanarak veri aralıklarını keşfet
description: Bu gelişmiş öğreticide, sıralı bir veri kümesinin dilimlerini incelemek üzere dizinler ve aralıklar kullanarak verileri araştırmanızı öğretilir.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 3d4c022ff8d6e7f260632e34d6f28277014c85c8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345626"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="e5785-103">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="e5785-103">Indices and ranges</span></span>

<span data-ttu-id="e5785-104">Aralıklar ve dizinler, bir dizideki tek öğe veya aralıklara erişmek için bir kısa sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5785-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="e5785-105">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="e5785-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e5785-106">Bir dizideki aralıklar için söz dizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5785-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="e5785-107">Her bir sıranın başlangıcı ve bitişi için tasarım kararlarını anlayın.</span><span class="sxs-lookup"><span data-stu-id="e5785-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="e5785-108"><xref:System.Index> ve <xref:System.Range> türleri için senaryolar öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e5785-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="e5785-109">Dizinler ve aralıklar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="e5785-109">Language support for indices and ranges</span></span>

<span data-ttu-id="e5785-110">Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:</span><span class="sxs-lookup"><span data-stu-id="e5785-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="e5785-111"><xref:System.Index?displayProperty=nameWithType> bir dizini bir diziye temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5785-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="e5785-112">Bitiş işlecinden Dizin `^`, bir dizinin bir dizinin sonuna göre olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5785-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="e5785-113"><xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5785-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="e5785-114">Aralık işleci, bir aralığın işlenenlerinin başlangıcını ve sonunu belirten `..`.</span><span class="sxs-lookup"><span data-stu-id="e5785-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="e5785-115">Dizin kurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="e5785-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="e5785-116">Dizi `sequence`değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="e5785-116">Consider an array `sequence`.</span></span> <span data-ttu-id="e5785-117">`0` Dizin `sequence[0]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e5785-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="e5785-118">`^0` Dizin `sequence[sequence.Length]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e5785-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="e5785-119">`sequence[^0]`, `sequence[sequence.Length]` olduğu gibi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5785-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="e5785-120">Herhangi bir sayı `n`için Dizin `^n` `sequence[sequence.Length - n]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e5785-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="e5785-121">Son kelimeyi `^1` diziniyle alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5785-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="e5785-122">Başlatmanın altına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5785-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="e5785-123">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5785-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="e5785-124">Aralıklar dışlamalı, yani *bitiş* aralığa dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="e5785-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="e5785-125">Aralık `[0..^0]`, tüm aralığı temsil eden `[0..sequence.Length]` aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5785-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="e5785-126">Aşağıdaki kod, "quick", "brown" ve "fox" sözcüklerinin bulunduğu bir alt aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5785-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="e5785-127">`words[1]` ile `words[3]` aralığını içerir.</span><span class="sxs-lookup"><span data-stu-id="e5785-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="e5785-128">Öğe `words[4]` Aralık içinde değil.</span><span class="sxs-lookup"><span data-stu-id="e5785-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="e5785-129">Aşağıdaki kodu aynı yönteme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e5785-129">Add the following code to the same method.</span></span> <span data-ttu-id="e5785-130">Etkileşimli pencerenin alt kısmına kopyalayıp yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5785-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="e5785-131">Aşağıdaki kod, "lazy" ve "dog" sözcüklerini içeren bir alt aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5785-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="e5785-132">`words[^2]` ile `words[^1]` aralığını içerir.</span><span class="sxs-lookup"><span data-stu-id="e5785-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="e5785-133">Son dizin `words[^0]` dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="e5785-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="e5785-134">Aşağıdaki kodu da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5785-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="e5785-135">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e5785-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="e5785-136">Ayrıca, aralıkları veya dizinleri değişken olarak da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5785-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="e5785-137">Değişken daha sonra `[` ve `]` karakterleri içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e5785-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="e5785-138">Aşağıdaki örnekte, bu seçimlerin pek çok nedeni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5785-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="e5785-139">Farklı birleşimler denemek için `x`, `y`ve `z` değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e5785-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="e5785-140">Denemeler yaparken, `x` `y`' den küçük olan değerleri kullanın ve `y` geçerli birleşimler için `z` küçüktür.</span><span class="sxs-lookup"><span data-stu-id="e5785-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="e5785-141">Aşağıdaki kodu yeni bir yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e5785-141">Add the following code in a new method.</span></span> <span data-ttu-id="e5785-142">Farklı birleşimler deneyin:</span><span class="sxs-lookup"><span data-stu-id="e5785-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="e5785-143">Dizinler ve aralıklar için tür desteği</span><span class="sxs-lookup"><span data-stu-id="e5785-143">Type support for indices and ranges</span></span>

<span data-ttu-id="e5785-144">Dizinler ve aralıklar, tek bir öğeye veya bir dizideki alt öğe aralığına erişmek için net, kısa sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5785-144">Indexes and ranges provide clear, concise syntax to access a single element or a sub-range of elements in a sequence.</span></span> <span data-ttu-id="e5785-145">Bir dizin ifadesi genellikle bir dizinin öğelerinin türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5785-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="e5785-146">Bir Aralık ifadesi genellikle kaynak dizisiyle aynı sıra türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5785-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="e5785-147">Bir tür bir <xref:System.Index> veya <xref:System.Range> parametresi olan bir [Dizin Oluşturucu](../programming-guide/indexers/index.md) sağlıyorsa, sırasıyla dizinleri veya aralıkları açıkça destekler.</span><span class="sxs-lookup"><span data-stu-id="e5785-147">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="e5785-148">Tür, tek bir <xref:System.Range> parametresi alan bir Dizin Oluşturucu sağlıyorsa, <xref:System.Span%601?displayProperty=nameWithType>gibi farklı bir dizi türü döndürmeyi tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="e5785-148">When the type provides an indexer that takes a single <xref:System.Range> parameter, it may choose to return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e5785-149">Bir tür, erişilebilir bir alıcı ve `int`dönüş türü `Length` veya `Count` adlı bir **özelliğe sahipse bir** tür oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e5785-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="e5785-150">Dizinleri veya aralıkları açıkça desteklemeyen bir sayılabilir türü, bunlar için örtülü bir destek sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e5785-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="e5785-151">Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [örtük Dizin desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [örtük Aralık desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e5785-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="e5785-152">Örtük Aralık desteği kullanan aralıklar, kaynak dizisiyle aynı sıra türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5785-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="e5785-153">Örneğin, aşağıdaki .NET türleri hem dizinleri hem de aralıkları destekler: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>ve <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="e5785-153">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="e5785-154"><xref:System.Collections.Generic.List%601> dizinleri destekler ancak aralıkları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e5785-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="e5785-155">Dizinler ve aralıklar için senaryolar</span><span class="sxs-lookup"><span data-stu-id="e5785-155">Scenarios for indices and ranges</span></span>

<span data-ttu-id="e5785-156">Genellikle tüm bir sıranın alt aralığında bazı analizler gerçekleştirmek istediğinizde aralıklar ve dizinler kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e5785-156">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="e5785-157">Yeni söz dizimi, tam olarak hangi alt aralığın ilgili olduğunu okumaktan daha net.</span><span class="sxs-lookup"><span data-stu-id="e5785-157">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="e5785-158">Yerel işlev `MovingAverage` bağımsız değişkeni olarak bir <xref:System.Range> alır.</span><span class="sxs-lookup"><span data-stu-id="e5785-158">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="e5785-159">Bu yöntem daha sonra Min, Max ve Average hesaplama yaparken yalnızca o aralığı numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e5785-159">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="e5785-160">Projenizde aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="e5785-160">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="e5785-161">Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5785-161">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
