---
title: Dizinler ve aralıklar kullanarak veri aralıklarını keşfet
description: Bu gelişmiş öğreticide, sıralı veri kümesinin sürekli bir aralığını incelemek üzere dizinler ve aralıklar kullanarak verileri araştırmanızı öğretilir.
ms.date: 09/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: cf6c83484332ed517b2326b3fd9d7458f191227e
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738872"
---
# <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Aralıklar ve dizinler, bir dizideki tek öğe veya aralıklara erişmek için bir kısa sözdizimi sağlar.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - Bir dizideki aralıklar için söz dizimini kullanın.
> - Her bir sıranın başlangıcı ve bitişi için tasarım kararlarını anlayın.
> - Ve türleri için senaryolar <xref:System.Index> öğrenin <xref:System.Range> .

## <a name="language-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için dil desteği

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:

- <xref:System.Index?displayProperty=nameWithType> bir dizinin dizisini temsil eder.
- `^`Bir dizinin bir sıranın sonuna göreli olduğunu belirten bitiş işlecinden dizin.
- <xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.
- `..`Aralık işleci, bir aralığın işlenenlerinin başlangıcını ve sonunu belirtir.

Dizin kurallarıyla başlayalım. Bir dizi düşünün `sequence` . `0`Dizin, ile aynıdır `sequence[0]` . `^0`Dizin, ile aynıdır `sequence[sequence.Length]` . İfadesi olduğu `sequence[^0]` gibi bir özel durum oluşturur `sequence[sequence.Length]` . Herhangi bir sayı için `n` Dizin `^n` aynı olur `sequence[sequence.Length - n]` .

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

Dizinle son sözcüğü alabilirsiniz `^1` . Başlatmanın altına aşağıdaki kodu ekleyin:

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralıklar dışlamalı, yani *bitiş* aralığa dahil değildir. Aralık, tüm aralığı temsil eden `[0..^0]` tüm aralığı temsil eder `[0..sequence.Length]` .

Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur. İle içerir `words[1]` `words[3]` . Öğe `words[4]` Aralık içinde değil. Aşağıdaki kodu aynı yönteme ekleyin. Etkileşimli pencerenin alt kısmına kopyalayıp yapıştırın.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Aşağıdaki kod, "Lazy" ve "köpek" ile aralığı döndürür. Ve içerir `words[^2]` `words[^1]` . Son dizin `words[^0]` dahil değildir. Aşağıdaki kodu da ekleyin:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Ayrıca, aralıkları veya dizinleri değişken olarak da bildirebilirsiniz. Değişken daha sonra `[` ve karakterleri içinde kullanılabilir `]` :

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Aşağıdaki örnekte, bu seçimlerin pek çok nedeni gösterilmektedir. `x` `y` `z` Farklı birleşimler denemek için, ve değiştirin. Denemeler yaptığınızda, `x` ' den küçük olan değerleri kullanın `y` ve `y` `z` geçerli kombinasyonlardan daha küçüktür. Aşağıdaki kodu yeni bir yöntemine ekleyin. Farklı birleşimler deneyin:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Dizinler ve aralıklar için tür desteği

Dizinler ve aralıklar, tek bir öğeye veya dizideki bir dizi öğeye erişmek için net, kısa sözdizimi sağlar. Bir dizin ifadesi genellikle bir dizinin öğelerinin türünü döndürür. Bir Aralık ifadesi genellikle kaynak dizisiyle aynı sıra türünü döndürür.

Or parametresi olan bir [Dizin Oluşturucu](../programming-guide/indexers/index.md) sağlayan herhangi bir tür, <xref:System.Index> <xref:System.Range> sırasıyla dizin veya aralıkları açıkça destekler. Tek bir parametre alan bir Dizin Oluşturucu <xref:System.Range> , gibi farklı bir dizi türü döndürebilir <xref:System.Span%601?displayProperty=nameWithType> .

> [!IMPORTANT]
> Aralık işleci kullanılarak kodun performansı, dizi işleneninin türüne bağlıdır.
>
> Aralık işlecinin zaman karmaşıklığı, dizi türüne bağlıdır. Örneğin, dizi bir `string` veya bir diziyse, sonuç girişin belirtilen bölümünün bir kopyasıdır, bu nedenle zaman karmaşıklığı O kadar ( *n)* olur (burada n aralığın uzunluğudur). Diğer taraftan, bir veya ise, <xref:System.Span%601?displayProperty=nameWithType> <xref:System.Memory%601?displayProperty=nameWithType> sonuç aynı yedekleme deposuna başvurur. Bu, kopya olmadığı ve işlemin *O (1)* olduğu anlamına gelir.
>
> Zaman karmaşıklığına ek olarak, bu, ek ayırmaya ve kopyalara neden olur ve performansı etkiler. Performans duyarlı kodda, `Span<T>` `Memory<T>` Aralık operatörü kendileri için ayrılmadığından, dizi türü olarak veya kullanmayı düşünün.

Bir **tür,** erişilebilir bir `Length` alıcı veya bir `Count` dönüş türü olan veya adında bir özelliğe sahipse bir tür `int` . Dizinleri veya aralıkları açıkça desteklemeyen bir sayılabilir türü, bunlar için örtülü bir destek sağlayabilir. Daha fazla bilgi için, [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/ranges.md) [örtük Dizin desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) ve [örtük Aralık desteği](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) bölümlerine bakın. Örtük Aralık desteği kullanan aralıklar, kaynak dizisiyle aynı sıra türünü döndürür.

Örneğin, aşağıdaki .NET türleri hem dizinleri hem de aralıkları destekler: <xref:System.String> , <xref:System.Span%601> ve <xref:System.ReadOnlySpan%601> . <xref:System.Collections.Generic.List%601>Dizinleri destekler ancak aralıkları desteklemez.

<xref:System.Array> daha fazla anormal davranışa sahiptir. Tek boyutlu diziler hem dizinleri hem de aralıkları destekler. Çok boyutlu diziler değildir. Çok boyutlu bir dizinin dizin oluşturucusunun tek bir parametre değil birden çok parametresi vardır. Dizi dizileri olarak da adlandırılan pürüzlü Diziler, hem aralıkları hem de dizin oluşturucuyu destekler. Aşağıdaki örnek, pürüzlü bir dizinin dikdörtgen alt bölümünün nasıl yineyükleneceğini gösterir. İlk ve son üç satırı ve seçili her satırdaki ilk ve son iki sütunu dışlayarak ortadaki bölümü yineler:

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

Her durumda, için Aralık işleci <xref:System.Array> döndürülen öğeleri depolamak için bir dizi ayırır.

## <a name="scenarios-for-indices-and-ranges"></a>Dizinler ve aralıklar için senaryolar

Daha büyük bir dizinin bir bölümünü çözümlemek istediğinizde genellikle aralıklar ve dizinler kullanırsınız. Yeni söz dizimi, sıranın tam olarak hangi kısmının dahil olduğunu okumaktan daha net bir şeydir. Yerel işlev, `MovingAverage` <xref:System.Range> bağımsız değişkeni olarak bir kullanır. Bu yöntem daha sonra Min, Max ve Average hesaplama yaparken yalnızca o aralığı numaralandırır. Projenizde aşağıdaki kodu deneyin:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
