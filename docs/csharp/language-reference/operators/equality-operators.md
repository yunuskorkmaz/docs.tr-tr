---
title: Eşitlik işleçleri- C# başvuru
description: Eşitlik karşılaştırma C# işleçleri ve C# tür eşitlik hakkında bilgi edinin.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 14bb8227a4a6c8beff6ab04c58d8e1a43db69856
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093142"
---
# <a name="equality-operators-c-reference"></a>Eşitlik işleçleri (C# başvuru)

[`==` (eşitlik)](#equality-operator-) ve [`!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenlerinin eşit olup olmadığını denetler.

## <a name="equality-operator-"></a>Eşitlik işleci = =

`==` eşitlik işleci, işlenenleri eşitse `true` döndürür `false` Aksi takdirde.

### <a name="value-types-equality"></a>Değer türleri eşitlik

[Yerleşik değer türlerinin](../builtin-types/value-types.md#built-in-value-types) işlenenleri, değerleri eşitse eşittir:

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> `==`, [`<`, `>`, `<=`ve `>=`](comparison-operators.md) işleçleri için, işlenenlerin herhangi biri bir sayı değilse (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucu `false`olur. Diğer bir deyişle, `NaN` değeri, `NaN`dahil herhangi bir `double` (veya `float`) değerinden daha fazla, daha küçüktür veya eşit değildir. Daha fazla bilgi ve örnek için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.

Temeldeki integral türünün karşılık gelen değerleri eşitse aynı [sabit listesi](../builtin-types/enum.md) türünün iki işleneni eşittir.

Kullanıcı tanımlı [Yapı](../keywords/struct.md) türleri, varsayılan olarak `==` işlecini desteklemez. `==` işlecini desteklemek için Kullanıcı tanımlı bir yapının onu [tekrar yüklemesi](operator-overloading.md) gerekir.

7,3 ile C# başlayarak, `==` ve `!=` işleçleri C# [diziler](../../tuples.md)tarafından desteklenir. Daha fazla bilgi için [ C# demet türleri](../../tuples.md) makalesinin [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümüne bakın.

### <a name="reference-types-equality"></a>Başvuru türleri eşitliği

Varsayılan olarak, iki başvuru türü işlenen aynı nesneye başvurduklarında eşittir:

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

Örnekte gösterildiği gibi, Kullanıcı tanımlı başvuru türleri varsayılan olarak `==` işlecini destekler. Ancak, bir başvuru türü `==` işlecini aşırı yükleyebilir. Bir başvuru türü `==` işlecini aşırı yükle, bu türden iki başvurunun aynı nesneye başvurmasını denetlemek için <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemini kullanın.

### <a name="string-equality"></a>Dize eşitlik

İki [dize](../builtin-types/reference-types.md#the-string-type) işleneni her ikisi de `null` veya her iki dize örneği de aynı uzunluktadır ve her bir karakter konumunda aynı karakterlere sahip olduğunda eşittir:

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

Bu, büyük/küçük harfe duyarlı bir sıra karşılaştırmasına sahiptir. Dize karşılaştırması hakkında daha fazla bilgi için bkz. [dizeleri C#karşılaştırma ](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Temsilci eşitlik

Aynı çalışma zamanı türünün iki [temsilci](../../programming-guide/delegates/index.md) işleneni, her ikisi de `null`, ya da çağrı listeleri aynı uzunluktadır ve her konumda eşit girdilere sahip olduğunda eşittir:

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçlerini devretmek](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.

Anlamsal olarak özdeş [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirmesinden üretilen temsilciler, aşağıdaki örnekte gösterildiği gibi eşit değildir:

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Eşitsizlik işleci! =

Eşitsizlik işleci `!=`, işlenenleri eşit değilse `true` döndürür `false` Aksi takdirde. [Yerleşik türlerin](../builtin-types/built-in-types.md)işlenenleri için ifade `x != y`, ifade `!(x == y)`aynı sonucu üretir. Tür eşitliği hakkında daha fazla bilgi için [eşitlik işleci](#equality-operator-) bölümüne bakın.

Aşağıdaki örnek `!=` işlecinin kullanımını gösterir:

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `==` ve `!=` işleçlerini [aşırı](operator-overloading.md) yükleyebilir. Bir tür iki işleçten birini aşırı yüklediğinden, başka bir tane de aşırı yüklemesi gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Eşitlik karşılaştırmaları](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Karşılaştırma işleçleri](comparison-operators.md)
