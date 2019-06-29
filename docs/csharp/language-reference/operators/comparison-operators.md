---
title: Karşılaştırma işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# sayısal değerlerin sırasını denetlemek için kullanabileceğiniz bir Karşılaştırma işleçleri.
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
ms.openlocfilehash: 5b6668e20e4d69b7d6bdf3e6283574f1b974ef54
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423964"
---
# <a name="comparison-operators-c-reference"></a>Karşılaştırma işleçleri (C# Başvurusu)

[ `<` (Küçüktür)](#less-than-operator-), [ `>` (büyüktür)](#greater-than-operator-), [ `<=` (küçüktür veya eşittir)](#less-than-or-equal-operator-), ve [ `>=` () büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması, işlenenleri Karşılaştırma işleçleri olarak ilişkisel'da bilinir. Tüm bu işleçleri destekler [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../keywords/floating-point-types-table.md) sayısal türler.

> [!NOTE]
> İçin `==`, `<`, `>`, `<=`, ve `>=` herhangi işlenenden değilse, birkaç işleçleri (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlem sonucu `false`. Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`. Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.

Numaralandırma türleri, Karşılaştırma işleçleri de destekler. Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.

[ `==` Ve `!=` işleçleri](equality-operators.md) işlenenlerini eşit olup olmadığını denetleyin.

## <a name="less-than-operator-"></a>Küçüktür işleci \<

`<` İşleci döndürür `true` sol işleneni, sağ işlenen altındaysa `false` Aksi takdirde:

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Büyüktür işleci >

`>` İşleci döndürür `true` sol işleneni, sağ işlenen büyükse `false` Aksi takdirde:

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Küçüktür veya eşittir işleci \<=

`<=` İşleci döndürür `true` sol işleneni, sağ işlenen küçük veya ona eşit olup olmadığını `false` Aksi takdirde:

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Büyüktür veya eşittir işleci > =

`>=` İşleci döndürür `true` sol işlenenin değerinden büyük veya eşittir, sağ işlenen ise `false` Aksi takdirde:

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `<`, `>`, `<=`, ve `>=` işleçleri.

Bir tür birini aşırı `<` veya `>` operatörleri onu gerekir aşırı yükleme hem de `<` ve `>`. Bir tür birini aşırı `<=` veya `>=` operatörleri onu gerekir aşırı yükleme hem de `<=` ve `>=`.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Eşitlik işleçleri](equality-operators.md)
