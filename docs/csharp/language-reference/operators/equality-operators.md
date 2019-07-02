---
title: Eşitlik işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# eşitlik Karşılaştırma işleçleri ve C# eşitlik yazın.
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
ms.openlocfilehash: cd14b51daee12e8de18586b262bdf2928bffbdc2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504014"
---
# <a name="equality-operators-c-reference"></a>Eşitlik işleçleri (C# Başvurusu)

[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenleri eşit olup olmadığını denetleyin.

## <a name="equality-operator-"></a>Eşitlik işleci ==

Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.

### <a name="value-types-equality"></a>Değer türleri eşitlik

İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> İçin `==`, [ `<`, `>`, `<=`, ve `>=` ](comparison-operators.md) herhangi işlenenden değilse, birkaç işleçleri (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucunu olduğu`false`. Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`. Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.

İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.

Kullanıcı tanımlı [yapı](../keywords/struct.md) türleri desteklemez `==` varsayılan işleci. Desteklemek için `==` işleci, bir kullanıcı tarafından tanımlanan yapı gerekir [aşırı](#operator-overloadability) bu.

İle başlayarak C# 7.3, `==` ve `!=` işleçleri tarafından desteklenen C# [diziler](../../tuples.md). Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.

### <a name="reference-types-equality"></a>Başvuru türleri eşitlik

Varsayılan olarak, iki başvuru türü işlenen, bunlar aynı nesneye başvuruyorsa eşitse:

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

Örnekte gösterildiği gibi destek kullanıcı tarafından tanımlanan başvuru türleri `==` varsayılan işleci. Ancak, bir başvuru türü aşırı yüklenebilir `==` işleci. Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.

### <a name="string-equality"></a>Dize eşitliği

İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

Büyük/küçük harfe sıralı karşılaştırma olmasıdır. Dize karşılaştırması hakkında daha fazla bilgi için bkz: [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Temsilci eşitlik

İki [temsilci](../../programming-guide/delegates/index.md) işlenenler aynı çalışma zamanı tür, bunların her ikisi de eşit `null` veya çağırma listelerini aynı uzunluktadır ve her konumda eşit girdiniz:

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

Daha fazla bilgi için [temsilci eşitlik işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

Anlamsal olarak özdeş bir değerlendirmesinden gelen üretilen Temsilciler [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi eşit değilse:

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Eşitsizlik işleci! =

Eşitsizlik işleci `!=` döndürür `true` işlenenleri eşit değilse `false` Aksi takdirde. İşlenen için [yerleşik türler](../keywords/built-in-types-table.md), ifade `x != y` ifade aynı sonucu üretir `!(x == y)`. Tür eşitlik hakkında daha fazla bilgi için bkz: [eşitlik işleci](#equality-operator-) bölümü.

Aşağıdaki örnek, kullanımını gösterir. `!=` işleci:

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `==` ve `!=` işleçleri. Bir tür iki işleçlerden aşırı de başka bir aşırı gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Eşitlik karşılaştırmaları](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Karşılaştırma işleçleri](comparison-operators.md)
