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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091597"
---
# <a name="numerics-in-net"></a>.NET Sayısal Değerleri

.NET, teorik üst veya alt sınıra sahip olmayan, <xref:System.Numerics.BigInteger?displayProperty=nameWithType> <xref:System.Numerics.Complex?displayProperty=nameWithType>karmaşık sayıları temsil eden ve <xref:System.Numerics> ad alanında SIMD özellikli bir dizi türü olan sayısal tamsayı ve kayan nokta ilkellerinin yanı sıra bir dizi sayısal tamsayı sağlar.
  
## <a name="integer-types"></a>Tam sayı türleri

.NET, aşağıdaki tabloda listelenen imzalı ve imzasız 8, 16, 32 ve 64 bit'lik tümseger türlerini destekler:
  
|Tür|İmzalı/İmzasız|Boyut (bayt olarak)|En küçük değer|En büyük değer|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Imzasız|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Imzalı|2|-32,768|32.767|  
|<xref:System.Int32?displayProperty=nameWithType>|Imzalı|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Imzalı|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Imzalı|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Imzasız|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Imzasız|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Imzasız|8|0|18,446,744,073,709,551,615|  
  
Her tamsayı türü standart aritmetik işleçleri kümesini destekler. Sınıf, <xref:System.Math?displayProperty=nameWithType> daha geniş bir matematiksel işlev ler kümesi için yöntemler sağlar.

Sınıfı kullanarak <xref:System.BitConverter?displayProperty=nameWithType> bir sonda değerindeki tek tek bitlerle de çalışabilirsiniz.  

> [!NOTE]  
> İmzalanmamış tümsader türleri CLS uyumlu değildir. Daha fazla bilgi için [bkz.](language-independence-and-language-independent-components.md)

## <a name="biginteger"></a>BigInteger

Yapı, <xref:System.Numerics.BigInteger?displayProperty=nameWithType> teoride değeri üst veya alt sınırları olmayan rasgele büyük bir sayayı temsil eden değişmez bir türdür. <xref:System.Numerics.BigInteger> Türün yöntemleri diğer integral türlerinin yöntemlerine yakından paraleldir.
  
## <a name="floating-point-types"></a>Kayan nokta türleri

.NET, aşağıdaki tabloda listelenen üç ilkel kayan nokta türü içerir:
  
|Tür|Boyut (bayt olarak)|Yaklaşık aralık|Duyarlık|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1,5 x 10<sup>−45</sup> ila ±3,4 x 10<sup>38</sup>|~6-9 basamak|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5,0 × 10<sup>−324</sup> ile ±1,7 ×<sup>10 308</sup>|~15-17 basamak|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1,0 x 10<sup>-28</sup> ile ±7,9228 x 10<sup>28</sup>|28-29 basamak|  
  
Hem <xref:System.Single> <xref:System.Double> de türler, sayı olmayan ve sonsuzluğu temsil eden özel değerleri destekler. <xref:System.Double> Örneğin, tür aşağıdaki değerleri <xref:System.Double.NaN?displayProperty=nameWithType>sağlar: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>ve . Bu özel <xref:System.Double.IsNaN%2A?displayProperty=nameWithType> <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>değerleri <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>test <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> etmek için , , ve yöntemleri kullanırsınız.

Her kayan nokta türü standart aritmetik işleçleri kümesini destekler. Sınıf, <xref:System.Math?displayProperty=nameWithType> daha geniş bir matematiksel işlev ler kümesi için yöntemler sağlar. .NET Core 2.0 ve <xref:System.MathF?displayProperty=nameWithType> daha sonra <xref:System.Single> türünün bağımsız değişkenlerini kabul eden yöntemleri sağlayan sınıfı içerir.

Ayrıca <xref:System.BitConverter?displayProperty=nameWithType> sınıfı kullanarak tek tek <xref:System.Double> bit <xref:System.Single> ve değerlerle de çalışabilirsiniz. Yapının <xref:System.Decimal?displayProperty=nameWithType> kendi yöntemleri <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> vardır <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>ve ondalık değerin bireysel bitleriyle çalışmak için, bazı ek matematiksel işlemleri gerçekleştirmek için kendi yöntem kümesini de kullanır.
  
Ve <xref:System.Double> <xref:System.Single> türleri, doğası gereği kesin olmayan değerler (örneğin, iki yıldız arasındaki mesafe) ve yüksek derecede kesinlik ve küçük yuvarlama hatası gerektirmediği uygulamalar için kullanılmak üzere tasarlanmıştır. Daha fazla <xref:System.Decimal?displayProperty=nameWithType> kesinlik gerektiren ve yuvarlama hatalarının en aza indirilmesi gereken durumlar için türü kullanmalısınız.

> [!NOTE]
> Tür <xref:System.Decimal> yuvarlama ihtiyacını ortadan kaldırmaz. Bunun yerine, yuvarlama nedeniyle hataları en aza indirir.
  
## <a name="complex"></a>Complex

Yapı <xref:System.Numerics.Complex?displayProperty=nameWithType> karmaşık bir sayıyı, yani gerçek sayı yı ve hayali bir sayı parçasını temsil eder. Standart bir aritmetik, karşılaştırma, eşitlik, açık ve örtülü dönüştürme işleçlerinin yanı sıra matematiksel, cebirsel ve trigonometrik yöntemleri destekler.  
  
## <a name="simd-enabled-types"></a>SIMD özellikli türleri

Ad <xref:System.Numerics> alanı .NET SIMD özellikli türleri kümesini içerir. SIMD (Tek Öğretim Çoklu Veri) işlemleri donanım düzeyinde paralellenebilir. Bu, matematiksel, bilimsel ve grafik uygulamalarında yaygın olan vektörel hesaplamaların iş bilgililiğini artırır.
  
.NET SIMD özellikli türleri şunlardır:

- 2, <xref:System.Numerics.Vector3>3 <xref:System.Numerics.Vector4> ve 4 <xref:System.Single> değerleri ile vektörleri temsil eden <xref:System.Numerics.Vector2>, , ve türleri.

- 3x2 <xref:System.Numerics.Matrix3x2>matrisi temsil eden ve <xref:System.Numerics.Matrix4x4>4x4 matrisi temsil eden iki matris türü.

- Üç <xref:System.Numerics.Plane> boyutlu uzayda bir düzlemi temsil eden tür.

- Üç <xref:System.Numerics.Quaternion> boyutlu fiziksel döndürmeleri kodlamak için kullanılan bir vektörü temsil eden tür.

- Belirli <xref:System.Numerics.Vector%601> bir sayısal türün vektörü temsil eden ve SIMD desteğinden yararlanan geniş bir işleç kümesi sağlayan tür. Bir <xref:System.Numerics.Vector%601> örneğin sayısı sabittir, ancak <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> değeri makinenin CPU bağlıdır, hangi kod yürütülür.
  > [!NOTE]
  > Tür <xref:System.Numerics.Vector%601> .NET Framework'e dahil edilmez. Bu türe erişmek için [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet paketini yüklemeniz gerekir.
  
SIMD özellikli türler, SIMD etkin olmayan donanım veya JIT derleyicileriyle kullanılabilecek şekilde uygulanır. SIMD yönergelerinden yararlanmak için, 64 bit uygulamalarınızın .NET Core ve .NET Framework 4.6 ve sonraki sürümlerde yer alan RyuJIT derleyicisini kullanan çalışma süresine göre çalıştırılması gerekir. 64 bit işlemcileri hedefalırken SIMD desteği ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Temelleri](application-essentials.md)
- [Standart Sayısal Biçim Dizeleri](base-types/standard-numeric-format-strings.md)
