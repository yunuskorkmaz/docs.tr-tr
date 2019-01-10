---
title: == İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655965"
---
# <a name="-operator-c-reference"></a>== İşleci (C# Başvurusu)

Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.

## <a name="value-types-equality"></a>Değer türleri eşitlik

İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`. Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri. Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.

İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.

Varsayılan olarak, `==` işleci bir kullanıcı tanımlı tanımlanmamış [yapı](../keywords/struct.md) türü. Kullanıcı tanımlı bir tür için [aşırı](#operator-overloadability) `==` işleci.

İle başlayarak C# 7.3, `==` ve [ `!=` ](not-equal-operator.md) işleçleri tarafından desteklenen C# [diziler](../../tuples.md). Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.

## <a name="string-equality"></a>Dize eşitliği

İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

Büyük/küçük harfe sıralı karşılaştırma olmasıdır. Dizeleri karşılaştırmak hakkında daha fazla bilgi için bkz. [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).

## <a name="reference-types-equality"></a>Başvuru türleri eşitlik

İki dışında `string` başvuru türü işlenen, bunlar aynı nesneye başvurduğunuzda eşit:

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

Bu örnek, gösterir `==` işleci, kullanıcı tarafından tanımlanan başvuru türleri tarafından desteklenir. Ancak, bir kullanıcı tarafından tanımlanan başvuru türü aşırı yüklenebilir `==` işleci. Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `==` işleci. Bir tür eşitlik işlecini aşırı `==`, ayrıca aşırı gerekir [eşitsizlik işleci](not-equal-operator.md) `!=`.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Eşitlik karşılaştırmaları](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
