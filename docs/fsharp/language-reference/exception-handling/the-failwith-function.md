---
title: "Özel Durumlar: failwith İşlevi (F#)"
description: "Nasıl 'failwith' işlevi bir F # özel durum oluşturur öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2017
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
[Özel durum işleme](index.md)

[Özel durum türleri](exception-types.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)

[Özel durumlar: `raise` işlevi](the-raise-function.md)
