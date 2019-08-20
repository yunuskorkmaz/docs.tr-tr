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
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605954"
---
# <a name="char-c-reference"></a>char (C# Başvurusu)

Anahtar sözcüğü, .NET Framework bir Unicode karakteri temsil etmek için <xref:System.Char?displayProperty=nameWithType> kullandığı yapının bir örneğini bildirmek için kullanılır. `char` Bir `Char` nesnenin değeri 16 bit sayısal (sıra sayısı) değeridir.

 Unicode karakterler, dünyanın her yerindeki yazılı dillerin çoğunu temsil etmek için kullanılır.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000-U + FFFF|Unicode 16 bit karakter|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

`char` Türün sabitleri, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir. İntegral karakter kodlarını da çevirebilirsiniz. Aşağıdaki örnekte, dört `char` değişken aynı karakterle `X`başlatılır:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Dönüşümler

Bir `char` , örtük olarak [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)veya [Decimal](../builtin-types/floating-point-numeric-types.md)'a dönüştürülebilir. Ancak, diğer türlerden `char` türüne örtülü dönüşüm yoktur.

Türü <xref:System.Char?displayProperty=nameWithType> , `char` değerleriyle çalışmak için çeşitli statik yöntemler sağlar.

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
- [Boş Değer Atanabilir Tipler](../../programming-guide/nullable-types/index.md)
- [Dizeler](../../programming-guide/strings/index.md)
