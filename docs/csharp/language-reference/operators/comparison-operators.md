---
title: Karşılaştırma işleçleri- C# başvuru
description: Sayısal değerlerin C# sırasını denetlemek için kullanabileceğiniz karşılaştırma işleçleri hakkında bilgi edinin.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: bb28e2adba896ae85b189858283376fbe3250dce
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039064"
---
# <a name="comparison-operators-c-reference"></a>Karşılaştırma işleçleri (C# başvuru)

İlişkisel olarak da bilinen [`<` (küçüktür)](#less-than-operator-), [`>` (büyüktür)](#greater-than-operator-), [`<=` (küçüktür veya eşittir](#less-than-or-equal-operator-)) ve [`>=` (büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması. Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.

> [!NOTE]
> `==`, `<`, `>`, `<=`ve `>=` işleçleri için, işlenenlerin herhangi biri bir sayı değilse (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucu `false`olur. Diğer bir deyişle, `NaN` değeri, `NaN` dahil diğer `double` (veya `float`) bir değere eşit, bundan küçüktür veya eşit değildir. Daha fazla bilgi ve örnek için <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesine bakın.

Numaralandırma türleri de karşılaştırma işleçlerini destekler. Aynı [sabit listesi](../keywords/enum.md) türünün işlenenleri için, temeldeki integral türünün karşılık gelen değerleri karşılaştırılır.

[`==` ve `!=` işleçleri](equality-operators.md) işlenenlerinin eşit olup olmadığını denetler.

## <a name="less-than-operator-"></a>Küçüktür işleci \<

`<` işleci, sol işlenenin sağ işleneninden daha küçükse `true` döndürür `false` Aksi takdirde:

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Büyüktür işleci >

`>` işleci, sol işleneni sağ işleneninden büyükse `true` döndürür `false` Aksi takdirde:

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Küçüktür veya eşittir işleci \<=

`<=` işleci, sol işlenenin sağ işleneninden küçük veya ona eşit olması durumunda `true` döndürür `false` Aksi takdirde:

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Büyüktür veya eşittir işleci > =

`>=` işleci, sol işlenenin sağ işleneninden büyük veya ona eşit olması durumunda `true` döndürür `false` Aksi takdirde:

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür `<`, `>`, `<=`ve `>=` işleçlerini [aşırı](operator-overloading.md) yükleyebilir.

Bir tür `<` veya `>` işleçlerinden birini aşırı yüklerinde, hem `<` hem de `>`aşırı yüklemesi gerekir. Bir tür `<=` veya `>=` işleçlerinden birini aşırı yüklerinde, hem `<=` hem de `>=`aşırı yüklemesi gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Eşitlik işleçleri](equality-operators.md)
