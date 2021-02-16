---
title: Gecikmeli İfadeler
description: 'F # yavaş ifadelerinin uygulamalarınızın ve kitaplıklarınızın performansını nasıl geliştirebileceğinizi öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425509"
---
# <a name="lazy-expressions"></a>Gecikmeli İfadeler

*Lazy ifadeleri* hemen değerlendirilmeyecek ifadelerdir, ancak bunun yerine sonuç gerektiğinde değerlendirilir. Bu, kodunuzun performansını artırmaya yardımcı olabilir.

## <a name="syntax"></a>Syntax

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *ifade* , yalnızca bir sonuç gerekli olduğunda değerlendirilen koddur ve *tanımlayıcı* sonucu depolayan bir değerdir. Değer `Lazy<'T>` , için kullanılan gerçek türün `'T` ifadenin sonucundan belirlendiği türdür.

Yavaş ifadeler, bir ifadenin yürütülmesini yalnızca bir sonucun gerekli olduğu durumlara göre kısıtlayarak performansı iyileştirmenize olanak tanır.

İfadeleri gerçekleştirilecek şekilde zorlamak için yöntemini çağırın `Force` . `Force` yürütmenin yalnızca bir kez gerçekleştirilmesine neden olur. Sonraki çağrılar `Force` aynı sonucu döndürecek, ancak herhangi bir kod yürütmüyor.

Aşağıdaki kod, geç ifadelerin kullanımını ve kullanımını gösterir `Force` . Bu kodda, türü, `result` `Lazy<int>` ve `Force` yöntemi döndürür `int` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Yavaş değerlendirme, ancak tür değil, `Lazy` diziler için de kullanılır. Daha fazla bilgi için bkz. [diziler](sequences.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [LazyExtensions modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
