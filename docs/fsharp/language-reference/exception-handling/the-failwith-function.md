---
title: 'Özel Durumlar: failwith İşlevi (F#)'
description: "Nasıl 'failwith' işlevi bir F # özel durum oluşturur öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 59f7129faf38668dd7390790e22d25f37c129750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-failwith-function"></a>Özel Durumlar: failwith İşlevi

`failwith` İşlevi F # özel durum oluşturur.


## <a name="syntax"></a>Sözdizimi

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Açıklamalar
*Hata ileti dizesi* önceki sözdiziminde sabit değerli bir dize türünde bir değer mi `string`. Bu duruma `Message` özel durum özelliği.

Tarafından oluşturulan özel durum `failwith` olan bir `System.Exception` adına sahip bir başvuru özel durumu `Failure` F # kodunda. Aşağıdaki kod kullanımını göstermektedir `failwith` bir özel durum için.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[Özel Durum İşleme](index.md)

[Özel Durum Türleri](exception-types.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)

[Özel durumlar: `raise` işlevi](the-raise-function.md)
