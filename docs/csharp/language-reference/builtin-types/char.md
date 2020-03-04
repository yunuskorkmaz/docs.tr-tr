---
title: karakter türü- C# başvuru
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a5aca12e4037d517c3bcfb403c990605a052d48f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239852"
---
# <a name="char-c-reference"></a>Char (C# başvuru)

`char` Type anahtar sözcüğü, bir Unicode UTF-16 karakteri temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türü için bir diğer addır.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000-U + FFFF|16 bit|<xref:System.Char?displayProperty=nameWithType>|

`char` türünün varsayılan değeri `\0`, yani U + 0000.

[Dize](reference-types.md#the-string-type) türü, metni `char` değerleri dizisi olarak temsil eder.

## <a name="literals"></a>Sabit değerler

İle bir `char` değeri belirtebilirsiniz:

- bir karakter sabit değeri.
- bir karakter kodunun dört basamaklı onaltılı temsili `\u` bir Unicode kaçış sırası.
- `\x` bir karakter kodunun onaltılı gösterimi tarafından izlenen bir onaltılık kaçış sırası.

[!code-csharp-interactive[char literals](~/samples/snippets/csharp/language-reference/builtin-types/CharType.cs#Literals)]

Yukarıdaki örnekte gösterildiği gibi, bir karakter kodunun değerini de karşılık gelen `char` değerine çevirebilirsiniz.

> [!NOTE]
> Unicode kaçış sırası söz konusu olduğunda, dört onaltılık basamağı de belirtmeniz gerekir. Yani, `\u006A` geçerli bir kaçış sırası, `\u06A` ve `\u6A` geçerli değildir.
>
> Onaltılı kaçış sırası söz konusu olduğunda, öndeki sıfırları atlayabilirsiniz. Diğer bir deyişle, `\x006A`, `\x06A`ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.

## <a name="conversions"></a>Dönüşümler

`char` türü örtük olarak şu [integral](integral-numeric-types.md) türlerine dönüştürülebilir: `ushort`, `int`, `uint`, `long`ve `ulong`. Ayrıca yerleşik [kayan nokta](floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float`, `double`ve `decimal`. `sbyte`, `byte`ve `short` integral türlerine açıkça dönüştürülebilir.

Diğer türlerden `char` türüne örtük dönüştürme yok. Ancak, herhangi bir [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türü `char`açıkça dönüştürülebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Değer türleri](value-types.md)
- [Dizeler](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
