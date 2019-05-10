---
title: Dizinleri ve aralıkları kullanarak veri aralıklarını keşfedin
description: Gelişmiş Bu öğretici, bir sıralı veri kümesinin dilimlerini incelemek için dizinler ve aralıkları kullanarak verileri araştırmak için öğretir.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 64fae4581e265d4f70b8356d5c651b4fdaca3fe9
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2019
ms.locfileid: "64431495"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="8ca42-103">Dizinleri ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="8ca42-103">Indices and ranges</span></span>

<span data-ttu-id="8ca42-104">Aralıkları ve dizinlerini sağlayan bir kısa sözdizimleri tek öğeleri veya aralıklardaki erişmek için bir <xref:System.Array>, <xref:System.Span%601>, veya <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="8ca42-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="8ca42-105">Bu özellikleri tek öğeleri veya dizideki öğeleri aralıklarına erişmek daha kısa ve NET sözdizimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ca42-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="8ca42-106">Bu öğreticide şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="8ca42-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8ca42-107">Bir dizideki aralıkları için söz dizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ca42-107">Use the syntax for ranges in a sequence.</span></span>
> * <span data-ttu-id="8ca42-108">Başlangıç ve bitiş her dizisinin tasarım kararlarına anlayın.</span><span class="sxs-lookup"><span data-stu-id="8ca42-108">Understand the design decisions for the start and end of each sequence.</span></span>
> * <span data-ttu-id="8ca42-109">Senaryolar için bilgi <xref:System.Index> ve <xref:System.Range> türleri.</span><span class="sxs-lookup"><span data-stu-id="8ca42-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="8ca42-110">Dizinleri ve aralıkları için dil desteği</span><span class="sxs-lookup"><span data-stu-id="8ca42-110">Language support for indices and ranges</span></span>

<span data-ttu-id="8ca42-111">Dizin belirtebilirsiniz **sonundan** kullanarak `^` dizini önce karakter.</span><span class="sxs-lookup"><span data-stu-id="8ca42-111">You can specify an index **from the end** using the `^` character before the index.</span></span> <span data-ttu-id="8ca42-112">Sondan dizin kuraldan başlatır, `0..^0` tüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-112">Indexing from the end starts from the rule that `0..^0` specifies the entire range.</span></span> <span data-ttu-id="8ca42-113">Tüm dizi numaralandırmak için başlangıç *ilk öğede*ve, olana kadar devam *son öğeden önceki*.</span><span class="sxs-lookup"><span data-stu-id="8ca42-113">To enumerate an entire array, you start *at the first element*, and continue until you are *past the last element*.</span></span> <span data-ttu-id="8ca42-114">Davranışını düşünün `MoveNext` bir numaralandırıcı metodunda: numaralandırma son öğeyi başarılı olduğunda false döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ca42-114">Think of the behavior of the `MoveNext` method on an enumerator: it returns false when the enumeration passes the last element.</span></span> <span data-ttu-id="8ca42-115">Dizin `^0` "Bitiş" anlamına gelir `array[array.Length]`, ya da son öğeyi izleyen dizin.</span><span class="sxs-lookup"><span data-stu-id="8ca42-115">The index `^0` means "the end", `array[array.Length]`, or the index that follows the last element.</span></span> <span data-ttu-id="8ca42-116">Bilginiz `array[2]` öğe "başından itibaren 2" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-116">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="8ca42-117">Şimdi, `array[^2]` öğe "2 sonundan" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-117">Now, `array[^2]` means the element "2 from the end".</span></span> 

<span data-ttu-id="8ca42-118">Belirtebileceğiniz bir **aralığı** ile **aralık işleci**: `..`.</span><span class="sxs-lookup"><span data-stu-id="8ca42-118">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="8ca42-119">Örneğin, `0..^0` dizi aralığının tamamı belirtir: 0'ın başından itibaren en fazla, ancak son 0 dahil değil.</span><span class="sxs-lookup"><span data-stu-id="8ca42-119">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="8ca42-120">İki işlenenden "Başlangıç" veya "sonuna" kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-120">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="8ca42-121">Ayrıca, iki işlenenden atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-121">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="8ca42-122">Varsayılanlar `0` başlangıç dizini ve `^0` son dizini.</span><span class="sxs-lookup"><span data-stu-id="8ca42-122">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

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

<span data-ttu-id="8ca42-123">Her öğenin dizini "Başlat" ve "Kimden"son kavramı güçlendirir ve aralığın sonunu fiyatlara aralıktır.</span><span class="sxs-lookup"><span data-stu-id="8ca42-123">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="8ca42-124">"Başlangıç" tüm dizinin ilk öğedir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-124">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="8ca42-125">Tüm dizi "End" *geçmiş* son öğe.</span><span class="sxs-lookup"><span data-stu-id="8ca42-125">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="8ca42-126">Son sözcüğü alabilirsiniz `^1` dizini.</span><span class="sxs-lookup"><span data-stu-id="8ca42-126">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="8ca42-127">Başlatma altına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8ca42-127">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="8ca42-128">Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ca42-128">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="8ca42-129">İçerdiği `words[1]` aracılığıyla `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="8ca42-129">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="8ca42-130">Öğe `words[4]` aralığında değil.</span><span class="sxs-lookup"><span data-stu-id="8ca42-130">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="8ca42-131">Aynı yönteme aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8ca42-131">Add the following code to the same method.</span></span> <span data-ttu-id="8ca42-132">Kopyala ve etkileşimli pencerenin alt kısmında yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="8ca42-132">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="8ca42-133">Aşağıdaki kod, "geç" ve "köpek" alt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ca42-133">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="8ca42-134">İçerdiği `words[^2]` ve `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="8ca42-134">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="8ca42-135">Bitiş dizini `words[^0]` dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-135">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="8ca42-136">De aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8ca42-136">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="8ca42-137">Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8ca42-137">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="8ca42-138">Aralıkları veya dizinler değişkenleri olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca42-138">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="8ca42-139">Değişkeni içinde sonra kullanılabilir `[` ve `]` karakter:</span><span class="sxs-lookup"><span data-stu-id="8ca42-139">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="8ca42-140">Önceki örneklerde, daha fazla açıklama gerektiren iki tasarım kararları göster:</span><span class="sxs-lookup"><span data-stu-id="8ca42-140">The previous examples show two design decisions that require more explanation:</span></span>

- <span data-ttu-id="8ca42-141">Aralıkları *özel*, yani son dizinindeki öğeyi aralığında değil.</span><span class="sxs-lookup"><span data-stu-id="8ca42-141">Ranges are *exclusive*, meaning the element at the last index isn't in the range.</span></span>
- <span data-ttu-id="8ca42-142">Dizin `^0` olduğu *son* koleksiyonun değil *son öğeyi* koleksiyondaki.</span><span class="sxs-lookup"><span data-stu-id="8ca42-142">The index `^0` is *the end* of the collection, not *the last element* in the collection.</span></span>

<span data-ttu-id="8ca42-143">Aşağıdaki örnek Bu seçeneklere nedenlerle çoğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-143">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="8ca42-144">Değiştirme `x`, `y`, ve `z` farklı birleşimlerini denemek için.</span><span class="sxs-lookup"><span data-stu-id="8ca42-144">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="8ca42-145">Kullanımı, denemeler, nerede değerleri `x` olduğu küçüktür `y`, ve `y` olduğu küçüktür `z` geçerli birleşimleri için.</span><span class="sxs-lookup"><span data-stu-id="8ca42-145">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="8ca42-146">İçinde yeni bir yöntem aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8ca42-146">Add the following code in a new method.</span></span> <span data-ttu-id="8ca42-147">Farklı birleşimleri deneyin:</span><span class="sxs-lookup"><span data-stu-id="8ca42-147">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="8ca42-148">Dizinleri ve aralıkları için senaryolar</span><span class="sxs-lookup"><span data-stu-id="8ca42-148">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="8ca42-149">Tüm dizisi alt aralığı üzerinde bazı analiz gerçekleştirmek istediğiniz zaman aralıkları ve dizinlerini genellikle kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8ca42-149">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="8ca42-150">Yeni sözdizimi, tam olarak hangi alt aralığı söz konusu okuma nettir.</span><span class="sxs-lookup"><span data-stu-id="8ca42-150">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="8ca42-151">Yerel işlev `MovingAverage` götüren bir <xref:System.Range> bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="8ca42-151">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="8ca42-152">Yöntemi daha sonra min, Maks ve ortalama hesaplarken yalnızca bu aralık numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8ca42-152">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="8ca42-153">Projenize aşağıdaki kodu deneyin:</span><span class="sxs-lookup"><span data-stu-id="8ca42-153">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="8ca42-154">Tamamlanan kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) depo.</span><span class="sxs-lookup"><span data-stu-id="8ca42-154">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
