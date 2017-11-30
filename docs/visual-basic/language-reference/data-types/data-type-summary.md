---
title: "Veri Türü Özeti (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f69a112718eed7bb7baaff9bdffd110865c21081
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-type-summary-visual-basic"></a>Veri Türü Özeti (Visual Basic)
Aşağıdaki tabloda, Visual Basic veri türleri, kendi destekleyen ortak dil çalışma zamanı türler, kendi nominal depolama ayırma ve bunların değer aralıklarını gösterir.  
  
|Visual Basic türü|Ortak dil çalışma zamanı türü yapısı|Nominal depolama ayırma|Değer aralığı|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boole değeri](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Platform uygulanmasına bağlıdır|`True`veya`False`|  
|[Bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bayt|0 ile 255 (imzalanmamış)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) (tek bir karakter)|<xref:System.Char>|2 bayt|0 ile 65535 (imzalanmamış)|  
|[Tarih](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bayt|0:1 Ocak 0001 11:59:59: 00 31 Aralık 9999 üzerinde aracılığıyla 00:00 (gece yarısı)|  
|[Ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bayt|0 ile 79,228,162,514,264,337,593,543,950,335 +/-(7,9... +/-E + 28) <sup>†</sup> hiçbir Ondalık ayırıcının; 0 ile 28 basamaklı ondalık; sağındaki 7.9228162514264337593543950335 +/-<br /><br /> en küçük sıfır olmayan bir sayıdır (+/-1E-28) 0.0000000000000000000000000001 +/- <sup>†</sup>|  
|[Çift](../../../visual-basic/language-reference/data-types/double-data-type.md) (çift duyarlıklı kayan nokta)|<xref:System.Double>|8 bayt|-1.79769313486231570E + 308 ile - 4.94065645841246544E-324 <sup>†</sup> negatif değerler;<br /><br /> 4.94065645841246544E-324 1.79769313486231570E + 308 aracılığıyla <sup>†</sup> pozitif değerler için|  
|[Tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bayt|-2.147.483.648 2.147.483.647 (imzalanmış) aracılığıyla|  
|[Uzun](../../../visual-basic/language-reference/data-types/long-data-type.md) (uzun tamsayı)|<xref:System.Int64>|8 bayt|-9,223,372,036,854,775,808 9,223,372,036,854,775,807 aracılığıyla (9.2... E + 18 <sup>†</sup>) (imzalanmış)|  
|[Nesne](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>(sınıfı)|32 bit platformda 4 bayt<br /><br /> 8 bayt 64-bit platformda|Herhangi bir tür türünde bir değişkende depolanan`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bayt|-128 ile 127 (imzalanmış)|  
|[Kısa](../../../visual-basic/language-reference/data-types/short-data-type.md) (kısa tamsayı)|<xref:System.Int16>|2 bayt|-32.768 ile 32.767 (imzalanmış)|  
|[Tek](../../../visual-basic/language-reference/data-types/single-data-type.md) (tek duyarlıklı kayan nokta)|<xref:System.Single>|4 bayt|-3.4028235E + 38 ile - 1.401298E-45 <sup>†</sup> negatif değerler;<br /><br /> 1.401298E-45 3.4028235E + 38 aracılığıyla <sup>†</sup> pozitif değerler için|  
|[Dize](../../../visual-basic/language-reference/data-types/string-data-type.md) (değişken uzunlukta)|<xref:System.String>(sınıfı)|Platform uygulanmasına bağlıdır|yaklaşık 2 milyara Unicode karakter 0|  
|[Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bayt|0 ile 4.294.967.295 (imzalanmamış)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bayt|0 ile 18,446,744,073,709,551,615 (1.8... E + 19 <sup>†</sup>) (imzalanmamış)|  
|[Kullanıcı tanımlı](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (yapı)|(devraldığı <xref:System.ValueType>)|Platform uygulanmasına bağlıdır|Her üyenin kendi veri türüne göre ve diğer üyeler aralıklarının bağımsız bir aralığına yapısı|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bayt|0 ile 65.535 (imzalanmamış)|  
  
 <sup>†</sup> İçinde *bilimsel gösterim*, "E" 10 kuvvetine başvuruyor. 3.56E + 2 3.56 x 10 olduğunu gösterir şekilde<sup>2</sup> veya 356 ve 3.56E-2 güveninin 3.56 / 10<sup>2</sup> veya 0.0356.  
  
> [!NOTE]
>  Metin içeren bir dizeler için kullanmak <xref:Microsoft.VisualBasic.Strings.StrConv%2A> bir metin biçimden diğerine dönüştürme işlevi.  
  
 Bir veri türü bildirimi deyiminde belirtmeye ek olarak bir tür karakteri kullanarak bazı programlama öğeleri veri türünü zorlayabilirsiniz. Bkz: [karakterleri yazın](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Bellek tüketimi  
 Başlangıç veri türü bildirirken kendi bellek tüketimi nominal depolama ayırma ile aynı olduğunu varsaymak güvenli değil. Bu, aşağıdaki noktaları nedeniyle oluşur:  
  
-   **Depolama ataması.** Ortak dil çalışma zamanı uygulamanızı yürütülmekte olduğu platform geçerli özellikler temelinde depolama atayabilirsiniz. Bellek neredeyse dolu ise, onu mümkün olduğunca birlikte yakından olarak bildirilen öğelerinizi paketi. Diğer durumlarda bellek adreslerini performansını iyileştirmek için doğal donanım sınırlara hizalamaya.  
  
-   **Platform genişliği.** Bir 64-bit platformu üzerinde depolama ataması, 32-bit platformu atamada farklıdır.  
  
### <a name="composite-data-types"></a>Bileşik Veri Türleri  
 Her bir yapı veya bir dizi gibi bir bileşik veri türünün üyesi için ilgili noktaların aynısı geçerlidir. Yalnızca birlikte tür üyeleri nominal depolama ayırmaları eklemek için yeterli olmaz. Ayrıca, aşağıdaki gibi diğer noktalar vardır:  
  
-   **Ek yükü.** Bazı bileşik türler ek bellek gereksinimleri vardır. Örneğin, bir dizi dizisi için ve ayrıca her boyut için ek bellek kullanır. Bir 32 bit platformda bu yükünü anda 12 bayt artı 8 bayt her boyut için değil. Bir 64-bit platformda bu gereksinim iki katına çıkarılır.  
  
-   **Depolama düzeni.** Güvenli Depolama bellekte sırasını siparişinizi bildirim ile aynı olduğunu varsayın olamaz. 2-bayt veya 4-bayt sınırını gibi bayt hizalama hakkında varsayımlar bile yapamazsınız. Bir sınıf veya yapı tanımlama ve üyeleri depolama düzenini denetlemek gereken, uygulayabileceğiniz <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği sınıf veya yapı.  
  
### <a name="object-overhead"></a>Nesnenin ek yükü  
 Bir `Object` başlangıç veya bileşik veri başvuran türü 4 bayt veri türü verilere ek olarak kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Tür karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
