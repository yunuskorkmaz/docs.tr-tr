---
title: Fazla yüklenebilir işleçler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: 104473c9659205258d8e160ce0820119a4108471
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301357"
---
# <a name="overloadable-operators-c-programming-guide"></a>Fazla yüklenebilir işleçler (C# programlama Kılavuzu)

C# işleçleri kullanarak statik üye işlevleri tanımlayarak aşırı yüklemek kullanıcı tanımlı türler verir [işleci](../../language-reference/keywords/operator.md) anahtar sözcüğü. Tüm işleçler, ancak aşırı yüklenebilir ve bu tabloda listelendiği gibi diğer kısıtlamaları olan:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-), [~](../../language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](../../language-reference/operators/arithmetic-operators.md#increment-operator-), [--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---), [true](../../language-reference/operators/true-false-operators.md), [false](../../language-reference/operators/true-false-operators.md)|Bu birli işleçler aşırı yüklenebilir.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-), [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-), [^](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](../../language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-), [>>](../../language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-)|Bu ikili işleçlerde aşırı yüklenebilir.|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/comparison-operators.md#less-than-operator-), [>](../../language-reference/operators/comparison-operators.md#greater-than-operator-), [\<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-), [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-)|Karşılaştırma işleçleri aşırı yüklenebilir (ancak bu tablonun altındaki nota bakın).|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez, ancak bunlar kullanılarak değerlendirilir `&` ve <code>&#124;</code>, hangi aşırı yüklenebilir.|
|[&#91;&#93;](../../language-reference/operators/member-access-operators.md#indexer-operator-)|Dizi dizin oluşturma işleci aşırı yüklenemez, ancak tanımlayabileceğiniz [dizin oluşturucular](../indexers/index.md).|
|[(T)x](../../language-reference/operators/invocation-operator.md)|Atama işleci aşırı yüklenemez, ancak yeni dönüştürme işleçleri tanımlayabilirsiniz (bkz [açık](../../language-reference/keywords/explicit.md) ve [örtük](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [-=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [\<\<=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|Atama İşleçleri açıkça aşırı yüklenmiş olamaz. İkili İşleç aşırı yükleme, ancak karşılık gelen atama işleci, varsa, ayrıca örtük olarak aşırı yüklenmiş andır. Örneğin, `+=` kullanarak değerlendirilir `+`, hangi aşırı yüklenebilir.|
|[=](../../language-reference/operators/assignment-operator.md), [.](../../language-reference/operators/member-access-operators.md#member-access-operator-), [?:](../../language-reference/operators/conditional-operator.md), [??](../../language-reference/operators/null-coalescing-operator.md), [->](../../language-reference/operators/pointer-related-operators.md#pointer-member-access-operator--), [=>](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/member-access-operators.md#invocation-operator-), [as](../../language-reference/keywords/as.md), [checked](../../language-reference/keywords/checked.md), [unchecked](../../language-reference/keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../language-reference/keywords/is.md), [new](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/keywords/typeof.md)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri aşırı, çiftlerinde aşırı gerekir; diğer bir deyişle, `==` aşırı yüklendi `!=` da aşırı yüklenmiş gerekir. Tersi de aşırı yükleme olduğunda true ise `!=` için aşırı yükleme gerektirir `==`. Karşılaştırma işleçleri için aynı geçerlidir `<` ve `>` ve `<=` ve `>=`.

Bir işleç aşırı yüklemesi hakkında daha fazla bilgi için bkz: [işleci](../../language-reference/keywords/operator.md) anahtar sözcüğü makalesi.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Deyimler, İfadeler ve İşleçler](index.md)
- [İşleçler](operators.md)
- [C# İşleçleri](../../language-reference/operators/index.md)
- [Neden aşırı yüklenmiş işleçler her zaman C# ' de statik misiniz?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
