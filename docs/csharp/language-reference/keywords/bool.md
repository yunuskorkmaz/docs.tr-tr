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
ms.openlocfilehash: 3e4e83b52cd6b275e68039693c774f6490f2b88f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606051"
---
# <a name="bool-c-reference"></a>bool (C# Başvurusu)

Anahtar sözcüğü öğesinin <xref:System.Boolean?displayProperty=nameWithType>diğer adıdır. `bool` Boole değerlerini depolamak için değişkenleri bildirmek üzere kullanılır: [true](true-literal.md) ve [false](false-literal.md).

> [!NOTE]
> Üç değerli mantığı desteklemeniz gerekiyorsa, örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken türünükullanın.`bool?` İşlenenler için, önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler. `bool?` Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

## <a name="literals"></a>Sabit değerler

Bir `bool` değişkene Boole değeri atayabilirsiniz. Ayrıca, bir `bool` `bool` değişkenine değerlendirilen bir ifade atayabilirsiniz.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

`bool` Bir`false`değişkenin varsayılan değeri. `bool?` Bir`null`değişkenin varsayılan değeri.

## <a name="conversions"></a>Dönüşümler

' C++De, türünde `bool` bir değer türünde `int`bir değere dönüştürülebilir; diğer bir deyişle, `false` sıfıra eşdeğerdir ve `true` sıfır dışında değerlere eşdeğerdir. İçinde C#, `bool` türü ve diğer türler arasında dönüştürme yoktur. Örneğin, aşağıdaki `if` ifade içinde C#geçersizdir:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Türün `int`bir değişkenini test etmek için, bunu aşağıdaki gibi sıfır gibi bir değerle açıkça karşılaştırmanız gerekir:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Örnek

Bu örnekte, klavyeden bir karakter girersiniz ve program giriş karakterinin bir harf olup olmadığını denetler. Bir harf ise, küçük harf veya büyük harf olup olmadığını denetler. Bu denetimler, <xref:System.Char.IsLetter%2A> herikisi<xref:System.Char.IsLower%2A>de türüdöndürenveilegerçekleştirilir:`bool`

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Integral türleri](../builtin-types/integral-numeric-types.md)
- [Yerleşik Türler Tablosu](./built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](./implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](./explicit-numeric-conversions-table.md)
