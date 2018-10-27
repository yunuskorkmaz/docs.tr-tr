---
title: .NET sayısal değerleri
ms.date: 10/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f180e459764d6e8e4484072218f01c8bab8a3b5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191161"
---
# <a name="numerics-in-net"></a>.NET sayısal değerleri

.NET sağlayan bir dizi sayısal tamsayı ve kayan nokta temelleri yanı <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, teorik bir üst veya alt sınırı, integral türünde olduğu <xref:System.Numerics.Complex?displayProperty=nameWithType>, karmaşık sayılar ve bir dizi SIMDetkintürlerindegösterir<xref:System.Numerics> ad alanı.
  
## <a name="integer-types"></a>Tamsayı türleri

.NET, hem imzalı ve imzasız 8 - 16, 32- ve 64-bit tamsayı türleri, aşağıdaki tabloda listelenen destekler:
  
|Tür|İmzalı/imzasız|Boyut (bayt cinsinden)|En düşük değer|En yüksek değer|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|İşaretsiz|1.|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|İmzalı|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|İmzalı|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|İmzalı|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|İmzalı|1.|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|İşaretsiz|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|İşaretsiz|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|İşaretsiz|8|0|18,446,744,073,709,551,615|  
  
Her bir tamsayı türü standart aritmetik işleçleri kümesini destekler. <xref:System.Math?displayProperty=nameWithType> Sınıfı daha geniş bir matematiksel işlevler kümesi için yöntemler sağlar.

Ayrıca bir tamsayı değeri içinde tek tek BITS kullanarak çalışabilirsiniz <xref:System.BitConverter?displayProperty=nameWithType> sınıfı.  

> [!NOTE]  
> İşaretsiz tamsayı türleri CLS uyumlu değildir. Daha fazla bilgi için [dil bağımsızlığı ve dilden bağımsız bileşenler](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> Yapısıdır teorik değeri üst veya alt sınır yoktur sahip büyük bir tamsayı temsil eden sabit bir tür. Yöntemlerinin <xref:System.Numerics.BigInteger> türü yakından paralel bir tam sayı türleri olanlar.
  
## <a name="floating-point-types"></a>Kayan nokta türleri

.NET aşağıdaki tabloda listelenen üç temel kayan nokta türleri içerir:
  
|Tür|Boyut (bayt cinsinden)|Yaklaşık aralık|Duyarlık|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1.5 x 10<sup>−45</sup> ±3.4 x 10 için<sup>38</sup>|~ 6-9 basamak|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup>|yaklaşık 15-17 basamak|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1.0 x 10<sup>-28</sup> ±7.9228 x 10 için<sup>28</sup>|28-29 basamak|  
  
Her ikisi de <xref:System.Single> ve <xref:System.Double> türlerini destekleyen bir sayı değil ve sonsuzluk temsil eden özel değerler. Örneğin, <xref:System.Double> türü, aşağıdaki değerleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Kullandığınız <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>, ve <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> bu özel değerler için test etmek için yöntemleri.

Her bir kayan nokta türü standart aritmetik işleçleri kümesini destekler. <xref:System.Math?displayProperty=nameWithType> Sınıfı daha geniş bir matematiksel işlevler kümesi için yöntemler sağlar. .NET core 2.0 ve sonraki sürümleri içeren <xref:System.MathF?displayProperty=nameWithType> bağımsız değişkenleri kabul yöntemler sağlar sınıfını <xref:System.Single> türü.

Ayrıca ayrı BITS ile çalışabilir <xref:System.Double> ve <xref:System.Single> kullanarak değerleri <xref:System.BitConverter?displayProperty=nameWithType> sınıfı. <xref:System.Decimal?displayProperty=nameWithType> Yapısının kendi yöntemlerini <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> ve <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, tek bir ondalık değer ile çalışmak için bazı ek matematik işlemlerini gerçekleştirmek için yöntemleri kendi kümesini yanı sıra BITS.
  
<xref:System.Double> Ve <xref:System.Single> türleri tarafından doğasını (örneğin, iki yıldız arasındaki uzaklığı) kesin değerler için kullanılacak yöneliktir ve uygulamaların, yüksek derecede duyarlık ve küçük hata yuvarlama gerekli değildir. Kullanmanız gereken <xref:System.Decimal?displayProperty=nameWithType> türü için daha büyük olduğu durumlarda duyarlık gereklidir ve yuvarlama hataları simge.

> [!NOTE]
> <xref:System.Decimal> Türü olmayan yuvarlama gereksinimini ortadan kaldırır. Bunun yerine, bunu nedeniyle yuvarlama hatalarını en aza indirir.
  
## <a name="complex"></a>Complex

<xref:System.Numerics.Complex?displayProperty=nameWithType> Yapısı, karmaşık bir sayıyı, diğer bir deyişle, bir gerçek sayı ve bir sanal numarası bölümlerini sayıyla temsil eder. Bu, aritmetik, karşılaştırma, eşitlik, açık ve örtük dönüşüm işleçleri yanı sıra matematik, cebirsel ve trigonometrik yöntemleri standart bir kümesini destekler.  
  
## <a name="simd-enabled-types"></a>SIMD etkin türleri

<xref:System.Numerics> Ad alanı .NET SIMD etkin türleri kümesi içerir. SIMD (tek yönerge birden çok veri) işlemleri donanım düzeyinde paralel hale. İçinde ortak vektör haline getirilmiş hesaplamaları verimini artırır matematik, bilimsel ve grafik uygulamaları.
  
.NET SIMD etkin türleri aşağıdakileri kapsamaktadır:

- <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, Ve <xref:System.Numerics.Vector4> 2, 3 ve 4 ile vektör temsil eden türleri <xref:System.Single> değerleri.

- İki matris türü <xref:System.Numerics.Matrix3x2>, bir 3 x 2 matrisi temsil eder ve <xref:System.Numerics.Matrix4x4>, 4 x 4 matrisi temsil eder.

- <xref:System.Numerics.Plane> Üç boyutlu boşluk düzlemde temsil eden tür.

- <xref:System.Numerics.Quaternion> Türü, üç boyutlu fiziksel dönüşümüne kodlamak için kullanılan bir vektörü temsil eder.

- <xref:System.Numerics.Vector%601> Belirtilen bir sayısal tür oluşan bir vektörü temsil eder ve çok sayıda SIMD Destek'ten yararlanan işleçler sağlayan tür. Sayısı bir <xref:System.Numerics.Vector%601> örneği sabittir, değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> kod yürütüldüğünde makinenin CPU üzerinde bağlıdır.
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Türü .NET Framework'e dahil değildir. Yüklemelisiniz [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) bu türe erişmek için NuGet paketi.
  
SIMD etkin türleri, bunların donanım SIMD etkin olmayan veya JIT derleyicileri ile kullanılabilir şekilde uygulanır. SIMD yönergeleri yararlanmak için 64-bit uygulamalar .NET Core ve .NET Framework 4.6 ve sonraki sürümlerinde bulunan Ryujıt derleyicinin kullandığı çalışma zamanı tarafından çalıştırılmalıdır. 64-bit işlemcileri hedeflerken SIMD desteği ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Temelleri](application-essentials.md)
- [Standart Sayısal Biçim Dizeleri](base-types/standard-numeric-format-strings.md)
