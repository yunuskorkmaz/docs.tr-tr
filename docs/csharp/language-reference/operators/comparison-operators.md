---
title: Karşılaştırma işleçleri - C# referansı
description: Sayısal değerlerin sırasını denetlemek için kullanabileceğiniz C# karşılaştırma işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399247"
---
# <a name="comparison-operators-c-reference"></a>Karşılaştırma işleçleri (C# başvurusu)

[ `<` (Daha az)](#less-than-operator-) [ `>` , (büyük)](#greater-than-operator-), [ `<=` (daha az veya eşit)](#less-than-or-equal-operator-)ve [ `>=` (büyük veya eşit)](#greater-than-or-equal-operator-) karşılaştırma, ayrıca ilişkisel olarak bilinen, işleçler kendi operands karşılaştırın. Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.

> [!NOTE]
> Için `==`, `<` `>`, `<=`, `>=` , ve operatörler, herhangi bir operands bir sayı değilse (veya<xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType>), operasyon sonucudur `false`. `NaN` Bu, değerin ne daha büyük, ne daha az, ne de dahil olmak üzere başka `double` bir (veya) `float`değere eşit olduğu anlamına `NaN`gelir. Daha fazla bilgi ve <xref:System.Double.NaN?displayProperty=nameWithType> örnekler <xref:System.Single.NaN?displayProperty=nameWithType> için, başvuru makalesine bakın.

Numaralandırma türleri karşılaştırma işleçlerini de destekler. Aynı [enum](../builtin-types/enum.md) türündeki operandlar için, altta yatan integral türünün karşılık gelen değerleri karşılaştırılır.

Ve [ `==` `!=` operatörler](equality-operators.md) operandlarının eşit olup olmadığını kontrol ederler.

## <a name="less-than-operator-"></a>Operatörden daha az\<

Sol `<` operand'ı sağ operand'dan daha azsa `false` operatör geri döner, `true` aksi takdirde:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Operatörden daha büyük >

Sol `>` operand'ı sağ operand'dan büyükse, işleç geri döner, `true` `false` aksi takdirde:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Daha az veya eşit işleç\<=

Sol `<=` operand'ı sağ operand'dan daha az veya eşitse, işleç geri döner, `true` `false` aksi takdirde:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Büyük veya eşit işleç >=

Sol `>=` operand'ı sağ operand'dan büyük veya eşitse, `false` işleç geri döner, `true` aksi takdirde:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür `<`, `>` `<=`, `>=` , ve işleçleri [aşırı yükleyebilir.](operator-overloading.md)

Bir tür operatörlerden birini `<` `>` aşırı yüklenirse, her ikisini de `<` aşırı yüklemesi gerekir. `>` Bir tür operatörlerden birini `<=` `>=` aşırı yüklenirse, her ikisini de `<=` aşırı yüklemesi gerekir. `>=`

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İlişkisel ve tür test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Eşitlik operatörleri](equality-operators.md)
