---
title: Kayan nokta sayısal türleri - C# referansı
description: 'Yerleşik C# kayan nokta türleri hakkında bilgi edinin: float, double ve ondalık'
ms.date: 02/10/2020
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a277215d438b5f6b0bbbef72e5e0121b6ce41990
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121478"
---
# <a name="floating-point-numeric-types-c-reference"></a>Kayan nokta sayısal türleri (C# başvurusu)

*Kayan nokta sayısal türleri* gerçek sayıları temsil ediyor. Tüm kayan nokta sayısal türleri [değer türleridir.](value-types.md) Onlar da [basit türleri](value-types.md#built-in-value-types) ve [literals](#real-literals)ile başharfolabilir. Tüm kayan nokta sayısal türleri [aritmetik,](../operators/arithmetic-operators.md) [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.

## <a name="characteristics-of-the-floating-point-types"></a>Kayan nokta türlerinin özellikleri

C# aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:
  
|C# türü/anahtar kelime|Yaklaşık aralık|Duyarlık|Boyut|.NET türü|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> ila ±3,4 x 10<sup>38</sup>|~6-9 basamak|4 bayt|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5,0 × 10<sup>−324</sup> ile ±1,7 ×<sup>10 308</sup>|~15-17 basamak|8 bayt|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> ile ±7,9228 x 10<sup>28</sup>|28-29 basamak|16 bayt|<xref:System.Decimal?displayProperty=nameWithType>|

Önceki tabloda, soldaki sütundaki her C# türü anahtar sözcüğü karşılık gelen .NET türüiçin bir diğer addır. Değiştirilebilirler. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Her kayan nokta türünün varsayılan değeri `0`sıfırdır. Kayan nokta türlerinin her `MinValue` biri, bu türün minimum ve maksimum sonlu değerini sağlayan sabitlere `MaxValue` sahiptir. `float` Ve `double` türleri de değil-a-sayı ve sonsuz değerleri temsil eden sabitler sağlar. `double` Örneğin, tür aşağıdaki sabitleri <xref:System.Double.NaN?displayProperty=nameWithType>sağlar: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, ve .

`decimal` Türü her ikisinden `float` de daha hassas ve daha küçük bir aralıkta olduğundan ve `double`finansal ve parasal hesaplamalar için uygundur.

Bir ifadede [integral](integral-numeric-types.md) `float` türlerini ve türleri `double` karıştırabilirsiniz. Bu durumda, integral türleri örtülü olarak kayan nokta türlerinden birine dönüştürülür `float` ve gerekirse tür örtülü `double`olarak . İfade, aşağıdaki gibi değerlendirilir:

- İfadede `double` tür varsa, ifade ilişkisel `double`ve eşitlik [`bool`](bool.md) karşılaştırmalarını değerlendirir.
- İfadede bir `double` tür yoksa, ifade ilişkisel `float`ve `bool` eşitlik karşılaştırmalarını değerlendirir.

Ayrıca, bir ifadedeki `decimal` integral türlerini ve türünü de karıştırabilirsiniz. Bu durumda, integral türleri örtülü olarak `decimal` türe dönüştürülür ve `decimal`ifade, `bool` ilişkisel ve eşitlik karşılaştırmaları için veya değerlendirir.

Bir ifadedeki `decimal` türü `float` ve `double` türleri karıştıramazsınız. Bu durumda, aritmetik, karşılaştırma veya eşitlik işlemleri gerçekleştirmek istiyorsanız, aşağıdaki örnekte görüldüğü gibi, operandları açıkça türe `decimal` dönüştürmeniz gerekir:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

Kayan nokta değerini biçimlendirmek için [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizeleri](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.

## <a name="real-literals"></a>Gerçek edebi

Gerçek bir edebi türü, sonek tarafından aşağıdaki gibi belirlenir:

- Sonek olmayan veya `d` `D` sonek olan edebi`double`
- Veya `F` sonek `f` ile literal türü`float`
- Veya `M` sonek `m` ile literal türü`decimal`

Aşağıdaki kod her birinin bir örneğini gösterir:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

Yukarıdaki örnek, C# 7.0 ile başlayan desteklenen bir basamak `_` *ayırıcısı*olarak da kullanılır. Sayısal literals her türlü ile basamak ayırıcı kullanabilirsiniz.

Aşağıdaki örnekte görüldüğü gibi, bilimsel gösterimi, diğer bir şekilde gerçek bir edebi bölümün üslü bir bölümünü belirtebilirsiniz:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Dönüşümler

Kayan nokta sayısal türleri arasında yalnızca bir örtük `float` `double`dönüştürme vardır: .'a kadar Ancak, herhangi bir kayan nokta türünü [açık dökümle](../operators/type-testing-and-cast.md#cast-expression)başka bir kayan nokta türüne dönüştürebilirsiniz. Daha fazla bilgi için yerleşik [sayısal dönüşümlere](numeric-conversions.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Kayan nokta türleri](~/_csharplang/spec/types.md#floating-point-types)
- [Ondalık tür](~/_csharplang/spec/types.md#the-decimal-type)
- [Gerçek edebi](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [İntegral tipleri](integral-numeric-types.md)
- [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
