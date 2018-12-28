---
title: Satır İçi İşlevler
description: Nasıl kullanacağınızı öğrenin F# satır içi işlevler, doğrudan çağıran kodun içine tümleştirilmiştir.
ms.date: 05/16/2016
ms.openlocfilehash: 12c175e3e46e12d978fe02d3e1fe83142e71a25d
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610573"
---
# <a name="inline-functions"></a>Satır İçi İşlevler

*Satır içi işlevleri* doğrudan çağıran kodun içine tümleştirilmiştir işlevlerdir.

## <a name="using-inline-functions"></a>Satır içi işlevleri kullanma

Statik tür parametreleri kullandığınızda, tür parametreleri tarafından parametre haline getirilen tüm İşlevler, satır içi olması gerekir. Bu, derleyici bu tür parametreleri çözümleyebileceğinden garanti eder. Normal genel tür parametrelerini kullandığınızda, bu tür bir kısıtlama yoktur.

Üye kısıtlamaları kullanımını etkinleştirme dışında satır içi işlevler kodu en iyi duruma getirme yararlı olabilir. Ancak, satır içi işlevlerin aşırı kodunuzu daha az derleyici iyileştirmeleri ve kitaplık işlevleri uygulaması değişikliklere dayanıklı olmasını neden olabilir. Bu nedenle, tüm iyileştirme teknikleri denediniz mi sürece iyileştirme için satır içi işlevleri kullanarak kaçınmanız gerekir. Satır içi işlev veya metot yapmak bazen performansı geliştirebilir, ancak bu her zaman böyle değildir. Bu nedenle, herhangi belirli bir işlevi satır içi yapmadan aslında olumlu bir etkiye sahip olduğunu doğrulamak için performans ölçümleri kullanmalısınız.

`inline` Değiştiricisi işlevleri en üst düzeyinde, Modül düzeyinde veya bir sınıftaki yöntemi düzeyinde uygulanabilir.

Aşağıdaki kod örneği bir satır içi işlevi en üst düzey, bir satır içi örnek yöntemi ve bir satır içi statik bir yöntemi gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Satır içi işlevleri ve tür çıkarımı

Varlığını `inline` tür çıkarımı etkiler. Satır içi işlevler statik olarak çözümlenmiş tür parametreleri, ancak satır içi işlevleri kullanılamaz olmasıdır. Aşağıdaki kod örneği bir durumu gösterir. burada `inline` bir statik olarak çözümlenen tür parametresi olan bir işlev kullandığından yararlıdır `float` dönüştürme işleci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Olmadan `inline` değiştiricisi, tür çıkarımı zorlar bu durumda, belirli bir türdeki yararlanmak için işlev `int`. Ancak `inline` statik olarak çözümlenmiş tür parametresi için de değiştiricisi, işlevin çıkarılan. İle `inline` aşağıdaki olmasını çıkarılan değiştiricisi, türü:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Bu işlev dönüştürmeyi destekleyen herhangi bir türü kabul eden anlamına gelir **float**.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
- [Kısıtlamalar](../generics/constraints.md)
- [Statik Olarak Çözümlenmiş Tür Parametreleri](../generics/statically-resolved-type-parameters.md)