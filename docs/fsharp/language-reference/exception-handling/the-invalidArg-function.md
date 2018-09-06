---
title: 'Özel Durumlar: invalidArg İşlevi (F#)'
description: "F # 'invalidArg' işlevi bir bağımsız değişken özel durum nasıl oluşturur? öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 8bf65fae9392a88205e3cdec8b7d7a3ff42f8416
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798188"
---
# <a name="exceptions-the-invalidarg-function"></a>Özel Durumlar: invalidArg İşlevi

`invalidArg` İşlevi bağımsız değişken özel durum oluşturur.

## <a name="syntax"></a>Sözdizimi

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde parametre adı, bağımsız değişken geçersiz parametre adı bir dizedir. *Hata iletisi dizesi* bir, dize veya türünde bir değer `string`. Bu duruma `Message` özelliğini özel durum nesnesi.

Özel durum oluşturdu `invalidArg` olduğu bir `System.ArgumentException` özel durum. Aşağıdaki kod kullanışını `invalidArg` özel durum oluşturabilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Aşağıdaki çıkış alınır (gösterilmemiştir) bir yığın çerçevesi izi tarafından izlenen.

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel durumlar: `try...with` ifadesi](the-try-with-expression.md)
- [Özel durumlar: `try...finally` ifadesi](the-try-finally-expression.md)
- [Özel durumlar: `raise` işlevi](the-raise-function.md)
- [Özel durumlar: `failwith` işlevi](the-failwith-function.md)
