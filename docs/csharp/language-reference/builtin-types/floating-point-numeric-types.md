---
title: Kayan nokta sayısal türleri - C# başvurusu
description: Yerleşik C# kayan nokta türleri'ne genel bakış
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236056"
---
# <a name="floating-point-numeric-types-c-reference"></a>Kayan nokta sayısal türleri (C# Başvurusu)

**Kayan nokta türleri** bir alt kümesidir **basit türler** ve ile başlatılabilir [ *değişmez değerleri*](#floating-point-literals). Tüm kayan nokta türleri de değer türleridir. Tüm kayan nokta sayısal türleri desteği [aritmetik](../operators/arithmetic-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçleri.

## <a name="characteristics-of-the-floating-point-types"></a>Kayan nokta türleri özellikleri

C#Aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:
  
|C#anahtar yazın|Yaklaşık aralık|Duyarlık|.NET türü|
|----------|-----------------------|---------------|--------------|
|`float`|±1.5 x 10<sup>−45</sup> ±3.4 x 10 için<sup>38</sup>|~ 6-9 basamak|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup>|yaklaşık 15-17 basamak|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1.0 x 10<sup>-28</sup> ±7.9228 x 10 için<sup>28</sup>|28-29 basamak|<xref:System.Decimal?displayProperty=nameWithType>|

Önceki tabloda her C# en soldaki sütun türü anahtar kelimedir karşılık gelen .NET türü için bir diğer ad. Birbirinin yerine kullanılabilir. Örneğin, aşağıdaki bildirimleri aynı türde değişkenleri bildirin:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Her bir kayan nokta türünün varsayılan değeri sıfırdır `0`. Kayan nokta türlerinden her birinin sahip `MinValue` ve `MaxValue` türü minimum ve maksimum sonlu değeri sağlayan sabitler. `float` Ve `double` türleri temsil eden bir sayı değil ve sonsuz değerler sabitleri de sağlar. Örneğin, `double` türü aşağıdaki sabitler sunar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Çünkü `decimal` türünde daha fazla duyarlık ve hem de daha küçük bir aralığı `float` ve `double`, finansal ve parasal hesaplamalar için uygundur.

Karıştırabilir miyim [integral](integral-numeric-types.md) türleri ve kayan nokta türlerinde bir ifade. Bu durumda, tamsayı türleri için kayan nokta türleri dönüştürülür. İfadenin değerlendirilmesi aşağıdaki kurallara göre gerçekleştirilir:

- Kayan nokta türlerinden biri ise `double`, ifadenin değerlendirdiği `double`, veya [bool](../keywords/bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.
- Yoksa hiçbir `double` değerlendirilen ifade ifadenin türü `float`, veya [bool](../keywords/bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.

Bir kayan nokta ifadesi, aşağıdaki adımlardan birini değerleri içerebilir:

- Pozitif ve negatif sıfırı
- Pozitif ve negatif sonsuz
- Bir sayı değil değeri (NaN)
- Sıfır olmayan değerler sınırlı kümesi

Bu değerler hakkında daha fazla bilgi için bkz. IEEE standardı ikili Floating-Point aritmetik, kullanılabilir [IEEE](https://www.ieee.org) Web sitesi.

Kullanabilirsiniz [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizeleri](../../../standard/base-types/custom-numeric-format-strings.md) bir kayan nokta değeri olarak biçimlendirmek için.

## <a name="floating-point-literals"></a>Kayan nokta değişmez değerleri

Varsayılan olarak, bir kayan nokta sayısal sabit değer atama işlecinin sağ tarafında kabul `double`. Bir kayan veya tamsayı sabit belirli bir türe dönüştürmek için sonekleri kullanabilirsiniz:

- `d` Veya `D` soneki için bir sabit değer dönüştürür bir `double`.
- `f` Veya `F` soneki için bir sabit değer dönüştürür bir `float`.
- `m` Veya `M` soneki için bir sabit değer dönüştürür bir `decimal`.

Aşağıdaki örnekler, her sonek gösterir:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Dönüşümler

Örtük bir dönüştürme (adlı bir *dönüştürme genişletme*) öğesinden `float` için `double` çünkü aralığını `float` değerleri olan uygun bir alt kümesini `double` ve Duyarlılıkkaybıolmadan`float` için `double`.

Örtük bir dönüştürme kaynak türden hedef türe tanımlı değil, bir kayan nokta türü başka bir kayan nokta türüne dönüştürmek için açık bir tür dönüştürme kullanmanız gerekir. Bu adlı bir *daraltma dönüştürmesi*. Dönüştürme veri kaybıyla sonuçlanabildiğinden açık durumda gereklidir. Diğer kayan nokta türleri arasında örtük dönüştürme vardır ve `decimal` türü için `decimal` türünde daha da fazla duyarlığa `float` veya `double`.

Örtük sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).

Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Tam sayı türleri](integral-numeric-types.md)
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
- [Tür Değiştirme ve Tür Dönüştürmeler](../../programming-guide/types/casting-and-type-conversions.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](../keywords/implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Sayısal sonuçlar tablosunu biçimlendirme](../keywords/formatting-numeric-results-table.md)
- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
