---
title: 'Koşullu Ifadeler: if... sonra... değilse'
description: Farklı kod dallarını yürütmek için ' F# de koşullu ifadeler yazmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630399"
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

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
