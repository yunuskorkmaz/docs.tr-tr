---
title: karakter türü- C# başvuru
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451166"
---
# <a name="char-c-reference"></a>Char (C# başvuru)

`char` Type anahtar sözcüğü, bir Unicode UTF-16 karakteri temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türü için bir diğer addır.

|Type|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000-U + FFFF|16 bit|<xref:System.Char?displayProperty=nameWithType>|

[Dize](reference-types.md#the-string-type) türü, metni `char` değerleri dizisi olarak temsil eder.

## <a name="literals"></a>Sabit değerler

İle bir `char` değeri belirtebilirsiniz:

- bir karakter sabit değeri.
- bir karakter kodunun dört basamaklı onaltılı temsili `\u` bir Unicode kaçış sırası.
- `\x` bir karakter kodunun onaltılı gösterimi tarafından izlenen bir onaltılık kaçış sırası.

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

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
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [Dizeler](../../programming-guide/strings/index.md)
