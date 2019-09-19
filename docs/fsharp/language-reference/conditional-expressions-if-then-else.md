---
title: 'Koşullu Ifadeler: if... sonra... değilse'
description: Farklı kod dallarını yürütmek için ' F# de koşullu ifadeler yazmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: d9763f37cd9170c42e968282b54a3ce925e92591
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083026"
---
# <a name="conditional-expressions-ifthenelse"></a>Koşullu Ifadeler:`if...then...else`

İfade `if...then...else` , kodun farklı dallarını çalıştırır ve ayrıca verilen Boolean ifadeye bağlı olarak farklı bir değer olarak değerlendirilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *İfade1* , Boolean ifadesi olarak `true`değerlendirildiğinde çalıştırılır; Aksi takdirde, *İfade2* çalışır.

Diğer dillerden farklı olarak, `if...then...else` yapı deyim değil bir ifadedir. Yani, yürüten daldaki son ifadenin değeri olan bir değer üretir. Her dalda üretilen değerlerin türleri eşleşmelidir. Açık `else` dal yoksa, türü ' dir `unit`. Bu nedenle, `then` dalın türü dışında `unit`herhangi bir tür ise, aynı dönüş türüne sahip bir `else` dal olmalıdır. İfadeleri birlikte `if...then...else` zincirlerse, yerine `else if`anahtar sözcüğünü `elif` kullanabilirsiniz; bunlar eşdeğerdir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `if...then...else` ifadesinin nasıl kullanılacağını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```console
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
