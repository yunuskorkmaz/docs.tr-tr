---
title: Yavaş ifadeler
description: Bilgi nasıl F# yavaş ifadeler, uygulamaları ve kitaplıkları performansını artırabilir.
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57851393"
---
# <a name="lazy-expressions"></a>Yavaş ifadeler

*Yavaş ifadeler* hemen değerlendirilmeyen, ancak bunun yerine sonucu gerektiğinde değerlendirilir ifadeler. Bu, kodunuzun performansını artırmak için yardımcı olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *ifade* kod, yalnızca bir sonuç gerekli olduğunda değerlendirilir ve *tanımlayıcı* sonucu depolayan bir değerdir. Değer türünde [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), burada gerçek türü için kullanılan `'T` ifadenin sonuç belirlenir.

Yavaş ifadeler bir ifade içinde bir sonuç gereken durumlar için yürütme kısıtlayarak performansını artırmak etkinleştirin.

Gerçekleştirilecek ifadeleri zorlamak için yöntemi çağırın. `Force`. `Force` yalnızca bir kez gerçekleştirilmek üzere yürütülmesine neden olur. Yapılan sonraki çağrılar `Force` aynı sonucu, ancak herhangi bir kod Yürütülmeyen döndürür.

Aşağıdaki kod yavaş ifadeler kullanımını ve kullanımını göstermektedir `Force`. Bu kodda, türü `result` olduğu `Lazy<int>`ve `Force` yöntemi döndürür bir `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Geç değerlendirme, ama `Lazy` yazın, sıraları için de kullanılır. Daha fazla bilgi için [dizileri](sequences.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [LazyExtensions Modülü](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
