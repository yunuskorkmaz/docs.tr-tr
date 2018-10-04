---
title: Fazla yüklenebilir işleçler (C# programlama Kılavuzu)
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: f819e94fd532c10478ac39da9485126aa4380dd5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583106"
---
# <a name="overloadable-operators-c-programming-guide"></a>Fazla yüklenebilir işleçler (C# programlama Kılavuzu)

C# işleçleri kullanarak statik üye işlevleri tanımlayarak aşırı yüklemek kullanıcı tanımlı türler verir [işleci](../../language-reference/keywords/operator.md) anahtar sözcüğü. Tüm işleçler, ancak aşırı yüklenebilir ve bu tabloda listelendiği gibi diğer kısıtlamaları olan:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/logical-negation-operator.md), [~](../../language-reference/operators/bitwise-complement-operator.md), [++](../../language-reference/operators/increment-operator.md), [--](../../language-reference/operators/decrement-operator.md) , [true](../../language-reference/keywords/true.md), [false](../../language-reference/keywords/false.md)|Bu birli işleçler aşırı yüklenebilir.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/multiplication-operator.md), [/](../../language-reference/operators/division-operator.md), [%](../../language-reference/operators/modulus-operator.md), [&](../../language-reference/operators/and-operator.md), [&#124;](../../language-reference/operators/or-operator.md), [^](../../language-reference/operators/xor-operator.md), [\<\<](../../language-reference/operators/left-shift-operator.md), [>>](../../language-reference/operators/right-shift-operator.md)|Bu ikili işleçlerde aşırı yüklenebilir.|
|[==](../../language-reference/operators/equality-comparison-operator.md), [!=](../../language-reference/operators/not-equal-operator.md), [\<](../../language-reference/operators/less-than-operator.md), [>](../../language-reference/operators/greater-than-operator.md), [\<=](../../language-reference/operators/less-than-equal-operator.md), [>=](../../language-reference/operators/greater-than-equal-operator.md)|Karşılaştırma işleçleri aşırı yüklenebilir (ancak bu tablonun altındaki nota bakın).|
|[&&](../../language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../language-reference/operators/conditional-or-operator.md)|Koşullu mantıksal işleçler aşırı yüklenemez, ancak bunlar kullanılarak değerlendirilir `&` ve <code>&#124;</code>, hangi aşırı yüklenebilir.|
|[&#91;&#93;](../../language-reference/operators/index-operator.md)|Dizi dizin oluşturma işleci aşırı yüklenemez, ancak tanımlayabileceğiniz [dizin oluşturucular](../indexers/index.md).|
|[(T)x](../../language-reference/operators/invocation-operator.md)|Atama işleci aşırı yüklenemez, ancak yeni dönüştürme işleçleri tanımlayabilirsiniz (bkz [açık](../../language-reference/keywords/explicit.md) ve [örtük](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/multiplication-assignment-operator.md), [/=](../../language-reference/operators/division-assignment-operator.md), [%=](../../language-reference/operators/modulus-assignment-operator.md), [&=](../../language-reference/operators/and-assignment-operator.md), [&#124;=](../../language-reference/operators/or-assignment-operator.md), [^=](../../language-reference/operators/xor-assignment-operator.md), [\<\<=](../../language-reference/operators/left-shift-assignment-operator.md), [>>=](../../language-reference/operators/right-shift-assignment-operator.md)|Atama İşleçleri açıkça aşırı yüklenmiş olamaz. İkili İşleç aşırı yükleme, ancak karşılık gelen atama işleci, varsa, ayrıca örtük olarak aşırı yüklenmiş andır. Örneğin, `+=` kullanarak değerlendirilir `+`, hangi aşırı yüklenebilir.|
|[=](../../language-reference/operators/assignment-operator.md), [.](../../language-reference/operators/member-access-operator.md), [?:](../../language-reference/operators/conditional-operator.md), [??](../../language-reference/operators/null-coalescing-operator.md), [->](../../language-reference/operators/dereference-operator.md), [=>](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/invocation-operator.md), [as](../../language-reference/keywords/as.md), [checked](../../language-reference/keywords/checked.md), [unchecked](../../language-reference/keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../language-reference/keywords/is.md), [new](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/keywords/typeof.md)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri aşırı, çiftlerinde aşırı gerekir; diğer bir deyişle, `==` aşırı yüklendi `!=` da aşırı yüklenmiş gerekir. Tersi de aşırı yükleme olduğunda true ise `!=` için aşırı yükleme gerektirir `==`. Karşılaştırma işleçleri için aynı geçerlidir `<` ve `>` ve `<=` ve `>=`.

Bir işleç aşırı yüklemesi hakkında daha fazla bilgi için bkz: [işleci](../../language-reference/keywords/operator.md) anahtar sözcüğü makalesi.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Deyimler, İfadeler ve İşleçler](index.md)
- [İşleçler](operators.md)
- [C# İşleçleri](../../language-reference/operators/index.md)  
- [Neden aşırı yüklenmiş işleçler her zaman C# ' de statik misiniz?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
