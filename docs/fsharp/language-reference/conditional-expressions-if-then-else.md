---
title: 'Koşullu İfadeler: if... then...else (F#)'
description: 'Koşullu ifadeler farklı dallara kod yürütmek için içinde F # yazmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177607"
---
# <a name="conditional-expressions-ifthenelse"></a>Koşullu ifadeler: `if...then...else`

`if...then...else` İfade kod farklı dallara çalıştırır ve verilen bir Boole ifadesi bağlı olarak farklı bir değer için değerlendirir.

## <a name="syntax"></a>Sözdizimi

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *İfade1* Boole ifadesi olarak değerlendirildiğinde çalıştıran `true`; Aksi takdirde *expression2* çalıştırır.

Aksine başka dillerde `if...then...else` yapıdır deyim olmayan bir ifade. Son yürütülen dal ifade değeri bir değer üretir anlamına gelir. Her dalda üretilen değer türleri eşleşmelidir. Varsa ACE'si `else` dalı, kendi türüdür `unit`. Bu nedenle, türünü `then` dalı olan her türlü dışında `unit`, olmalıdır bir `else` dal aynı dönüş türüne sahip. Zincirleme olduğunda `if...then...else` ifadeler birlikte anahtar sözcüğü kullanabileceğiniz `elif` yerine `else if`; bunlar eşdeğerdir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `if...then...else` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
