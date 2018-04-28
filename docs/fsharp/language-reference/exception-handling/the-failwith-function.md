---
title: 'Özel Durumlar: failwith İşlevi (F#)'
description: "Nasıl 'failwith' işlevi bir F # özel durum oluşturur öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: af1e3b7dc96b3b822e2e19b7bac435940d15922f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
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
