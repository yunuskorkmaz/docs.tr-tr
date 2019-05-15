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
# <a name="indices-and-ranges"></a>Dizinleri ve aralıkları

Aralıkları ve dizinlerini sağlayan bir kısa sözdizimleri tek öğeleri veya aralıklardaki erişmek için bir <xref:System.Array>, <xref:System.Span%601>, veya <xref:System.ReadOnlySpan%601>. Bu özellikleri tek öğeleri veya dizideki öğeleri aralıklarına erişmek daha kısa ve NET sözdizimini sağlar.

Bu öğreticide şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Bir dizideki aralıkları için söz dizimi kullanın.
> * Başlangıç ve bitiş her dizisinin tasarım kararlarına anlayın.
> * Senaryolar için bilgi <xref:System.Index> ve <xref:System.Range> türleri.

## <a name="language-support-for-indices-and-ranges"></a>Dizinleri ve aralıkları için dil desteği

Bu dil desteği, iki yeni türler ve iki yeni işleç kullanır.
- <xref:System.Index?displayProperty=nameWithType> Dizin bir dizisi temsil eder.
- `^` İşleci bir dizin dizinin sonuna göreli olduğunu belirtir.
- <xref:System.Range?displayProperty=nameWithType> bir dizi alt aralığını temsil eder.
- Aralık işleci (`..`), belirten başlangıç ve bitiş aralığının işlenenleri.

Dizinler için kuralları başlayalım. Bir dizi göz önünde bulundurun `sequence`. `0` Dizin aynıdır `sequence[0]`. `^0` Dizin aynıdır `sequence[sequence.Length]`. Unutmayın `sequence[^0]` gibi bir özel durum `sequence[sequence.Length]` yapar. Herhangi bir sayı için `n`, dizin `^n` aynı `sequence[sequence.Length - n]`.

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

Son sözcüğü alabilirsiniz `^1` dizini. Başlatma altına aşağıdaki kodu ekleyin:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Bir aralığı belirtir *Başlat* ve *son* aralığının. Aralıkları özel anlamı *son* aralığında yer almaz. Aralığın `[0..^0]` gibi tüm aralığını temsil eden `[0..sequence.Length]` tüm aralığını temsil eder. 

Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur. İçerdiği `words[1]` aracılığıyla `words[3]`. Öğe `words[4]` aralığında değil. Aynı yönteme aşağıdaki kodu ekleyin. Kopyala ve etkileşimli pencerenin alt kısmında yapıştırın.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Aşağıdaki kod, "geç" ve "köpek" alt oluşturur. İçerdiği `words[^2]` ve `words[^1]`. Bitiş dizini `words[^0]` dahil değildir. De aşağıdaki kodu ekleyin:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Aralıkları veya dizinler değişkenleri olarak bildirebilirsiniz. Değişkeni içinde sonra kullanılabilir `[` ve `]` karakter:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Aşağıdaki örnek Bu seçeneklere nedenlerle çoğunu gösterir. Değiştirme `x`, `y`, ve `z` farklı birleşimlerini denemek için. Kullanımı, denemeler, nerede değerleri `x` olduğu küçüktür `y`, ve `y` olduğu küçüktür `z` geçerli birleşimleri için. İçinde yeni bir yöntem aşağıdaki kodu ekleyin. Farklı birleşimleri deneyin:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Dizinleri ve aralıkları için senaryolar

Tüm dizisi alt aralığı üzerinde bazı analiz gerçekleştirmek istediğiniz zaman aralıkları ve dizinlerini genellikle kullanacaksınız. Yeni sözdizimi, tam olarak hangi alt aralığı söz konusu okuma nettir. Yerel işlev `MovingAverage` götüren bir <xref:System.Range> bağımsız değişken olarak. Yöntemi daha sonra min, Maks ve ortalama hesaplarken yalnızca bu aralık numaralandırır. Projenize aşağıdaki kodu deneyin:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Tamamlanan kodu indirebileceğiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) depo.
