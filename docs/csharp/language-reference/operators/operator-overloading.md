---
title: Operatör aşırı yüklemesi - C# referansı
description: C# işlecinin nasıl aşırı yüklenebilir olduğunu ve hangi C# işleçlerinin aşırı yüklenebildiğini öğrenin.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: cdb35b212d5bfc4cc685fbfd6c294066983709df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847306"
---
# <a name="operator-overloading-c-reference"></a>Operatör aşırı yüklemesi (C# referansı)

Kullanıcı tanımlı bir tür, önceden tanımlanmış bir C# işlecinin aşırı yüklenmesi olabilir. Diğer bir deyişle, bir tür, operands biri veya her ikisi bu tür olması durumunda bir işlemin özel uygulama sağlayabilir. [Aşırı Yüklenebilir işleçler](#overloadable-operators) bölümü, hangi C# işleçlerin aşırı yüklenebilir olduğunu gösterir.

İşleç bildirmek için `operator` anahtar sözcüğü kullanın. İşleç bildirimi aşağıdaki kuralları karşılamalıdır:

- Hem bir `public` hem `static` de bir değiştirici içerir.
- Unary işlecinin bir giriş parametresi vardır. Bir ikili işleç iki giriş parametrevardır. Her durumda, en az bir parametre `T?` `T` türüne `T` veya işleç bildirimini içeren tür nerede olmalıdır.

Aşağıdaki örnek, rasyonel bir sayıyı temsil etmek için basitleştirilmiş bir yapı tanımlar. Yapı bazı [aritmetik işleçleri](arithmetic-operators.md)aşırı yükler:

[!code-csharp[fraction example](snippets/OperatorOverloading.cs)]

Örtük [bir dönüştürmeyi](user-defined-conversion-operators.md) 'den `int` ' e `Fraction`doğru tanımlayarak önceki örneği genişletebilirsiniz. Daha sonra, aşırı yüklenen işleçler bu iki tür bağımsız değişkenleri destekler. Diğer bir deyişle, bir kesir için bir tamsayı eklemek ve sonuç olarak bir kesir elde etmek mümkün olacaktır.

Özel tür `operator` dönüştürmesini tanımlamak için anahtar sözcüğü de kullanırsınız. Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](user-defined-conversion-operators.md)

## <a name="overloadable-operators"></a>Aşırı yüklenebilir operatörler

Aşağıdaki tablo, C# işleçlerinin aşırı yüklenebilirliği hakkında bilgi sağlar:

| İşleçler | Aşırı yüklenebilirlik |
| --------- | --------------- |
|[+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [!x](boolean-logical-operators.md#logical-negation-operator-) [--](arithmetic-operators.md#decrement-operator---), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), , [doğru](true-false-operators.md), [yanlış](true-false-operators.md)|Bu unary işleçleri aşırı yüklenebilir.|
|[x + y](addition-operator.md), [x - y](subtraction-operator.md), x [ \* y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), x % [y](arithmetic-operators.md#remainder-operator-), x [& y](boolean-logical-operators.md#logical-and-operator-), x [&#124; y](boolean-logical-operators.md#logical-or-operator-), x ^ [y](boolean-logical-operators.md#logical-exclusive-or-operator-), [ \< \< x y](bitwise-and-shift-operators.md#left-shift-operator-), x >> [y](bitwise-and-shift-operators.md#right-shift-operator-), x [== y](equality-operators.md#equality-operator-), x [== y](equality-operators.md#inequality-operator-), x y , x [ \<y](comparison-operators.md#less-than-or-equal-operator-), [>](comparison-operators.md#greater-than-operator-) [x \< ](comparison-operators.md#less-than-operator-)= y , x = y , x >>= [y](comparison-operators.md#greater-than-or-equal-operator-)|Bu ikili işleçler aşırı yüklenebilir. Bazı işleçler çiftler halinde aşırı yüklenmelidir; daha fazla bilgi için bu tabloyu izleyen nota bakın.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez. Ancak, aşırı `&` yüklü <code>&#124;</code> `&&` [ `true` ve `false` işleçli](true-false-operators.md) bir tür de belirli bir şekilde veya işleci aşırı yüklerse, sırasıyla veya <code>&#124;&#124;</code> işleci, bu tür operands için değerlendirilebilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı koşullu mantıksal işleçleri](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.|
|[bir&#91;i&#93;](member-access-operators.md#indexer-operator-)|Öğe erişimi aşırı yüklenebilir işleç olarak kabul edilmez, ancak bir [dizinleyici](../../programming-guide/indexers/index.md)tanımlayabilirsiniz.|
|[(T)x](type-testing-and-cast.md#cast-operator-)|Döküm işleci aşırı yüklenemez, ancak yeni dönüşüm işleçleri tanımlayabilirsiniz. Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](user-defined-conversion-operators.md)|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment) [ \* ](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment) [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), , [^=](boolean-logical-operators.md#compound-assignment) [ \< \< ](bitwise-and-shift-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), , ,[>>=](bitwise-and-shift-operators.md#compound-assignment)|Bileşik atama işleçleri açıkça aşırı yüklenemez. Ancak, bir ikili işleci aşırı yüklediğinizde, ilgili bileşik atama işleci, varsa, aynı zamanda örtülü olarak aşırı yüklenir. Örneğin, `+=` aşırı yüklenebilir `+`, kullanılarak değerlendirilir.|
|[^x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x.y](member-access-operators.md#member-access-operator-), [c ? t : f](conditional-operator.md), x ?? [y](null-coalescing-operator.md), [x ?? = y](null-coalescing-operator.md), [x. y](member-access-operators.md#range-operator-), [x->y](pointer-related-operators.md#pointer-member-access-operator--) [=>](lambda-operator.md), , [f(x)](member-access-operators.md#invocation-operator-), [olarak](type-testing-and-cast.md#as-operator), [bekliyor](await.md), [kontrol ,](../keywords/checked.md) [işaretsiz](../keywords/unchecked.md), [varsayılan](default.md), [temsilci](delegate-operator.md), [is](type-testing-and-cast.md#is-operator) [, nameof](nameof.md), [yeni](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri çiftler halinde aşırı yüklenmelidir. Diğer bir deyişle, bir çiftin her iki işleci de aşırı yüklüyse, diğer işleç de aşırı yüklenmiş olmalıdır. Bu çiftler aşağıdaki gibidir:
>
> - `==`ve `!=` operatörler
> - `<`ve `>` operatörler
> - `<=`ve `>=` operatörler

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Operatör aşırı yükleme](~/_csharplang/spec/expressions.md#operator-overloading)
- [İşleçler](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md)
- [Tasarım yönergeleri - Operatör aşırı yükleri](../../../standard/design-guidelines/operator-overloads.md)
- [Tasarım yönergeleri - Eşitlik operatörleri](../../../standard/design-guidelines/equality-operators.md)
- [Aşırı yüklü operatörler neden C#'da her zaman statiktir?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
