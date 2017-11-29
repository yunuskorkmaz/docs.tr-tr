---
title: "Özel Durumlar: invalidArg İşlevi (F#)"
description: "Nasıl F # 'invalidArg' işlevi bağımsız değişken özel durum oluşturur öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d375b704-6b27-493e-bd1d-ee217a53c4b5
ms.openlocfilehash: 107bef361a6bd034e3d6a2227e18cf64b1b04576
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-invalidarg-function"></a>Özel Durumlar: invalidArg İşlevi

`invalidArg` İşlevi bağımsız değişken özel durum oluşturur.


## <a name="syntax"></a>Sözdizimi

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde parametre adı olan bağımsız değişkeni geçersiz parametre adı bir dizedir. *Hata ileti dizesi* sabit değerli bir dize ya da türde bir değer `string`. Bu duruma `Message` özel durum nesnesi özelliği.

Tarafından oluşturulan özel durum `invalidArg` olan bir `System.ArgumentException` özel durum. Aşağıdaki kod kullanımını göstermektedir `invalidArg` bir özel durum için.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

Çıktı aşağıda verilmektedir (gösterilmez) yığın izlemesi tarafından izlenen.

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Ayrıca Bkz.
[Özel durum işleme](index.md)

[Özel durum türleri](exception-types.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)

[Özel durumlar: `raise` işlevi](the-raise-function.md)

[Özel durumlar: `failwith` işlevi](the-failwith-function.md)
