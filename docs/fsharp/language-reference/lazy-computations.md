---
title: Geç Hesaplamalar (F#)
description: 'F # geç hesaplamalar uygulamalar ve kitaplıklar performansını nasıl artırabileceğinizi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037074"
---
# <a name="lazy-computations"></a>Geç Hesaplamalar

*Geç hesaplamalar* hemen değerlendirilmeyen, ancak bunun yerine sonucu gerektiğinde değerlendirilir hesaplamalar şunlardır. Bu, kodunuzun performansını artırmak için yardımcı olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *ifade* kod, yalnızca bir sonuç gerekli olduğunda değerlendirilir ve *tanımlayıcı* sonucu depolayan bir değerdir. Değer türünde [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), burada gerçek türü için kullanılan `'T` ifadenin sonuç belirlenir.

Geç hesaplamalar performansını hesaplamanın içinde bir sonuç gereken durumlar için yürütme kısıtlayarak olanak sağlar.

Hesaplama gerçekleştirilmesini zorlamak için yöntemi çağırın. `Force`. `Force` yalnızca bir kez gerçekleştirilmek üzere yürütülmesine neden olur. Yapılan sonraki çağrılar `Force` aynı sonucu, ancak herhangi bir kod Yürütülmeyen döndürür.

Aşağıdaki kod, yavaş bir hesaplama kullanımını ve kullanımını göstermektedir `Force`. Bu kodda, türü `result` olduğu `Lazy<int>`ve `Force` yöntemi döndürür bir `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Geç değerlendirme, ama `Lazy` yazın, sıraları için de kullanılır. Daha fazla bilgi için [dizileri](sequences.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [LazyExtensions Modülü](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
