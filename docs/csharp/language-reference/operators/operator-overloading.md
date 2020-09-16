---
title: İşleç aşırı yüklemesi-C# başvurusu
description: C# işlecinin nasıl aşırı yükleneceğini ve hangi C# işleçlerinin aşırı yüklenebilir olduğunu öğrenin.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 65f417c06886c32da8057ae612043b95c31a31bd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536424"
---
# <a name="operator-overloading-c-reference"></a>İşleç aşırı yüklemesi (C# Başvurusu)

Kullanıcı tanımlı bir tür, önceden tanımlanmış bir C# işlecini aşırı yükleyebilir. Diğer bir deyişle, bir tür işlenenlerinin bir veya her ikisinin de o türden olması durumunda bir işlemin özel uygulamasını sağlayabilir. [Fazla yüklenebilir işleçler](#overloadable-operators) bölümünde hangi C# işleçleri aşırı yüklenebilir.

`operator`Bir işleç bildirmek için anahtar sözcüğünü kullanın. Bir işleç bildiriminin aşağıdaki kuralları karşılaması gerekir:

- Hem a hem de `public` değiştirici içerir `static` .
- Birli işlecin bir giriş parametresi vardır. İkili işlecin iki giriş parametresi vardır. Her durumda, en az bir parametre türünde `T` veya `T?` `T` işleç bildirimini içeren tür olmalıdır.

Aşağıdaki örnek, bir Rational Number öğesini temsil eden Basitleştirilmiş yapıyı tanımlar. Yapı, [Aritmetik operatörlerin](arithmetic-operators.md)bazılarını aşırı yükler:

[!code-csharp[fraction example](snippets/shared/OperatorOverloading.cs)]

' Den ' den [örtük bir dönüştürme tanımlayarak](user-defined-conversion-operators.md) yukarıdaki örneği genişletebilirsiniz `int` `Fraction` . Daha sonra, aşırı yüklenmiş işleçler bu iki türün bağımsız değişkenlerini destekleyecektir. Diğer bir deyişle, bir kesire tamsayı eklemek ve sonuç olarak bir kesir elde etmek mümkün olacaktır.

`operator`Özel bir tür dönüştürmesi tanımlamak için anahtar sözcüğünü de kullanabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Fazla yüklenebilir işleçler

Aşağıdaki tabloda, C# işleçlerinin fazla gözlebilirlik hakkında bilgi verilmektedir:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-) , [--](arithmetic-operators.md#decrement-operator---) , [true](true-false-operators.md), [false](true-false-operators.md)|Bu birli işleçler aşırı yüklenebilir.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \<\< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-), [x = = y](equality-operators.md#equality-operator-), x [! = y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)|Bu ikili işleçler aşırı yüklenebilir. Belirli operatörler çiftler halinde aşırı yüklenmiş olmalıdır; daha fazla bilgi için bu tabloyu izleyen nota bakın.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez. Ancak, aşırı yüklenmiş [ `true` ve `false` işleçlere](true-false-operators.md) sahip bir tür `&` ya da işlecini belirli bir şekilde aşırı yükleiyorsa, <code>&#124;</code> `&&` sırasıyla or <code>&#124;&#124;</code> işleci bu türün işlenenleri için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.|
|[bir&#91;&#93;](member-access-operators.md#indexer-operator-), [`a?[i]`](member-access-operators.md#null-conditional-operators--and-)|Öğe erişimi aşırı yüklenebilir bir operatör olarak kabul edilmez, ancak bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md)tanımlayabilirsiniz.|
|[(T) x](type-testing-and-cast.md#cast-expression)|Atama işleci aşırı yüklenemez, ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment) , [\*=](arithmetic-operators.md#compound-assignment) , [/=](arithmetic-operators.md#compound-assignment) , [%=](arithmetic-operators.md#compound-assignment) , [&=](boolean-logical-operators.md#compound-assignment) , [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment) , [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Bileşik atama işleçleri açık olarak aşırı yüklenemez. Ancak, bir ikili işleci aşırı yüklerken, varsa buna karşılık gelen bileşik atama işleci de dolaylı olarak aşırı yüklenmiştir. Örneğin, `+=` kullanılarak değerlendirilir `+` , aşırı yüklenmiş olabilir.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-expression-), [`x?.y`](member-access-operators.md#null-conditional-operators--and-) , [c? t: f](conditional-operator.md), [x?? y](null-coalescing-operator.md), [x?? = y](null-coalescing-operator.md), [x. y](member-access-operators.md#range-operator-), [x->y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md) , [f (x)](member-access-operators.md#invocation-expression-), [as](type-testing-and-cast.md#as-operator), [await](await.md), [Checked](../keywords/checked.md), [denetimsiz](../keywords/unchecked.md), [Default](default.md), [Delegate](delegate-operator.md), [,](type-testing-and-cast.md#is-operator), [NameOf](nameof.md), [New](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [Switch](switch-expression.md), [typeof](type-testing-and-cast.md#typeof-operator)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri çiftler halinde aşırı yüklenmiş olmalıdır. Diğer bir deyişle, bir çiftin işleci aşırı yüklenmişse, diğer işlecin da aşırı yüklenmesi gerekir. Böyle çiftler aşağıdaki gibidir:
>
> - `==` ve `!=` işleçleri
> - `<` ve `>` işleçleri
> - `<=` ve `>=` işleçleri

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [İşleç aşırı yüklemesi](~/_csharplang/spec/expressions.md#operator-overloading)
- [İşleçler](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md)
- [Tasarım yönergeleri-Işleç aşırı yüklemeleri](../../../standard/design-guidelines/operator-overloads.md)
- [Tasarım yönergeleri-eşitlik işleçleri](../../../standard/design-guidelines/equality-operators.md)
- [Neden aşırı yüklenmiş işleçler C# ' de her zaman statiktir?](/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
