---
title: Char anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698781"
---
# <a name="char-c-reference"></a>char (C# Başvurusu)

@No__t-0 anahtar sözcüğü, .NET Framework bir Unicode karakteri temsil etmek için kullandığı <xref:System.Char?displayProperty=nameWithType> yapısının bir örneğini bildirmek için kullanılır. @No__t-0 nesnesinin değeri 16 bit sayısal (sıra sayısı) değeridir.

 Unicode karakterler, dünyanın her yerindeki yazılı dillerin çoğunu temsil etmek için kullanılır.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000-U + FFFF|Unicode 16 bit karakter|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

@No__t-0 türündeki sabitler, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir. İntegral karakter kodlarını da çevirebilirsiniz. Aşağıdaki örnekte, `char` dizisinin dört öğesi, `X` karakteriyle birlikte başlatılır:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Dönüşümler

@No__t-0 örtük olarak [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)veya [Decimal](../builtin-types/floating-point-numeric-types.md)'a dönüştürülebilir. Ancak, diğer türlerden `char` türüne örtük dönüştürmeler yoktur.

@No__t-0 türü `char` değerleriyle çalışmak için birkaç statik yöntem sağlar.

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Integral türleri](~/_csharplang/spec/types.md#integral-types) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Char>
- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Integral türleri](../builtin-types/integral-numeric-types.md)
- [Yerleşik Türler Tablosu](./built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](./implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](./explicit-numeric-conversions-table.md)
- [Dizeler](../../programming-guide/strings/index.md)
