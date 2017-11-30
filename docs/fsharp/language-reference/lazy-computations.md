---
title: "Geç Hesaplamalar (F#)"
description: "F # geç hesaplamalar uygulamalarınızı ve kitaplıkları performansını geliştirebilirsiniz nasıl öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3499293e-1d53-4b02-b764-f687fbdaa7fe
ms.openlocfilehash: 984c96ab68a8919e2382eefe8260b07f191027dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lazy-computations"></a>Geç Hesaplamalar

*Geç hesaplamalar* hemen değerlendirilmez, ancak sonuç gerektiğinde yerine değerlendirilir hesaplamalar şunlardır. Bu, kodunuzu performansının artırılmasına yardımcı olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *ifade* yalnızca bir sonuç gerekli olduğunda değerlendirilen kodu ve *tanımlayıcısı* sonucu depolayan bir değerdir. Değer [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), burada gerçek türü için kullanılan `'T` ifade sonucundan belirlenir.

Geç hesaplamalar hesaplamanın sonucu gerekli durumlar için yürütmesi kısıtlayarak performansını artırmak etkinleştirin.

Gerçekleştirilecek hesaplama zorlamak için yöntemi çağırın `Force`. `Force`yalnızca bir kez gerçekleştirilmesi yürütme neden olur. Sonraki çağrılar `Force` aynı sonucu, ancak herhangi bir kod yürütülmez döndürür.

Aşağıdaki kod yavaş hesaplama kullanımını ve kullanımını gösterir `Force`. Bu kod türünü `result` olan `Lazy<int>`ve `Force` yöntemi döndürür bir `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Geç değerlendirme, ama `Lazy` yazın, sıraları için de kullanılır. Daha fazla bilgi için bkz: [sıraları](sequences.md).

## <a name="see-also"></a>Ayrıca Bkz.

[F # dili başvurusu](index.md)

[LazyExtensions Modülü](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
