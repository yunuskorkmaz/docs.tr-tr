---
title: "bool (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d52955d64a6c8063e4ea93ceb096459c1c5e984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)
`bool` Sözcüktür bir diğer ad <xref:System.Boolean?displayProperty=nameWithType>. Boole değerlerini depolamak için değişkenleri bildirmek için kullanılan [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md).  
  
> [!NOTE]
>  Ayrıca değeri olabilir bir Boolean değişkeni gerektirip gerektirmediğini `null`, kullanmak `bool?`. Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="literals"></a>Sabit değerler  
 Bir Boolean değeri atayabilirsiniz bir `bool` değişkeni. Ayrıca değerlendiren bir ifade atayabilirsiniz `bool` için bir `bool` değişkeni.  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 Varsayılan değer olan bir `bool` değişken `false`. Varsayılan değer olan bir `bool?` değişken `null`.  
  
## <a name="conversions"></a>Dönüşümler  
 C++, türünde bir değer `bool` türünde bir değer dönüştürülebilir `int`; diğer bir deyişle, `false` sıfır olarak eşdeğerdir ve `true` için sıfır olmayan değerler eşdeğerdir. C# ' ta yok arasında dönüştürme `bool` türü ve diğer türleri. Örneğin, aşağıdaki `if` deyimi C# ' geçerli değil:  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 Türünde bir değişken test etmek için `int`, açıkça sıfır gibi bir değer gibi karşılaştırın gerekir:  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, klavyeden bir karakter girin ve program giriş karakteri bir harf olup olmadığını denetler. Bir harf ise küçük harfler veya büyük olup olmadığını denetler. Bu denetimler ile gerçekleştirilen <xref:System.Char.IsLetter%2A>, ve <xref:System.Char.IsLower%2A>, hangi return her ikisi de `bool` türü:  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
