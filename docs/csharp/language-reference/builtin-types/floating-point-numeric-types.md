---
title: Kayan nokta sayısal türleri-C# başvurusu
description: 'Yerleşik C# kayan nokta türleri hakkında bilgi edinin: float, Double ve Decimal'
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
ms.openlocfilehash: a1142d1aa04003ae1942902672cfc7a05edc99c0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662673"
---
# <a name="floating-point-numeric-types-c-reference"></a>Kayan nokta sayısal türleri (C# Başvurusu)

*Kayan nokta sayısal türleri* gerçek sayıları temsil eder. Tüm kayan nokta sayısal türleri [değer türlerdir](value-types.md). Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#real-literals)ile başlatılabilir. Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.

## <a name="characteristics-of-the-floating-point-types"></a>Kayan nokta türlerinin özellikleri

C#, aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:
  
|C# türü/anahtar sözcüğü|Yaklaşık Aralık|Duyarlık|Boyut|.NET türü|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup>|~ 6-9 basamak|4 bayt|<xref:System.Single?displayProperty=nameWithType>|
|`double`|± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup>|~ 15-17 basamak|8 bayt|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup>|28-29 basamak|16 bayt|<xref:System.Decimal?displayProperty=nameWithType>|

Yukarıdaki tabloda, en soldaki sütundan her C# tür anahtar sözcüğü, karşılık gelen .NET türü için bir diğer addır. Bunlar arasında değiştirilebilir. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Her kayan nokta türünün varsayılan değeri sıfırdır `0` . Kayan nokta türlerinin her biri, `MinValue` `MaxValue` Bu türün minimum ve maksimum sonlu değerini sağlayan ve sabitleridir. `float`Ve `double` türleri ayrıca, sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar. Örneğin, `double` türü aşağıdaki sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType> , <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .

`decimal`Türün hem hem de daha küçük bir aralığı olduğundan `float` `double` , bu, mali ve parasal hesaplamalar için uygundur.

Bir ifadede [integral](integral-numeric-types.md) türlerini ve `float` ve türlerini karıştırabilirsiniz `double` . Bu durumda, integral türler örtük olarak kayan nokta türlerinden birine dönüştürülür ve gerekirse `float` tür örtülü olarak dönüştürülür `double` . İfade, aşağıdaki gibi değerlendirilir:

- `double`İfadede tür varsa, ifade olarak `double` veya [`bool`](bool.md) ilişkisel ve eşitlik karşılaştırmaları olarak değerlendirilir.
- İfadede hiçbir tür yoksa `double` , ifade olarak `float` veya `bool` ilişkisel ve eşitlik karşılaştırmaları olarak değerlendirilir.

Ayrıca integral türlerini ve `decimal` bir ifadede türü karıştırabilirsiniz. Bu durumda, integral türleri örtük olarak `decimal` türüne dönüştürülür ve ifade olarak `decimal` veya `bool` ilişkisel ve eşitlik karşılaştırmaları olarak değerlendirilir.

`decimal`Türü `float` `double` bir ifadede ve türleriyle karıştırılamaz. Bu durumda, aritmetik, karşılaştırma veya eşitlik işlemleri gerçekleştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi, işlenenleri ya da türünden türüne açıkça dönüştürmeniz gerekir `decimal` :

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.

## <a name="real-literals"></a>Gerçek sabit değerler

Gerçek bir sabit değerin türü, soneki tarafından aşağıdaki şekilde belirlenir:

- Sonek olmadan veya veya sonekine sahip sabit `d` değer `D` türü`double`
- Veya sonekine sahip sabit `f` değer `F` tür`float`
- Veya sonekine sahip sabit `m` değer `M` tür`decimal`

Aşağıdaki kod, her birine bir örnek gösterir:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

Yukarıdaki örnek ayrıca `_` C# 7,0 ile başlayarak desteklenen bir *rakam ayırıcısı*olarak kullanımını gösterir. Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.

Ayrıca, aşağıdaki örnekte gösterildiği gibi bilimsel gösterim kullanabilirsiniz, yani gerçek bir sabit değerin üs bir kısmını belirtebilirsiniz:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Dönüşümler

Kayan nokta sayısal türleri arasında yalnızca bir örtük dönüşüm vardır: öğesinden `float` öğesine `double` . Ancak, herhangi bir kayan nokta türünü [açık atama](../operators/type-testing-and-cast.md#cast-expression)ile başka bir kayan nokta türüne dönüştürebilirsiniz. Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Kayan nokta türleri](~/_csharplang/spec/types.md#floating-point-types)
- [Ondalık tür](~/_csharplang/spec/types.md#the-decimal-type)
- [Gerçek sabit değerler](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Integral türleri](integral-numeric-types.md)
- [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
