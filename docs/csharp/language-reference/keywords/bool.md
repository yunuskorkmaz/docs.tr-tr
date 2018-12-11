---
title: bool anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: a5a5fa37905df9fb9369e9c0c26a2e39d03353f2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128329"
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)

`bool` Anahtar sözcüğü, bir diğer adını <xref:System.Boolean?displayProperty=nameWithType>. Boole değerleri depolamak üzere değişkenler bildirmek için kullanılır: [true](true-literal.md) ve [false](false-literal.md).

> [!NOTE]
> Bir değeri de olabilir bir Boolean değişkeni gerektirip gerektirmediğini `null`, kullanın `bool?`. Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.

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

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  