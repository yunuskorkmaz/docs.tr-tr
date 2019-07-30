---
title: 'Özel durumlar: failwith İşlevi'
description: "' Failwith ' işlevinin bir F# özel durum oluşturması hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630332"
---
# <a name="exceptions-the-failwith-function"></a>Özel durumlar: failwith İşlevi

İşlev bir F# `failwith`

## <a name="syntax"></a>Sözdizimi

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Açıklamalar

Önceki söz diziminde *hata-ileti dizesi* , sabit bir dize veya türünde `string`bir değer. Özel durumun `Message` özelliği olur.

Tarafından `failwith` oluşturulan özel durum, `Failure` F# kodda adı olan `System.Exception` bir başvuru olan bir özel durumdur. Aşağıdaki kod, bir özel durum `failwith` oluşturmak için kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel Durumlar: `try...with` İfade](the-try-with-expression.md)
- [Özel Durumlar: `try...finally` İfade](the-try-finally-expression.md)
- [Özel durumlar: `raise` işlev](the-raise-function.md)
