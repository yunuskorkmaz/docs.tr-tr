---
title: Dizinler ve aralıklar kullanarak veri aralıklarını keşfet
description: Bu gelişmiş öğreticide, sıralı bir veri kümesinin dilimlerini incelemek üzere dizinler ve aralıklar kullanarak verileri araştırmanızı öğretilir.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 5b6277763cfccfc75947f6fa0534964389b1dea3
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240047"
---
# <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Aralıklar ve dizinler, bir dizideki tek öğe veya aralıklara erişmek için bir kısa sözdizimi sağlar.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Bir dizideki aralıklar için söz dizimini kullanın.
> - Her bir sıranın başlangıcı ve bitişi için tasarım kararlarını anlayın.
> - <xref:System.Index> ve <xref:System.Range> türleri için senaryolar öğrenin.

## <a name="language-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için dil desteği

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:

- <xref:System.Index?displayProperty=nameWithType> bir dizini bir diziye temsil eder.
- Bitiş işlecinden Dizin `^`, bir dizinin bir dizinin sonuna göre olduğunu belirtir.
- <xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.
- Aralık işleci, bir aralığın işlenenlerinin başlangıcını ve sonunu belirten `..`.

Dizin kurallarıyla başlayalım. Dizi `sequence`değerlendirin. `0` Dizin `sequence[0]`ile aynıdır. `^0` Dizin `sequence[sequence.Length]`ile aynıdır. `sequence[^0]`, `sequence[sequence.Length]` olduğu gibi bir özel durum oluşturur. Herhangi bir sayı `n`için Dizin `^n` `sequence[sequence.Length - n]`ile aynıdır.

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

Son kelimeyi `^1` diziniyle alabilirsiniz. Başlatmanın altına aşağıdaki kodu ekleyin:

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralıklar dışlamalı, yani *bitiş* aralığa dahil değildir. Aralık `[0..^0]`, tüm aralığı temsil eden `[0..sequence.Length]` aralığını temsil eder. 

Aşağıdaki kod, "quick", "brown" ve "fox" sözcüklerinin bulunduğu bir alt aralık oluşturur. `words[3]`üzerinden `words[1]` içerir. Öğe `words[4]` Aralık içinde değil. Aşağıdaki kodu aynı yönteme ekleyin. Etkileşimli pencerenin alt kısmına kopyalayıp yapıştırın.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Aşağıdaki kod, "lazy" ve "dog" sözcüklerini içeren bir alt aralık oluşturur. `words[^2]` ve `words[^1]`içerir. Son dizin `words[^0]` dahil değildir. Aşağıdaki kodu da ekleyin:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Ayrıca, aralıkları veya dizinleri değişken olarak da bildirebilirsiniz. Değişken daha sonra `[` ve `]` karakterleri içinde kullanılabilir:

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Aşağıdaki örnekte, bu seçimlerin pek çok nedeni gösterilmektedir. Farklı birleşimler denemek için `x`, `y`ve `z` değiştirin. Denemeler yaparken, `x` `y`' den küçük olan değerleri kullanın ve `y` geçerli birleşimler için `z` küçüktür. Aşağıdaki kodu yeni bir yöntemine ekleyin. Farklı birleşimler deneyin:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için tür desteği

Dizinler ve aralıklar, tek bir öğeye veya bir dizideki alt öğe aralığına erişmek için net, kısa sözdizimi sağlar. Bir dizin ifadesi genellikle bir dizinin öğelerinin türünü döndürür. Bir Aralık ifadesi genellikle kaynak dizisiyle aynı sıra türünü döndürür.

Bir tür bir <xref:System.Index> veya <xref:System.Range> parametresi olan bir [Dizin Oluşturucu](../programming-guide/indexers/index.md) sağlıyorsa, sırasıyla dizinleri veya aralıkları açıkça destekler. Tür, tek bir <xref:System.Range> parametresi alan bir Dizin Oluşturucu sağlıyorsa, <xref:System.Span%601?displayProperty=nameWithType>gibi farklı bir dizi türü döndürmeyi tercih edebilir.

Bir tür, erişilebilir bir alıcı ve `int`dönüş türü `Length` veya `Count` adlı bir **özelliğe sahipse bir** tür oluşturulabilir. Dizinleri veya aralıkları açıkça desteklemeyen bir sayılabilir türü, bunlar için örtülü bir destek sağlayabilir. Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [örtük Dizin desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [örtük Aralık desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın. Örtük Aralık desteği kullanan aralıklar, kaynak dizisiyle aynı sıra türünü döndürür.

Örneğin, aşağıdaki .NET türleri hem dizinleri hem de aralıkları destekler: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>ve <xref:System.ReadOnlySpan%601>. <xref:System.Collections.Generic.List%601> dizinleri destekler ancak aralıkları desteklemez.

## <a name="scenarios-for-indices-and-ranges"></a>Dizinler ve aralıklar için senaryolar

Genellikle tüm bir sıranın alt aralığında bazı analizler gerçekleştirmek istediğinizde aralıklar ve dizinler kullanırsınız. Yeni söz dizimi, tam olarak hangi alt aralığın ilgili olduğunu okumaktan daha net. Yerel işlev `MovingAverage` bağımsız değişkeni olarak bir <xref:System.Range> alır. Bu yöntem daha sonra Min, Max ve Average hesaplama yaparken yalnızca o aralığı numaralandırır. Projenizde aşağıdaki kodu deneyin:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) deposundan indirebilirsiniz.
