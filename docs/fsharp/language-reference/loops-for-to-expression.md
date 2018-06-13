---
title: 'Döngüler: for...to İfadesi (F#)'
description: 'Bkz. nasıl F # for... ifade için bir döngü değişken değerlerini aralığında bir döngüde yinelemek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563408"
---
# <a name="loops-forto-expression"></a>Döngüler: for...to İfadesi

`for...to` İfade Döngü değişkeninin değerini aralığında bir döngüde yinelemek için kullanılır.


## <a name="syntax"></a>Sözdizimi

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Açıklamalar
Tanımlayıcı türü türünden algılanır *Başlat* ve *son* ifadeler. Bu deyimler türlerinde 32 bit tamsayı olması gerekir.

Teknik olarak bir ifade rağmen `for...to` daha geleneksel deyimi kesinlik temelli bir programlama dili gibi. Dönüş türü için *gövde ifade* olmalıdır `unit`. Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Döngüler: `for...in` ifade](loops-for-in-expression.md)

[Döngüler: `while...do` ifade](loops-while-do-expression.md)
