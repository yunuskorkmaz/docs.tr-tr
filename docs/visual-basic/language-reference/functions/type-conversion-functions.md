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
ms.openlocfilehash: 0516a579c1ad9944284d25f2f057f2f03619bbab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582984"
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

## <a name="part"></a>Bölümüyle

`expression`  
Gerekli. Kaynak veri türünün herhangi bir ifadesi.

## <a name="return-value-data-type"></a>Dönüş değeri veri türü

İşlev adı, aşağıdaki tabloda gösterildiği gibi, döndürdüğü değerin veri türünü belirler.

|İşlev adı|Dönüş veri türü|@No__t_0 bağımsız değişkeni aralığı|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Geçerli bir `Char` veya `String` ya da sayısal ifade.|
|`CByte`|[Byte Veri Türü](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını `CByte` işlevi ile bayt dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CChar`|[Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)|Herhangi bir geçerli `Char` veya `String` ifadesi; `String` yalnızca ilk karakteri dönüştürülür; değer 0 ile 65535 (işaretsiz) olabilir.|
|`CDate`|[Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Tarih ve saatin geçerli bir gösterimi.|
|`CDbl`|[Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 ile-4.94065645841246544 E-324 arasında negatif değerler için; 4.94065645841246544 e-324-1.79769313486231570 E + 308 arası pozitif değerler için.|
|`CDec`|[Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79228162514264337593543950335 sıfır ölçekli sayılar, diğer bir deyişle ondalık basamak içermeyen sayılar. 28 ondalık basamak içeren sayılar için, Aralık +/-7.9228162514264337593543950335 olur. Olası en küçük sıfır olmayan sayı 0,0000000000000000000000000001 ' dir (+/-1E-28).|
|`CInt`|[Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); kesirli parçalar yuvarlanır. <sup>1</sup> <br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CInt` işlevi ile tam sayı dönüştürmesi için en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın. |
|`CLng`|[Long Veri Türü](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını `CLng` işlevi ile 64 bit tam sayı dönüştürmeye iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CObj`|[Object Veri Türü](../../../visual-basic/language-reference/data-types/object-data-type.md)|Herhangi bir geçerli ifade.|
|`CSByte`|[SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, `CSByte` işlevi ile kayan nokta olarak işaretli bayt dönüştürmesinin performansını iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CShort`|[Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını `CShort` işlevi ile 16 bit tam sayı dönüştürmeye iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CSng`|[Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 ila-1.401298 E-45 negatif değerler için; 1.401298 e-45 ile pozitif değerler için 3.402823 E + 38 arası.|
|`CStr`|[String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)|@No__t_0 için döndürür `expression` bağımsız değişkenine bağlıdır. Bkz. [CStr işlevi Için dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|
|`CUInt`|[UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını `CUInt` işlevi ile işaretsiz tamsayı dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CULng`|[ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını `CULng` işlevi ile işaretsiz uzun tamsayı dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|
|`CUShort`|[UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup><br/><br/>Visual Basic 15,8 ' den başlayarak, Visual Basic, `CUShort` işlevi ile kayan noktalı işaretsiz 16 bit tam sayı dönüştürmesi performansını iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. Örnek için [CInt örnek](#cint-example) bölümüne bakın.|

<sup>1</sup> kesirli parçalar *banker 'in yuvarlanması*adlı özel bir yuvarlama türüne tabi olabilir. Daha fazla bilgi için "açıklamalar" başlığına bakın.

## <a name="remarks"></a>Açıklamalar

Kural olarak, <xref:System.Convert> sınıfında veya tek bir tür yapısında veya sınıfında `ToString()` gibi .NET Framework yöntemlere tercih olarak Visual Basic tür dönüştürme işlevlerini kullanmanız gerekir. Visual Basic işlevleri Visual Basic kodla en iyi etkileşim için tasarlanmıştır ve ayrıca, kaynak kodunuzu daha kısa ve daha kolay okunabilir hale getirir. Ayrıca, .NET Framework dönüştürme yöntemleri her zaman Visual Basic işlevlerle aynı sonuçları oluşturmaz, örneğin `Boolean` `Integer` dönüştürmektir. Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

Visual Basic 15,8 ' den başlayarak, aşağıdaki yöntemlerle döndürülen <xref:System.Single> veya <xref:System.Double> değeri tamsayı dönüştürme işlevlerinden birine (`CByte`, `CShort`, `CInt`, @no__ geçirdiğinizde) kayan noktalı tamsayı dönüştürme performansı en iyi duruma getirilir. t_5, `CSByte`, `CUShort`, `CUInt`, `CULng`):

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

- **Zorlama.** Genel olarak, bir işlemin sonucunu varsayılan veri türü yerine belirli bir veri türüne zorlamak için veri türü dönüştürme işlevlerini kullanabilirsiniz. Örneğin, tek duyarlıklı, çift duyarlıklı veya tamsayı aritmetiğinin normalde gerçekleştiği durumlarda ondalık aritmetiğini zorlamak için `CDec` kullanın.

- **Dönüştürme başarısız oldu.** İşleve geçirilen `expression`, dönüştürülecek veri türü aralığının dışındaysa, bir <xref:System.OverflowException> oluşur.

- **Kesirli parçalar.** İntegral olmayan bir değeri integral türüne dönüştürdüğünüzde, tamsayı dönüştürme işlevleri (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` ve `CUShort`) Kesirli parçayı kaldırır ve değeri en yakın tamsayıya yuvarlar.

     Kesirli bölüm tam olarak 0,5 ise, tamsayı dönüştürme işlevleri onu en yakın çift tamsayıya yuvarlar. Örneğin, 0,5, 0, 1,5 ve 2,5 her ikisi de 2 ' ye yuvarlanır. Bu bazen Banker yuvarlama olarak adlandırılır ve amacı, bu tür sayıları birlikte eklerken *birikmekte*olan bir sapma için telafi sağlamaktır.

     `CInt` ve `CLng` <xref:Microsoft.VisualBasic.Conversion.Int%2A> ve <xref:Microsoft.VisualBasic.Conversion.Fix%2A> işlevlerinden farklıdır, bu, sayının kesirli kısmını yuvarlayıp keser. Ayrıca, `Fix` ve `Int`, her zaman geçirdiğiniz veri türünde bir değer döndürür.

- **Tarih/saat dönüştürmeleri.** Değerin tarih ve saate dönüştürülebileceğini öğrenmek için <xref:Microsoft.VisualBasic.Information.IsDate%2A> işlevini kullanın. `CDate` Tarih değişmez değerlerini ve zaman rakamlarını tanır, ancak sayısal değerleri tanımaz. Visual Basic 6,0 `Date` değerini Visual Basic 2005 veya sonraki sürümlerde `Date` değere dönüştürmek için <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

- **Bağımsız tarih/saat değerleri.** [Tarih veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md) her zaman hem tarih hem de saat bilgilerini içerir. Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir. Bir `Date` değerini bir dizeye dönüştürürseniz, `CStr` sonuç dizesinde nötr değerler içermez. Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00" olur. tarih bilgileri bastırılır. Ancak, tarih bilgileri özgün `Date` değerinde hala vardır ve <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> işlevi gibi işlevlerle kurtarılabilir.

- **Kültür duyarlılığı.** Dizeleri içeren tür dönüştürme işlevleri, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüştürme işlemleri gerçekleştirir. Örneğin, `CDate` tarih biçimlerini sisteminizin yerel ayara göre tanır. Yerel ayarınız için doğru sırada gün, ay ve yıl girmelisiniz veya tarih doğru şekilde yorumlanmayabilir. Uzun tarih biçimi, "Çarşamba" gibi bir haftanın günü dizesi içeriyorsa tanınmıyor.

     Bir değerin dize gösterimine ya da yerel ayarınız tarafından belirtilenden farklı bir biçimde dönüştürmeniz gerekiyorsa Visual Basic tür dönüştürme işlevlerini kullanamazsınız. Bunu yapmak için, bu değerin türünün `ToString(IFormatProvider)` ve `Parse(String, IFormatProvider)` yöntemlerini kullanın. Örneğin, bir dizeyi bir `Double` dönüştürürken <xref:System.Double.Parse%2A?displayProperty=nameWithType> kullanın ve `Double` türündeki bir değeri bir dizeye dönüştürürken <xref:System.Double.ToString%2A?displayProperty=nameWithType> kullanın.

## <a name="ctype-function"></a>CType İşlevi

[CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ikinci bir bağımsız değişken alır, `typename` ve `typename` `expression` ve `typename`, geçerli bir dönüştürme var olan herhangi bir veri türü, yapı, sınıf veya arabirim olabilir.

Diğer tür dönüştürme anahtar sözcükleriyle `CType` bir karşılaştırması için bkz. [DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md).

## <a name="cbool-example"></a>CBool örneği

Aşağıdaki örnek, ifadeleri `Boolean` değerlerine dönüştürmek için `CBool` işlevini kullanır. Bir ifade sıfır dışında bir değere değerlendirilirse, `CBool` `True` döndürür. Aksi takdirde, `False` döndürür.

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a>CByte örneği

Aşağıdaki örnek, bir ifadeyi `Byte` dönüştürmek için `CByte` işlevini kullanır.

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a>CChar örneği

Aşağıdaki örnek, bir `String` ifadesinin ilk karakterini `Char` türüne dönüştürmek için `CChar` işlevini kullanır.

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

@No__t_0 giriş bağımsız değişkeni `Char` veya `String` veri türünde olmalıdır. @No__t_1 sayısal bir veri türü kabul edemediğinden bir sayıyı bir karaktere dönüştürmek için `CChar` kullanamazsınız. Aşağıdaki örnek, bir kod noktasını temsil eden bir sayı edinir (karakter kodu) ve karşılık gelen karaktere dönüştürür. Basamak dizesini almak için <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> işlevini kullanır, dizeyi `Integer` türüne dönüştürmek için `CInt` ve sayıyı `Char` türüne dönüştürmek için `ChrW`.

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a>CDate örneği

Aşağıdaki örnek, dizeleri `Date` değerlerine dönüştürmek için `CDate` işlevini kullanır. Genel olarak, sabit kodlama tarihleri ve saatleri dizeler (Bu örnekte gösterildiği gibi) önerilmez. #Feb 12, 1969 # ve #4:45:23 PM # gibi tarih değişmez değerlerini ve zaman değişmez değerlerini kullanın.

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a>CDbl örneği

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a>CDec örneği

Aşağıdaki örnek, sayısal bir değeri `Decimal` dönüştürmek için `CDec` işlevini kullanır.

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a>CInt örneği

Aşağıdaki örnek, bir değeri `Integer` dönüştürmek için `CInt` işlevini kullanır.

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a>CLng örneği

Aşağıdaki örnek, değerleri `Long` dönüştürmek için `CLng` işlevini kullanır.

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a>CObj örneği

Aşağıdaki örnek, sayısal bir değeri `Object` dönüştürmek için `CObj` işlevini kullanır. @No__t_0 değişkeni, kendisine atanan `Double` değerine işaret eden yalnızca dört baytlık bir işaretçi içerir.

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a>CSByte örneği

Aşağıdaki örnek, sayısal bir değeri `SByte` dönüştürmek için `CSByte` işlevini kullanır.

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a>CShort örneği

Aşağıdaki örnek, sayısal bir değeri `Short` dönüştürmek için `CShort` işlevini kullanır.

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a>CSng örneği

Aşağıdaki örnek, değerleri `Single` dönüştürmek için `CSng` işlevini kullanır.

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a>CStr örneği

Aşağıdaki örnek, sayısal bir değeri `String` dönüştürmek için `CStr` işlevini kullanır.

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

Aşağıdaki örnek, `Date` değerlerini `String` değerlerine dönüştürmek için `CStr` işlevini kullanır.

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

`CStr`, geçerli yerel ayar için standart kısa biçimde her zaman bir `Date` değeri oluşturur, örneğin, "6/15/2003 4:35:47 PM". Ancak, `CStr` tarihi için 1/1/0001 *nötr değerlerini* ve saat için 00:00:00 ' i bastırır.

@No__t_0 tarafından döndürülen değerler hakkında daha fazla ayrıntı için bkz. [CStr işlevi Için dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).

## <a name="cuint-example"></a>CUInt örneği

Aşağıdaki örnek, sayısal bir değeri `UInteger` dönüştürmek için `CUInt` işlevini kullanır.

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a>Külörnek örneği

Aşağıdaki örnek, sayısal bir değeri `ULong` dönüştürmek için `CULng` işlevini kullanır.

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a>CUShort örneği

Aşağıdaki örnek, sayısal bir değeri `UShort` dönüştürmek için `CUShort` işlevini kullanır.

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
- [Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Visual Basic dönüşümler yazın](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
