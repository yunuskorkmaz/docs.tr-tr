---
title: 'Özel Durumlar: failwith İşlevi (F#)'
description: Nasıl 'failwith' işlevi bir F# özel durum oluşturur öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 69a2eb69e0157d3bde8cb8884cb0ae960634dddc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863435"
---
# <a name="exceptions-the-failwith-function"></a>Özel Durumlar: failwith İşlevi

`failwith` İşlevi bir F# özel durum oluşturur.

## <a name="syntax"></a>Sözdizimi

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Açıklamalar

*Hata iletisi dizesi* önceki sözdiziminde bir değişmez değer dize türünde bir değer mi `string`. Bu duruma `Message` özel durumun özelliği.

Tarafından oluşturulan özel durum `failwith` olduğu bir `System.Exception` adına sahip bir başvurudur özel durum `Failure` F# kodu. Aşağıdaki kod kullanışını `failwith` özel durum oluşturabilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel durumlar: `try...with` ifadesi](the-try-with-expression.md)
- [Özel durumlar: `try...finally` ifadesi](the-try-finally-expression.md)
- [Özel durumlar: `raise` işlevi](the-raise-function.md)
