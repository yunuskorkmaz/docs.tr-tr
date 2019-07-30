---
title: Gecikmeli İfadeler
description: Yavaş ifadelerin F# uygulamalarınızın ve kitaplıklarınızın performansını nasıl geliştirebileceğinizi öğrenin.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630744"
---
# <a name="lazy-expressions"></a>Gecikmeli İfadeler

*Lazy ifadeleri* hemen değerlendirilmeyecek ifadelerdir, ancak bunun yerine sonuç gerektiğinde değerlendirilir. Bu, kodunuzun performansını artırmaya yardımcı olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *ifade* , yalnızca bir sonuç gerekli olduğunda değerlendirilen koddur ve *tanımlayıcı* sonucu depolayan bir değerdir. Değer, için `'T` kullanılan gerçek [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)türün ifadenin sonucundan belirlendiği türdür.

Yavaş ifadeler, bir ifadenin yürütülmesini yalnızca bir sonucun gerekli olduğu durumlara göre kısıtlayarak performansı iyileştirmenize olanak tanır.

İfadeleri gerçekleştirilecek şekilde zorlamak için yöntemini `Force`çağırın. `Force`yürütmenin yalnızca bir kez gerçekleştirilmesine neden olur. Sonraki çağrılar `Force` aynı sonucu döndürecek, ancak herhangi bir kod yürütmüyor.

Aşağıdaki kod, geç ifadelerin kullanımını ve `Force`kullanımını gösterir. `result` Bu kodda, türü `Lazy<int>`, `Force`veyöntemi döndürür. `int`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Yavaş değerlendirme, ancak `Lazy` tür değil, diziler için de kullanılır. Daha fazla bilgi için bkz. [diziler](sequences.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [LazyExtensions modülü](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
