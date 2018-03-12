---
title: "Koşullu İfadeler: if... then...else (F#)"
description: "Koşullu deyimler F farklı dalları kod yürütmek için #'de yazma öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 5823e46cd13053fcd31f94f2d79d1f7470ca5118
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="conditional-expressions-ifthenelse"></a>Koşullu ifadeler: `if...then...else`

`if...then...else` İfade kodunun farklı dalları çalıştırır ve verilen Boole ifadesi bağlı olarak farklı bir değere de değerlendirir.


## <a name="syntax"></a>Sözdizimi

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde *İfade1* Boole ifadesi olarak değerlendirildiğinde çalıştıran `true`; Aksi halde, *İfade2* çalıştırır.

Aksine başka dillerde `if...then...else` yapıdır bir ifade, bir ifade. Yürütür şube son ifade değeri bir değer üreten anlamına gelir. Her dalda üretilen değerlerin türleri eşleşmelidir. Varsa ACE'si `else` dal, kendi türüdür `unit`. Bu nedenle, varsa türünü `then` dalı olan herhangi bir tür dışında `unit`, olmalıdır bir `else` şube aynı dönüş türüne sahip. Zincirleme zaman `if...then...else` ifadeleri birlikte, anahtar sözcüğünü kullanabilirsiniz `elif` yerine `else if`; bunlar eşdeğerdir.

## <a name="example"></a>Örnek
Aşağıdaki örnekte nasıl kullanılacağını anlatan `if...then...else` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

