---
title: Dizinler ve aralıklar kullanarak veri aralıklarını keşfet
description: Bu gelişmiş öğreticide, sıralı bir veri kümesinin dilimlerini incelemek üzere dizinler ve aralıklar kullanarak verileri araştırmanızı öğretilir.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: d53f32bcb310d4859cea67a742ac0e2c4be5d942
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105781"
---
# <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Aralıklar ve dizinler <xref:System.Array>, bir, <xref:System.Span%601>veya <xref:System.ReadOnlySpan%601>içinde tek öğe veya aralıklara erişmek için bir kısa söz dizimi sağlar. Bu özellikler, bir dizideki tek öğelere veya öğe aralıklarına erişmek için daha kısa, sözdizimini açık bir şekilde etkinleştirir.

Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
> - Bir dizideki aralıklar için söz dizimini kullanın.
> - Her bir sıranın başlangıcı ve bitişi için tasarım kararlarını anlayın.
> - <xref:System.Index> Ve<xref:System.Range> türleri için senaryolar öğrenin.

## <a name="language-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için dil desteği

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır.
- <xref:System.Index?displayProperty=nameWithType>bir dizinin dizisini temsil eder.
- Bir dizinin bir sıranın sonuna göreli olduğunu belirten işleç.`^`
- <xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.
- Aralık işleci (`..`), bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.

Dizin kurallarıyla başlayalım. Bir dizi `sequence`düşünün. Dizin, ile `sequence[0]`aynıdır. `0` Dizin, ile `sequence[sequence.Length]`aynıdır. `^0` `sequence[^0]` Bunun gibi`sequence[sequence.Length]` bir özel durum oluşturur. Herhangi bir sayı `n`için Dizin `^n` aynı `sequence[sequence.Length - n]`olur.

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

`^1` Dizinle son sözcüğü alabilirsiniz. Başlatmanın altına aşağıdaki kodu ekleyin:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralıklar dışlamalı, yani *bitiş* aralığa dahil değildir. Aralık, tüm aralığı temsil eden tüm `[0..sequence.Length]` aralığı temsileder.`[0..^0]` 

Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur. `words[1]` İle`words[3]`içerir. Öğe `words[4]` Aralık içinde değil. Aşağıdaki kodu aynı yönteme ekleyin. Etkileşimli pencerenin alt kısmına kopyalayıp yapıştırın.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur. `words[^2]` Ve`words[^1]`içerir. Son dizin `words[^0]` dahil değildir. Aşağıdaki kodu da ekleyin:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Ayrıca, aralıkları veya dizinleri değişken olarak da bildirebilirsiniz. Değişken daha sonra `[` ve `]` karakterleri içinde kullanılabilir:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Aşağıdaki örnekte, bu seçimlerin pek çok nedeni gösterilmektedir. Farklı birleşimler denemek için `z` , ve değiştirin `x`. `y` Denemeler `x` yaptığınızda, `y` 'den`y` küçük olan değerleri kullanın ve geçerli kombinasyonlardan daha küçüktür. `z` Aşağıdaki kodu yeni bir yöntemine ekleyin. Farklı birleşimler deneyin:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Dizinler ve aralıklar için senaryolar

Genellikle tüm bir sıranın alt aralığında bazı analizler gerçekleştirmek istediğinizde aralıklar ve dizinler kullanırsınız. Yeni söz dizimi, tam olarak hangi alt aralığın ilgili olduğunu okumaktan daha net. Yerel işlev `MovingAverage` , bağımsız değişkeni <xref:System.Range> olarak bir kullanır. Bu yöntem daha sonra Min, Max ve Average hesaplama yaparken yalnızca o aralığı numaralandırır. Projenizde aşağıdaki kodu deneyin:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) deposundan indirebilirsiniz.
