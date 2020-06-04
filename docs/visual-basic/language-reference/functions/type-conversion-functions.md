---
title: Tür Dönüştürme İşlevleri
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
ms.openlocfilehash: 5c0cfae01da02222d0827e81ec1ed35ce353ead1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415381"
---
# <a name="type-conversion-functions-visual-basic"></a>Tür Dönüştürme İşlevleri (Visual Basic)

Bu işlevler satır içi olarak derlenir, yani dönüştürme kodu, ifadeyi değerlendiren kodun bir parçasıdır. Bazen dönüştürmeyi gerçekleştirmek için bir yordam çağrısı yoktur ve bu da performansı geliştirir. Her işlev bir ifadeyi belirli bir veri türüne zorlar.

## <a name="syntax"></a>Sözdizimi

```vb
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

## <a name="part"></a>Bölüm

`expression`  
Gereklidir. Kaynak veri türünün herhangi bir ifadesi.

## <a name="return-value-data-type"></a>Dönüş değeri veri türü

İşlev adı, aşağıdaki tabloda gösterildiği gibi, döndürdüğü değerin veri türünü belirler.

|İşlev adı|Dönüş veri türü|`expression`Bağımsız değişken aralığı|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[Boolean Veri Türü](../data-types/boolean-data-type.md)|Herhangi bir geçerli `Char` veya `String` veya sayısal ifade.|
|`CByte`|[Byte Veri Türü](../data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType>(0) ila <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile kayan nokta ile bayta dönüştürme performansını iyileştirir `CByte` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CChar`|[Char Veri Türü](../data-types/char-data-type.md)|Herhangi `Char` bir geçerli veya `String` ifade; yalnızca ilk karakter `String` dönüştürülür; değer 0 ile 65535 (işaretsiz) olabilir.|
|`CDate`|[Date Veri Türü](../data-types/date-data-type.md)|Tarih ve saatin geçerli bir gösterimi.|
|`CDbl`|[Double Veri Türü](../data-types/double-data-type.md)|-1.79769313486231570 e + 308 ile-4.94065645841246544 E-324 arasında negatif değerler için; 4.94065645841246544 e-324-1.79769313486231570 E + 308 arası pozitif değerler için.|
|`CDec`|[Decimal Veri Türü](../data-types/decimal-data-type.md)|+/-79228162514264337593543950335 sıfır ölçekli sayılar, diğer bir deyişle ondalık basamak içermeyen sayılar. 28 ondalık basamak içeren sayılar için, Aralık +/-7.9228162514264337593543950335 olur. Olası en küçük sıfır olmayan sayı 0,0000000000000000000000000001 ' dir (+/-1E-28).|
|`CInt`|[Integer Veri Türü](../data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType>(-2.147.483.648)- <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); Kesirli parçalar yuvarlanır.<sup> 1</sup> <br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını, işlevle tamsayı dönüştürmeye en iyi duruma getirir `CInt` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın. |
|`CLng`|[Long Veri Türü](../data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType>(-9223372036854775808) ila <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile, kayan noktanın performansını 64 bit tamsayı dönüştürmeye en iyi duruma getirir `CLng` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CObj`|[Nesne Veri Türü](../data-types/object-data-type.md)|Herhangi bir geçerli ifade.|
|`CSByte`|[SByte Veri Türü](../data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType>(-128)- <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile, kayan nokta ile işaretli bayt dönüştürmesinin performansını iyileştirir `CSByte` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CShort`|[Short Veri Türü](../data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType>(-32.768)- <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile kayan noktalı 16 bit tam sayı dönüştürmesi performansını en iyi duruma getirir `CShort` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CSng`|[Single Veri Türü](../data-types/single-data-type.md)|-3.402823 e + 38 ila-1.401298 E-45 negatif değerler için; 1.401298 e-45 ile pozitif değerler için 3.402823 E + 38 arası.|
|`CStr`|[Dize Veri Türü](../data-types/string-data-type.md)|`CStr`Bağımsız değişkene bağlı olarak döndürür `expression` . Bkz. [CStr işlevi Için dönüş değerleri](return-values-for-the-cstr-function.md).|
|`CUInt`|[UInteger Veri Türü](../data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType>(0) ila <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını, işlevle işaretsiz tamsayı dönüştürmeye en iyi duruma getirir `CUInt` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CULng`|[ULong Veri Türü](../data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType>(0)- <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını, işlevle işaretsiz uzun tamsayı dönüştürmeye en iyi duruma getirir `CULng` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CUShort`|[UShort Veri Türü](../data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType>(0) ila <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile kayan noktalı işaretsiz 16 bit tam sayı dönüştürmesi performansını en iyi duruma getirir `CUShort` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|

<sup>1</sup> kesirli parçalar *banker 'in yuvarlanması*adlı özel bir yuvarlama türüne tabi olabilir. Daha fazla bilgi için "açıklamalar" başlığına bakın.

## <a name="remarks"></a>Açıklamalar

Bir kural olarak, `ToString()` <xref:System.Convert> veya bağımsız bir tür yapısı ya da sınıf üzerinde gibi .NET Framework yöntemlerine Visual Basic tür dönüştürme işlevlerini tercih etmelisiniz. Visual Basic işlevleri Visual Basic kodla en iyi etkileşim için tasarlanmıştır ve ayrıca, kaynak kodunuzu daha kısa ve daha kolay okunabilir hale getirir. Ayrıca, .NET Framework dönüştürme yöntemleri her zaman Visual Basic işlevlerle aynı sonuçları oluşturmaz, örneğin, öğesine dönüştürme sırasında `Boolean` `Integer` . Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

Visual Basic 15,8 ' den itibaren, <xref:System.Single> <xref:System.Double> Aşağıdaki yöntemler tarafından döndürülen veya değeri tamsayı dönüştürme işlevlerinden birine geçirdiğinizde (,,, `CByte` `CShort` ,, `CInt` `CLng` `CSByte` `CUShort` , `CUInt` `CULng` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

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

Bu iyileştirme, çok sayıda tamsayı dönüştürme yapan kodun hızlı bir şekilde çalışmasını sağlar. Aşağıdaki örnekte, bu en iyileştirilmiş kayan noktadan tamsayı dönüştürmeleri gösterilmektedir:

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

- **Zorlama.** Genel olarak, bir işlemin sonucunu varsayılan veri türü yerine belirli bir veri türüne zorlamak için veri türü dönüştürme işlevlerini kullanabilirsiniz. Örneğin, `CDec` tek duyarlıklı, çift duyarlıklı veya tamsayı aritmetiğinin normalde gerçekleştiğinin ondalık aritmetiğini zorlamak için kullanın.

- **Dönüştürme başarısız oldu.** `expression`İşlevine geçirilen, dönüştürülecek veri türü aralığının dışındaysa, bir <xref:System.OverflowException> gerçekleşir.

- **Kesirli parçalar.** İntegral olmayan bir değeri integral türüne dönüştürdüğünüzde, tamsayı dönüştürme işlevleri ( `CByte` , `CInt` ,, `CLng` `CSByte` , `CShort` , `CUInt` , `CULng` , ve `CUShort` ) Kesirli parçayı kaldırır ve değeri en yakın tamsayıya yuvarlar.

     Kesirli bölüm tam olarak 0,5 ise, tamsayı dönüştürme işlevleri onu en yakın çift tamsayıya yuvarlar. Örneğin, 0,5, 0, 1,5 ve 2,5 her ikisi de 2 ' ye yuvarlanır. Bu bazen Banker yuvarlama olarak adlandırılır ve amacı, bu tür sayıları birlikte eklerken *birikmekte*olan bir sapma için telafi sağlamaktır.

     `CInt`ve, `CLng` <xref:Microsoft.VisualBasic.Conversion.Int%2A> <xref:Microsoft.VisualBasic.Conversion.Fix%2A> bir sayının kesirli kısmını yuvarlamak yerine kesten ve işlevlerinden farklıdır. Ayrıca, `Fix` ve `Int` her zaman geçirdiğiniz veri türünde bir değer döndürür.

- **Tarih/saat dönüştürmeleri.** <xref:Microsoft.VisualBasic.Information.IsDate%2A>Bir değerin tarih ve saate dönüştürülebileceğini öğrenmek için işlevini kullanın. `CDate`Tarih değişmez değerlerini ve zaman rakamlarını tanır, ancak sayısal değerleri tanımaz. Visual Basic 6,0 `Date` değerini `Date` Visual Basic 2005 veya sonraki sürümlerde bir değere dönüştürmek için <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

- **Bağımsız tarih/saat değerleri.** [Tarih veri türü](../data-types/date-data-type.md) her zaman hem tarih hem de saat bilgilerini içerir. Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir. Bir `Date` değeri dizeye dönüştürürseniz, `CStr` sonuçta elde edilen dizedeki nötr değerler içermez. Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00 har" olur; tarih bilgileri bastırılır. Ancak, tarih bilgileri özgün değerde hala bulunur `Date` ve işlev gibi işlevlerle kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .

- **Kültür duyarlılığı.** Dizeleri içeren tür dönüştürme işlevleri, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüştürme işlemleri gerçekleştirir. Örneğin, `CDate` tarih biçimlerini sisteminizin yerel ayara göre tanır. Yerel ayarınız için doğru sırada gün, ay ve yıl girmelisiniz veya tarih doğru şekilde yorumlanmayabilir. Uzun tarih biçimi, "Çarşamba" gibi bir haftanın günü dizesi içeriyorsa tanınmıyor.

     Bir değerin dize gösterimine ya da yerel ayarınız tarafından belirtilenden farklı bir biçimde dönüştürmeniz gerekiyorsa Visual Basic tür dönüştürme işlevlerini kullanamazsınız. Bunu yapmak için, bu `ToString(IFormatProvider)` `Parse(String, IFormatProvider)` değerin türünün ve yöntemlerini kullanın. Örneğin, bir <xref:System.Double.Parse%2A?displayProperty=nameWithType> dizeyi öğesine dönüştürürken `Double` ve <xref:System.Double.ToString%2A?displayProperty=nameWithType> türü bir değeri dizeye dönüştürürken kullanın `Double` .

## <a name="ctype-function"></a>CType İşlevi

[CType işlevi](ctype-function.md) ikinci bir bağımsız değişken alır, `typename` ve, `expression` `typename` `typename` geçerli bir dönüştürme var olan herhangi bir veri türü, yapı, sınıf veya arabirim olabilir.

`CType`Diğer tür dönüştürme anahtar sözcükleriyle bir karşılaştırması için bkz. [DirectCast Işleci](../operators/directcast-operator.md) ve [TryCast İşleci](../operators/trycast-operator.md).

## <a name="cbool-example"></a>CBool örneği

Aşağıdaki örnek, `CBool` ifadeleri değerlere dönüştürmek için işlevini kullanır `Boolean` . Bir ifade sıfır dışında bir değer olarak değerlendirilirse, değerini `CBool` döndürür `True` ; Aksi takdirde döndürür `False` .

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a>CByte örneği

Aşağıdaki örnek, `CByte` bir ifadeyi öğesine dönüştürmek için işlevini kullanır `Byte` .

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a>CChar örneği

Aşağıdaki örnek, `CChar` bir ifadenin ilk karakterini bir türe dönüştürmek için işlevini kullanır `String` `Char` .

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

Giriş bağımsız değişkeni `CChar` veri türünde `Char` veya olmalıdır `String` . `CChar` `CChar` Sayısal bir veri türü kabul edilemediğinden bir sayıyı karaktere dönüştürmek için kullanamazsınız. Aşağıdaki örnek, bir kod noktasını temsil eden bir sayı edinir (karakter kodu) ve karşılık gelen karaktere dönüştürür. Bu, <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> `CInt` dizeyi türe dönüştürmek `Integer` ve `ChrW` sayıyı türe dönüştürmek için, basamak dizesini almak için işlevini kullanır `Char` .

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a>CDate örneği

Aşağıdaki örnek, `CDate` dizeleri değerlere dönüştürmek için işlevini kullanır `Date` . Genel olarak, sabit kodlama tarihleri ve saatleri dizeler (Bu örnekte gösterildiği gibi) önerilmez. #Feb 12, 1969 # ve #4:45:23 PM # gibi tarih değişmez değerlerini ve zaman değişmez değerlerini kullanın.

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a>CDbl örneği

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a>CDec örneği

Aşağıdaki örnek, `CDec` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `Decimal` .

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a>CInt örneği

Aşağıdaki örnek, `CInt` bir değeri öğesine dönüştürmek için işlevini kullanır `Integer` .

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a>CLng örneği

Aşağıdaki örnek, `CLng` değerlerini değerine dönüştürmek için işlevini kullanır `Long` .

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a>CObj örneği

Aşağıdaki örnek, `CObj` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `Object` . `Object`Değişken kendisine atanan değere işaret eden yalnızca dört baytlık bir işaretçi içerir `Double` .

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a>CSByte örneği

Aşağıdaki örnek, `CSByte` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `SByte` .

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a>CShort örneği

Aşağıdaki örnek, `CShort` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `Short` .

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a>CSng örneği

Aşağıdaki örnek, `CSng` değerlerini değerine dönüştürmek için işlevini kullanır `Single` .

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a>CStr örneği

Aşağıdaki örnek, `CStr` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `String` .

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

Aşağıdaki örnek, `CStr` değerleri değerlere dönüştürmek için işlevini kullanır `Date` `String` .

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

`CStr`her zaman `Date` geçerli yerel ayar için standart kısa biçimde (örneğin, "6/15/2003 4:35:47 PM") bir değer oluşturur. Ancak, `CStr` Tarih ve 00:00:00 için 1/1/0001 *nötr değerlerini* saat için bastırır.

Tarafından döndürülen değerler hakkında daha fazla ayrıntı için `CStr` bkz. [CStr Işlevi Için dönüş değerleri](return-values-for-the-cstr-function.md).

## <a name="cuint-example"></a>CUInt örneği

Aşağıdaki örnek, `CUInt` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `UInteger` .

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a>Külörnek örneği

Aşağıdaki örnek, `CULng` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `ULong` .

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a>CUShort örneği

Aşağıdaki örnek, `CUShort` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `UShort` .

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Dönüşüm İşlevleri](conversion-functions.md)
- [Visual Basic'de Tür Dönüştürmeleri](../../programming-guide/language-features/data-types/type-conversions.md)
