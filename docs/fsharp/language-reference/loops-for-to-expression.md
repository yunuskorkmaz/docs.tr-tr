---
title: 'Döngüler: for...to İfadesi'
description: F# İçin bkz.... to ifadesi bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283909"
---
# <a name="loops-forto-expression"></a>Döngüler: for...to İfadesi

`for...to` ifadesi bir döngü değişkeninin bir dizi değeri üzerinde bir döngüde yinelemek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Açıklamalar

Tanımlayıcının türü *Başlangıç* ve *bitiş* ifadelerinin türünden algılanır. Bu ifadeler için türler 32 bitlik tamsayılar olmalıdır.

Teknik olarak bir ifade, `for...to`, bir zorunlu programlama dilinde geleneksel bir ifadeye benzer. *Body ifadesi* için dönüş türü `unit`olmalıdır. Aşağıdaki örneklerde `for...to` ifadesinin çeşitli kullanımları gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Döngüler: `for...in` Ifade](loops-for-in-expression.md)
- [Döngüler: `while...do` Ifade](loops-while-do-expression.md)
