---
title: Kayan nokta sayısal türleri- C# başvuru
description: Yerleşik C# kayan nokta türlerine genel bakış
ms.date: 10/22/2019
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
ms.openlocfilehash: 9fde2b28288b58d7da3a4d003ec50af7d7e7a965
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980177"
---
# <a name="floating-point-numeric-types-c-reference"></a>Kayan nokta sayısal türleri (C# başvuru)

**Kayan nokta türleri** **basit türlerin** bir alt kümesidir ve [*değişmez değerler*](#real-literals)ile başlatılabilir. Tüm kayan nokta türleri de değer türlerdir. Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.

## <a name="characteristics-of-the-floating-point-types"></a>Kayan nokta türlerinin özellikleri

C#aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:
  
|C#tür/anahtar sözcük|Yaklaşık Aralık|Duyarlık|Boyut|.NET türü|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup>|~ 6-9 basamak|4 bayt|<xref:System.Single?displayProperty=nameWithType>|
|`double`|± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup>|~ 15-17 basamak|8 bayt|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup>|28-29 basamak|16 bayt|<xref:System.Decimal?displayProperty=nameWithType>|

Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır. Bunlar arasında değiştirilebilir. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Her kayan nokta türünün varsayılan değeri sıfırdır `0`. Kayan nokta türlerinin her biri, bu türün minimum ve maksimum sonlu değerini sağlayan `MinValue` ve `MaxValue` sabitlerini içerir. `float` ve `double` türleri, sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar. Örneğin, `double` türü şu sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

`decimal` türü daha fazla kesinlik ve `float` ve `double`daha küçük bir aralığa sahip olduğundan, finansal ve parasal hesaplamalar için uygundur.

Bir ifadede [integral](integral-numeric-types.md) türlerini ve kayan nokta türlerini karıştırabilirsiniz. Bu durumda, integral türler kayan nokta türlerine dönüştürülür. İfadenin değerlendirmesi aşağıdaki kurallara göre gerçekleştirilir:

- Kayan nokta türlerinden biri `double`, ifade `double`veya ilişkisel ve eşitlik karşılaştırmalarında [bool](bool.md) olarak değerlendirilir.
- İfadede `double` tür yoksa, ifade `float`veya ilişkisel ve eşitlik karşılaştırmalarında [bool](bool.md) olarak değerlendirilir.

Kayan nokta ifadesi aşağıdaki değer kümelerini içerebilir:

- Pozitif ve negatif sıfır
- Pozitif ve negatif sonsuzluk
- Sayı olmayan değer (NaN)
- Sınırlı olmayan değerler kümesi

Bu değerler hakkında daha fazla bilgi için, [IEEE](https://www.ieee.org) Web sitesinde kullanılabilen Ikili kayan nokta ARITMETIĞI Için IEEE Standard ' a bakın.

Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.

## <a name="real-literals"></a>Gerçek sabit değerler

Gerçek bir sabit değerin türü, soneki tarafından aşağıdaki şekilde belirlenir:

- Sonek olmadan veya `d` ya da `D` sonekine sahip sabit değer `double` türündedir
- `f` veya `F` sonekine sahip sabit değer `float` türündedir
- `m` veya `M` sonekine sahip sabit değer `decimal` türündedir

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

Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir. Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.

Ayrıca, aşağıdaki örnekte gösterildiği gibi bilimsel gösterim kullanabilirsiniz, yani gerçek bir sabit değerin üs bir kısmını belirtebilirsiniz:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Dönüşümler

Kayan nokta sayısal türleri arasında yalnızca bir örtük dönüşüm vardır: `float` 'den `double`. Ancak, herhangi bir kayan nokta türünü [açık atama](../operators/type-testing-and-cast.md#cast-operator-)ile başka bir kayan nokta türüne dönüştürebilirsiniz. Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Kayan nokta türleri](~/_csharplang/spec/types.md#floating-point-types)
- [Ondalık tür](~/_csharplang/spec/types.md#the-decimal-type)
- [Gerçek sabit değerler](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [Integral türleri](integral-numeric-types.md)
- [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
