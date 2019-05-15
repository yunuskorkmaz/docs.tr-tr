---
title: Dizinleri ve aralıkları kullanarak veri aralıklarını keşfedin
description: Gelişmiş Bu öğretici, bir sıralı veri kümesinin dilimlerini incelemek için dizinler ve aralıkları kullanarak verileri araştırmak için öğretir.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 118d3c9ccad98ec02195c2b5e26a2ca203990adf
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557181"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="2a906-103">Dizinleri ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="2a906-103">Indices and ranges</span></span>

<span data-ttu-id="2a906-104">Aralıkları ve dizinlerini sağlayan bir kısa sözdizimleri tek öğeleri veya aralıklardaki erişmek için bir <xref:System.Array>, <xref:System.Span%601>, veya <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="2a906-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="2a906-105">Bu özellikleri tek öğeleri veya dizideki öğeleri aralıklarına erişmek daha kısa ve NET sözdizimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a906-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="2a906-106">Bu öğreticide şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="2a906-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="2a906-107">Bir dizideki aralıkları için söz dizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a906-107">Use the syntax for ranges in a sequence.</span></span>
> * <span data-ttu-id="2a906-108">Başlangıç ve bitiş her dizisinin tasarım kararlarına anlayın.</span><span class="sxs-lookup"><span data-stu-id="2a906-108">Understand the design decisions for the start and end of each sequence.</span></span>
> * <span data-ttu-id="2a906-109">Senaryolar için bilgi <xref:System.Index> ve <xref:System.Range> türleri.</span><span class="sxs-lookup"><span data-stu-id="2a906-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="2a906-110">Dizinleri ve aralıkları için dil desteği</span><span class="sxs-lookup"><span data-stu-id="2a906-110">Language support for indices and ranges</span></span>

<span data-ttu-id="2a906-111">Bu dil desteği, iki yeni türler ve iki yeni işleç kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a906-111">This language support relies on two new types and two new operators.</span></span>
- <span data-ttu-id="2a906-112"><xref:System.Index?displayProperty=nameWithType> Dizin bir dizisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a906-112"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="2a906-113">`^` İşleci bir dizin dizinin sonuna göreli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a906-113">The `^` operator, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="2a906-114"><xref:System.Range?displayProperty=nameWithType> bir dizi alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a906-114"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="2a906-115">Aralık işleci (`..`), belirten başlangıç ve bitiş aralığının işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="2a906-115">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="2a906-116">Dizinler için kuralları başlayalım.</span><span class="sxs-lookup"><span data-stu-id="2a906-116">Let's start with the rules for indices.</span></span> <span data-ttu-id="2a906-117">Bir dizi göz önünde bulundurun `sequence`.</span><span class="sxs-lookup"><span data-stu-id="2a906-117">Consider an array `sequence`.</span></span> <span data-ttu-id="2a906-118">`0` Dizin aynıdır `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="2a906-118">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="2a906-119">`^0` Dizin aynıdır `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="2a906-119">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="2a906-120">Unutmayın `sequence[^0]` gibi bir özel durum `sequence[sequence.Length]` yapar.</span><span class="sxs-lookup"><span data-stu-id="2a906-120">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="2a906-121">Herhangi bir sayı için `n`, dizin `^n` aynı `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="2a906-121">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp-interactive
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

<span data-ttu-id="2a906-122">Son sözcüğü alabilirsiniz `^1` dizini.</span><span class="sxs-lookup"><span data-stu-id="2a906-122">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="2a906-123">Başlatma altına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a906-123">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="2a906-124">Bir aralığı belirtir *Başlat* ve *son* aralığının.</span><span class="sxs-lookup"><span data-stu-id="2a906-124">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="2a906-125">Aralıkları özel anlamı *son* aralığında yer almaz.</span><span class="sxs-lookup"><span data-stu-id="2a906-125">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="2a906-126">Aralığın `[0..^0]` gibi tüm aralığını temsil eden `[0..sequence.Length]` tüm aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a906-126">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="2a906-127">Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a906-127">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="2a906-128">İçerdiği `words[1]` aracılığıyla `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="2a906-128">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="2a906-129">Öğe `words[4]` aralığında değil.</span><span class="sxs-lookup"><span data-stu-id="2a906-129">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="2a906-130">Aynı yönteme aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a906-130">Add the following code to the same method.</span></span> <span data-ttu-id="2a906-131">Kopyala ve etkileşimli pencerenin alt kısmında yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2a906-131">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="2a906-132">Aşağıdaki kod, "geç" ve "köpek" alt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a906-132">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="2a906-133">İçerdiği `words[^2]` ve `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="2a906-133">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="2a906-134">Bitiş dizini `words[^0]` dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="2a906-134">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="2a906-135">De aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a906-135">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="2a906-136">Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2a906-136">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="2a906-137">Aralıkları veya dizinler değişkenleri olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a906-137">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="2a906-138">Değişkeni içinde sonra kullanılabilir `[` ve `]` karakter:</span><span class="sxs-lookup"><span data-stu-id="2a906-138">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="2a906-139">Aşağıdaki örnek Bu seçeneklere nedenlerle çoğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a906-139">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="2a906-140">Değiştirme `x`, `y`, ve `z` farklı birleşimlerini denemek için.</span><span class="sxs-lookup"><span data-stu-id="2a906-140">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="2a906-141">Kullanımı, denemeler, nerede değerleri `x` olduğu küçüktür `y`, ve `y` olduğu küçüktür `z` geçerli birleşimleri için.</span><span class="sxs-lookup"><span data-stu-id="2a906-141">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="2a906-142">İçinde yeni bir yöntem aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a906-142">Add the following code in a new method.</span></span> <span data-ttu-id="2a906-143">Farklı birleşimleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="2a906-143">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="2a906-144">Dizinleri ve aralıkları için senaryolar</span><span class="sxs-lookup"><span data-stu-id="2a906-144">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="2a906-145">Tüm dizisi alt aralığı üzerinde bazı analiz gerçekleştirmek istediğiniz zaman aralıkları ve dizinlerini genellikle kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2a906-145">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="2a906-146">Yeni sözdizimi, tam olarak hangi alt aralığı söz konusu okuma nettir.</span><span class="sxs-lookup"><span data-stu-id="2a906-146">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="2a906-147">Yerel işlev `MovingAverage` götüren bir <xref:System.Range> bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="2a906-147">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="2a906-148">Yöntemi daha sonra min, Maks ve ortalama hesaplarken yalnızca bu aralık numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2a906-148">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="2a906-149">Projenize aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="2a906-149">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="2a906-150">Tamamlanan kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) depo.</span><span class="sxs-lookup"><span data-stu-id="2a906-150">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
