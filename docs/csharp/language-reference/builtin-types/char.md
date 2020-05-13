---
title: Char türü-C# başvurusu
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205788"
---
# <a name="char-c-reference"></a>Char (C# Başvurusu)

`char`Type anahtar sözcüğü, <xref:System.Char?displayProperty=nameWithType> BIR Unicode UTF-16 karakteri temsil eden .net yapı türü için bir diğer addır.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000-U + FFFF|16 bit|<xref:System.Char?displayProperty=nameWithType>|

Türün varsayılan değeri, yani `char` `\0` u + 0000 olur.

`char`Tür [karşılaştırma](../operators/comparison-operators.md), [eşitlik](../operators/equality-operators.md), [artış](../operators/arithmetic-operators.md#increment-operator-)ve [azaltma](../operators/arithmetic-operators.md#decrement-operator---) işleçlerini destekler. Üstelik, `char` işlenenler, [Aritmetik](../operators/arithmetic-operators.md) ve [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md) işleçler için ilgili karakter kodları üzerinde bir işlem gerçekleştirir ve türün sonucunu üretir `int` .

[Dize](reference-types.md#the-string-type) türü, metni bir dizi değer olarak temsil eder `char` .

## <a name="literals"></a>Sabit değerler

Şunu `char` içeren bir değer belirtebilirsiniz:

- bir karakter sabit değeri.
- bir Unicode kaçış sırası, bu, `\u` bir karakter kodunun dört symbol onaltılı gösterimi izler.
- `\x`bir karakter kodunun onaltılı gösteriminden sonra gelen onaltılı kaçış sırası.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Yukarıdaki örnekte gösterildiği gibi, bir karakter kodunun değerini karşılık gelen değere de çevirebilirsiniz `char` .

> [!NOTE]
> Unicode kaçış sırası söz konusu olduğunda, dört onaltılık basamağı de belirtmeniz gerekir. Yani, `\u006A` geçerli bir kaçış sırası, `\u06A` ve `\u6A` geçerli değildir.
>
> Onaltılı kaçış sırası söz konusu olduğunda, öndeki sıfırları atlayabilirsiniz. Diğer bir deyişle, `\x006A` , `\x06A` ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.

## <a name="conversions"></a>Dönüşümler

`char`Türü örtük olarak şu [integral](integral-numeric-types.md) türlerine dönüştürülebilir: `ushort` ,,, `int` `uint` `long` ve `ulong` . Ayrıca, yerleşik [kayan nokta](floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float` , `double` ve `decimal` . Açık olarak `sbyte` , `byte` ve `short` tam sayı türlerine dönüştürülebilir.

Diğer türlerden türe örtük dönüştürme yok `char` . Ancak, tüm [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türleri açıkça dönüştürülebilir `char` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Dizeler](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [.NET içinde karakter kodlaması](../../../standard/base-types/character-encoding-introduction.md)
