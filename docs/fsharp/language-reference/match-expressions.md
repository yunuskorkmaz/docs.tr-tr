---
title: Eşleşme ifadeleri (F#)
description: F# eşleşme ifadesi ifade desenleri ile karşılaştırma temel alan dallanma denetim nasıl sağladığını öğrenin.
ms.date: 04/19/2018
ms.openlocfilehash: e4cb82f20fe82bff562736557c2346562c557f59
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44221850"
---
# <a name="match-expressions"></a>Eşleşme ifadeleri

`match` İfade karşılaştırma ifade desenleri temel alan dallanma denetim sağlar.

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

Desen eşleştirme ifadeler, karşılaştırma test ifade desenleri temel karmaşık dallara ayırmaya olanak tanır. İçinde `match` ifade *test ifade* etkinleştirin ve bir eşleşme bulunduğunda, karşılık gelen her desen ile karşılaştırıldığında *sonuç ifadesi* değerlendirilir ve elde edilen değer eşleştirme ifadesi değerini döndürdü.

Önceki sözdiziminde gösterilen işlev desen, hangi desen eşleştirme hemen bağımsız değişken üzerinde gerçekleştirilen bir lambda ifadesidir. Önceki sözdiziminde gösterilen işlev desen aşağıdakine eşdeğerdir.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md).

Desenler tam kümesini giriş değişkeni, tüm olası eşleşmeler kapsamalıdır. Joker karakter deseni sıkça kullandığınız (`_`) olarak daha önce eşleşmeyen tüm giriş değerlerini eşleştirmek için son desen.

Aşağıdaki kod, bazı yöntemler gösterir `match` ifade kullanılır. Başvuru ve kullanılabilir tüm olası düzeni örnekleri için bkz: [desen eşleştirme](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Cf desenleriyle ilgili

Kullanabileceğiniz bir `when` yan tümcesi değişkeni bir desenle eşleşen için karşılaması gereken ek bir koşulu belirtmek için. Böyle bir yan tümce olarak adlandırılır bir *koruyucu*. İfade aşağıdaki `when` anahtar sözcüğü bir eşleşme deseni, koruyucusu ile ilişkili yapılmıyorsa değerlendirilmez.

Aşağıdaki örnek, bir değişken desen için sayısal bir aralık belirtmek için bir koruma kullanımını gösterir. Not Boole işleçleri kullanarak birden çok koşulu birleştirilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Değişmez değerler dışındaki değerler desende kullanılamaz çünkü kullanmanız gerektiğini unutmayın bir `when` değerle giriş kısmı Karşılaştırılacak varsa yan tümcesi. Bu, aşağıdaki kodda gösterilmiştir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Bir birleşim deseni guard tarafından ele alınmıştır, koruma için geçerli olduğunu unutmayın **tüm** yalnızca sonuncu desenlerinin. Örneğin, aşağıdaki kod, koruma verilen `when a > 12` hem `A a` ve `B a`:

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

- [F# Dili Başvurusu](index.md)  
- [Etkin Desenler](active-patterns.md)  
- [Desen Eşleştirme](pattern-matching.md)  
