---
title: bool anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d87da29872582e9c0d47a6c999312ce88252a5cc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334178"
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)

`bool` Anahtar sözcüğü, bir diğer adını <xref:System.Boolean?displayProperty=nameWithType>. Boole değerleri depolamak üzere değişkenler bildirmek için kullanılır: [true](true-literal.md) ve [false](false-literal.md).

> [!NOTE]
> Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli Boole türü destekleyen veritabanları ile. İçin `bool?` işlenenler, önceden tanımlanmış `&` ve `|` üç değerli mantıksal işleçleri destekler. Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](../operators/boolean-logical-operators.md) makalesi.

## <a name="literals"></a>Sabit değerler

Bir Boolean değerine atayabilirsiniz bir `bool` değişkeni. İçin değerlendirilen bir ifade de atayabilirsiniz `bool` için bir `bool` değişkeni.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Varsayılan değer olan bir `bool` değişkendir `false`. Varsayılan değer olan bir `bool?` değişkendir `null`.

## <a name="conversions"></a>Dönüşümler

C++ ' türünde bir değer `bool` türün değerine dönüştürülebilir `int`; diğer bir deyişle, `false` Sıfıra eşdeğer olan ve `true` sıfır olmayan değerlere eşdeğerdir. C# ' ta yoktur arasında dönüştürme `bool` türü ve diğer türleri. Örneğin, aşağıdaki `if` ifadesi C# içinde geçerli değil:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Türünde bir değişken test etmek için `int`, açıkça gibi sıfır, bir değer gibi karşılaştırın gerekir:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Örnek

Bu örnekte, bir karakter klavyeden girmeniz ve program, girdi karakteri bir harf olup olmadığını denetler. Bir harf ise, küçük harfler veya büyük olup olmadığını denetler. Bu denetimler ile gerçekleştirilen <xref:System.Char.IsLetter%2A>, ve <xref:System.Char.IsLower%2A>, hangi iade her ikisi de `bool` türü:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Örtük Sayısal Dönüşümler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüşümler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
