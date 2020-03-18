---
title: char türü - C# referans
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846528"
---
# <a name="char-c-reference"></a>char (C# referansı)

Tür `char` anahtar kelimesi, UNicode UTF-16 karakterini temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türüiçin bir diğer addır.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 için U+FFFF|16 bit|<xref:System.Char?displayProperty=nameWithType>|

`char` Türünün varsayılan değeri `\0`, yani U+0000'dir.

[Dize](reference-types.md#the-string-type) türü, metni bir `char` değerler dizisi olarak temsil eder.

## <a name="literals"></a>Sabit değerler

Aşağıdakilerle bir `char` değer belirtebilirsiniz:

- gerçek bir karakter.
- bir karakter kodunun dört `\u` sembollü hexadecimal gösterimi tarafından izlenen bir Unicode kaçış sırası.
- bir karakter kodunun hexadecimal gösterimi takip eden `\x` bir hexadecimal kaçış dizisi.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Önceki örnekte de görüldüğü gibi, karakter kodunun değerini karşılık `char` gelen değere de atabilirsiniz.

> [!NOTE]
> Unicode kaçış sırası durumunda, dört hexadecimal basamak belirtmeniz gerekir. Diğer bir `\u006A` süre geçerli bir `\u06A` kaçış `\u6A` dizisidir ve geçerli değildir.
>
> Bir hexadecimal kaçış sırası durumunda, önde gelen sıfırları atlayabilirsiniz. Diğer bir `\x006A`şey, , , `\x06A`ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.

## <a name="conversions"></a>Dönüşümler

Türü `char` örtülü olarak aşağıdaki [integral](integral-numeric-types.md) türlerine `ushort`dönüştürülebilir: `long`, `ulong`, `int` `uint`, ve . Ayrıca dahili [kayan nokta](floating-point-numeric-types.md) sayısal türlerine dolaylı olarak dönüştürülebilir: `float` `double`, `decimal`, ve . Açıkça dönüştürülebilir `sbyte`, `byte`, ve `short` integral türleri.

Diğer türlerden `char` türe örtülü dönüşüm yoktur. Ancak, herhangi bir [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türü `char`açıkça dönüştürülebilir .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İntegral türleri](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Dize](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
