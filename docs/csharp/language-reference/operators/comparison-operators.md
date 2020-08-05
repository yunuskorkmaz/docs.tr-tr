---
title: Karşılaştırma işleçleri-C# başvurusu
description: Sayısal değerlerin sırasını denetlemek için kullanabileceğiniz C# karşılaştırma işleçleri hakkında bilgi edinin.
ms.date: 05/11/2020
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
ms.openlocfilehash: d57f96b9c80bdc5f40169180b40326ffed91cf10
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555375"
---
# <a name="comparison-operators-c-reference"></a>Karşılaştırma işleçleri (C# Başvurusu)

İlişkisel olarak da bilinen [ `<` (küçüktür)](#less-than-operator-), [ `>` (büyüktür)](#greater-than-operator-), [ `<=` (küçüktür veya eşittir](#less-than-or-equal-operator-)) ve [ `>=` (büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması, işleçlerini karşılaştırın. Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.

> [!NOTE]
> ,, `==` , `<` `>` `<=` Ve `>=` işleçleri için İşlenenlerden herhangi biri bir sayı ( <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> ) değilse, işlemin sonucu olur `false` . Bu, değeri, `NaN` dahil olmak üzere herhangi bir değerden büyük, küçüktür veya eşit olmayan bir değere eşit değil anlamına gelir `double` `float` `NaN` . Daha fazla bilgi ve örnek için bkz <xref:System.Double.NaN?displayProperty=nameWithType> . veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.

[Char](../builtin-types/char.md) türü de karşılaştırma işleçlerini destekler. İşlenenler söz konusu olduğunda `char` , karşılık gelen karakter kodları karşılaştırılır.

Numaralandırma türleri de karşılaştırma işleçlerini destekler. Aynı [sabit listesi](../builtin-types/enum.md) türünün işlenenleri için, temeldeki integral türünün karşılık gelen değerleri karşılaştırılır.

[ `==` Ve `!=` işleçleri](equality-operators.md) , işlenenleri eşit olup olmadığını denetler.

## <a name="less-than-operator-"></a>Küçüktür işleci\<

`<`İşleci, `true` sol işlenenin sağ tarafından daha az ise, `false` tersi durumda, döndürür:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Büyüktür işleci >

`>`İşleci, `true` sol işleneni sağ işleneninden büyükse, `false` Aksi takdirde döndürür:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Küçüktür veya eşittir işleci\<=

`<=`İşleci, `true` sol işlenenin sağ işleneninden küçük veya ona eşit ise, `false` Aksi takdirde döndürür:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Büyüktür veya eşittir işleci >=

`>=`İşleci, `true` sol işlenenin sağ işleneninden büyük veya ona eşitse, `false` Aksi takdirde, döndürür:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür,, [overload](operator-overloading.md) , `<` `>` `<=` ve işleçlerini aşırı yükleyebilir `>=` .

Bir tür veya işleçlerden birini aşırı yüklerinde `<` `>` , hem hem de aşırı yüklemesi gerekir `<` `>` . Bir tür veya işleçlerden birini aşırı yüklerinde `<=` `>=` , hem hem de aşırı yüklemesi gerekir `<=` `>=` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Eşitlik İşleçleri](equality-operators.md)
