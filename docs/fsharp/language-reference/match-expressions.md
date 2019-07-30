---
title: Match ifadeleri
description: F# Match ifadesinin bir desen kümesine sahip bir ifadenin karşılaştırmasına dayalı olarak dallanma denetimi nasıl sağladığını öğrenin.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627615"
---
# <a name="match-expressions"></a>Match ifadeleri

`match` İfade, bir ifadenin bir dizi deseniyle karşılaştırmasını temel alan dallanma denetimi sağlar.

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

Desen eşleştirme ifadeleri, bir dizi desenle bir test ifadesinin karşılaştırmasına bağlı olarak karmaşık dallandırma sağlar. İfadede, *Test ifadesi* her bir düzen ile karşılaştırılır ve bir eşleşme bulunduğunda, karşılık gelen *Sonuç ifadesi* değerlendirilir ve elde edilen değer, eşleşme ifadesinin değeri olarak döndürülür. `match`

Önceki sözdiziminde gösterilen model eşleştirme işlevi, bir lambda ifadesidir ve bu ifade, bağımsız değişkende hemen bu düzende yapılır. Önceki sözdiziminde gösterilen kalıp eşleştirme işlevi aşağıdaki gibidir.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Lambda ifadeleri hakkında daha fazla bilgi için bkz [. Lambda ifadeleri: `fun` Anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md).

Tüm desen kümesi, giriş değişkeninin tüm olası eşleşmelerini kapsamalıdır. Genellikle, daha önce eşleşmeyen giriş değerleriyle eşleştirmek`_`için en son model olarak () joker karakter stilini kullanın.

Aşağıdaki kod, `match` ifadenin kullanıldığı bazı yolları gösterir. Bir başvuru ve kullanılabilecek tüm olası desenlerin örnekleri için bkz. [desen eşleştirme](pattern-matching.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Desenlerdeki koruyucular

Değişkenin bir düzeniyle eşleştirmek `when` için karşılaması gereken ek bir koşul belirtmek için bir yan tümce kullanabilirsiniz. Böyle bir yan tümce *koruma*olarak adlandırılır. `when` Anahtar sözcüğünü izleyen ifade, bu Guard ile ilişkili bir eşleme yapılmadığı takdirde değerlendirilmez.

Aşağıdaki örnek, bir değişken deseninin sayısal aralığını belirtmek için bir koruyucu kullanımını gösterir. Birden çok koşulun Boole işleçleri kullanılarak birleştirildiğine unutmayın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Değişmez değerler dışındaki değerlerin, düzende kullanılmadığından, girişin bazı bölümlerini bir değere göre karşılaştırmanız gerekiyorsa, `when` bir yan tümce kullanmanız gerektiğini unutmayın. Bu, aşağıdaki kodda gösterilmiştir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Bir birleşim deseninin bir koruyucu kapsamında ele alındığına, koruanın yalnızca son bir değil, **Tüm** desenlere uygulandığını unutmayın. Örneğin, aşağıdaki kod verildiğinde, koruma `when a > 12` `B a`hem hem de `A a` için geçerlidir:

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
