---
title: 'Döngüler: for...to İfadesi (F#)'
description: 'Bkz. nasıl F # for... ifade için bir döngü değişken değerlerini aralığında bir döngüde yinelemek için kullanılır.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 95a8960d71c82c01118d2e71479fc0ec5298a02b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
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
