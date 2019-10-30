---
title: Dizinler ve aralıklar kullanarak veri aralıklarını keşfet
description: Bu gelişmiş öğreticide, sıralı bir veri kümesinin dilimlerini incelemek üzere dizinler ve aralıklar kullanarak verileri araştırmanızı öğretilir.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: bbf3f257db9079c4f69f25c9ea08e7711b5ea04b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039669"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="1487d-103">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="1487d-103">Indices and ranges</span></span>

<span data-ttu-id="1487d-104">Aralıklar ve dizinler, bir dizideki tek öğe veya aralıklara erişmek için bir kısa sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1487d-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="1487d-105">Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1487d-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1487d-106">Bir dizideki aralıklar için söz dizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1487d-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="1487d-107">Her bir sıranın başlangıcı ve bitişi için tasarım kararlarını anlayın.</span><span class="sxs-lookup"><span data-stu-id="1487d-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="1487d-108"><xref:System.Index> ve <xref:System.Range> türleri için senaryolar öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1487d-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="1487d-109">Dizinler ve aralıklar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="1487d-109">Language support for indices and ranges</span></span>

<span data-ttu-id="1487d-110">Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:</span><span class="sxs-lookup"><span data-stu-id="1487d-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="1487d-111"><xref:System.Index?displayProperty=nameWithType> bir dizinin bir dizinini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1487d-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="1487d-112">Bitiş işlecinden Dizin `^`, bir dizinin bir dizinin sonuna göre olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1487d-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="1487d-113"><xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1487d-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="1487d-114">Aralık işleci `..`, bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1487d-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="1487d-115">Dizin kurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1487d-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="1487d-116">Dizi `sequence` değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="1487d-116">Consider an array `sequence`.</span></span> <span data-ttu-id="1487d-117">`0` Dizin `sequence[0]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1487d-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="1487d-118">`^0` Dizin `sequence[sequence.Length]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1487d-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="1487d-119">`sequence[^0]`, `sequence[sequence.Length]` olduğu gibi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1487d-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="1487d-120">Herhangi bir sayı `n`için Dizin `^n` `sequence[sequence.Length - n]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1487d-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="1487d-121">Son kelimeyi `^1` diziniyle alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1487d-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="1487d-122">Başlatmanın altına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1487d-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="1487d-123">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="1487d-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="1487d-124">Aralıklar dışlamalı, yani *bitiş* aralığa dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="1487d-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="1487d-125">Aralık `[0..^0]`, tüm aralığı temsil eden `[0..sequence.Length]` aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1487d-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="1487d-126">Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1487d-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="1487d-127">`words[3]`üzerinden `words[1]` içerir.</span><span class="sxs-lookup"><span data-stu-id="1487d-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="1487d-128">Öğe `words[4]` Aralık içinde değil.</span><span class="sxs-lookup"><span data-stu-id="1487d-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="1487d-129">Aşağıdaki kodu aynı yönteme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1487d-129">Add the following code to the same method.</span></span> <span data-ttu-id="1487d-130">Etkileşimli pencerenin alt kısmına kopyalayıp yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="1487d-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="1487d-131">Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1487d-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="1487d-132">`words[^2]` ve `words[^1]`içerir.</span><span class="sxs-lookup"><span data-stu-id="1487d-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="1487d-133">Son dizin `words[^0]` dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="1487d-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="1487d-134">Aşağıdaki kodu da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1487d-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="1487d-135">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1487d-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="1487d-136">Ayrıca, aralıkları veya dizinleri değişken olarak da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1487d-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="1487d-137">Değişken daha sonra `[` ve `]` karakterleri içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1487d-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="1487d-138">Aşağıdaki örnekte, bu seçimlerin pek çok nedeni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1487d-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="1487d-139">Farklı birleşimler denemek için `x`, `y`ve `z` değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1487d-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="1487d-140">Denemeler yaparken, `x` `y`' den küçük olan değerleri kullanın ve `y` geçerli birleşimler için `z` küçüktür.</span><span class="sxs-lookup"><span data-stu-id="1487d-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="1487d-141">Aşağıdaki kodu yeni bir yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1487d-141">Add the following code in a new method.</span></span> <span data-ttu-id="1487d-142">Farklı birleşimler deneyin:</span><span class="sxs-lookup"><span data-stu-id="1487d-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="1487d-143">Dizinler ve aralıklar için tür desteği</span><span class="sxs-lookup"><span data-stu-id="1487d-143">Type support for indices and ranges</span></span>

<span data-ttu-id="1487d-144">Bir tür bir <xref:System.Index> veya <xref:System.Range> parametresi olan bir [Dizin Oluşturucu](../programming-guide/indexers/index.md) sağlıyorsa, sırasıyla dizinleri veya aralıkları açıkça destekler.</span><span class="sxs-lookup"><span data-stu-id="1487d-144">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span>

<span data-ttu-id="1487d-145">Bir tür, erişilebilir bir alıcı ve `int`dönüş türü `Length` veya `Count` adlı bir **özelliğe sahipse bir** tür oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1487d-145">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="1487d-146">Dizinleri veya aralıkları açıkça desteklemeyen bir sayılabilir türü, bunlar için örtülü bir destek sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1487d-146">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="1487d-147">Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [örtük Dizin desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [örtük Aralık desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1487d-147">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

<span data-ttu-id="1487d-148">Örneğin, aşağıdaki .NET türleri hem dizinleri hem de aralıkları destekler: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>ve <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="1487d-148">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="1487d-149"><xref:System.Collections.Generic.List%601> dizinleri destekler ancak aralıkları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1487d-149">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="1487d-150">Dizinler ve aralıklar için senaryolar</span><span class="sxs-lookup"><span data-stu-id="1487d-150">Scenarios for indices and ranges</span></span>

<span data-ttu-id="1487d-151">Genellikle tüm bir sıranın alt aralığında bazı analizler gerçekleştirmek istediğinizde aralıklar ve dizinler kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1487d-151">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="1487d-152">Yeni söz dizimi, tam olarak hangi alt aralığın ilgili olduğunu okumaktan daha net.</span><span class="sxs-lookup"><span data-stu-id="1487d-152">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="1487d-153">Yerel işlev `MovingAverage` bağımsız değişkeni olarak bir <xref:System.Range> alır.</span><span class="sxs-lookup"><span data-stu-id="1487d-153">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="1487d-154">Bu yöntem daha sonra Min, Max ve Average hesaplama yaparken yalnızca o aralığı numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1487d-154">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="1487d-155">Projenizde aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="1487d-155">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="1487d-156">Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1487d-156">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
