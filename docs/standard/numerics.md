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
ms.openlocfilehash: a2a795fb52c123840c1ba7b82f77d6745feba89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="numerics-in-the-net-framework"></a>.NET Framework'te sayısal türler
Standart sayısal Entegral ve kayan nokta temelleri, .NET Framework destekler yanı <xref:System.Numerics.BigInteger>, bir tam sayı türü hiçbir teorik üst veya alt sınırı ile <xref:System.Numerics.Complex>, bir karmaşık numaralar temsil eden tür ve bir SIMD etkin kümesi vektör türlerinde <xref:System.Numerics> ad alanı.  
  
 Ayrıca, System.Numerics.Vectors, vectory türlerinin SIMD etkin kitaplığı NuGet paketi olarak yayımlanmıştır.  
  
## <a name="integral-types"></a>Tam sayı türleri  
 .NET Framework, tek bir bayt uzunluğu sekiz bayt arasında değişen imzalı ve imzasız tamsayılar destekler. Aşağıdaki tabloda, tam sayı türleri ve boyutlarını listeler, bunlar imzalanmış veya imzalanmamış ve menzil belgeleri olup olmadığını gösterir. Tüm tamsayı değer türleridir.  
  
|Tür|İmzalı ve imzasız|Boyut (bayt)|Minimum değer|En büyük değer|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|İmzasız|1.|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|İmzalı|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|İmzalı|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|İmzalı|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|İmzalı|1.|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|İmzasız|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|İmzasız|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|İmzasız|8|0|18,446,744,073,709,551,615|  
  
 Her bir tam sayı türü aritmetik, karşılaştırma, eşitlik, açık Dönüşüm ve örtük dönüşüm işleçleri, standart bir kümesini destekler. Her tamsayı ayrıca eşitlik karşılaştırmaları ve bir numara dize gösterimini bu tamsayıya dönüştürmek için ve tamsayı, dize gösterimi dönüştürmek için göreli karşılaştırmaları gerçekleştirmek için yöntemler içerir. Bazı ek matematiksel işlemler ötesinde yuvarlama ve iki tamsayı, küçük veya büyük değer tanımlama gibi kullanılabilir standart işleçleri tarafından işlenen <xref:System.Math> sınıfı. Ayrıca bir tamsayı değeri tek tek bitleri kullanarak çalışabileceğiniz <xref:System.BitConverter> sınıfı.  
  
 İmzasız tam sayı türleri CLS uyumlu değildir. Daha fazla bilgi için bkz: [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Kayan nokta türleri  
 Aşağıdaki tabloda listelenen üç temel kayan nokta türleri, .NET Framework içerir.  
  
|Tür|Boyutu (bayt)|Minimum|Maksimum|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1.79769313486232e308|1.79769313486232E308|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3.402823e38|3.402823E38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Kayan nokta her tür aritmetik, karşılaştırma, eşitlik, açık Dönüşüm ve örtük dönüşüm işleçleri, standart bir kümesini destekler. Her eşitlik karşılaştırmaları ve kayan noktalı sayı dize gösterimini dönüştürmek için ve kayan noktalı sayı, dize gösterimi dönüştürmek için göreli karşılaştırmaları gerçekleştirmek için yöntemler de içerir. Bazı ek matematiksel, cebirsel ve trigonometrik işlemleri edinilebilir <xref:System.Math> sınıfı. Tek tek bitleri ile çalışabilirsiniz <xref:System.Double> ve <xref:System.Single> kullanarak değerleri <xref:System.BitConverter> sınıfı. <xref:System.Decimal?displayProperty=nameWithType> Yapısının kendi yöntemlerini <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> ve <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, tek bir ondalık değeri ile çalışmak için bazı ek matematik işlemlerini gerçekleştirmek için yöntemleri kendi kümesini yanı sıra BITS.  
  
 <xref:System.Double> Ve <xref:System.Single> türleri yapılarına göre (örneğin, iki yıldız güneş sistemi arasındaki uzaklığı) kesin değerler için ve içinde duyarlık ve küçük hata yuvarlama yüksek derecede olmayan uygulamalar için kullanılacak yöneliktir Gerekli. Kullanmanız gereken <xref:System.Decimal?displayProperty=nameWithType> büyük olduğu durumlarda türü Duyarlığı gereklidir ve hata yuvarlama istenmeyen,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> hiçbir üst veya alt sınır değeri teorik sahip büyük bir tamsayı temsil eden bir değişmez türüdür. Yöntemlerinin <xref:System.Numerics.BigInteger> türü yakından paralel bir tam sayı türleri olanlar.  
  
## <a name="complex"></a>Complex  
 <xref:System.Numerics.Complex> Türü bir karmaşık numarası, diğer bir deyişle, bir gerçek sayı bölüm ve bir sanal numarası bölümü ile temsil eder. Aritmetik, karşılaştırma, eşitlik, açık Dönüşüm ve örtük dönüşüm işleçleri yanı matematiksel, cebirsel ve trigonometrik yöntemleri standart bir kümesini destekler.  
  
## <a name="simd-enabled-vector-types"></a>Vektör SIMD etkin türleri  
 <xref:System.Numerics> Ad alanı .NET Framework için SIMD etkin vektör türleri kümesi içerir. SIMD (tek bir yönerge birden çok veri işlemleri) paralel büyük performans geliştirmeleri matematiksel, bilimsel sonuçları, donanım düzeyinde ve vektörler hesaplamalar grafik uygulamaları birkaç ölçeklendirin bazı işlemlere izin verir.  
  
 .NET Framework'teki SIMD etkin vektör türleri şunlardır:.  Ayrıca, System.Numerics.Vectors düzlemi türü ve bir dördey türü içerir.  
  
-   <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, ve <xref:System.Numerics.Vector4> 2, 3 ve 4 boyutlu vektörlerinin türü türleri <xref:System.Single>.  
  
-   İki matris türleri <xref:System.Numerics.Matrix3x2>, 3 x 2 matrisi; temsil eder ve <xref:System.Numerics.Matrix4x4>, 4 x 4 matris temsil eder.  
  
-   <xref:System.Numerics.Plane> Ve <xref:System.Numerics.Quaternion> türleri.  
  
 Vektör SIMD etkin türleri SIMD etkin olmayan donanım ve JIT derleyicileri kullanılacak veren IL uygulanır. SIMD yönergeleri yararlanmak için 64-bit uygulamaları ile .NET Framework 4.6 bulunan yönetilen kod için yeni 64-bit JIT derleyicisi tarafından derlenmelidir; x64 hedeflerken SIMD desteği ekler işlemci.  
  
 SIMD ayrıca indirilebilir olarak bir [NuGet paketi](https://www.nuget.org/packages/System.Numerics.Vectors).  NuGET paketini de genel içerir <xref:System.Numerics.Vector%601> herhangi bir ilkel sayısal türde bir vektör oluşturmanıza olanak tanıyan yapısı. (İçindeki tüm sayısal türler basit sayısal türler dahil <xref:System> ad alanı dışında <xref:System.Decimal>.) Ayrıca, <xref:System.Numerics.Vector%601> yapısı bir kitaplık vektörlerinin ile çalışırken çağırabilirsiniz kullanışlı yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Temelleri](../../docs/standard/application-essentials.md)
