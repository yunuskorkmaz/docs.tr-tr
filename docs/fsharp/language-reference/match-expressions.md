---
title: "Eşleşme İfadeleri (F#)"
description: "F # eşleşme ifadesi karşılaştırmaya ifade desenleri dayalı dallanma denetim nasıl sağladığını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a>Eşleşme İfadeleri

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

Değişmez değerler dışında değerleri düzende kullanılamadığından kullanmanız gerektiğini unutmayın bir `when` değerle giriş kısmı karşılaştırmak varsa, yan tümcesi. Bu aşağıdaki kodda gösterilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a>Ayrıca Bkz.

[F # dili başvurusu](index.md)

[Etkin desenler](active-patterns.md)

[Desen eşleştirme](pattern-matching.md)
