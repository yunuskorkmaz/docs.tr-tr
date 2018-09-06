---
title: .NET Framework'te sayısal türler
ms.date: 03/30/2017
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
ms.openlocfilehash: 1d253e7a32d5f302b095a86ddb5c296d5fa8fa11
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037087"
---
# <a name="numerics-in-the-net-framework"></a>.NET Framework'te sayısal türler
Standart sayısal integral ve kayan nokta temelleri, .NET Framework'ü destekleyen yanı <xref:System.Numerics.BigInteger>, teorik bir üst veya alt sınırı olmayan bir tamsayı türü <xref:System.Numerics.Complex>, bir karmaşık sayılar temsil eden tür ve SIMD etkin kümesi vektör türleri <xref:System.Numerics> ad alanı.  
  
 Ayrıca, System.Numerics.Vectors, vectory türlerinin SIMD etkin kitaplığı NuGet paketi olarak yayımlanmıştır.  
  
## <a name="integral-types"></a>Tam sayı türleri  
 .NET Framework, tek bir bayt uzunluğu sekiz bayt arasında değişen imzalı ve imzasız tamsayılar destekler. Aşağıdaki tabloda, tam sayı türleri ve bunların boyutu listeler, bunlar imzalı veya imzasız ve menzil belgeleri olup olmadığını gösterir. Tüm tamsayı değer türleridir.  
  
|Tür|İmzalı/imzasız|Boyut (bayt)|En düşük değer|En yüksek değer|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|İşaretsiz|1.|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|İmzalı|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|İmzalı|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|İmzalı|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|İmzalı|1.|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|İşaretsiz|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|İşaretsiz|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|İşaretsiz|8|0|18,446,744,073,709,551,615|  
  
 Her tamsayı türü aritmetik, karşılaştırma, eşitlik, açık bir dönüştürme ve örtük dönüşüm işleçleri, standart bir kümesini destekler. Her bir tamsayının ayrıca eşitlik karşılaştırmaları ve göreli karşılaştırmalar, bir sayının dize gösterimini, bir tamsayıya dönüştürmek için ve bir tamsayı, dize gösterimine dönüştürmek için gerçekleştirmek için yöntemler içerir. Bazı ek matematiksel işlemler ötesinde, yuvarlama ve iki tamsayı, küçük veya büyük değerini tanımlayan gibi kullanılabilir standart işleçleri tarafından işlenen <xref:System.Math> sınıfı. Ayrıca bir tamsayı değeri içinde tek tek BITS kullanarak çalışabilirsiniz <xref:System.BitConverter> sınıfı.  
  
 İmzasız tam sayı türleri CLS uyumlu olmadığına dikkat edin. Daha fazla bilgi için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Kayan nokta türleri  
 .NET Framework aşağıdaki tabloda listelenen üç temel kayan nokta türleri, içerir.  
  
|Tür|Boyut (bayt cinsinden)|Minimum|Maksimum|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1.79769313486232e308|1.79769313486232E308|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3.402823e38|3.402823E38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Her bir kayan nokta türü aritmetik, karşılaştırma, eşitlik, açık bir dönüştürme ve örtük dönüşüm işleçleri, standart bir kümesini destekler. Her ayrıca eşitlik karşılaştırmaları ve göreli karşılaştırmalar, kayan noktalı bir sayının dize gösterimini dönüştürmek için ve bir kayan noktalı sayı dize gösterimine dönüştürme gerçekleştirmek için yöntemler içerir. Bazı ek matematik, cebirsel ve trigonometrik işlemler kullanılabilir <xref:System.Math> sınıfı. Ayrıca ayrı BITS ile çalışabilir <xref:System.Double> ve <xref:System.Single> kullanarak değerleri <xref:System.BitConverter> sınıfı. <xref:System.Decimal?displayProperty=nameWithType> Yapısının kendi yöntemlerini <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> ve <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, tek bir ondalık değer ile çalışmak için bazı ek matematik işlemlerini gerçekleştirmek için yöntemleri kendi kümesini yanı sıra BITS.  
  
 <xref:System.Double> Ve <xref:System.Single> türleri ve uygulamaları, yüksek derecede duyarlık ve küçük hata yuvarlama değil yapılarına göre (örneğin, Güneş sisteminde iki yıldız arasındaki uzaklığı) kesin değerler için kullanılacak yöneliktir Gerekli. Kullanmanız gereken <xref:System.Decimal?displayProperty=nameWithType> türü için daha büyük olduğu durumlarda duyarlık gereklidir ve hata yuvarlama istenmeyen,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> hiçbir üst veya alt sınır değeri teorik sahip büyük bir tamsayı temsil eden bir değişmez türüdür. Yöntemlerinin <xref:System.Numerics.BigInteger> türü yakından paralel bir tam sayı türleri olanlar.  
  
## <a name="complex"></a>Complex  
 <xref:System.Numerics.Complex> Türü karmaşık bir sayıyı, diğer bir deyişle, bir gerçek sayı ve bir sanal numarası bölümlerini sayıyla temsil eder. Bu, standart bir aritmetik, karşılaştırma, eşitlik, açık bir dönüştürme ve örtük dönüşüm işleçleri, ek olarak matematik, cebirsel ve trigonometrik yöntemleri destekler.  
  
## <a name="simd-enabled-vector-types"></a>SIMD etkin vektör türlerinin  
 <xref:System.Numerics> Ad alanı .NET Framework için SIMD etkin vektör türleri kümesi içerir. (Tek yönerge birden çok veri işlemleri) SIMD vektör üzerinde hesaplamalar grafik uygulamaları ve büyük performans geliştirmeleri matematik, bilimsel sonuçları, donanım düzeyinde paralel hale bazı işlemlere izin verir.  
  
 .NET Framework'teki SIMD etkin vektör türleri şunlardır:.  Ayrıca, bir uçak türü ve dördey türü System.Numerics.Vectors içerir.  
  
-   <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, ve <xref:System.Numerics.Vector4> 2, 3 ve 4-boyutlu vektör türü türlerinden <xref:System.Single>.  
  
-   İki matris türü <xref:System.Numerics.Matrix3x2>, 3 x 2 matris; temsil eder ve <xref:System.Numerics.Matrix4x4>, 4 x 4 matrisi temsil eder.  
  
-   <xref:System.Numerics.Plane> Ve <xref:System.Numerics.Quaternion> türleri.  
  
 SIMD etkin vektör türlerinin SIMD etkin-donanım ve JIT derleyiciler kullanılacak veren IL uygulanır. SIMD yönergeleri yararlanmak için 64-bit uygulamalarınızı .NET Framework 4.6 ile bulunan yönetilen kod için yeni 64 bit JIT Derleyici tarafından derlenmelidir; x64 hedeflenirken SIMD desteği ekler işlemci.  
  
 SIMD da yüklenebilir olarak bir [NuGet paketi](https://www.nuget.org/packages/System.Numerics.Vectors).  NuGET paketini de genel içerir <xref:System.Numerics.Vector%601> yapısı, herhangi bir basit sayısal tür oluşan bir vektörü oluşturmanıza olanak sağlar. (Tüm sayısal türlerin basit sayısal türler dahil <xref:System> ad alanı dışında <xref:System.Decimal>.) Ayrıca, <xref:System.Numerics.Vector%601> yapısı vektörleri ile çalışırken çağırabileceğiniz yöntemler bir kitaplık sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Temelleri](../../docs/standard/application-essentials.md)
