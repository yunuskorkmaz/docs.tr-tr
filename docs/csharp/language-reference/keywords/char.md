---
title: char anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: b58730d945582ded7b76fcd5c4c65bc1dd9324da
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661463"
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

A `char` örtük olarak dönüştürülebilir [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [çift](../builtin-types/floating-point-numeric-types.md), veya [ondalık](../builtin-types/floating-point-numeric-types.md). Ancak, diğer türlerinden herhangi bir örtük dönüştürme vardır `char` türü.

<xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Char>
- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [Tam sayı türleri](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)
- [Dizeler](../../../csharp/programming-guide/strings/index.md)
