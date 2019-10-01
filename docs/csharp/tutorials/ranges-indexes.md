---
title: Dizinler ve aralıklar kullanarak veri aralıklarını keşfet
description: Bu gelişmiş öğreticide, sıralı bir veri kümesinin dilimlerini incelemek üzere dizinler ve aralıklar kullanarak verileri araştırmanızı öğretilir.
ms.date: 09/20/2019
ms.custom: mvc
ms.openlocfilehash: 1be144560d2b20bafc66cd68de0735e6dc7f0124
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699932"
---
# <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Aralıklar ve dizinler, bir dizideki tek öğe veya aralıklara erişmek için bir kısa sözdizimi sağlar.

Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> - Bir dizideki aralıklar için söz dizimini kullanın.
> - Her bir sıranın başlangıcı ve bitişi için tasarım kararlarını anlayın.
> - @No__t-0 ve <xref:System.Range> türleri için senaryolar öğrenin.

## <a name="language-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için dil desteği

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:

- <xref:System.Index?displayProperty=nameWithType> bir dizinin bir dizinini temsil eder.
- Bir dizinin bir sıranın sonuna göreli olduğunu belirten-0 @no__t bitiş işlecinden dizin.
- <xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.
- Aralık işleci `..`, bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.

Dizin kurallarıyla başlayalım. Bir dizi @no__t düşünün-0. @No__t-0 dizini, `sequence[0]` ile aynıdır. @No__t-0 dizini, `sequence[sequence.Length]` ile aynıdır. @No__t-0 ' ın, `sequence[sequence.Length]` olduğu gibi bir özel durum oluşturmadığını unutmayın. @No__t-0 olan herhangi bir sayı için, `^n` dizini `sequence[sequence.Length - n]` ile aynıdır.

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

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralıklar dışlamalı, yani *bitiş* aralığa dahil değildir. @No__t-0 aralığı tüm aralığı temsil eder, tıpkı `[0..sequence.Length]` tüm aralığı temsil eder. 

Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur. @No__t-0 ile `words[3]` arasında içerir. @No__t-0 öğesi Aralık içinde değil. Aşağıdaki kodu aynı yönteme ekleyin. Etkileşimli pencerenin alt kısmına kopyalayıp yapıştırın.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur. @No__t-0 ve `words[^1]` ' i içerir. @No__t-0 bitiş dizini dahil değildir. Aşağıdaki kodu da ekleyin:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Ayrıca, aralıkları veya dizinleri değişken olarak da bildirebilirsiniz. Değişken daha sonra `[` ve `]` karakterleri içinde kullanılabilir:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Aşağıdaki örnekte, bu seçimlerin pek çok nedeni gösterilmektedir. Farklı birleşimler denemek için `x`, `y` ve `z` ' yi değiştirin. Denemeler yaparken `x` ' ı `y` ' den küçük olan değerleri kullanın ve geçerli birleşimler için `y` ' den az @no__t. Aşağıdaki kodu yeni bir yöntemine ekleyin. Farklı birleşimler deneyin:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için tür desteği

Bir tür, <xref:System.Index> veya <xref:System.Range> parametresiyle bir [Dizin Oluşturucu](../programming-guide/indexers/index.md) sağlıyorsa, sırasıyla dizinleri veya aralıkları açıkça destekler.

Bir tür, erişilebilir bir alıcı ve `int` dönüş türüyle `Length` veya `Count` adlı bir **özellik varsa oluşturulabilir** . Dizinleri veya aralıkları açıkça desteklemeyen bir sayılabilir türü, bunlar için örtülü bir destek sağlayabilir. Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [örtük Dizin desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [örtük Aralık desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın.

Örneğin, aşağıdaki .NET türleri hem dizinleri hem de aralıkları destekler: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601> ve <xref:System.ReadOnlySpan%601>. @No__t-0 dizinleri destekler ancak aralıkları desteklemez.

## <a name="scenarios-for-indices-and-ranges"></a>Dizinler ve aralıklar için senaryolar

Genellikle tüm bir sıranın alt aralığında bazı analizler gerçekleştirmek istediğinizde aralıklar ve dizinler kullanırsınız. Yeni söz dizimi, tam olarak hangi alt aralığın ilgili olduğunu okumaktan daha net. @No__t-0 yerel işlevi, bağımsız değişkeni olarak bir <xref:System.Range> alır. Bu yöntem daha sonra Min, Max ve Average hesaplama yaparken yalnızca o aralığı numaralandırır. Projenizde aşağıdaki kodu deneyin:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) deposundan indirebilirsiniz.
