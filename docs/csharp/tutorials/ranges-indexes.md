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
# <a name="indices-and-ranges"></a>Endeksler ve aralıklar

Aralıklar ve endeksler, bir dizideki tek öğelere veya aralıklara erişmek için kısa bir sözdizimi sağlar.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Aralıklar için sıralı sözdizimini kullanın.
> - Her dizinin başlangıç ve bitişi için tasarım kararlarını anlayın.
> - Senaryoları <xref:System.Index> ve <xref:System.Range> türleri öğrenin.

## <a name="language-support-for-indices-and-ranges"></a>Endeksler ve aralıklar için dil desteği

Bu dil desteği iki yeni türe ve iki yeni işleçe dayanır:

- <xref:System.Index?displayProperty=nameWithType>diziye bir dizi içine bir dizi temsil eder.
- Bir dizinin dizinin `^`sonuna göreolduğunu belirten son işleçten gelen dizin.
- <xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.
- Aralık işleci, `..`bir aralığın başlangıcını ve sonunu operands olarak belirtir.

Endekskurallarıyla başlayalım. Bir dizi `sequence`düşünün. Dizin `0` `sequence[0]`aynıdır. Dizin `^0` `sequence[sequence.Length]`aynıdır. İfade, `sequence[^0]` tıpkı olduğu gibi `sequence[sequence.Length]` bir özel durum oluşturur. Herhangi bir `n`sayı `^n` için dizin `sequence[sequence.Length - n]`.

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

`^1` Dizinle son sözcüğü alabilirsiniz. Başlatmanın altına aşağıdaki kodu ekleyin:

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralıklar özeldir, yani *sonu* aralıkta dahil değildir. Aralık, `[0..^0]` tüm aralığı `[0..sequence.Length]` temsil eder gibi tüm aralığı temsil eder.

Aşağıdaki kod ,"hızlı", "kahverengi" ve "tilki" sözcükleri içeren bir alt aralık oluşturur. Bu `words[1]` aracılığıyla `words[3]`içerir. Öğe `words[4]` aralıkta değil. Aynı yönteme aşağıdaki kodu ekleyin. Etkileşimli pencerenin altına kopyalayıp yapıştırın.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Aşağıdaki kod "tembel" ve "köpek" ile bir alt aralığı oluşturur. Bu `words[^2]` içerir `words[^1]`ve . Bitiş dizini `words[^0]` dahil değil. Aşağıdaki kodu da ekleyin:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık uçlu aralıklar oluşturur:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Aralıkları veya endeksleri değişken olarak da bildirebilirsiniz. Değişken daha sonra `[` ve `]` karakterler içinde kullanılabilir:

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Aşağıdaki örnek, bu seçimlerin birçok nedeni gösterir. `x`Değiştirin `y`ve `z` farklı kombinasyonları denemek için. Deneme yaptığınızda, geçerli `x` kombinasyonlardan `y`daha `y` az `z` ve daha az olan değerleri kullanın. Yeni bir yöntemde aşağıdaki kodu ekleyin. Farklı kombinasyonları deneyin:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Endeksler ve aralıklar için tip desteği

Dizinler ve aralıklar, tek bir öğeye veya bir dizideki öğelerin bir alt aralığına erişmek için net, kısa sözdizimini sağlar. Dizin ifadesi genellikle bir dizinin öğelerinin türünü döndürür. Aralık ifadesi genellikle kaynak sırası ile aynı sıra türünü döndürür.

Bir [dizin leyiciye](../programming-guide/indexers/index.md) bir <xref:System.Index> <xref:System.Range> veya parametre içeren herhangi bir tür, sırasıyla endeksleri veya aralıkları açıkça destekler. Tek <xref:System.Range> bir parametre alan bir dizinleyici, <xref:System.Span%601?displayProperty=nameWithType>', .

Bir tür, adı verilen `Length` bir özelliği `Count` varsa veya erişilebilir bir getter ve bir dönüş türü ne varsa `int` **sayılabilir.** Endeksleri veya aralıkları açıkça desteklemeyen sayılabilir bir tür, bunlar için örtülü bir destek sağlayabilir. Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [Örtük Dizini desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [Örtük Aralık destek](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın. Örtük aralık desteği kullanan aralıklar, kaynak sırası ile aynı sıra türünü döndürer.

Örneğin, aşağıdaki .NET türleri hem endeksleri hem <xref:System.String>de <xref:System.Span%601>aralıkları destekler: , ve <xref:System.ReadOnlySpan%601>. Endeksleri <xref:System.Collections.Generic.List%601> destekler, ancak aralıkları desteklemez.

<xref:System.Array>daha nüanslı bir davranış almıştır. Tek boyutlu diziler hem endeksleri hem de aralıkları destekler. Çok boyutlu diziler yapmaz. Çok boyutlu bir dizi için dizinleyici, tek bir parametre değil, birden çok parametre vardır. Bir dizi dizi dizi olarak da adlandırılan pürüzlü diziler, hem aralıkları hem de dizinleyicileri destekler. Aşağıdaki örnek, pürüzlü bir dizinin dikdörtgen alt kısmını nasıl yinelergösterilir. İlk ve son üç satır hariç, merkezdeki bölümü ve seçilen her satırdan ilk ve son iki sütunu yineler:

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a>Endeksler ve aralıklar için senaryolar

Daha büyük bir dizinin bir alt aralığını çözümlemek istediğinizde genellikle aralıkları ve endeksleri kullanırsınız. Yeni sözdizimi tam olarak hangi alt aralığın dahil olduğunu okumada daha açıktır. Yerel işlev `MovingAverage` bir <xref:System.Range> bağımsız değişken olarak alır. Yöntem daha sonra min, max ve ortalama hesaplanırken sadece bu aralığı sıralar. Projenizde aşağıdaki kodu deneyin:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
