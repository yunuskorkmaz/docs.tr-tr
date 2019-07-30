---
title: 'Döngüler: for...to İfadesi'
description: F# İçin bkz.... to ifadesi bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626620"
---
# <a name="loops-forto-expression"></a>Döngüler: for...to İfadesi

İfade `for...to` , bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Açıklamalar

Tanımlayıcının türü *Başlangıç* ve *bitiş* ifadelerinin türünden algılanır. Bu ifadeler için türler 32 bitlik tamsayılar olmalıdır.

Teknik olarak bir ifade, `for...to` bir zorunlu programlama dilinde geleneksel bir ifadeye benzer. *Body ifadesi* `unit`için dönüş türü olmalıdır. Aşağıdaki örneklerde, `for...to` ifadesinin çeşitli kullanımları gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Lerin `for...in`İfadesini](loops-for-in-expression.md)
- [Lerin `while...do`İfadesini](loops-while-do-expression.md)
