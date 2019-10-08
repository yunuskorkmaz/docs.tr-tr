---
title: Kayan nokta sayısal türleri- C# başvuru
description: Yerleşik C# kayan nokta türlerine genel bakış
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002200"
---
# <a name="floating-point-numeric-types-c-reference"></a>Kayan nokta sayısal türleri (C# başvuru)

**Kayan nokta türleri** **basit türlerin** bir alt kümesidir ve [*değişmez değerler*](#floating-point-literals)ile başlatılabilir. Tüm kayan nokta türleri de değer türlerdir. Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçlerini destekler.

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

Her kayan nokta türünün varsayılan değeri sıfır, `0` ' dır. Kayan nokta türlerinin her biri, bu türün minimum ve maksimum sonlu değerini sağlayan `MinValue` ve `MaxValue` sabitleri vardır. @No__t-0 ve `double` türleri ayrıca sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar. Örneğin, `double` türü şu sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

@No__t-0 türü daha fazla duyarlık ve `float` ve `double` ' den daha küçük bir aralığa sahip olduğundan, finansal ve parasal hesaplamalar için uygundur.

Bir ifadede [integral](integral-numeric-types.md) türlerini ve kayan nokta türlerini karıştırabilirsiniz. Bu durumda, integral türler kayan nokta türlerine dönüştürülür. İfadenin değerlendirmesi aşağıdaki kurallara göre gerçekleştirilir:

- Kayan nokta türlerinden biri `double` ise, ifade `double` ' i veya ilişkisel karşılaştırmalarda [bool](../keywords/bool.md) ya da eşitlik karşılaştırmaları ' ne göre değerlendirilir.
- İfadede `double` türü yoksa, ifade `float` ' i veya ilişkisel karşılaştırmalar ya da eşitlik karşılaştırmaları için [bool](../keywords/bool.md) değerini değerlendirir.

Kayan nokta ifadesi aşağıdaki değer kümelerini içerebilir:

- Pozitif ve negatif sıfır
- Pozitif ve negatif sonsuzluk
- Sayı olmayan değer (NaN)
- Sınırlı olmayan değerler kümesi

Bu değerler hakkında daha fazla bilgi için, [IEEE](https://www.ieee.org) Web sitesinde kullanılabilen Ikili kayan nokta ARITMETIĞI Için IEEE Standard ' a bakın.

Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.

## <a name="floating-point-literals"></a>Kayan nokta sabit değerleri

Varsayılan olarak, atama işlecinin sağ tarafındaki kayan nokta sayısal değişmez değeri `double` olarak değerlendirilir. Bir kayan nokta veya integral sabit değerini belirli bir türe dönüştürmek için son ekleri kullanabilirsiniz:

- @No__t-0 veya `D` soneki, bir sabit değeri `double` ' e dönüştürür.
- @No__t-0 veya `F` soneki, bir sabit değeri `float` ' e dönüştürür.
- @No__t-0 veya `M` soneki, bir sabit değeri `decimal` ' e dönüştürür.

Aşağıdaki örneklerde her bir sonek gösterilmektedir:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Dönüşümler

@No__t-1 ' den `double` ' ye ait `float` değerlerinin doğru bir alt @no__t kümesi olduğundan ve `float` ' e `double` ' a bir duyarlık kaybı olmadığı için,-1 ' den-2 ' den örtük bir dönüştürme ( *genişleyen dönüştürme*denir) vardır.

Örtük bir dönüştürme, kaynak türünden hedef türüne tanımlanmamışsa, bir kayan nokta türünü başka bir kayan nokta türüne dönüştürmek için açık bir atama kullanmanız gerekir. Bu, *daraltma dönüştürmesi*olarak adlandırılır. Dönüştürme işlemi veri kaybına neden olabileceğinden açık durum gereklidir. @No__t-1 türü `float` veya `double` ' ten daha büyük bir duyarlık içerdiğinden, diğer kayan nokta türleri ve `decimal` türü arasında örtük dönüşüm yoktur.

Örtük Sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [örtük sayısal dönüştürmeler tablosu](../keywords/implicit-numeric-conversions-table.md).

Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Açık Sayısal Dönüşümler Tablosu](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [Integral türleri](integral-numeric-types.md)
- [Yerleşik türler tablosu](../keywords/built-in-types-table.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
- [Tür Değiştirme ve Tür Dönüştürmeler](../../programming-guide/types/casting-and-type-conversions.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](../keywords/implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Sayısal sonuçlar tablosunu biçimlendirme](../keywords/formatting-numeric-results-table.md)
- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
