---
title: 'Eşleşme ifadeleri (F #)'
description: 'F # eşleşme ifadesi karşılaştırmaya ifade desenleri dayalı dallanma denetim nasıl sağladığını öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f843e6fde98eae8a10235dd5cae38ffc10a4fb9f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="match-expressions"></a>Eşleşme ifadeleri

`match` İfade karşılaştırmaya ifade desenleri dayalı dallanma denetim sağlar.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>Açıklamalar

Desen eşleştirme ifadeleri karşılaştırmaya test ifadesinin desenleri dayalı karmaşık dallanma için izin verir. İçinde `match` ifadesi *test ifade* açın ve bir eşleşme bulunduğunda, karşılık gelen her deseni ile karşılaştırıldığında *sonuç ifadesi* değerlendirilir ve çıkan değeri eşleşme ifadesi değeri olarak döndürdü.

Desen eşleştirme önceki sözdiziminde gösterilen işlevi hangi desen eşleştirme hemen bağımsız gerçekleştirilir lambda ifadesi ' dir. Desen eşleştirme önceki sözdiziminde gösterilen işlevi şuna eşdeğerdir.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md).

Desenler tam kümesi giriş değişkenin tüm olası eşleşmeler kapsamalıdır. Joker karakter deseni sık kullandığınız (`_`) daha önce eşleşmeyen tüm giriş değerlerini eşleştirmek için son desen olarak.

Aşağıdaki kod, yollardan bazılarını gösterir `match` ifade kullanılır. Bir başvuru ve kullanılabilir tüm olası düzeni örnekleri için bkz: [desen eşleştirme](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Modeli koruyucuları

Kullanabileceğiniz bir `when` değişkeni bir desenle eşleşen için karşılaması gereken ek bir koşulu belirtmek için yan tümcesi. Bu tür bir yan tümce olarak adlandırılır bir *koruma*. İfade aşağıdaki `when` anahtar sözcüğü bu koruyucusu ile ilişkili desenle eşleşen bir kılmadığınız sürece değerlendirilmez.

Aşağıdaki örnekte değişken deseni için sayısal bir aralık belirtmek için bir koruma kullanımını göstermektedir. Boole işleçleri kullanarak birden çok koşul birleştirilir unutmayın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Değişmez değerler dışında değerleri düzende kullanılamadığından kullanmanız gerektiğini unutmayın bir `when` değerle giriş kısmı karşılaştırmak varsa, yan tümcesi. Bu aşağıdaki kodda gösterilir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Birleşim deseni koruyucu tarafından kapsanan, koruma için geçerli olduğunu unutmayın **tüm** yalnızca sonuncu desen. Örneğin, aşağıdaki kod, koruma verilen `when a > 12` hem de geçerli `A a` ve `B a`:

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>Ayrıca bkz.

[F# Dili Başvurusu](index.md)  
[Etkin Desenler](active-patterns.md)  
[Desen Eşleştirme](pattern-matching.md)  
