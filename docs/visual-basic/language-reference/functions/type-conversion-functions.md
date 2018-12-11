---
title: Tür Dönüştürme İşlevleri (Visual Basic)
ms.date: 10/24/2018
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
ms.openlocfilehash: cbc9891170cde4b993a5dc890ed71c07a6f59f9e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129564"
---
# <a name="type-conversion-functions-visual-basic"></a>Tür Dönüştürme İşlevleri (Visual Basic)
Bu da dönüştürme kodunun ifadeyi değerlendiren kodun bir parçası olduğu anlamına derlenmiş satır içi işlevlerdir. Bazen bir yordam performansı artıran dönüştürme gerçekleştirmek için hiçbir çağrı yoktur. Her işlev bir özel veri türü için bir ifade olacak şekilde zorlar.  
  
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
 İşlev adı, aşağıdaki tabloda gösterildiği gibi döndürür, değeri veri türünü belirler.  
  
|İşlev adı|Dönüş veri türü|İçin aralık `expression` bağımsız değişken|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Herhangi bir geçerli `Char` veya `String` veya sayısal ifade.|  
|`CByte`|[Byte Veri Türü](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile bayt dönüştürme kayan nokta performansını iyileştirir `CByte` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
|`CChar`|[Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)|Herhangi bir geçerli `Char` veya `String` ifadesi; yalnızca ilk karakteri bir `String` dönüştürülür; değeri 0-65535 (işaretsiz) olabilir.|  
|`CDate`|[Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Tüm geçerli temsili bir tarih ve saat.|  
|`CDbl`|[Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570E + 308 - aracılığıyla 4.94065645841246544E-324; negatif değerleri 4.94065645841246544E-324 1.79769313486231570E + 308 pozitif değerler için aracılığıyla.|  
|`CDec`|[Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|sıfır ölçeklendirilmiş sayılar için diğer bir deyişle, ondalık konumu olmayan sayılar 79,228,162,514,264,337,593,543,950,335 +/-. 28 ondalık basamaklı sayılar için +/-7.9228162514264337593543950335 aralığıdır. En küçük olası sıfır olmayan 0.0000000000000000000000000001 (+/-1E-28) sayısıdır.|  
|`CInt`|[Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) aracılığıyla <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); kesirli bölümleri yuvarlanır.<sup> 1</sup> <br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile tamsayı dönüştürmesi için kayan nokta performansını iyileştirir `CInt` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek. |  
|`CLng`|[Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MaxValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) aracılığıyla <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile 64-bit tamsayıya dönüştürme kayan nokta performansını iyileştirir `CLng` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
|`CObj`|[Object Veri Türü](../../../visual-basic/language-reference/data-types/object-data-type.md)|Herhangi bir geçerli ifade.|  
|`CSByte`|[SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) aracılığıyla <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile işaretli bayt dönüştürme kayan nokta performansını iyileştirir `CSByte` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
|`CShort`|[Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) aracılığıyla <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile 16 bit tam sayı dönüşümü kayan nokta performansını iyileştirir `CShort` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
|`CSng`|[Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38 ile - 1.401298E-45 negatif değerleri; 1.401298E-45 3.402823E + 38 pozitif değerler için aracılığıyla.|  
|`CStr`|[String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)|Döndüren `CStr` bağımlı `expression` bağımsız değişken. Bkz: [CStr işlevi dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295'e) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile işaretsiz tamsayı dönüştürme kayan nokta performansını iyileştirir `CUInt` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
|`CULng`|[ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile işaretsiz uzun tamsayı dönüştürmesi için kayan nokta performansını iyileştirir `CULng` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
|`CUShort`|[UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ile başlayarak, Visual Basic ile 16 bit işaretsiz tamsayı dönüştürme kayan nokta performansını iyileştirir `CUShort` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için. Bkz: [CInt örnek](#cint-example) bölüm bir örnek.|  
  
 <sup>1</sup> kesirli bölümleri çağrılan yuvarlama özel bir tür tabi olabilir *banker yuvarlama*. "Açıklamalar" daha fazla bilgi için bkz.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kural olarak, .NET Framework yöntemlerini değişkenden Visual Basic tür dönüştürme işlevleri gibi kullanmalısınız `ToString()`, ya da üzerinde <xref:System.Convert> sınıfı veya tek tek tür yapı ya da sınıfı. Visual Basic işlevleri, Visual Basic kod ile en iyi etkileşim sağlamak için tasarlanmıştır ve ayrıca kaynak kodunuzu daha kısa ve kolay okunur hale. Ayrıca, .NET Framework dönüştürme yöntemleri her zaman aynı sonucu dönüştürülürken bir örnek için Visual Basic işlevleri olarak vermez `Boolean` için `Integer`. Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  


Geçirdiğinizde, Visual Basic 15,8 ile başlayarak, kayan-noktaya-boolean'dan tamsayıya dönüştürmeyi performansını optimize edilmiştir <xref:System.Single> veya <xref:System.Double> değeri bir tamsayı dönüştürme işlevleri aşağıdaki yöntemlerle döndürdü (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Bu iyileştirme, çok sayıda iki kat daha hızlı şekilde çalışması için tamsayı dönüştürmeleri yapan kod sağlar. Aşağıdaki örnekte, bu en iyi duruma getirilmiş kayan-noktaya boolean'dan tamsayıya dönüştürme gösterilmektedir:

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>Davranış  
  
-   **Zorlama.** Genel olarak, varsayılan veri türü yerine belirli bir veri türüne bir işlemin sonucunu coerce için veri türü dönüştürme işlevleri kullanabilirsiniz. Örneğin, `CDec` burada tek duyarlıklı, çift duyarlıklı veya tamsayı aritmetik normalde geçtiğine durumlarda ondalık aritmetik zorlamak için.  
  
-   **Dönüştürme başarısız.** Varsa `expression` işleve geçirilen için hangi BT dönüştürülmekte olan veri türü aralığının dışında olduğundan bir <xref:System.OverflowException> gerçekleşir.  
  
-   **Kesirli bölümleri.** Bir tam sayıya nonintegral değeri dönüştürdüğünüzde türü, tamsayı dönüştürme işlevleri (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, ve `CUShort`) Kaldır kesirli bölümü ve değeri en yakın tamsayıya yuvarlar.  
  
     Kesirli bölümü tam olarak ise 0,5, tamsayı dönüştürme işlevleri yuvarlak kendisine en yakın çift tamsayıya. Örneğin, 0 ve 1.5 hem de 2 yuvarlak 2.5 0,5 yuvarlar. Bazen adlandırılır *banker yuvarlama*, ve amacı dengelemek birlikte birçok sayı eklerken birikebilir sapması.  
  
     `CInt` ve `CLng` farklı <xref:Microsoft.VisualBasic.Conversion.Int%2A> ve <xref:Microsoft.VisualBasic.Conversion.Fix%2A> hangi round, bir sayının kesirli kısmını yerine truncate işlevleri. Ayrıca, `Fix` ve `Int` , geçirdiğiniz her zaman aynı veri türünde bir değer döndürür.  
  
-   **Tarih/saat dönüştürme.** Kullanım <xref:Microsoft.VisualBasic.Information.IsDate%2A> işlevi bir tarih ve saat değeri dönüştürülebilir ise belirlemek için. `CDate` Tarih değişmez değerleri ve zaman değişmez ancak sayısal değerleri algılar. Visual Basic 6.0 dönüştürülecek `Date` değerini bir `Date` değer Visual Basic 2005 veya sonraki sürümler, kullanabileceğiniz <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemi.  
  
-   **Nötr tarih/saat değerleri.** [Date veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md) her zaman tarih ve saat bilgileri içerir. Tür dönüştürme amacı doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *bağımsız değer* tarihini ve 00:00:00 (gece yarısı) süresi için bağımsız bir değer olarak. Dönüştürürseniz, bir `Date` bir dize değerine `CStr` nötr değerlerini sonuç dizesindeki içermez. Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dize, "9:30:00 AM" sonucudur; tarih bilgisi bastırılır. Ancak, tarih bilgileri özgün hala mevcut `Date` değeri ve işlevlerinde aşağıdaki gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> işlevi.  
  
-   **Kültür duyarlılık.** Dizeleri içeren tür dönüştürme işlevleri, uygulama için geçerli kültür ayarlara dayanan dönüştürmeler gerçekleştirin. Örneğin, `CDate` tarih biçimleri sisteminizin yerel ayarına göre tanır. Gün, ay ve yıl bölgeniz için doğru sırada sağlamanız gerekir ya da tarih doğru şekilde yorumlanabilir değil. "Çarşamba" gibi bir haftanın gün dize içeriyorsa, uzun tarih biçimi tanınmıyor.  
  
     İçin veya bir biçimde, yerel ayar tarafından belirtilen dışında bir değer bir dize gösterimini dönüştürmek istiyorsanız, Visual Basic tür dönüştürme işlevleri kullanamazsınız. Bunu yapmak için `ToString(IFormatProvider)` ve `Parse(String, IFormatProvider)` yöntemleri bu değerin türü. Örneğin, <xref:System.Double.Parse%2A?displayProperty=nameWithType> bir dizeye dönüştürürken bir `Double`ve <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` bir dize.  
  
## <a name="ctype-function"></a>CType İşlevi  
 [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ikinci bağımsız değişken `typename`ve olacak şekilde zorlar `expression` için `typename`burada `typename` veri türü, yapı, sınıf veya arabirim için hangi verilmesiyle geçerli bir dönüşümü olabilir.  
  
 Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>CBool örneği  
 Aşağıdaki örnekte `CBool` ifadeleri dönüştürmek için işlevi `Boolean` değerleri. Bir ifade sıfır olmayan bir değer olarak değerlendirilirse `CBool` döndürür `True`; Aksi halde döndürür `False`.  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>CByte örneği  
 Aşağıdaki örnekte `CByte` bir ifadeye dönüştürmek için işlevi bir `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>CChar örneği  
 Aşağıdaki örnekte `CChar` ilk karakteri dönüştürmek için işlevi bir `String` ifade bir `Char` türü.  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 Giriş bağımsız değişkeni için `CChar` veri türünde olmalıdır `Char` veya `String`. Kullanamazsınız `CChar` çünkü bir karakter, bir sayı dönüştürmek için `CChar` bir sayısal veri türü kabul edemez. Aşağıdaki örnek, bir kod noktası (karakter kodu) temsil eden bir sayı alır ve karşılık gelen karaktere dönüştürür. Kullandığı <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> basamak dizisini elde etmek için işlevi `CInt` dize türüne dönüştürmek için `Integer`, ve `ChrW` sayı türüne dönüştürmek için `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>CDate örneği  
 Aşağıdaki örnekte `CDate` dizelere dönüştürmek için işlevi `Date` değerleri. Genel olarak, kodlama sabit tarih ve saat dizeleri (Bu örnekte gösterildiği gibi) önerilmez. Tarih değişmez değerleri ve #Feb 12 1969 # gibi zaman değişmez değerleri kullanın ve # 4:45:23 PM #, bunun yerine.  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>CDbl örneği  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>CDec örneği  
 Aşağıdaki örnekte `CDec` sayısal bir değere dönüştürmek için işlevi `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>CInt örneği  
 Aşağıdaki örnekte `CInt` değerine dönüştürmek için işlevi `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  

## <a name="clng-example"></a>CLng örneği
 Aşağıdaki örnekte `CLng` değerlerine dönüştürmek için işlevi `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>CObj örneği  
 Aşağıdaki örnekte `CObj` sayısal bir değere dönüştürmek için işlevi `Object`. `Object` Değişkenin kendisine işaret yalnızca dört bayt işaretçi içeren `Double` atanmış değer.  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>CSByte örneği  
 Aşağıdaki örnekte `CSByte` sayısal bir değere dönüştürmek için işlevi `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>CShort örneği  
 Aşağıdaki örnekte `CShort` sayısal bir değere dönüştürmek için işlevi `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>CSng örneği  
 Aşağıdaki örnekte `CSng` değerlerine dönüştürmek için işlevi `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>CStr örneği  
 Aşağıdaki örnekte `CStr` sayısal bir değere dönüştürmek için işlevi `String`.  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 Aşağıdaki örnekte `CStr` dönüştürmek için işlevi `Date` değerler `String` değerleri.  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr` her zaman oluşturur bir `Date` geçerli yerel ayar için örneğin, standart kısa biçiminde bir değer "6/15/2003 4:35:47 PM". Ancak, `CStr` bastırır *nötr değerleri* , 1/1/0001 tarih ve saat için 00:00:00 için.  
  
 Tarafından döndürülen değerleri hakkında daha fazla ayrıntı için `CStr`, bkz: [CStr işlevinin dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Cuınt örneği  
 Aşağıdaki örnekte `CUInt` sayısal bir değere dönüştürmek için işlevi `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>CULng örneği  
 Aşağıdaki örnekte `CULng` sayısal bir değere dönüştürmek için işlevi `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>CUShort örneği  
 Aşağıdaki örnekte `CUShort` sayısal bir değere dönüştürmek için işlevi `UShort`.  
  
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
