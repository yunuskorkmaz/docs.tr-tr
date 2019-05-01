---
title: 'Döngüler: for...to İfadesi'
description: Bkz. nasıl F# for... ifade bir döngüde bir dizi bir döngü değişkeninin değerleri üzerinden yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 041e98fa4bcc140aa3cd699f6ed35bf52c8b4175
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904039"
---
# <a name="loops-forto-expression"></a>Döngüler: for...to İfadesi

`for...to` İfadesi, bir dizi bir döngü değişkeninin değerleri üzerinden bir döngü içinde yineleme için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Açıklamalar

Tanımlayıcı türü türünden çıkarılan *Başlat* ve *son* ifadeler. Bu ifadeler için türler, 32 bit tamsayılar olmalıdır.

Teknik olarak bir ifade rağmen `for...to` daha geleneksel bir kesinlik temelli bir programlama dili deyiminde gibi. İçin dönüş türü *gövde ifadesi* olmalıdır `unit`. Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Döngüler: `for...in` İfade](loops-for-in-expression.md)
- [Döngüler: `while...do` İfade](loops-while-do-expression.md)