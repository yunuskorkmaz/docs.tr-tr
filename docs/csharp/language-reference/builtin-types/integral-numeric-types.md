---
title: Tamsayı sayısal türleri - C# başvurusu
description: Aralık, depolama boyutu ve kullandığı her tamsayı sayısal türleri için öğrenin.
ms.date: 06/25/2019
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
ms.openlocfilehash: 141475c4d92278be02d6a832a93cd8553a4bcbd8
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661134"
---
# <a name="integral-numeric-types--c-reference"></a>Tamsayı sayısal türleri (C# Başvurusu)

**Tamsayı sayısal türleri** bir alt kümesidir **basit türler** ve ile başlatılabilir [ *değişmez değerleri*](#integral-literals). Tüm tamsayı türleri de değer türleridir.

Tüm tamsayı sayısal türleri desteği [aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçleri.

## <a name="sizes-and-ranges"></a>Boyutları ve aralıkları

Aşağıdaki tabloda, boyutları ve tam sayı türleri aralığı gösterilmektedir:

|Tür|Aralık|Boyut|  
|----------|-----------|----------|  
|`sbyte`|-128 ila 127 arasında|İşaretli 8 bit tam sayı|  
|`byte`|0 ile 255 arasında|İmzalanmamış 8 bit tam sayı|  
|`short`|-32.768 için 32.767|İşaretli 16 bit tam sayı|  
|`ushort`|0 ile 65.535 arasındaki|16 bit işaretsiz tamsayı|  
|`int`|-2.147.483.648 için 2.147.483.647|İşaretli 32 bit tam sayı|  
|`uint`|0 için 4.294.967.295'e|32-bit işaretsiz tamsayı|  
|`long`|-9,223,372,036,854,775,808 için 9.223.372.036.854.775.807|İşaretli 64 bit tam sayı|  
|`ulong`|0 için 18,446,744,073,709,551,615|64-bit işaretsiz tamsayı|  

Tüm tamsayı türleri için varsayılan değerdir `0`. Her bir integral türü sabitleri adlı sahip `MinValue` ve `MaxValue` türü için minimum ve maksimum değeri.

Kullanım <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısı hiçbir üst işaretli bir tam sayı veya alt sınırlarını temsil etmek için.

## <a name="integral-literals"></a>Tamsayı sabit değerleri

Tamsayı sabit değerleri olarak belirtilebilir *ondalık sabit değerleri*, *onaltılık değişmez değerler*, veya *ikili sabit dizeler*. Her bir örneği aşağıda gösterilmiştir:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Ondalık sabit değerleri herhangi bir önek gerektirmez. `x` Veya `X` önek belirten bir *onaltılık değişmez değeri*. `b` Veya `B` önek belirten bir *ikili değişmez değer*. Bildirimi `binaryLiteral` kullanımını gösteren `_` olarak bir *basamak ayıracı*. Basamak ayırıcı, tüm sayısal değişmez değerleri ile kullanılabilir. İkili sabit değerler ve basamak ayıracı `_` başlayarak desteklenir C# 7.0.

## <a name="literal-suffixes"></a>Değişmez değer soneki 

`l` Veya `L` sonekini belirtir, tam sayı sabiti olmalıdır `long` türü. `ul` Veya `UL` sonekini belirtir `ulong` türü. Varsa `L` soneki 9.223.372.036.854.775.807 büyük bir sabit değer ınternationalized (en büyük değerini `long`), değeri dönüştürülür `ulong` türü. Bir tamsayı sabit değeri tarafından temsil edilen değeri aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, bir derleyici hatası [CS1021](../../misc/cs1021.md) gerçekleşir. 

> [!NOTE]
> Küçük harf "l" sonek olarak kullanabilirsiniz. Ancak, bu bir derleyici uyarısı oluşturur çünkü "m" harfinin basamağı "1" ile kolaylıkla karıştırılır "M" daha anlaşılır olması için kullanın.

## <a name="type-of-an-integral-literal"></a>Bir integral sabit değerinin türü

Bir tamsayı sabit değeri sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:

1. `int`
1. `uint`
1. `long`
1. `ulong`

Bir integral sabit değer atama ya da bir tür dönüştürme kullanarak varsayılandan daha küçük bir aralık türüyle dönüştürebilirsiniz:

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

Bir integral sabit hazır değeri üzerinden ataması, bir tür dönüştürme veya son ekini kullanarak varsayılan değerinden daha büyük bir aralıkla türüne dönüştürebilirsiniz:

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>Dönüşümler

Örtük bir dönüştürme (adlı bir *dönüştürme genişletme*) hedef türüne kaynak türündeki tüm değerleri depolayabileceği herhangi iki tamsayı türleri arasında. Örneğin, örtük bir dönüştürme yoktur `int` için `long` çünkü aralığını `int` değerleri olan uygun bir alt kümesini `long`. Bir küçük işeritsiz tamsayı türünü daha büyük bir işaretli tamsayı türüne örtük dönüşümlere vardır. Herhangi bir kayan nokta türü için herhangi bir tamsayı türü arasında'örtük bir dönüştürme yoktur.  Herhangi işaretli integral türünden herhangi bir işaretsiz tamsayı türü için örtük dönüştürme vardır.

Örtük bir dönüştürme kaynak türden hedef türe tanımlı değil, bir tamsayı türü başka bir integral türe dönüştürmek için açık bir tür dönüştürme kullanmanız gerekir. Bu adlı bir *daraltma dönüştürmesi*. Dönüştürme veri kaybıyla sonuçlanabildiğinden açık durumda gereklidir.

## <a name="see-also"></a>Ayrıca bkz.

- [C#dil belirtimi - tam sayı türleri](~/_csharplang/spec/types.md#integral-types)
- [C#başvuru](../index.md)
- [Kayan nokta türleri](floating-point-numeric-types.md)
- [Varsayılan değerler tablosu](../keywords/default-values-table.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](../keywords/formatting-numeric-results-table.md)
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
