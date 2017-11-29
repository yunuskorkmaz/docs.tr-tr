---
title: "Döngüler: for...to İfadesi (F#)"
description: "Bkz. nasıl F # for... ifade için bir döngü değişken değerlerini aralığında bir döngüde yinelemek için kullanılır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[F # dili başvurusu](index.md)

[Döngüler: `for...in` ifade](loops-for-in-expression.md)

[Döngüler: `while...do` ifade](loops-while-do-expression.md)
