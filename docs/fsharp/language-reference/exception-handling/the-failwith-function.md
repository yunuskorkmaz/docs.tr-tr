---
title: 'Özel durumlar: Failwith işlevi'
description: Nasıl 'failwith' işlevi oluşturur öğrenin bir F# özel durum.
ms.date: 05/16/2016
ms.openlocfilehash: 08107966ddc2f55625347deb92d224b286df7761
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641943"
---
# <a name="exceptions-the-failwith-function"></a>Özel durumlar: Failwith işlevi

`failwith` İşlevi oluşturur bir F# özel durum.

## <a name="syntax"></a>Sözdizimi

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Açıklamalar

*Hata iletisi dizesi* önceki sözdiziminde bir değişmez değer dize türünde bir değer mi `string`. Bu duruma `Message` özel durumun özelliği.

Tarafından oluşturulan özel durum `failwith` olduğu bir `System.Exception` adına sahip bir başvurudur özel durum `Failure` içinde F# kod. Aşağıdaki kod kullanışını `failwith` özel durum oluşturabilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel Durumlar: `try...with` İfadesi](the-try-with-expression.md)
- [Özel Durumlar: `try...finally` İfadesi](the-try-finally-expression.md)
- [Özel durumlar: `raise` işlevi](the-raise-function.md)
