---
title: bool tipi - C# referans
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846451"
---
# <a name="bool-c-reference"></a>bool (C# referansı)

Tür `bool` anahtar kelimesi,.NET <xref:System.Boolean?displayProperty=nameWithType> yapı türüiçin boolean değerini temsil eden bir `true` diğer `false`addır ve bu da .

`bool` Mantıksal işlemleri türünün değerleriyle gerçekleştirmek için [Boolean mantıksal](../operators/boolean-logical-operators.md) işleçlerini kullanın. Tür, `bool` [karşılaştırma](../operators/comparison-operators.md) ve [eşitlik](../operators/equality-operators.md) işleçlerinin sonuç türüdür. Bir `bool` ifade [if,](../keywords/if-else.md) [do](../keywords/do.md), [while](../keywords/while.md), ve ifadeler [için](../keywords/for.md) ve [ `?:`koşullu işleç ](../operators/conditional-operator.md)bir kontrol koşullu ifade olabilir.

`bool` Türünün varsayılan `false`değeri.

## <a name="literals"></a>Sabit değerler

Bir `bool` değişkeni `true` `false` başlatmak veya bir `bool` değeri geçirmek için ve literals'i kullanabilirsiniz:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Üç değerli Boolean mantığı

Örneğin, üç `bool?` değerli Boolean türünü destekleyen veritabanlarıyla çalışırken, üç değerli mantığı desteklemeniz gerekiyorsa, nullable türünü kullanın. `bool?` Operands için, önceden `&` tanımlanmış `|` ve operatörler üç değerli mantığı destekler. Daha fazla bilgi için [Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

Nullable değer türleri hakkında daha fazla bilgi için, [Nullable değer türleri](nullable-value-types.md)bakın.

## <a name="conversions"></a>Dönüşümler

C# `bool` türü içeren yalnızca iki dönüşüm sağlar. Bunlar, karşılık gelen geçersiz `bool?` türüne örtülü bir dönüştürme `bool?` ve türden açık bir dönüştürmedir. Ancak,.NET, `bool` türe dönüştürmek için kullanabileceğiniz ek yöntemler sağlar. Daha fazla bilgi için API başvuru sayfasının [Boolean değerleri bölümüne dönüştürme ve](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) değiştirme bölümüne <xref:System.Boolean?displayProperty=nameWithType> bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [bool türü](~/_csharplang/spec/types.md#the-bool-type) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [true ve false işleçleri](../operators/true-false-operators.md)
