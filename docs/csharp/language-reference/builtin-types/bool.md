---
title: bool türü- C# başvuru
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 577ccd3bb9a20964dcdfc79ef2028854e4a55dc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342707"
---
# <a name="bool-c-reference"></a>bool (C# başvuru)

`bool` Type anahtar sözcüğü, `true` veya `false`olabilen bir Boolean değeri temsil eden .NET <xref:System.Boolean?displayProperty=nameWithType> yapı türü için bir diğer addır.

`bool` türünün değerleriyle mantıksal işlemler gerçekleştirmek için, [Boolean mantıksal](../operators/boolean-logical-operators.md) işleçler kullanın. `bool` türü [karşılaştırma](../operators/comparison-operators.md) ve [eşitlik](../operators/equality-operators.md) işleçlerinin sonuç türüdür. `bool` ifade, [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md)ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleç `?:`](../operators/conditional-operator.md)bir denetim koşullu ifadesi olabilir.

`bool` türünün varsayılan değeri `false`.

## <a name="literals"></a>Sabit değerler

`bool` değişkenini başlatmak veya bir `bool` değeri geçirmek için `true` ve `false` değişmez değerleri kullanabilirsiniz:

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Üç değerli Boole mantığı

Üç değerli mantığı desteketmeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken) null yapılabilir `bool?` türünü kullanın. `bool?` işlenenleri için, önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler. Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

Null yapılabilir değer türleri hakkında daha fazla bilgi için bkz. [Nullable değer türleri](nullable-value-types.md).

## <a name="conversions"></a>Dönüşümler

C#`bool` türünü içeren yalnızca iki dönüştürme sağlar. Bunlar, karşılık gelen null yapılabilir `bool?` türüne örtülü bir dönüşümtür ve `bool?` türünden açık bir dönüştürme. Ancak, .NET `bool` türüne dönüştürmek için kullanabileceğiniz ek yöntemler sağlar. Daha fazla bilgi için, <xref:System.Boolean?displayProperty=nameWithType> API başvurusu sayfasının [Boole değerlerine dönüştürme](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) bölümüne bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [bool türü](~/_csharplang/spec/types.md#the-bool-type) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [true ve false işleçleri](../operators/true-false-operators.md)
