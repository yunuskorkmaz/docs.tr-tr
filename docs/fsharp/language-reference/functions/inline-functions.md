---
title: "Satır İçi İşlevler (F#)"
description: "Doğrudan çağırma koda tümleşik F # satır içi işlevler kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a>Satır İçi İşlevler

*Satır içi işlevler* doğrudan çağıran koda tümleşik işlevlerdir.


## <a name="using-inline-functions"></a>Satır içi işlevler kullanma
Statik tür parametreleri kullandığınızda, türü parametrelere göre parametreli hiçbir işlev satır içi olması gerekir. Bu, bu tür parametreleri derleyici çözebilirsiniz garanti eder. Sıradan genel tür parametreleri kullandığınızda, bu tür bir kısıtlama yoktur.

Üye kısıtlamaları kullanımını etkinleştirmenin dışında satır içi işlevler kodu en iyi duruma getirme yararlı olabilir. Ancak, satır içi işlevlerin aşırı kullanımı kodunuzu derleyici en iyi duruma getirme ve kitaplık işlevleri uyarlamasını değişiklikler daha az dayanıklı olması neden olabilir. Bu nedenle, diğer tüm iyileştirme tekniklerini denediyseniz sürece satır içi işlevler için en iyi duruma getirme yapmaktan kaçınmalısınız. Bir işlev veya yöntem satır içi yapma performansı artırır ancak, her zaman geçerli değildir. Bu nedenle, tüm verilen işlev satır içi yapmadan aslında pozitif bir etkiye sahip olup olmadığını doğrulamak için performans ölçümleri kullanmalısınız.

`inline` Değiştiricisi işlevler en üst düzeyinde, modülü düzeyinde ya da bir sınıf yöntemi düzeyinde uygulanabilir.

Aşağıdaki kod örneği, en üst düzeyinde, satır içi örnek yöntemi ve satır içi statik yöntemi satır içi işlev gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>Satır içi işlevler ve tür çıkarımı
Varlığını `inline` etkiler çıkarım yazın. Satır içi işlevler statik olarak çözümlenmiş tür parametreleri, çünkü olmayan satır içi işlevler edilemez ise. Aşağıdaki kod örneğinde bir durumu gösterir nerede `inline` statik olarak çözümlenmiş tür parametresi olan bir işlev kullandığından yararlıdır `float` dönüşüm işleci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Olmadan `inline` değiştiricisi, tür çıkarımı zorlar belirli bir türdeki bu durumda yapılacak işlevi `int`. Ancak `inline` değiştiricisi, işlevi bir statik olarak çözümlenmiş tür parametreye sahip olayla de. İle `inline` değiştiricisi, türü olayla aşağıdaki olmalıdır:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Bu işlev bir dönüştürme destekleyen herhangi bir türü kabul eden anlamına gelir **float**.


## <a name="see-also"></a>Ayrıca Bkz.
[İşlevler](index.md)

[Kısıtlamaları](../generics/constraints.md)

[Statik olarak çözümlenmiş tür parametreleri](../generics/statically-resolved-type-parameters.md)
