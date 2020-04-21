---
title: İntegral sayısal türleri - C# referansı
description: İntegral sayısal türlerinher biri için aralığı, depolama boyutunu ve kullanımlarını öğrenin.
ms.date: 10/22/2019
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
ms.openlocfilehash: 51ea64065ea8422e5885022105545780bc916f06
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739013"
---
# <a name="integral-numeric-types--c-reference"></a>İntegral sayısal türleri (C# referansı)

*İntegral sayısal türleri,* tümsel sayılarını temsil emzdir. Tüm integral sayısal türleri [değer türleridir.](value-types.md) Onlar da [basit türleri](value-types.md#built-in-value-types) ve [literals](#integer-literals)ile başharfolabilir. Tüm integral sayısal türleri [aritmetik,](../operators/arithmetic-operators.md) [bitwise mantıksal,](../operators/bitwise-and-shift-operators.md) [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçleri destekler.

## <a name="characteristics-of-the-integral-types"></a>İntegral türlerinin özellikleri

C# aşağıdaki önceden tanımlanmış integral türlerini destekler:

|C# türü/anahtar kelime|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------|
|`sbyte`|-128 ile 127 arası|İmzalı 8 bit'lik bir sayı|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 ile 255 arasında|İmzasız 8 bit'lik tümseci|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32.768 ile 32.767 arası|İmzalı 16 bit'lik bir sayı|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 ile 65.535 arası|İmzasız 16 bit'lik bir sayı|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2.147.483.648 ila 2.147.483.647|İmzalı 32 bit'lik bir sayı|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 ile 4.294.967.295 arası|İmzasız 32 bit'lik tümseci|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9.223.372.036.854.775.808 ila 9.223.372.036.854.775.807|İmzalı 64 bit'lik bir sayı|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 ila 18,446,744,073,709,551,615|İmzasız 64 bit'lik bir sayı|<xref:System.UInt64?displayProperty=nameWithType>|

Önceki tabloda, soldaki sütundaki her C# türü anahtar sözcüğü karşılık gelen .NET türüiçin bir diğer addır. Değiştirilebilirler. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
int a = 123;
System.Int32 b = 123;
```

Her integral türünün varsayılan değeri `0`sıfırdır. İntegral türlerinin `MinValue` `MaxValue` her biri, bu türün minimum ve maksimum değerini sağlayan sabitlere sahiptir.

Üst <xref:System.Numerics.BigInteger?displayProperty=nameWithType> veya alt sınırları olmayan imzalı bir tamsayıyı temsil etmek için yapıyı kullanın.

## <a name="integer-literals"></a>Sonda lı edebi

İnteger literals olabilir

- *ondalık*: herhangi bir önek olmadan
- *hexadecimal*: `0x` veya `0X` önek ile
- *ikili*: `0b` veya `0B` önek ile (C# 7.0 ve sonrası mevcuttur)

Aşağıdaki kod her birinin bir örneğini gösterir:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Yukarıdaki örnek, C# 7.0 ile başlayan desteklenen bir basamak `_` *ayırıcısı*olarak da kullanılır. Sayısal literals her türlü ile basamak ayırıcı kullanabilirsiniz.

Bir sonda sının yazımı, sonek tarafından aşağıdaki gibi belirlenir:

- Literal'ın sonekyoksa, türü, değerinin temsil edilebildiği aşağıdaki türlerden `int`ilkidir: , , `uint` `long`. `ulong`
- `U` Eğer literal tarafından suffixed `u`veya , türü değeri temsil edilebilir aşağıdaki türlerden ilki: `uint`. `ulong`.
- `L` Eğer literal tarafından suffixed `l`veya , türü değeri temsil edilebilir aşağıdaki türlerden ilki: `long`. `ulong`.

  > [!NOTE]
  > Küçük harfi `l` sonek olarak kullanabilirsiniz. Ancak, bu bir derleyici uyarısı `l` oluşturur, çünkü harf `1`basamakla karıştırılabilir. Netlik için kullanın. `L`

- Eğer edebi olarak `UL`, , `Ul` `uL` `ul` `LU`, , `Lu`, `lU`, `lu`, , `ulong`veya , türü .

Bir tamsayı ile temsil edilen değer gerçek <xref:System.UInt64.MaxValue?displayProperty=nameWithType>değeri aşıyorsa, [cs1021](../../misc/cs1021.md) derleyici hatası oluşur.

Bir bir insalı literal'In belirlenen `int` türü ve gerçek tarafından temsil edilen değer hedef türün aralığındaysa, `sbyte`değer `byte` `short`dolaylı `ushort` `uint`olarak `ulong`, , , , , veya :

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Yukarıdaki örnekte de görüldüğü gibi, literal değeri hedef türü aralığında değilse, [cs0031](../../misc/cs0031.md) derleyici hatası oluşur.

Bir tamsayı tarafından temsil edilen değeri, belirlenen edebi tür dışında türe dönüştürmek için bir döküm de kullanabilirsiniz:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Dönüşümler

Herhangi bir integral sayısal türü diğer integral sayısal türe dönüştürebilirsiniz. Hedef türü kaynak türün tüm değerlerini depolayabiliyorsa, dönüştürme örtülüdür. Aksi takdirde, açık bir dönüştürme gerçekleştirmek için [bir döküm ifadesi](../operators/type-testing-and-cast.md#cast-expression) kullanmanız gerekir. Daha fazla bilgi için yerleşik [sayısal dönüşümlere](numeric-conversions.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [İntegral tipleri](~/_csharplang/spec/types.md#integral-types)
- [Sonda lı edebi](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Kayan nokta türleri](floating-point-numeric-types.md)
- [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
