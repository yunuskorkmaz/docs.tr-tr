---
title: İşleç aşırı yüklemesi C# -başvuru
description: Bir C# işlecin aşırı yüklenmesine ve hangi C# operatörlerin aşırı yüklenebilir olduğunu öğrenin.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 130eb4be66d13b43e5605ef98a647fa9f4223014
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116088"
---
# <a name="operator-overloading-c-reference"></a>İşleç aşırı yüklemesiC# (başvuru)

Kullanıcı tanımlı bir tür önceden tanımlanmış C# bir işleci aşırı yükleyebilir. Diğer bir deyişle, bir tür işlenenden biri veya her ikisi bu türden olduğunda bir işlemin özel uygulamasını sağlayabilir. [Fazla yüklenebilir işleçler](#overloadable-operators) bölümünde hangi işleçlerin aşırı C# yüklenmiş olduğu gösterilmektedir.

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
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Bu birli işleçler aşırı yüklenebilir.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x > > y](bitwise-and-shift-operators.md#right-shift-operator-), [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)|Bu ikili işleçler aşırı yüklenebilir. Belirli operatörler çiftler halinde aşırı yüklenmiş olmalıdır; daha fazla bilgi için bu tabloyu izleyen nota bakın.|
|[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez. Ancak, aşırı yüklenmiş [ `true` ve `false` işleçlere](true-false-operators.md) sahip bir tür `&` ya <code>&#124;</code> da işlecini belirli bir şekilde `&&` aşırı yükleiyorsa, sırasıyla veya <code>&#124;&#124;</code> işleci için değerlendirilebilir Bu türün işlenenleri. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.|
|[bir&#91;i&#93;](member-access-operators.md#indexer-operator-)|Öğe erişimi aşırı yüklenebilir bir operatör olarak kabul edilmez, ancak bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md)tanımlayabilirsiniz.|
|[(T)x](type-testing-and-cast.md#cast-operator-)|Atama işleci aşırı yüklenemez, ancak yeni dönüştürme işleçleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Bileşik atama işleçleri açık olarak aşırı yüklenemez. Ancak, bir ikili işleci aşırı yüklerken, varsa buna karşılık gelen bileşik atama işleci de dolaylı olarak aşırı yüklenmiştir. Örneğin, `+=` kullanılarak `+`değerlendirilir, aşırı yüklenmiş olabilir.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-operator-), [c? t: f](conditional-operator.md), [x?? y](null-coalescing-operator.md), [x?? = y](null-coalescing-operator.md), [x. y](member-access-operators.md#range-operator-), [x-> y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-cast.md#as-operator), [await](await.md), [Checked](../keywords/checked.md), [denetimsiz](../keywords/unchecked.md), [varsayılan](default.md), [Delegate](delegate-operator.md) [,,,](type-testing-and-cast.md#is-operator) [NameOf](nameof.md), [New](new-operator.md), [sizeof ](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Bu işleçler aşırı yüklenemez.|

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
