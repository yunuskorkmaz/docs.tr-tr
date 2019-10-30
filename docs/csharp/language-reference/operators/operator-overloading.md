---
title: İşleç aşırı yüklemesi C# -başvuru
description: Bir C# işlecin aşırı yüklenmesine ve hangi C# operatörlerin aşırı yüklenebilir olduğunu öğrenin.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 04c8731867e32ce1000a511c9ab36db554664a97
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038944"
---
# <a name="operator-overloading-c-reference"></a>İşleç aşırı yüklemesiC# (başvuru)

Kullanıcı tanımlı bir tür önceden tanımlanmış C# bir işleci aşırı yükleyebilir. Diğer bir deyişle, bir tür işlenenlerinin bir veya her ikisinin de o türden olması durumunda bir işlemin özel uygulamasını sağlayabilir. [Fazla yüklenebilir işleçler](#overloadable-operators) bölümünde hangi işleçlerin aşırı C# yüklenmiş olduğu gösterilmektedir.

Bir işleç bildirmek için `operator` anahtar sözcüğünü kullanın. Bir işleç bildiriminin aşağıdaki kuralları karşılaması gerekir:

- Hem `public` hem de `static` değiştiricisini içerir.
- Birli işlecin bir giriş parametresi vardır. İkili işlecin iki giriş parametresi vardır. Her durumda, en az bir parametre tür `T` veya `T?` olmalıdır; burada `T` işleç bildirimini içeren türdür.

Aşağıdaki örnek, bir Rational Number öğesini temsil eden Basitleştirilmiş yapıyı tanımlar. Yapı, [Aritmetik operatörlerin](arithmetic-operators.md)bazılarını aşırı yükler:

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

`int` ' den `Fraction`[örtük bir dönüştürme tanımlayarak](user-defined-conversion-operators.md) yukarıdaki örneği genişletebilirsiniz. Daha sonra, aşırı yüklenmiş işleçler bu iki türün bağımsız değişkenlerini destekleyecektir. Diğer bir deyişle, bir kesire tamsayı eklemek ve sonuç olarak bir kesir elde etmek mümkün olacaktır.

Ayrıca, özel bir tür dönüştürmesi tanımlamak için `operator` anahtar sözcüğünü kullanırsınız. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Fazla yüklenebilir işleçler

Aşağıdaki tabloda C# işleçlerin fazla gözlebilirlik hakkında bilgi verilmektedir:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Bu birli işleçler aşırı yüklenebilir.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), x [% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), x [^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \<\< y](bitwise-and-shift-operators.md#left-shift-operator-), x [> > y](bitwise-and-shift-operators.md#right-shift-operator-), x [= = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-), x [\< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)|Bu ikili işleçler aşırı yüklenebilir. Belirli operatörler çiftler halinde aşırı yüklenmiş olmalıdır; daha fazla bilgi için bu tabloyu izleyen nota bakın.|
|[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez. Ancak, aşırı yüklenmiş [`true` ve `false` işleçleriyle](true-false-operators.md) bir tür `&` ya da <code>&#124;</code> işlecini belirli bir şekilde aşırı yükiyorsa, sırasıyla `&&` veya <code>&#124;&#124;</code> işleci bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.|
|[bir&#91;i&#93;](member-access-operators.md#indexer-operator-)|Öğe erişimi aşırı yüklenebilir bir operatör olarak kabul edilmez, ancak bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md)tanımlayabilirsiniz.|
|[(T) x](type-testing-and-cast.md#cast-operator-)|Atama işleci aşırı yüklenemez, ancak yeni dönüştürme işleçleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [ &#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [@no__ t_22_](bitwise-and-shift-operators.md#compound-assignment)|Bileşik atama işleçleri açık olarak aşırı yüklenemez. Ancak, bir ikili işleci aşırı yüklerken, varsa buna karşılık gelen bileşik atama işleci de dolaylı olarak aşırı yüklenmiştir. Örneğin `+=`, aşırı yüklenmiş olabilecek `+`kullanılarak değerlendirilir.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-operator-), [c? t: f](conditional-operator.md), [x?? y](null-coalescing-operator.md), [x?? = y](null-coalescing-operator.md), [x. y](member-access-operators.md#range-operator-), [x-> y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-cast.md#as-operator), [await](await.md), [Checked](../keywords/checked.md), [denetimsiz](../keywords/unchecked.md), [varsayılan](default.md), [Delegate](delegate-operator.md) [,,,](type-testing-and-cast.md#is-operator) [NameOf](nameof.md), [New](new-operator.md), [ sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri çiftler halinde aşırı yüklenmiş olmalıdır. Diğer bir deyişle, bir çiftin işleci aşırı yüklenmişse, diğer işlecin da aşırı yüklenmesi gerekir. Böyle çiftler aşağıdaki gibidir:
>
> - `==` ve `!=` işleçleri
> - `<` ve `>` işleçleri
> - `<=` ve `>=` işleçleri

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [İşleç aşırı yüklemesi](~/_csharplang/spec/expressions.md#operator-overloading)
- [işleçler](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md)
- [Neden aşırı yüklenmiş işleçler ' de C#her zaman statiktir?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
