---
title: Veri Türü Özeti
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
ms.openlocfilehash: 5eb52ef937a677c0b7498d058b5a39a375351ddc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415627"
---
# <a name="data-type-summary-visual-basic"></a>Veri Türü Özeti (Visual Basic)

Aşağıdaki tabloda Visual Basic veri türleri, bunların destekleyici ortak dil çalışma zamanı türleri, nominal depolama ayırması ve bunların değer aralıkları gösterilmektedir.  
  
|Visual Basic türü|Ortak dil çalışma zamanı türü yapısı|Nominal depolama ayırması|Değer aralığı|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boole](boolean-data-type.md)|<xref:System.Boolean>|Uygulama platformuna bağlıdır|`True` veya `False`|  
|[Bayt](byte-data-type.md)|<xref:System.Byte>|1 bayt|0 ila 255 (işaretsiz)|  
|[Char](char-data-type.md) (tek karakter)|<xref:System.Char>|2 bayt|0 ila 65535 (işaretsiz)|  
|[Date](date-data-type.md)|<xref:System.DateTime>|8 bayt|1 Ocak 0:00:00 ' de (gece yarısı), 31 Aralık 9999 tarihinde 11:59:59 PM|  
|[Kategori](decimal-data-type.md)|<xref:System.Decimal>|16 bayt|0-+/-79228162514264337593543950335 (+/-7.9...E + 28) <sup>†</sup> ile ondalık noktası yok; 0 ile +/-7.9228162514264337593543950335, Decimal 'ın sağında 28 yer arasında;<br /><br /> sıfır olmayan en küçük sayı +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Double](double-data-type.md) (çift duyarlıklı kayan nokta)|<xref:System.Double>|8 bayt|-1.79769313486231570 e + 308 ile-4.94065645841246544 E-324 <sup>†</sup> -negatif değerler için;<br /><br /> 4.94065645841246544 e-324-1.79769313486231570 E + 308 <sup>†</sup> pozitif değerler için|  
|[Tamsayı](integer-data-type.md)|<xref:System.Int32>|4 bayt|-2.147.483.648-2.147.483.647 (imzalı)|  
|[Long](long-data-type.md) (uzun tamsayı)|<xref:System.Int64>|8 bayt|-9223372036854775808 ila 9.223.372.036.854.775.807 (9.2... E + 18 <sup>†</sup>) (imzalı)|  
|[Nesne](object-data-type.md)|<xref:System.Object>sınıfı|32 bit platformda 4 bayt<br /><br /> 64 bit platformda 8 bayt|Herhangi bir tür, türünde bir değişkende depolanabilir`Object`|  
|[SByte](sbyte-data-type.md)|<xref:System.SByte>|1 bayt|-128-127 (imzalı)|  
|[Short](short-data-type.md) (kısa tamsayı)|<xref:System.Int16>|2 bayt|-32.768-32.767 (imzalı)|  
|[Tek](single-data-type.md) (tek duyarlıklı kayan nokta)|<xref:System.Single>|4 bayt|-3.4028235 e + 38 ila-1.401298 E-45 <sup>†</sup> -negatif değerler için;<br /><br /> 1.401298 e-45 ile 3.4028235 E + 38 <sup>†</sup> pozitif değerler için|  
|[Dize](string-data-type.md) (değişken uzunlukta)|<xref:System.String>sınıfı|Uygulama platformuna bağlıdır|0 ile yaklaşık 2.000.000.000 Unicode karakter|  
|[UInteger](uinteger-data-type.md)|<xref:System.UInt32>|4 bayt|0 ila 4.294.967.295 (işaretsiz)|  
|['Tur](ulong-data-type.md)|<xref:System.UInt64>|8 bayt|0 ile 18446744073709551615 (1.8... E + 19 <sup>†</sup>) (imzasız)|  
|[Kullanıcı tanımlı](user-defined-data-type.md) (yapı)|(öğesinden devralır <xref:System.ValueType> )|Uygulama platformuna bağlıdır|Yapının her üyesi, veri türü ve diğer üyelerin aralıklarından bağımsız olarak belirlenen aralığa sahiptir|  
|[UShort](ushort-data-type.md)|<xref:System.UInt16>|2 bayt|0 ila 65.535 (işaretsiz)|  
  
 <sup>†</sup> *Bilimsel gösterimde*, "E" 10 ' un bir kuvvetinin anlamına gelir. Bu nedenle, 3.56 E + 2 3,56 x 10<sup>2</sup> veya 356 olduğunu ve 3.56 e-2 ' nin 3,56/10<sup>2</sup> veya 0,0356 olduğunu belirtir.  
  
> [!NOTE]
> Metin içeren dizeler için, <xref:Microsoft.VisualBasic.Strings.StrConv%2A> bir metin biçiminden diğerine dönüştürmek için işlevini kullanın.  
  
 Bir bildirim bildiriminde bir veri türü belirtmenin yanı sıra, bazı programlama öğelerinin veri türünü bir tür karakteri kullanarak zorlayabilirsiniz. Bkz. [tür karakterleri](../../programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Bellek Tüketimi  

 Bir Öğesel veri türü bildirdiğinizde, bellek tüketiminin nominal depolama ayırması ile aynı olduğunu varsaymak güvenli değildir. Bunun nedeni aşağıdaki noktalara dikkat edin:  
  
- **Depolama ataması.** Ortak dil çalışma zamanı, uygulamanızın yürütüldüğü platformun geçerli özelliklerine göre depolama alanı atayabilir. Bellek dolmak üzere ise, belirtilen öğeleri mümkün olduğunca yakından paketleyebilir. Diğer durumlarda, performansı iyileştirmek için bellek adreslerini doğal donanım sınırlarına göre hizalayabilirsiniz.  
  
- **Platform genişliği.** 64 bitlik bir platformda depolama ataması, 32 bit platformun atamasından farklıdır.  
  
### <a name="composite-data-types"></a>Bileşik Veri Türleri  

 Aynı noktalar, bir yapı veya dizi gibi bileşik veri türünün her üyesi için de geçerlidir. Türün üyelerinin nominal depolama ayırmalarını bir araya ekleme ' ye güvenebilirsiniz. Ayrıca, aşağıdakiler gibi başka hususlar de vardır:  
  
- **Giderlerini.** Bazı bileşik türlerin ek bellek gereksinimleri vardır. Örneğin, bir dizi, dizinin kendisi için ve ayrıca her boyut için ek bellek kullanır. 32 bitlik bir platformda bu ek yük, her boyut için şu anda 12 bayt ve 8 bayttır. 64 bitlik bir platformda bu gereksinim iki katına çıkar.  
  
- **Depolama düzeni.** Bellekteki depolama sırasının, bildirim sıralamayla aynı olduğunu güvenli bir şekilde varsayamaz. 2 baytlık veya 4 baytlık sınır gibi, bayt hizalaması hakkında de varsayımlar yapamazsınız. Bir sınıf veya yapı tanımlıyorsanız ve üyelerinin depolama yerleşimini kontrol etmeniz gerekiyorsa, bu <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği sınıfa veya yapıya uygulayabilirsiniz.  
  
### <a name="object-overhead"></a>Nesne ek yükü  

 `Object`Herhangi bir öğesel veya bileşik veri türüne başvuran, veri türünde bulunan verilere ek olarak 4 bayt kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Tür Karakterleri](../../programming-guide/language-features/data-types/type-characters.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
