---
title: Tür Dönüştürme İşlevleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c9222bdb31f4fd7c792d5a50c100067e29e9d537
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605088"
---
# <a name="type-conversion-functions-visual-basic"></a>Tür Dönüştürme İşlevleri (Visual Basic)
Bu işlevlerdir derlenmiş satır içi dönüştürme kodu ifadeyi hesaplar kod parçası olan anlamına gelir. Bazen performansı artırır dönüştürme gerçekleştirmek için bir yordam hiçbir çağrı yoktur. Her işlev belirli bir veri türüne bir ifadeyi olacak şekilde zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a>Bölümü  
 `expression`  
 Gerekli. Herhangi bir ifade kaynak veri türü.  
  
## <a name="return-value-data-type"></a>Dönüş değeri veri türü  
 İşlev adı aşağıdaki tabloda gösterildiği gibi döndürür, değerin veri türü belirler.  
  
|İşlev adı|Dönüş veri türü|İçin aralığı `expression` bağımsız değişken|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Tüm geçerli `Char` veya `String` veya sayısal ifade.|  
|`CByte`|[Byte Veri Türü](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 ile 255 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CChar`|[Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)|Tüm geçerli `Char` veya `String` ifade; yalnızca ilk karakteri bir `String` dönüştürülür; değeri, 0-65535 (imzalanmamış) olabilir.|  
|`CDate`|[Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Tüm geçerli temsili bir tarih ve saat.|  
|`CDbl`|[Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570E + 308 ile - 4.94065645841246544E-324 negatif değerler; 4.94065645841246544E-324 1.79769313486231570E + 308 pozitif değerler için aracılığıyla.|  
|`CDec`|[Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|sıfır ölçeklendirilmiş numaraları için diğer bir deyişle, ondalık konumu olmayan sayılar 79,228,162,514,264,337,593,543,950,335 +/-. İle 28 ondalık sayılar için 7.9228162514264337593543950335 +/-aralığıdır. En küçük olası sıfır 0.0000000000000000000000000001 (+/-1E-28) sayısıdır.|  
|`CInt`|[Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)|-2.147.483.648 2.147.483.647 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CLng`|[Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)|-9,223,372,036,854,775,808 9,223,372,036,854,775,807 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CObj`|[Object Veri Türü](../../../visual-basic/language-reference/data-types/object-data-type.md)|Herhangi bir geçerli ifade.|  
|`CSByte`|[SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|-128 127 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CShort`|[Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)|-32.768 32.767 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CSng`|[Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38 ile - 1.401298E-45 negatif değerler; 1.401298E-45 3.402823E + 38 pozitif değerler için aracılığıyla.|  
|`CStr`|[String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)|İçin döndürür `CStr` bağımlı `expression` bağımsız değişkeni. Bkz: [CStr işlevinin dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 ile 4.294.967.295 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CULng`|[ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 ile 18,446,744,073,709,551,615 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup>|  
|`CUShort`|[UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 ile 65.535 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup>|  
  
 <sup>1</sup> kesirli bölümleri çağrılan yuvarlama bir özel tür tabi olabilir *banker yuvarlaması*. "Açıklamalar" daha fazla bilgi için bkz.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kural olarak, .NET Framework yöntemlerini yerine Visual Basic tür dönüştürme işlevleri gibi kullanmalısınız `ToString()`, her iki üzerinde <xref:System.Convert> sınıfı ya da bir bireysel tür yapısına veya sınıfı. Visual Basic işlevleri, Visual Basic kodu en iyi etkileşim için tasarlanmıştır ve bunlar da kaynak kodunuzu daha kısa ve kolay okunur yapın. Ayrıca, .NET Framework dönüştürme yöntemleri her zaman aynı sonucu dönüştürülürken örneğin Visual Basic işlevleri olarak vermez `Boolean` için `Integer`. Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="behavior"></a>Davranış  
  
-   **Zorlama.** Genel olarak, varsayılan veri türü yerine belirli bir veri türüne bir işlemin sonucunu coerce için veri türüne dönüştürme işlevleri kullanabilirsiniz. Örneğin, `CDec` burada tek duyarlıklı, çift duyarlıklı ya da tamsayı aritmetik normalde alırken yer durumlarda ondalık aritmetik zorlamak için.  
  
-   **Başarısız dönüştürme.** Varsa `expression` işleve hangi BT dönüştürülmekte olan veri türü aralık dışında olduğu bir <xref:System.OverflowException> oluşur.  
  
-   **Kesirli bölümleri.** Bir tam sayıya nonintegral değeri dönüştürürken türü, tamsayı dönüştürme işlevleri (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, ve `CUShort`) Kaldır kesirli kısım ve değeri en yakın tamsayıya yuvarlar.  
  
     Kesirli tam olarak bir parçasıysa 0,5, tamsayı dönüştürme işlevleri yuvarlamak kendisine en yakın çift tam sayı. Örneğin, 0, 1.5 ve her ikisi de 2 yuvarlamak 2.5 0,5 yuvarlar. Buna bazen denir *banker yuvarlaması*, ve amacı gibi birçok numaraları birlikte eklerken birikebilir sapması dengelemek için.  
  
     `CInt` ve `CLng` farklı <xref:Microsoft.VisualBasic.Conversion.Int%2A> ve <xref:Microsoft.VisualBasic.Conversion.Fix%2A> hangi round, bir sayının kesirli kısmını yerine truncate işlevleri. Ayrıca, `Fix` ve `Int` , geçirdiğiniz olarak her zaman aynı veri türünde bir değer döndürür.  
  
-   **Dönüşümler tarih veya saat.** Kullanım <xref:Microsoft.VisualBasic.Information.IsDate%2A> bir tarih ve saat için bir değer dönüştürülüp dönüştürülemeyeceğini belirlemek için işlev. `CDate` Tarih değişmez değerleri ve Saat rakamları ancak sayısal değerleri algılar. Visual Basic 6.0 dönüştürmek için `Date` değeri bir `Date` değeri Visual Basic 2005 veya sonraki sürümler, kullanabileceğiniz <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemi.  
  
-   **Nötr tarih/saat değerleri.** [Tarih veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md) her zaman tarih ve saat bilgilerini içerir. Tür dönüşümü amaçları doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *nötr değeri* tarihini ve 00:00:00 (gece yarısı) süresi dilden bağımsız bir değer olmalıdır. Dönüştürürseniz, bir `Date` değerini bir dizeyle `CStr` nötr değerleri sonuç dizesinde içermez. Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dizeye sonucu "9:30:00 AM"; tarih bilgisini engellenir. Ancak, tarih bilgisini özgün hala mevcut olduğu `Date` değer ve işlevleriyle gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> işlevi.  
  
-   **Kültür hassasiyet.** Dizeleri içeren tür dönüştürme işlevleri dönüştürmeleri uygulama için geçerli kültür ayarları göre gerçekleştirin. Örneğin, `CDate` tarih biçimleri, sisteminizin yerel ayarına göre tanır. Gün, ay ve yıl bölgeniz için doğru sırada sağlamanız gerekir veya tarih doğru yorumlanabilir değil. "Çarşamba" gibi bir haftanın günü dize içeriyorsa, bir uzun tarih biçimi tanınmıyor.  
  
     İçin veya bir biçimde bölgeniz tarafından belirtilen bir dışında bir değer bir dize gösterimini dönüştürmek istiyorsanız, Visual Basic tür dönüştürme işlevleri kullanamazsınız. Bunu yapmak için kullanın `ToString(IFormatProvider)` ve `Parse(String, IFormatProvider)` yöntemleri bu değerin türü. Örneğin, <xref:System.Double.Parse%2A?displayProperty=nameWithType> bir dizesine dönüştürürken bir `Double`ve <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` dizeye.  
  
## <a name="ctype-function"></a>CType İşlevi  
 [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ikinci bir bağımsız değişken `typename`ve olacak şekilde zorlar `expression` için `typename`, burada `typename` veri türü, yapısı, sınıf veya arabirim için mevcut geçerli bir dönüştürme olabilir.  
  
 Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>CBool örneği  
 Aşağıdaki örnek kullanır `CBool` ifadeleri için dönüştürmek için işlevi `Boolean` değerleri. Bir ifadenin sıfırdan farklı bir değere değerlendirilirse `CBool` döndürür `True`; Aksi takdirde döndürdüğü `False`.  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>CByte örneği  
 Aşağıdaki örnek kullanır `CByte` bir ifadeyi dönüştürmek için işlevi bir `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>CChar örneği  
 Aşağıdaki örnek kullanır `CChar` ilk karakteri dönüştürmek için işlevi bir `String` ifade bir `Char` türü.  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 Giriş bağımsız değişkeni `CChar` veri türünde olmalıdır `Char` veya `String`. Kullanamazsınız `CChar` olduğundan bir karakter, sayı dönüştürülemiyor `CChar` sayısal veri türü kabul edemez. Aşağıdaki örnek kod noktası (karakter kodu) gösteren bir sayı alır ve karşılık gelen karakter dönüştürür. Kullandığı <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> basamak dizisini elde etmek için işlevi `CInt` dize türüne dönüştürmek için `Integer`, ve `ChrW` sayıyı türüne dönüştürmek için `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>CDate örneği  
 Aşağıdaki örnek kullanır `CDate` dizeye dönüştürmek için işlevi `Date` değerleri. Genel olarak, kodlama sabit tarihler ve saatler (Bu örnekte gösterildiği gibi) dizesi olarak önerilmez. Tarih değişmez değerleri ve #Feb 12 1969 # gibi saat değişmez değerleri kullanın ve # 4:45:23 PM #, bunun yerine.  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>CDbl örneği  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>CDec örneği  
 Aşağıdaki örnek kullanır `CDec` sayısal değerine dönüştürmek için işlevi `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>CInt örneği  
 Aşağıdaki örnek kullanır `CInt` değerine dönüştürmek için işlevi `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a>CLng örneği  
 Aşağıdaki örnek kullanır `CLng` değerine dönüştürmek için işlevi `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>CObj örneği  
 Aşağıdaki örnek kullanır `CObj` sayısal değerine dönüştürmek için işlevi `Object`. `Object` Değişkenin kendisine içerir, işaret yalnızca dört bayt işaretçi `Double` kendisine atanmış bir değer.  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>CSByte örneği  
 Aşağıdaki örnek kullanır `CSByte` sayısal değerine dönüştürmek için işlevi `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>CShort örneği  
 Aşağıdaki örnek kullanır `CShort` sayısal değerine dönüştürmek için işlevi `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>CSng örneği  
 Aşağıdaki örnek kullanır `CSng` değerine dönüştürmek için işlevi `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>CStr örneği  
 Aşağıdaki örnek kullanır `CStr` sayısal değerine dönüştürmek için işlevi `String`.  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 Aşağıdaki örnek kullanır `CStr` dönüştürmek için işlevi `Date` değerler `String` değerleri.  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr` her zaman işleyen bir `Date` geçerli yerel ayar için örneğin, standart kısa biçimindeki değerini "15/6/2003 4:35:47 PM". Ancak, `CStr` bastırır *nötr değerleri* 1/1/0001 için tarih ve saat için 00:00:00.  
  
 Tarafından döndürülen değerleri hakkında daha fazla ayrıntı için `CStr`, bkz: [CStr işlevinin dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Cuınt örneği  
 Aşağıdaki örnek kullanır `CUInt` sayısal değerine dönüştürmek için işlevi `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>CULng örneği  
 Aşağıdaki örnek kullanır `CULng` sayısal değerine dönüştürmek için işlevi `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>CUShort örneği  
 Aşağıdaki örnek kullanır `CUShort` sayısal değerine dönüştürmek için işlevi `UShort`.  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
