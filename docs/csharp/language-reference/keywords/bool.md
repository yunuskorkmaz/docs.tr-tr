---
title: bool anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d6b0cb91dd9b8159919b0d155bb2f9773e7ba534
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315114"
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)

`bool` Sözcüktür bir diğer ad <xref:System.Boolean?displayProperty=nameWithType>. Boole değerlerini depolamak için değişkenleri bildirmek için kullanılan [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md).

> [!NOTE]
> Ayrıca değeri olabilir bir Boolean değişkeni gerektirip gerektirmediğini `null`, kullanmak `bool?`. Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).

## <a name="literals"></a>Sabit değerler

Bir Boolean değeri atayabilirsiniz bir `bool` değişkeni. Ayrıca değerlendiren bir ifade atayabilirsiniz `bool` için bir `bool` değişkeni.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Varsayılan değer olan bir `bool` değişken `false`. Varsayılan değer olan bir `bool?` değişken `null`.

## <a name="conversions"></a>Dönüşümler

C++, türünde bir değer `bool` türünde bir değer dönüştürülebilir `int`; diğer bir deyişle, `false` sıfır olarak eşdeğerdir ve `true` için sıfır olmayan değerler eşdeğerdir. C# ' ta yok arasında dönüştürme `bool` türü ve diğer türleri. Örneğin, aşağıdaki `if` deyimi C# ' geçerli değil:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Türünde bir değişken test etmek için `int`, açıkça sıfır gibi bir değer gibi karşılaştırın gerekir:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Örnek

Bu örnekte, klavyeden bir karakter girin ve program giriş karakteri bir harf olup olmadığını denetler. Bir harf ise küçük harfler veya büyük olup olmadığını denetler. Bu denetimler ile gerçekleştirilen <xref:System.Char.IsLetter%2A>, ve <xref:System.Char.IsLower%2A>, hangi return her ikisi de `bool` türü:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[C# başvurusu](../../../csharp/language-reference/index.md)  
[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
[C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
[Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
[Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  