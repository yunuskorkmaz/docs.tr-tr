---
title: 'Özel durumlar: Failwith işlevi'
description: Nasıl 'failwith' işlevi oluşturur öğrenin bir F# özel durum.
ms.date: 05/16/2016
ms.openlocfilehash: 05d385ddfc98a910779a6f59949a7187c38f0812
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772690"
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