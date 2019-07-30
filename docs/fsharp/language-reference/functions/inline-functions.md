---
title: Satır İçi İşlevler
description: Doğrudan çağıran kodun içinde F# tümleşik olan satır içi işlevleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630685"
---
# <a name="inline-functions"></a>Satır İçi İşlevler

*Satır içi işlevler* doğrudan çağıran koda tümleştirilen işlevlerdir.

## <a name="using-inline-functions"></a>Satır Içi Işlevleri kullanma

Statik tür parametreleri kullandığınızda, tür parametrelerine göre parametreli olan tüm işlevler satır içi olmalıdır. Bu, derleyicinin bu tür parametrelerini çözümleyebilecek olmasını güvence altına alır. Sıradan genel tür parametreleri kullandığınızda böyle bir kısıtlama yoktur.

Üye kısıtlamaları kullanımını etkinleştirmenin dışında, satır içi işlevler kodu iyileştirmek için yararlı olabilir. Ancak, satır içi işlevlerin aşırı kullanımı, kodunuzun, derleyici iyileştirmeleri ve kitaplık işlevlerinin uygulanması için değişikliklere daha az dayanıklı olmasına neden olabilir. Bu nedenle, diğer en iyi duruma getirme tekniklerini denemediğiniz takdirde en iyi duruma getirme için satır içi işlevleri kullanmaktan kaçının. İşlevin veya yöntemin satır içi yapılması bazen performansı iyileştirebilir, ancak bu her zaman durum değildir. Bu nedenle, belirli bir işlevi satır içi olarak yapmanın aslında pozitif bir etkiye sahip olduğunu doğrulamak için performans ölçümlerini da kullanmanız gerekir.

`inline` Değiştirici, en üst düzeydeki işlevlere, modül düzeyinde veya bir sınıftaki yöntem düzeyinde uygulanabilir.

Aşağıdaki kod örneği, en üst düzeydeki bir satır içi işlev, bir satır içi örnek yöntemi ve bir satır içi statik yöntem gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Satır içi Işlevler ve tür çıkarımı

' Nin `inline` varlığı tür çıkarımı etkiler. Bunun nedeni, satır içi işlevlerin statik olarak çözümlenen tür parametrelerine sahip olmasından kaynaklanır, ancak satır içi olmayan işlevler olamaz. Aşağıdaki kod örneğinde, statik olarak çözümlenen bir `inline` tür parametresine sahip bir işlev kullandığınız için `float` , dönüştürme işleci olan bir durum gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Değiştirici olmadan, tür çıkarımı işlevi belirli bir tür almaya zorlar, bu durumda `int`. `inline` Ancak `inline` değiştiriciyle işlev statik olarak çözümlenen bir tür parametresine sahip olacak şekilde de algılanır. `inline` Değiştiriciyle, tür şu şekilde algılanır:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Bu, işlevin **float**öğesine dönüştürmeyi destekleyen herhangi bir türü kabul ettiği anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
- [Kısıtlamalar](../generics/constraints.md)
- [Statik Olarak Çözümlenmiş Tür Parametreleri](../generics/statically-resolved-type-parameters.md)
