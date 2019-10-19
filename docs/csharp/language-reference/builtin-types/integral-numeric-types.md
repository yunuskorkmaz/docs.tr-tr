---
title: Integral sayısal türleri- C# başvuru
description: İntegral sayısal türlerin her biri için aralığı, depolama boyutunu ve kullanımları öğrenin.
ms.date: 10/18/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579189"
---
# <a name="integral-numeric-types--c-reference"></a>Integral sayısal türleri (C# başvuru)

**İntegral sayısal türleri** **basit türlerin** bir alt kümesidir ve [*değişmez değerler*](#integer-literals)ile başlatılabilir. Tüm integral türleri de değer türlerdir. Tüm integral sayısal türler [Aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.

## <a name="characteristics-of-the-integral-types"></a>İntegral türlerinin özellikleri

C#aşağıdaki önceden tanımlanmış integral türlerini destekler:

|C#tür/anahtar sözcük|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------|
|`sbyte`|-128-127|İmzalanan 8 bit tamsayı|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0-255|İşaretsiz 8 bit tamsayı|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32.768-32.767|İmzalanan 16 bit tamsayı|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0-65.535|İşaretsiz 16 bit tamsayı|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2.147.483.648-2.147.483.647|İmzalanan 32 bit tamsayı|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0-4.294.967.295|İşaretsiz 32 bit tamsayı|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9223372036854775808-9.223.372.036.854.775.807|İmzalanan 64 bit tamsayı|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0-18446744073709551615|İşaretsiz 64 bit tamsayı|<xref:System.UInt64?displayProperty=nameWithType>|

Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır. Bunlar arasında değiştirilebilir. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
int a = 123;
System.Int32 b = 123;
```

Her integral türünün varsayılan değeri sıfırdır `0`. İntegral türlerinin her biri, bu türün en düşük ve en büyük değerini sağlayan `MinValue` ve `MaxValue` sabitlerini içerir.

Büyük veya alt sınır olmadan işaretli bir tamsayıyı temsil etmek için <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısını kullanın.

## <a name="integer-literals"></a>Tamsayı sabit değerleri

Tamsayı sabit değerleri

- *Decimal*: herhangi bir ön ek olmadan
- *onaltılı*: `0x` veya `0X` ön eki ile
- *ikili*: `0b` veya `0B` önekiyle ( C# 7,0 ve üzeri sürümlerde mevcuttur)

Aşağıdaki kod, her birine bir örnek gösterir:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir. Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.

Bir tamsayı sabit değerinin türü, soneki tarafından aşağıdaki şekilde belirlenir:

- Değişmez değer için bir sonek yoksa, türü, değerinin gösterilebileceği aşağıdaki türlerin birincsahiptir: `int`, `uint`, `long`, `ulong`.
- Sabit değer `U` veya `u` ile sondiçeriyorsa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `uint`, `ulong`.
- Sabit değer `L` veya `l` ile sondiçeriyorsa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `long`, `ulong`.

  > [!NOTE]
  > Küçük harf `l` bir sonek olarak kullanabilirsiniz. Ancak, harf `l` `1` basamak ile karıştırıabileceğinden bu bir derleyici uyarısı oluşturur. Açıklık için `L` kullanın.

- Sabit değer `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` veya `lu` tarafından düzeltildiğinde, türü `ulong` olur.

Bir tamsayı değişmez değeri ile temsil edilen değer <xref:System.UInt64.MaxValue?displayProperty=nameWithType> aşarsa, bir derleyici hatası [CS1021](../../misc/cs1021.md) oluşur.

Bir tamsayı değişmez değeri tarafından temsil edilen değer, örtük olarak, sabit değer türü tarafından belirlenen değerden daha küçük bir aralığa dönüştürülebilir. Bu, değer hedef türünün aralığı dahilinde olduğunda mümkündür:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Yukarıdaki örnekte gösterildiği gibi, değişmez değerin değeri hedef türü Aralık içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.

Ayrıca, bir tamsayı değişmez değeri ile temsil edilen değeri, değişmez değerin belirlenen türü dışında bir türe dönüştürmek için bir cast kullanabilirsiniz:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Dönüşümler

Hedef türün kaynak türünün tüm değerlerini depolayabileceği iki integral tür arasında örtük bir dönüştürme ( *genişleyen dönüştürme*denir) vardır. Örneğin, `int` değerlerinin aralığı `long` uygun bir alt kümesi olduğundan, `int` `long` ' den örtük bir dönüştürme vardır. Daha küçük bir işaretsiz integral türünden daha büyük bir işaretli integral türüne örtük dönüştürmeler vardır. Ayrıca herhangi bir integral türünden herhangi bir kayan nokta türüne örtük bir dönüştürme de vardır.  Herhangi bir imzalı integral türünden hiçbir işaretsiz integral türüne örtülü dönüşüm yoktur.

Örtük bir dönüştürme, kaynak türünden hedef türüne tanımlanmadığında, bir integral türünü başka bir integral türüne dönüştürmek için açık bir atama kullanmanız gerekir. Bu, *daraltma dönüştürmesi*olarak adlandırılır. Dönüştürme işlemi veri kaybına neden olabileceğinden açık durum gereklidir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Integral türleri](~/_csharplang/spec/types.md#integral-types)
- [Tamsayı sabit değerleri](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Kayan nokta türleri](floating-point-numeric-types.md)
- [Varsayılan değerler tablosu](../keywords/default-values-table.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](../keywords/formatting-numeric-results-table.md)
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
