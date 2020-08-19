---
title: Gecikmeli İfadeler
description: 'F # yavaş ifadelerinin uygulamalarınızın ve kitaplıklarınızın performansını nasıl geliştirebileceğinizi öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 71c466ca3b74c9e92b81a3c268e07438ec944905
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558094"
---
# <a name="lazy-expressions"></a>Gecikmeli İfadeler

*Lazy ifadeleri* hemen değerlendirilmeyecek ifadelerdir, ancak bunun yerine sonuç gerektiğinde değerlendirilir. Bu, kodunuzun performansını artırmaya yardımcı olabilir.

## <a name="syntax"></a>Syntax

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *ifade* , yalnızca bir sonuç gerekli olduğunda değerlendirilen koddur ve *tanımlayıcı* sonucu depolayan bir değerdir. Değer [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html) , için kullanılan gerçek türün `'T` ifadenin sonucundan belirlendiği türdür.

Yavaş ifadeler, bir ifadenin yürütülmesini yalnızca bir sonucun gerekli olduğu durumlara göre kısıtlayarak performansı iyileştirmenize olanak tanır.

İfadeleri gerçekleştirilecek şekilde zorlamak için yöntemini çağırın `Force` . `Force` yürütmenin yalnızca bir kez gerçekleştirilmesine neden olur. Sonraki çağrılar `Force` aynı sonucu döndürecek, ancak herhangi bir kod yürütmüyor.

Aşağıdaki kod, geç ifadelerin kullanımını ve kullanımını gösterir `Force` . Bu kodda, türü, `result` `Lazy<int>` ve `Force` yöntemi döndürür `int` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Yavaş değerlendirme, ancak tür değil, `Lazy` diziler için de kullanılır. Daha fazla bilgi için bkz. [diziler](sequences.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [LazyExtensions modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
