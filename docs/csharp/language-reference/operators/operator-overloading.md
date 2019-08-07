---
title: İşleç aşırı yüklemesi C# -başvuru
description: Bir C# işlecin aşırı yüklenmesine ve hangi C# operatörlerin aşırı yüklenebilir olduğunu öğrenin.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: da1e47d7ebdf91084d94fc895f0ce46d773353d7
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796573"
---
# <a name="operator-overloading-c-reference"></a>İşleç aşırı yüklemesiC# (başvuru)

Kullanıcı tanımlı bir tür önceden tanımlanmış C# bir işleci aşırı yükleyebilir. Diğer bir deyişle, bir tür, bir veya her iki işlenen bu türden olduğunda bir işlemin özel uygulamasını sağlayabilir. [Fazla yüklenebilir işleçler](#overloadable-operators) bölümünde hangi işleçlerin aşırı C# yüklenmiş olduğu gösterilmektedir.

Bir işleç bildirmek için anahtarsözcüğünükullanın.`operator` Bir işleç bildiriminin aşağıdaki kuralları karşılaması gerekir:

- Hem a `public` `static` hem de değiştirici içerir.
- Birli operatör bir parametre alır. İkili işleç iki parametre alır. Her durumda, en az bir parametre türünde `T` `T` veya `T?` işleç bildirimini içeren tür olmalıdır.

Aşağıdaki örnek, bir Rational Number öğesini temsil eden Basitleştirilmiş yapıyı tanımlar. Yapı, [Aritmetik operatörlerin](arithmetic-operators.md)bazılarını aşırı yükler:

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

' Den ' den `int` `Fraction`örtük bir dönüştürme tanımlayarak yukarıdaki örneği genişletebilirsiniz. Daha sonra, aşırı yüklenmiş işleçler bu iki türün bağımsız değişkenlerini destekleyecektir. Diğer bir deyişle, bir kesire tamsayı eklemek ve sonuç olarak bir kesir elde etmek mümkün olacaktır.

Özel bir tür dönüştürmesi `operator` tanımlamak için anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Fazla yüklenebilir işleçler

Aşağıdaki tabloda C# işleçlerin fazla gözlebilirlik hakkında bilgi verilmektedir:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [](true-false-operators.md) [](true-false-operators.md) , [--](arithmetic-operators.md#decrement-operator---)doğru, yanlış|Bu birli işleçler aşırı yüklenebilir.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-) , [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-),[>=](comparison-operators.md#greater-than-or-equal-operator-)|Bu ikili işleçler aşırı yüklenebilir. Belirli operatörler çiftler halinde aşırı yüklenmiş olmalıdır; daha fazla bilgi için bu tabloyu izleyen nota bakın.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez. Ancak, aşırı yüklenmiş [ `true` ve `false` işleçlere](true-false-operators.md) sahip bir tür `&` ya <code>&#124;</code> da işlecini belirli bir şekilde `&&` aşırı yükleiyorsa, sırasıyla veya <code>&#124;&#124;</code> işleci için değerlendirilebilir Bu türün işlenenleri. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|Öğe erişimi aşırı yüklenebilir bir operatör olarak kabul edilmez, ancak bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md)tanımlayabilirsiniz.|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|Atama işleci aşırı yüklenemez, ancak yeni dönüştürme işleçleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Bileşik atama işleçleri açık olarak aşırı yüklenemez. Ancak, bir ikili işleci aşırı yüklerken, varsa buna karşılık gelen bileşik atama işleci de dolaylı olarak aşırı yüklenmiştir. Örneğin, `+=` kullanılarak `+`değerlendirilir, aşırı yüklenmiş olabilir.|
|[=](assignment-operator.md), [.](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [??](null-coalescing-operator.md), [->](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-conversion-operators.md#as-operator), [Checked](../keywords/checked.md), [denetimsiz](../keywords/unchecked.md), [varsayılan](default.md), [temsilci](delegate-operator.md),,, [NameOf](nameof.md), [New](new-operator.md), [](type-testing-and-conversion-operators.md#is-operator) [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri çiftler halinde aşırı yüklenmiş olmalıdır. Diğer bir deyişle, bir çiftin işleci aşırı yüklenmişse, diğer işlecin da aşırı yüklenmesi gerekir. Böyle çiftler aşağıdaki gibidir:
>
> - `==`ve `!=` işleçleri
> - `<`ve `>` işleçleri
> - `<=`ve `>=` işleçleri

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [İşleç aşırı yüklemesi](~/_csharplang/spec/expressions.md#operator-overloading)
- [İşleçler](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md)
- [Neden aşırı yüklenmiş işleçler ' de C#her zaman statiktir?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
