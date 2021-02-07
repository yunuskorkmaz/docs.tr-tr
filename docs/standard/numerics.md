---
description: Daha fazla bilgi için bkz. .NET 'te Numerics
title: .NET Sayısal Değerleri
ms.date: 10/18/2018
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
ms.openlocfilehash: 386b5322a19b1f59358a941d7c37f7e5a81df30c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731675"
---
# <a name="numerics-in-net"></a>.NET Sayısal Değerleri

.NET, bir dizi sayısal tamsayı ve kayan nokta temel noktaları ve ayrıca, <xref:System.Numerics.BigInteger?displayProperty=nameWithType> karmaşık sayıları temsil eden bir tamsayı türü <xref:System.Numerics.Complex?displayProperty=nameWithType> ve ad alanında bir Simd etkin türler kümesini temsil eden, teorik bir üst veya alt sınır içeren bir integral türü sağlar <xref:System.Numerics> .
  
## <a name="integer-types"></a>Tam sayı türleri

.NET, aşağıdaki tabloda listelenen hem imzalı hem de imzasız 8, 16-, 32-ve 64 bit tamsayı türlerini destekler:
  
|Tür|İmzalandı/Imzasız|Boyut (bayt)|En küçük değer|En büyük değer|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|İşaretlenmemiş|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|İmza|2|-32.768|32.767|  
|<xref:System.Int32?displayProperty=nameWithType>|İmza|4|-2.147.483.648|2.147.483.647|  
|<xref:System.Int64?displayProperty=nameWithType>|İmza|8|-9223372036854775808|9.223.372.036.854.775.807|  
|<xref:System.SByte?displayProperty=nameWithType>|İmza|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|İşaretlenmemiş|2|0|65.535|  
|<xref:System.UInt32?displayProperty=nameWithType>|İşaretlenmemiş|4|0|4.294.967.295|  
|<xref:System.UInt64?displayProperty=nameWithType>|İşaretlenmemiş|8|0|18446744073709551615|  
  
Her tamsayı türü bir standart aritmetik işleçler kümesini destekler. <xref:System.Math?displayProperty=nameWithType>Sınıfı, daha geniş bir matematik işlevleri kümesi için yöntemler sağlar.

Sınıfını kullanarak bir tamsayı değerindeki tek tek bitler ile de çalışabilirsiniz <xref:System.BitConverter?displayProperty=nameWithType> .  

> [!NOTE]  
> İşaretsiz tamsayı türleri CLS uyumlu değildir. Daha fazla bilgi için bkz. [Dil bağımsızlığı ve Language-Independent bileşenleri](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType>Yapı, teorik içindeki değeri üst veya alt sınır olmadan rastgele büyük bir tamsayıyı temsil eden sabit bir türdür. Türün yöntemleri, <xref:System.Numerics.BigInteger> diğer integral türlerin birbirlerine yakın bir şekilde paraleldir.
  
## <a name="floating-point-types"></a>Kayan nokta türleri

.NET, aşağıdaki tabloda listelenen üç temel kayan nokta türü içerir:
  
|Tür|Boyut (bayt)|Yaklaşık Aralık|Duyarlık|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup>|~ 6-9 basamak|  
|<xref:System.Double?displayProperty=nameWithType>|8|± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup>|~ 15-17 basamak|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup>|28-29 basamak|  
  
Hem hem de <xref:System.Single> <xref:System.Double> türleri, sayı olmayan ve sonsuz olmayan özel değerleri destekler. Örneğin, <xref:System.Double> türü aşağıdaki değerleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType> , <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> . <xref:System.Double.IsNaN%2A?displayProperty=nameWithType> <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType> <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> Bu özel değerleri sınamak için,, ve yöntemlerini kullanın.

Her kayan nokta türü bir standart aritmetik işleçler kümesini destekler. <xref:System.Math?displayProperty=nameWithType>Sınıfı, daha geniş bir matematik işlevleri kümesi için yöntemler sağlar. .NET Core 2,0 ve üzeri, <xref:System.MathF?displayProperty=nameWithType> türün bağımsız değişkenlerini kabul eden yöntemler sağlayan sınıfını içerir <xref:System.Single> .

Ayrıca, sınıfını kullanarak tek bir bit <xref:System.Double> ve değerleri ile çalışabilirsiniz <xref:System.Single> <xref:System.BitConverter?displayProperty=nameWithType> . <xref:System.Decimal?displayProperty=nameWithType>Yapının kendi yöntemleri vardır <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> ve <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29> bir ondalık değerin tek tek bitleri ile çalışmak için ve bazı ek matematik işlemleri gerçekleştirmek için kendi yöntem kümesi vardır.
  
<xref:System.Double>Ve türleri, doğası gereği, <xref:System.Single> kesin bir şekilde (örneğin, iki yıldız arasındaki uzaklık) ve yüksek derecede duyarlık ve küçük yuvarlama hatası gerekmeyen uygulamalar için kullanılmak üzere tasarlanmıştır. <xref:System.Decimal?displayProperty=nameWithType>Daha büyük Duyarlığın gerekli olduğu durumlarda ve yuvarlama hatalarının en aza indirilebilmesi için türü kullanın.

> [!NOTE]
> <xref:System.Decimal>Tür, yuvarlama gereksinimini ortadan kaldırmaz. Bunun yerine, yuvarlama nedeniyle hataları en aza indirir.
  
## <a name="complex"></a>Complex

Yapı, bir <xref:System.Numerics.Complex?displayProperty=nameWithType> karmaşık sayıyı, yani gerçek sayı bölümü ve sanal sayı bölümünü temsil eden bir sayıyı temsil eder. Matematiksel, Algebraic ve trigonometrik yöntemlerin yanı sıra standart bir aritmetik, karşılaştırma, eşitlik, açık ve örtük dönüştürme işleçleri kümesini destekler.  
  
## <a name="simd-enabled-types"></a>SIMD özellikli türler

<xref:System.Numerics>Ad alanı, bir dizi .net SIMD etkin türler içerir. SıMD (Tek Yönerge Birden Çok Veri) işlemleri donanım düzeyinde paralelleştirilmiş olabilir. Bu, matematiksel, bilimsel ve grafik uygulamalarda ortak olan vektörleştirilmiş hesaplamaların verimini artırır.
  
.NET SıMD özellikli türler şunları içerir:

- <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3> <xref:System.Numerics.Vector4> 2, 3 ve 4 değerli vektörleri temsil eden, ve türleri <xref:System.Single> .

- <xref:System.Numerics.Matrix3x2>Bir 3X2 matrisini temsil eden ve <xref:System.Numerics.Matrix4x4> bir 4x4 matrisini temsil eden iki matris türü.

- <xref:System.Numerics.Plane>Üç boyutlu alanda bir düzlemi temsil eden tür.

- <xref:System.Numerics.Quaternion>Üç boyutlu fiziksel döndürmeler kodlamak için kullanılan bir vektörü temsil eden tür.

- <xref:System.Numerics.Vector%601>Belirtilen bir sayısal türün vektörünü temsil eden ve SıMD desteğinden yararlanan geniş bir işleç kümesi sağlayan tür. Bir <xref:System.Numerics.Vector%601> Örneğin sayısı sabittir, ancak değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> , kodun yürütüldüğü makinenin CPU 'suna bağlıdır.

  > [!NOTE]
  > <xref:System.Numerics.Vector%601>Tür .NET Core ve .NET 5 + ile birlikte gelir, ancak .NET Framework değildir. .NET Framework kullanıyorsanız, bu türe erişim sağlamak için [System. Numerics. vektörleri](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet paketini yükledikten sonra.
  
SıMD özellikli türler, SıMD özellikli olmayan donanımla veya JıT derleyicilerle kullanılabilecek şekilde uygulanır. SıMD yönergelerinden yararlanmak için 64 bitlik uygulamalarınızın, .NET Core 'a ve .NET Framework 4,6 ve sonraki sürümlere dahil olan RyuJIT derleyicisini kullanan çalışma zamanı tarafından çalıştırılması gerekir. 64 bitlik işlemcileri hedeflerken SıMD desteği ekler.

Daha fazla bilgi için bkz. [SıMD-hızlandırılmış sayısal türleri kullanma](simd.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Standart Sayısal Biçim Dizeleri](base-types/standard-numeric-format-strings.md)
