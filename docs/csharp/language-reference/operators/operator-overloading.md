---
title: İşleç aşırı yüklemesi - C# başvurusu
description: Aşırı yükleme öğrenin bir C# işleci ve hangi C# işleçleri aşırı yüklenebilir.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: e225acedde5f097fd12680080c7f6b242e882b04
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235925"
---
# <a name="operator-overloading-c-reference"></a>İşleç aşırı yüklemesi (C# Başvurusu)

Kullanıcı tanımlı bir tür önceden tanımlanmış bir aşırı C# işleci. Diğer bir deyişle, bir tür bir işlem özel uygulanışı sağlayabilir veya her iki işlenen de bu türüdür. [Fazla yüklenebilir işleçler](#overloadable-operators) bölüm gösterir, C# işleçleri aşırı yüklenebilir.

Kullanım `operator` bir işleç bildirmek için anahtar sözcüğü. İşleç bildirimi, aşağıdaki kurallar karşılamanız gerekir:

- Her ikisini de içeren bir `public` ve `static` değiştiricisi.
- Birli işleci bir parametre alır. Bir ikili işleci iki parametre alır. Her durumda en az bir parametre türüne sahip olmalıdır `T` veya `T?` burada `T` işleç bildirimi içeren türüdür.

Aşağıdaki örnek, bir rasyonel sayıyı temsil etmek için basitleştirilmiş bir yapı tanımlar. Yapı bazı aşırı yüklemeler [aritmetik işleçler](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

Yukarıdaki örnekte örtük bir dönüştürme tanımlayarak genişletebilirsiniz `int` için `Fraction`. Ardından, aşırı yüklenmiş işleçler, bu iki tür bağımsız değişkenleri destekleyecektir. Diğer bir deyişle, bir kesir olarak bir tamsayı eklemek ve bir sonuç olarak elde mümkün olacak.

Ayrıca `operator` anahtar sözcüğü, bir özel tür dönüştürme tanımlamak için. Daha fazla bilgi için [kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Fazla yüklenebilir işleçler

Aşağıdaki tabloda overloadability hakkında bilgi sağlar C# işleçleri:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---) , [true](true-false-operators.md), [false](true-false-operators.md)|Bu birli işleçler aşırı yüklenebilir.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [& ](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-), [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-), [>=](comparison-operators.md#greater-than-or-equal-operator-)|Bu ikili işleçlerde aşırı yüklenebilir. Belirli çiftler halinde aşırı yüklenmiş işleçler gerekir; Daha fazla bilgi için bu tablonun altındaki nota bakın.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Koşullu mantıksal işleçler aşırı yüklenemez. Ancak, aşırı yüklenmiş sahip bir tür, [ `true` ve `false` işleçleri](true-false-operators.md) de aşırı `&` veya <code>&#124;</code> işleci belirli bir şekilde `&&` veya <code>&#124;&#124;</code> işleci Sırasıyla, o türündeki işlenenler için değerlendirilir. Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|Bir aşırı yüklenebilir işleç öğe erişimi dikkate alınmaz, ancak tanımlayabileceğiniz bir [dizin oluşturucu](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|Atama işleci aşırı yüklenemez, ancak yeni dönüştürme işleçleri tanımlayabilirsiniz. Daha fazla bilgi için [kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Bileşik atama işleçleri açıkça aşırı yüklenemez. İkili bir işleç aşırı yüklemesi, ancak karşılık gelen bileşik atama işleci, varsa, ayrıca örtük olarak aşırı yüklenmiş andır. Örneğin, `+=` kullanarak değerlendirilir `+`, hangi aşırı yüklenebilir.|
|[=](assignment-operator.md), [. ](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [?? ](null-coalescing-operator.md), [ -> ](pointer-related-operators.md#pointer-member-access-operator--), [ => ](lambda-operator.md), [f(x)](member-access-operators.md#invocation-operator-), [olarak](type-testing-and-conversion-operators.md#as-operator), [işaretli ](../keywords/checked.md), [denetlenmeyen](../keywords/unchecked.md), [varsayılan](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [temsilci](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [olduğu](type-testing-and-conversion-operators.md#is-operator), [nameof](nameof.md), [yeni](new-operator.md), [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Bu işleçler aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri çiftler halinde aşırı gerekir. Çifti ya da İşleç aşırı yüklenmişse, diğer bir deyişle, diğer işleci de aşırı gerekir. Bu tür çiftleri aşağıdaki gibidir:
>
> - `==` ve `!=` işleçleri
> - `<` ve `>` işleçleri
> - `<=` ve `>=` işleçleri

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [İşleç aşırı yüklemesi](~/_csharplang/spec/expressions.md#operator-overloading)
- [İşleçler](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md)
- [Neden aşırı yüklenmiş işleçler her zaman C# ' de statik misiniz?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
