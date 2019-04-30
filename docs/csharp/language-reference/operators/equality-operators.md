---
title: Eşitlik işleçleri - C# başvurusu
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 297285ccb9aba7eae1d70a7d28a62241646a023c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689391"
---
# <a name="equality-operators-c-reference"></a>Eşitlik işleçleri (C# Başvurusu)

[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenleri eşit olup olmadığını denetleyin.

## <a name="equality-operator-"></a>Eşitlik işleci ==

Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.

### <a name="value-types-equality"></a>Değer türleri eşitlik

İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> Eşitlik ve operatörler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlem sonucu `false`. Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`. Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.

İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.

Kullanıcı tanımlı [yapı](../keywords/struct.md) türleri desteklemez `==` varsayılan işleci. Desteklemek için `==` işleci, bir kullanıcı tarafından tanımlanan yapı gerekir [aşırı](#operator-overloadability) bu.

İle başlayarak C# 7.3, `==` ve `!=` işleçleri tarafından desteklenen C# [diziler](../../tuples.md). Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.

### <a name="string-equality"></a>Dize eşitliği

İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

Büyük/küçük harfe sıralı karşılaştırma olmasıdır. Dize karşılaştırması hakkında daha fazla bilgi için bkz: [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).

### <a name="reference-types-equality"></a>Başvuru türleri eşitlik

İki dışında `string` başvuru türü işlenen, bunlar aynı nesneye başvurduğunuzda eşit:

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

Örnekte gösterildiği gibi destek kullanıcı tarafından tanımlanan başvuru türleri `==` varsayılan işleci. Ancak, bir kullanıcı tarafından tanımlanan başvuru türü aşırı yüklenebilir `==` işleci. Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.

## <a name="inequality-operator-"></a>Eşitsizlik işleci! =

Eşitsizlik işleci `!=` döndürür `true` işlenenleri eşit değilse `false` Aksi takdirde. İşlenen için [yerleşik türler](../keywords/built-in-types-table.md), ifade `x != y` ifade aynı sonucu üretir `!(x == y)`. Tür eşitlik hakkında daha fazla bilgi için bkz: [eşitlik işleci](#equality-operator-) bölümü.

Aşağıdaki örnek, kullanımını gösterir. `!=` işleci:

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `==` ve `!=` işleçleri. Bir tür iki işleçlerden aşırı de başka bir aşırı gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Eşitlik karşılaştırmaları](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
