---
description: "C 'de yerleşik Boole türü hakkında bilgi edinin #"
title: bool türü-C# başvurusu
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126469"
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)

`bool`Type anahtar sözcüğü, <xref:System.Boolean?displayProperty=nameWithType> ya da olabilen bir Boole değerini temsil eden .net yapı türü için bir diğer addır `true` `false` .

Tür değerleriyle mantıksal işlemler gerçekleştirmek için `bool` [Boolean mantıksal](../operators/boolean-logical-operators.md) işleçler kullanın. `bool`Tür, [karşılaştırma](../operators/comparison-operators.md) ve [eşitlik](../operators/equality-operators.md) işleçlerinin sonuç türüdür. Bir `bool` ifade, [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md)ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleçte `?:` ](../operators/conditional-operator.md)bir denetim koşullu ifadesi olabilir.

Türün varsayılan değeri `bool` `false` .

## <a name="literals"></a>Değişmez Değerler

`true` `false` Bir `bool` değişkeni başlatmak veya bir değeri geçirmek için ve değişmez `bool` değerlerini kullanabilirsiniz:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Üç değerli Boole mantığı

Üç `bool?` değerli mantığı desteketmeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken), null yapılabilir türü kullanın. İşlenenler için `bool?` , önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler. Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

Null yapılabilir değer türleri hakkında daha fazla bilgi için bkz. [Nullable değer türleri](nullable-value-types.md).

## <a name="conversions"></a>Dönüşümler

C# yalnızca türü içeren iki dönüştürme sağlar `bool` . Bunlar, karşılık gelen null yapılabilir `bool?` türe ve türden açık dönüştürmeye örtülü bir dönüşümtür `bool?` . Ancak, .NET, türden veya türünden dönüştürmek için kullanabileceğiniz ek yöntemler sağlar `bool` . Daha fazla bilgi için, API başvurusu sayfasının [Boole değerlerine dönüştürme](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) bölümüne bakın <xref:System.Boolean?displayProperty=nameWithType> .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [bool türü](~/_csharplang/spec/types.md#the-bool-type) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [true ve false işleçleri](../operators/true-false-operators.md)
