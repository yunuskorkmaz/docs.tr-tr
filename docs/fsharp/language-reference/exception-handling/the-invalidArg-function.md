---
title: 'Özel durumlar: İnvalidArg işlevi'
description: Bilgi nasıl F# 'invalidArg' işlevi bağımsız değişken özel durum oluşturur.
ms.date: 05/16/2016
ms.openlocfilehash: 7fd8d48b80970dbbafc0c23a478b4ccf3490f3ee
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613342"
---
# <a name="exceptions-the-invalidarg-function"></a>Özel durumlar: İnvalidArg işlevi

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
- [Özel durumlar: `try...with` İfadesi](the-try-with-expression.md)
- [Özel durumlar: `try...finally` İfadesi](the-try-finally-expression.md)
- [Özel durumlar: `raise` işlevi](the-raise-function.md)
- [Özel durumlar: `failwith` İşlevi](the-failwith-function.md)