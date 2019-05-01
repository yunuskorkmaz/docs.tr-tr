---
title: Veri Türü Özeti (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 29e5cbe09026dd52811c6c5fb88e940b45b7c0bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971749"
---
# <a name="data-type-summary-visual-basic"></a>Veri Türü Özeti (Visual Basic)
Aşağıdaki tabloda, Visual Basic veri türleri, destek, ortak dil çalışma zamanı türleri, kendi nominal depolama alanı ayırma ve kendi değer aralıklarına gösterir.  
  
|Visual Basic türü|Ortak dil çalışma zamanı türü yapısı|Nominal depolama ayırma|Değer aralığı|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boole değeri](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Platform uygulamaya bağlıdır.|`True` veya `False`|  
|[Bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bayt|0 ile 255 (işaretsiz)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) (tek bir karakter)|<xref:System.Char>|2 bayt|0-65535 (işaretsiz)|  
|[Tarih](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bayt|0:00:00 (gece yarısı) 1 Ocak 0001 ila 11:59:59 PM 31 Aralık 9999 '|  
|[Ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bayt|0 ile 79,228,162,514,264,337,593,543,950,335 +/-(7,9... +/-E + 28) <sup>†</sup> olmadan ondalık nokta; 0 ile 28; ondalık basamak sağındaki basamak ile 7.9228162514264337593543950335 +/-<br /><br /> en küçük sıfır olmayan bir sayıdır (+/-1E-28) 0.0000000000000000000000000001 +/- <sup>†</sup>|  
|[Çift](../../../visual-basic/language-reference/data-types/double-data-type.md) (çift duyarlıklı kayan nokta)|<xref:System.Double>|8 bayt|-1.79769313486231570E + 308 - aracılığıyla 4.94065645841246544E-324 <sup>†</sup> negatif değerleri;<br /><br /> 4.94065645841246544E-324 1.79769313486231570E + 308 aracılığıyla <sup>†</sup> pozitif değerler için|  
|[tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bayt|-2.147.483.648 ile 2.147.483.647 (imzalanmış)|  
|[Uzun](../../../visual-basic/language-reference/data-types/long-data-type.md) (büyük tamsayı)|<xref:System.Int64>|8 bayt|-9,223,372,036,854,775,808 aracılığıyla 9.223.372.036.854.775.807 (9.2... E + 18 <sup>†</sup>) (imzalanmış)|  
|[Nesne](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> (sınıfı)|32-bit platformlarda 4 bayt<br /><br /> 64-bit platformlarda 8 bayt|Her türlü türünde bir değişkende depolanabilecek `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bayt|-128 ile 127 (imzalanmış)|  
|[Kısa](../../../visual-basic/language-reference/data-types/short-data-type.md) (kısa tamsayı)|<xref:System.Int16>|2 bayt|-32.768 32.767 (imzalanmış) aracılığıyla|  
|[Tek](../../../visual-basic/language-reference/data-types/single-data-type.md) (tek duyarlıklı kayan nokta)|<xref:System.Single>|4 bayt|-3.4028235E + 38 ile - 1.401298E-45 <sup>†</sup> negatif değerleri;<br /><br /> 1.401298E-45 3.4028235E + 38 aracılığıyla <sup>†</sup> pozitif değerler için|  
|[Dize](../../../visual-basic/language-reference/data-types/string-data-type.md) (değişken uzunluklu)|<xref:System.String> (sınıfı)|Platform uygulamaya bağlıdır.|yaklaşık 2 milyar Unicode karakter 0|  
|[Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bayt|0'dan 4.294.967.295'e (işaretsiz)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bayt|0 ile 18,446,744,073,709,551,615 (1.8... E + 19 <sup>†</sup>) (işaretsiz)|  
|[Kullanıcı tanımlı](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (yapı)|(devralınan <xref:System.ValueType>)|Platform uygulamaya bağlıdır.|Her üyesinin kendi veri türüne göre ve diğer üyelerin aralıkların bağımsız bir aralığına yapısı|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bayt|0 ile 65.535 (işaretsiz)|  
  
 <sup>†</sup> İçinde *bilimsel gösterim*, "E" 10 'un bir kuvveti ifade eder. 3.56E + 2 3.56 x 10 gösterir şekilde<sup>2</sup> veya 356 ve 3.56E-2 gösterir 3.56 / 10<sup>2</sup> veya 0.0356.  
  
> [!NOTE]
>  Metin içeren dizeleri için kullanın <xref:Microsoft.VisualBasic.Strings.StrConv%2A> bir metin biçimden diğerine dönüştürmek için işlevi.  
  
 Bir bildirim deyiminde veri türü belirtmeye ek olarak, bazı programlama öğelerin veri türü bir tür karakteri kullanarak zorlayabilirsiniz. Bkz: [karakter yazın](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Bellek tüketimi  
 Başlangıç veri türü bildirdiğinizde, kendi bellek tüketimi kendi nominal depolama ayırma ile aynı olduğunu varsaymak güvenli değildir. Aşağıdaki konular nedeniyle budur:  
  
- **Depolama ataması.** Ortak dil çalışma zamanı, geçerli uygulama yürütülmekte olan platform özelliklerine dayanan depolama alanı atayabilir. Bellek neredeyse dolu ise, bunu mümkün olduğunca birbirine yakın, bildirilen öğeler paketi. Diğer durumlarda bellek adresleri doğal donanım sınırlarına performansını en iyi duruma Hizala.  
  
- **Platform genişliği.** Bir 64-bit platformlarda depolama ataması, 32-bit platformlarda atama farklıdır.  
  
### <a name="composite-data-types"></a>Bileşik Veri Türleri  
 Bileşik veri türünün, bir yapının ya da bir dizi gibi her üyesine ilgili noktaların aynısı geçerlidir. Yalnızca birlikte türün üyelerinin nominal depolama ayırmalarını eklemeyi üzerinde güvenemezsiniz. Ayrıca, aşağıdaki gibi diğer önemli noktalar vardır:  
  
- **Ek yükü.** Bazı bileşik türler ek bellek gereksinimleri vardır. Örneğin, bir dizi dizisi için ve ayrıca her boyut için ek bellek kullanır. Bir 32 bit platformda bu ek şu anda 12 bayt artı 8 bayt her boyut için yüktür. Bu gereksinim, bir 64-bit platformda iki katına çıkarılır.  
  
- **Depolama düzeni.** Ayrıca, siparişin bellekteki depolama sırasının bildirim ile aynı olduğunu güvenli bir şekilde varsayamazsınız. Hatta 2 baytlık veya 4 baytlık bir sınır gibi bayt hizalama hakkında varsayımlar yapamazsınız. Bir sınıf veya yapı tanımlama ve üyelerini depolama düzenini denetlemek için ihtiyacınız varsa uygulayabileceğiniz <xref:System.Runtime.InteropServices.StructLayoutAttribute> sınıf veya yapı için özniteliği.  
  
### <a name="object-overhead"></a>Nesnenin ek yükü  
 Bir `Object` başvuran başlangıç veya bileşik veri türü 4 bayt veri türünde yer alan veriler ek olarak kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
