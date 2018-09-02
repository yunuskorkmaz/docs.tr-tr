---
title: char anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 95ecfaaf1397f7a4598faba6528b38170062145a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463227"
---
# <a name="char-c-reference"></a>char (C# Başvurusu)

`char` Örneği bildirmek için anahtar sözcüğü kullanılır <xref:System.Char?displayProperty=nameWithType> yapısı, .NET Framework, Unicode karakterini temsil etmek için kullanır. Değerini bir `Char` nesnedir (sıra) 16 bit sayısal değer.

 Unicode karakterler yazma dillerinin ve dünyanın en iyi temsil etmek için kullanılır.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000'u + FFFF için|Unicode 16-bit karakteri|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

Sabitleri `char` tür karakter değişmez değerleri, onaltılık çıkış dizisi veya Unicode gösterimi yazılabilir. Ayrıca, integral karakter kodlarını çevirebilirsiniz. Aşağıdaki örnekte dört `char` değişkenleri, aynı karakterle başlatılır `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Dönüşümler

A `char` örtük olarak dönüştürülebilir [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md). Ancak, diğer türlerinden herhangi bir örtük dönüştürme vardır `char` türü.

<xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Char>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)  
- [Dizeler](../../../csharp/programming-guide/strings/index.md)