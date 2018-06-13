---
title: 'Özel Durumlar: invalidArg İşlevi (F#)'
description: "Nasıl F # 'invalidArg' işlevi bağımsız değişken özel durum oluşturur öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 43e1b6f3f36774ac50aeff147f75f133d6e3e5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564514"
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
[Özel Durum İşleme](index.md)

[Özel Durum Türleri](exception-types.md)

[Özel durumlar: `try...with` ifade](the-try-with-expression.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)

[Özel durumlar: `raise` işlevi](the-raise-function.md)

[Özel durumlar: `failwith` işlevi](the-failwith-function.md)
