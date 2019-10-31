---
title: .NET Sayısal Değerleri
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
ms.openlocfilehash: e5815058898cac165e7a47d761ee86bb9c4cb940
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091597"
---
# <a name="numerics-in-net"></a>.NET Sayısal Değerleri

.NET, bir dizi sayısal tamsayı ve kayan nokta temel noktaları ve <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, teorik bir üst veya alt sınır olmadan bir integral türü, karmaşık sayıları temsil eden <xref:System.Numerics.Complex?displayProperty=nameWithType>ve <xref:System.Numerics> ad alanında bir SIMD özellikli türler kümesi sağlar .
  
## <a name="integer-types"></a>Tam sayı türleri

.NET, aşağıdaki tabloda listelenen hem imzalı hem de imzasız 8, 16-, 32-ve 64 bit tamsayı türlerini destekler:
  
|Tür|İmzalandı/Imzasız|Boyut (bayt)|En küçük değer|En büyük değer|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|İşaretlenmemiş|1\.|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|İmza|2|-32.768|32.767|  
|<xref:System.Int32?displayProperty=nameWithType>|İmza|4|-2.147.483.648|2\.147.483.647|  
|<xref:System.Int64?displayProperty=nameWithType>|İmza|8|-9223372036854775808|9\.223.372.036.854.775.807|  
|<xref:System.SByte?displayProperty=nameWithType>|İmza|1\.|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|İşaretlenmemiş|2|0|65.535|  
|<xref:System.UInt32?displayProperty=nameWithType>|İşaretlenmemiş|4|0|4\.294.967.295|  
|<xref:System.UInt64?displayProperty=nameWithType>|İşaretlenmemiş|8|0|18446744073709551615|  
  
Her tamsayı türü bir standart aritmetik işleçler kümesini destekler. <xref:System.Math?displayProperty=nameWithType> sınıfı, daha geniş bir matematik işlevleri kümesi için yöntemler sağlar.

Ayrıca, <xref:System.BitConverter?displayProperty=nameWithType> sınıfını kullanarak bir tamsayı değerindeki tek bir bitler ile de çalışabilirsiniz.  

> [!NOTE]  
> İşaretsiz tamsayı türleri CLS uyumlu değildir. Daha fazla bilgi için bkz. [Dil bağımsızlığı ve dilden bağımsız bileşenler](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısı, teorik içindeki değeri üst veya alt sınır olmadan rastgele büyük bir tamsayıyı temsil eden sabit bir türdür. <xref:System.Numerics.BigInteger> türünün yöntemleri, diğer integral türlerin birbirlerine yakın bir şekilde paraleldir.
  
## <a name="floating-point-types"></a>Kayan nokta türleri

.NET, aşağıdaki tabloda listelenen üç temel kayan nokta türü içerir:
  
|Tür|Boyut (bayt)|Yaklaşık Aralık|Duyarlık|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup>|~ 6-9 basamak|  
|<xref:System.Double?displayProperty=nameWithType>|8|± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup>|~ 15-17 basamak|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup>|28-29 basamak|  
  
Hem <xref:System.Single> hem de <xref:System.Double> türleri bir sayı değil ve sonsuz olmayan özel değerleri destekler. Örneğin, <xref:System.Double> türü şu değerleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Bu özel değerleri sınamak için <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>ve <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> yöntemlerini kullanırsınız.

Her kayan nokta türü bir standart aritmetik işleçler kümesini destekler. <xref:System.Math?displayProperty=nameWithType> sınıfı, daha geniş bir matematik işlevleri kümesi için yöntemler sağlar. .NET Core 2,0 ve üzeri, <xref:System.Single> türünün bağımsız değişkenlerini kabul eden yöntemler sağlayan <xref:System.MathF?displayProperty=nameWithType> sınıfını içerir.

Ayrıca, <xref:System.BitConverter?displayProperty=nameWithType> sınıfını kullanarak <xref:System.Double> ve <xref:System.Single> değerlerinde tek bir bit ile çalışabilirsiniz. <xref:System.Decimal?displayProperty=nameWithType> yapısının kendi yöntemlerine, <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> ve <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, Ondalık değerin tek tek bitleri ile çalışmaya ve bazı ek matematiksel işlemler gerçekleştirmeye yönelik kendi yöntem kümesine sahip olduğu bir yöntem vardır.
  
<xref:System.Double> ve <xref:System.Single> türlerinin, doğası (iki yıldız arasındaki uzaklık) ve yüksek derecede duyarlık ve küçük yuvarlama hatası olması gereken uygulamalar için kullanılmak üzere tasarlanmıştır. Daha büyük duyarlık gerektiren durumlar için <xref:System.Decimal?displayProperty=nameWithType> türünü kullanmanız gerekir ve yuvarlama hataları en aza indirilir.

> [!NOTE]
> <xref:System.Decimal> türü, yuvarlama gereksinimini ortadan kaldırmaz. Bunun yerine, yuvarlama nedeniyle hataları en aza indirir.
  
## <a name="complex"></a>Complex

<xref:System.Numerics.Complex?displayProperty=nameWithType> yapısı karmaşık bir sayıyı, yani gerçek sayı bölümü ve sanal sayı bölümünü temsil eden bir sayıyı temsil eder. Matematiksel, Algebraic ve trigonometrik yöntemlerin yanı sıra standart bir aritmetik, karşılaştırma, eşitlik, açık ve örtük dönüştürme işleçleri kümesini destekler.  
  
## <a name="simd-enabled-types"></a>SıMD özellikli türler

<xref:System.Numerics> ad alanı, .NET SıMD özellikli türler kümesi içerir. SıMD (Tek Yönerge Birden Çok Veri) işlemleri donanım düzeyinde paralelleştirilmiş olabilir. Bu, matematiksel, bilimsel ve grafik uygulamalarda ortak olan vektörleştirilmiş hesaplamaların verimini artırır.
  
.NET SıMD özellikli türler şunları içerir:

- 2, 3 ve 4 <xref:System.Single> değeri olan vektörleri temsil eden <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>ve <xref:System.Numerics.Vector4> türleri.

- İki matris türü, bir 3X2 matrisini temsil eden <xref:System.Numerics.Matrix3x2>ve bir 4x4 matrisini temsil eden <xref:System.Numerics.Matrix4x4>.

- Üç boyutlu alanda bir düzlemi temsil eden <xref:System.Numerics.Plane> türü.

- Üç boyutlu fiziksel döndürmeler kodlamak için kullanılan bir vektörü temsil eden <xref:System.Numerics.Quaternion> türü.

- Belirtilen bir sayısal türün vektörünü temsil eden <xref:System.Numerics.Vector%601> türü ve SıMD desteğinden yararlanan geniş bir işleç kümesi sağlar. Bir <xref:System.Numerics.Vector%601> örneğinin sayısı sabittir, ancak değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType>, kodun yürütüldüğü makinenin CPU 'suna bağlıdır.
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> türü .NET Framework dahil değildir. Bu türe erişim sağlamak için [System. Numerics. vektörleri](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet paketini yüklemelisiniz.
  
SıMD özellikli türler, SıMD özellikli olmayan donanımla veya JıT derleyicilerle kullanılabilecek şekilde uygulanır. SıMD yönergelerinden yararlanmak için 64 bitlik uygulamalarınızın, .NET Core 'a ve .NET Framework 4,6 ve sonraki sürümlere dahil olan RyuJIT derleyicisini kullanan çalışma zamanı tarafından çalıştırılması gerekir. 64 bitlik işlemcileri hedeflerken SıMD desteği ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Temelleri](application-essentials.md)
- [Standart Sayısal Biçim Dizeleri](base-types/standard-numeric-format-strings.md)
