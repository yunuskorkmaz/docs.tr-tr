---
title: bool anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771855"
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)

@No__t_0 anahtar sözcüğü <xref:System.Boolean?displayProperty=nameWithType> diğer adıdır. Boole değerlerini depolamak için değişkenleri bildirmek üzere kullanılır: [true](true-literal.md) ve [false](false-literal.md).

> [!NOTE]
> Üç değerli mantığı desteklemeniz gerekiyorsa (örneğin, üç değerli bir Boole türünü destekleyen veritabanlarıyla çalışırken) `bool?` türünü kullanın. @No__t_0 işlenenleri için, önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler. Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

## <a name="literals"></a>Sabit değerler

Bir `bool` değişkenine Boole değeri atayabilirsiniz. Ayrıca, bir `bool` değişkenine `bool` değerlendirilen bir ifade da atayabilirsiniz.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Bir `bool` değişkeninin varsayılan değeri `false`. Bir `bool?` değişkeninin varsayılan değeri `null`.

## <a name="conversions"></a>Dönüşümler

' C++De, `bool` türünde bir değer `int` türünde bir değere dönüştürülebilir. diğer bir deyişle, `false` sıfır ile eşdeğerdir ve `true` sıfır dışında bir değere eşdeğerdir. ' C#De, `bool` türü ve diğer türler arasında dönüştürme yok. Örneğin, aşağıdaki `if` ifade içinde C#geçersizdir:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

@No__t_0 türünde bir değişkeni test etmek için, bunu aşağıdaki gibi, sıfır gibi bir değerle açıkça karşılaştırmanız gerekir:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Örnek

Bu örnekte, klavyeden bir karakter girersiniz ve program giriş karakterinin bir harf olup olmadığını denetler. Bir harf ise, küçük harf veya büyük harf olup olmadığını denetler. Bu denetimler, her ikisi de `bool` türünü döndüren <xref:System.Char.IsLetter%2A> ve <xref:System.Char.IsLower%2A> ile gerçekleştirilir:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Integral türleri](../builtin-types/integral-numeric-types.md)
- [Yerleşik Türler Tablosu](./built-in-types-table.md)
