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
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="08b11-102">Tür Dönüştürme İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08b11-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="08b11-103">Bu işlevlerdir derlenmiş satır içi dönüştürme kodu ifadeyi hesaplar kod parçası olan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="08b11-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="08b11-104">Bazen performansı artırır dönüştürme gerçekleştirmek için bir yordam hiçbir çağrı yoktur.</span><span class="sxs-lookup"><span data-stu-id="08b11-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="08b11-105">Her işlev belirli bir veri türüne bir ifadeyi olacak şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="08b11-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b11-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08b11-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="08b11-107">Bölümü</span><span class="sxs-lookup"><span data-stu-id="08b11-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="08b11-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="08b11-108">Required.</span></span> <span data-ttu-id="08b11-109">Herhangi bir ifade kaynak veri türü.</span><span class="sxs-lookup"><span data-stu-id="08b11-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="08b11-110">Dönüş değeri veri türü</span><span class="sxs-lookup"><span data-stu-id="08b11-110">Return Value Data Type</span></span>  
 <span data-ttu-id="08b11-111">İşlev adı aşağıdaki tabloda gösterildiği gibi döndürür, değerin veri türü belirler.</span><span class="sxs-lookup"><span data-stu-id="08b11-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="08b11-112">İşlev adı</span><span class="sxs-lookup"><span data-stu-id="08b11-112">Function name</span></span>|<span data-ttu-id="08b11-113">Dönüş veri türü</span><span class="sxs-lookup"><span data-stu-id="08b11-113">Return data type</span></span>|<span data-ttu-id="08b11-114">İçin aralığı `expression` bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="08b11-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="08b11-115">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="08b11-116">Tüm geçerli `Char` veya `String` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="08b11-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="08b11-117">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="08b11-118">0 ile 255 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="08b11-119">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="08b11-120">Tüm geçerli `Char` veya `String` ifade; yalnızca ilk karakteri bir `String` dönüştürülür; değeri, 0-65535 (imzalanmamış) olabilir.</span><span class="sxs-lookup"><span data-stu-id="08b11-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="08b11-121">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="08b11-122">Tüm geçerli temsili bir tarih ve saat.</span><span class="sxs-lookup"><span data-stu-id="08b11-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="08b11-123">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="08b11-124">-1.79769313486231570E + 308 ile - 4.94065645841246544E-324 negatif değerler; 4.94065645841246544E-324 1.79769313486231570E + 308 pozitif değerler için aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="08b11-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="08b11-125">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="08b11-126">sıfır ölçeklendirilmiş numaraları için diğer bir deyişle, ondalık konumu olmayan sayılar 79,228,162,514,264,337,593,543,950,335 +/-.</span><span class="sxs-lookup"><span data-stu-id="08b11-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="08b11-127">İle 28 ondalık sayılar için 7.9228162514264337593543950335 +/-aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="08b11-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="08b11-128">En küçük olası sıfır 0.0000000000000000000000000001 (+/-1E-28) sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="08b11-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="08b11-129">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="08b11-130">-2.147.483.648 2.147.483.647 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="08b11-131">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="08b11-132">-9,223,372,036,854,775,808 9,223,372,036,854,775,807 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="08b11-133">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="08b11-134">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="08b11-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="08b11-135">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="08b11-136">-128 127 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="08b11-137">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="08b11-138">-32.768 32.767 aracılığıyla; kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="08b11-139">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="08b11-140">-3.402823E + 38 ile - 1.401298E-45 negatif değerler; 1.401298E-45 3.402823E + 38 pozitif değerler için aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="08b11-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="08b11-141">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="08b11-142">İçin döndürür `CStr` bağımlı `expression` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="08b11-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="08b11-143">Bkz: [CStr işlevinin dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="08b11-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="08b11-144">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="08b11-145">0 ile 4.294.967.295 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="08b11-146">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="08b11-147">0 ile 18,446,744,073,709,551,615 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="08b11-148">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="08b11-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="08b11-149">0 ile 65.535 (imzalanmamış); kesirli bölümleri yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08b11-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="08b11-150"><sup>1</sup> kesirli bölümleri çağrılan yuvarlama bir özel tür tabi olabilir *banker yuvarlaması*.</span><span class="sxs-lookup"><span data-stu-id="08b11-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="08b11-151">"Açıklamalar" daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="08b11-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08b11-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08b11-152">Remarks</span></span>  
 <span data-ttu-id="08b11-153">Bir kural olarak, .NET Framework yöntemlerini yerine Visual Basic tür dönüştürme işlevleri gibi kullanmalısınız `ToString()`, her iki üzerinde <xref:System.Convert> sınıfı ya da bir bireysel tür yapısına veya sınıfı.</span><span class="sxs-lookup"><span data-stu-id="08b11-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="08b11-154">Visual Basic işlevleri, Visual Basic kodu en iyi etkileşim için tasarlanmıştır ve bunlar da kaynak kodunuzu daha kısa ve kolay okunur yapın.</span><span class="sxs-lookup"><span data-stu-id="08b11-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="08b11-155">Ayrıca, .NET Framework dönüştürme yöntemleri her zaman aynı sonucu dönüştürülürken örneğin Visual Basic işlevleri olarak vermez `Boolean` için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="08b11-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="08b11-156">Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="08b11-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="08b11-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="08b11-157">Behavior</span></span>  
  
-   <span data-ttu-id="08b11-158">**Zorlama.**</span><span class="sxs-lookup"><span data-stu-id="08b11-158">**Coercion.**</span></span> <span data-ttu-id="08b11-159">Genel olarak, varsayılan veri türü yerine belirli bir veri türüne bir işlemin sonucunu coerce için veri türüne dönüştürme işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08b11-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="08b11-160">Örneğin, `CDec` burada tek duyarlıklı, çift duyarlıklı ya da tamsayı aritmetik normalde alırken yer durumlarda ondalık aritmetik zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="08b11-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="08b11-161">**Başarısız dönüştürme.**</span><span class="sxs-lookup"><span data-stu-id="08b11-161">**Failed Conversions.**</span></span> <span data-ttu-id="08b11-162">Varsa `expression` işleve hangi BT dönüştürülmekte olan veri türü aralık dışında olduğu bir <xref:System.OverflowException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="08b11-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="08b11-163">**Kesirli bölümleri.**</span><span class="sxs-lookup"><span data-stu-id="08b11-163">**Fractional Parts.**</span></span> <span data-ttu-id="08b11-164">Bir tam sayıya nonintegral değeri dönüştürürken türü, tamsayı dönüştürme işlevleri (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, ve `CUShort`) Kaldır kesirli kısım ve değeri en yakın tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="08b11-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="08b11-165">Kesirli tam olarak bir parçasıysa 0,5, tamsayı dönüştürme işlevleri yuvarlamak kendisine en yakın çift tam sayı.</span><span class="sxs-lookup"><span data-stu-id="08b11-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="08b11-166">Örneğin, 0, 1.5 ve her ikisi de 2 yuvarlamak 2.5 0,5 yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="08b11-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="08b11-167">Buna bazen denir *banker yuvarlaması*, ve amacı gibi birçok numaraları birlikte eklerken birikebilir sapması dengelemek için.</span><span class="sxs-lookup"><span data-stu-id="08b11-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="08b11-168">`CInt` ve `CLng` farklı <xref:Microsoft.VisualBasic.Conversion.Int%2A> ve <xref:Microsoft.VisualBasic.Conversion.Fix%2A> hangi round, bir sayının kesirli kısmını yerine truncate işlevleri.</span><span class="sxs-lookup"><span data-stu-id="08b11-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="08b11-169">Ayrıca, `Fix` ve `Int` , geçirdiğiniz olarak her zaman aynı veri türünde bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="08b11-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="08b11-170">**Dönüşümler tarih veya saat.**</span><span class="sxs-lookup"><span data-stu-id="08b11-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="08b11-171">Kullanım <xref:Microsoft.VisualBasic.Information.IsDate%2A> bir tarih ve saat için bir değer dönüştürülüp dönüştürülemeyeceğini belirlemek için işlev.</span><span class="sxs-lookup"><span data-stu-id="08b11-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="08b11-172">`CDate` Tarih değişmez değerleri ve Saat rakamları ancak sayısal değerleri algılar.</span><span class="sxs-lookup"><span data-stu-id="08b11-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="08b11-173">Visual Basic 6.0 dönüştürmek için `Date` değeri bir `Date` değeri Visual Basic 2005 veya sonraki sürümler, kullanabileceğiniz <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08b11-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="08b11-174">**Nötr tarih/saat değerleri.**</span><span class="sxs-lookup"><span data-stu-id="08b11-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="08b11-175">[Tarih veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md) her zaman tarih ve saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="08b11-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="08b11-176">Tür dönüşümü amaçları doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *nötr değeri* tarihini ve 00:00:00 (gece yarısı) süresi dilden bağımsız bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08b11-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="08b11-177">Dönüştürürseniz, bir `Date` değerini bir dizeyle `CStr` nötr değerleri sonuç dizesinde içermez.</span><span class="sxs-lookup"><span data-stu-id="08b11-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="08b11-178">Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dizeye sonucu "9:30:00 AM"; tarih bilgisini engellenir.</span><span class="sxs-lookup"><span data-stu-id="08b11-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="08b11-179">Ancak, tarih bilgisini özgün hala mevcut olduğu `Date` değer ve işlevleriyle gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> işlevi.</span><span class="sxs-lookup"><span data-stu-id="08b11-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="08b11-180">**Kültür hassasiyet.**</span><span class="sxs-lookup"><span data-stu-id="08b11-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="08b11-181">Dizeleri içeren tür dönüştürme işlevleri dönüştürmeleri uygulama için geçerli kültür ayarları göre gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="08b11-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="08b11-182">Örneğin, `CDate` tarih biçimleri, sisteminizin yerel ayarına göre tanır.</span><span class="sxs-lookup"><span data-stu-id="08b11-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="08b11-183">Gün, ay ve yıl bölgeniz için doğru sırada sağlamanız gerekir veya tarih doğru yorumlanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="08b11-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="08b11-184">"Çarşamba" gibi bir haftanın günü dize içeriyorsa, bir uzun tarih biçimi tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="08b11-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="08b11-185">İçin veya bir biçimde bölgeniz tarafından belirtilen bir dışında bir değer bir dize gösterimini dönüştürmek istiyorsanız, Visual Basic tür dönüştürme işlevleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="08b11-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="08b11-186">Bunu yapmak için kullanın `ToString(IFormatProvider)` ve `Parse(String, IFormatProvider)` yöntemleri bu değerin türü.</span><span class="sxs-lookup"><span data-stu-id="08b11-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="08b11-187">Örneğin, <xref:System.Double.Parse%2A?displayProperty=nameWithType> bir dizesine dönüştürürken bir `Double`ve <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` dizeye.</span><span class="sxs-lookup"><span data-stu-id="08b11-187">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="08b11-188">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="08b11-188">CType Function</span></span>  
 <span data-ttu-id="08b11-189">[CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ikinci bir bağımsız değişken `typename`ve olacak şekilde zorlar `expression` için `typename`, burada `typename` veri türü, yapısı, sınıf veya arabirim için mevcut geçerli bir dönüştürme olabilir.</span><span class="sxs-lookup"><span data-stu-id="08b11-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="08b11-190">Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="08b11-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="08b11-191">CBool örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-191">CBool Example</span></span>  
 <span data-ttu-id="08b11-192">Aşağıdaki örnek kullanır `CBool` ifadeleri için dönüştürmek için işlevi `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="08b11-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="08b11-193">Bir ifadenin sıfırdan farklı bir değere değerlendirilirse `CBool` döndürür `True`; Aksi takdirde döndürdüğü `False`.</span><span class="sxs-lookup"><span data-stu-id="08b11-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="08b11-194">CByte örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-194">CByte Example</span></span>  
 <span data-ttu-id="08b11-195">Aşağıdaki örnek kullanır `CByte` bir ifadeyi dönüştürmek için işlevi bir `Byte`.</span><span class="sxs-lookup"><span data-stu-id="08b11-195">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="08b11-196">CChar örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-196">CChar Example</span></span>  
 <span data-ttu-id="08b11-197">Aşağıdaki örnek kullanır `CChar` ilk karakteri dönüştürmek için işlevi bir `String` ifade bir `Char` türü.</span><span class="sxs-lookup"><span data-stu-id="08b11-197">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="08b11-198">Giriş bağımsız değişkeni `CChar` veri türünde olmalıdır `Char` veya `String`.</span><span class="sxs-lookup"><span data-stu-id="08b11-198">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="08b11-199">Kullanamazsınız `CChar` olduğundan bir karakter, sayı dönüştürülemiyor `CChar` sayısal veri türü kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="08b11-199">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="08b11-200">Aşağıdaki örnek kod noktası (karakter kodu) gösteren bir sayı alır ve karşılık gelen karakter dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="08b11-200">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="08b11-201">Kullandığı <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> basamak dizisini elde etmek için işlevi `CInt` dize türüne dönüştürmek için `Integer`, ve `ChrW` sayıyı türüne dönüştürmek için `Char`.</span><span class="sxs-lookup"><span data-stu-id="08b11-201">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="08b11-202">CDate örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-202">CDate Example</span></span>  
 <span data-ttu-id="08b11-203">Aşağıdaki örnek kullanır `CDate` dizeye dönüştürmek için işlevi `Date` değerleri.</span><span class="sxs-lookup"><span data-stu-id="08b11-203">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="08b11-204">Genel olarak, kodlama sabit tarihler ve saatler (Bu örnekte gösterildiği gibi) dizesi olarak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="08b11-204">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="08b11-205">Tarih değişmez değerleri ve #Feb 12 1969 # gibi saat değişmez değerleri kullanın ve # 4:45:23 PM #, bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="08b11-205">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="08b11-206">CDbl örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-206">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="08b11-207">CDec örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-207">CDec Example</span></span>  
 <span data-ttu-id="08b11-208">Aşağıdaki örnek kullanır `CDec` sayısal değerine dönüştürmek için işlevi `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="08b11-208">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="08b11-209">CInt örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-209">CInt Example</span></span>  
 <span data-ttu-id="08b11-210">Aşağıdaki örnek kullanır `CInt` değerine dönüştürmek için işlevi `Integer`.</span><span class="sxs-lookup"><span data-stu-id="08b11-210">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a><span data-ttu-id="08b11-211">CLng örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-211">CLng Example</span></span>  
 <span data-ttu-id="08b11-212">Aşağıdaki örnek kullanır `CLng` değerine dönüştürmek için işlevi `Long`.</span><span class="sxs-lookup"><span data-stu-id="08b11-212">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="08b11-213">CObj örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-213">CObj Example</span></span>  
 <span data-ttu-id="08b11-214">Aşağıdaki örnek kullanır `CObj` sayısal değerine dönüştürmek için işlevi `Object`.</span><span class="sxs-lookup"><span data-stu-id="08b11-214">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="08b11-215">`Object` Değişkenin kendisine içerir, işaret yalnızca dört bayt işaretçi `Double` kendisine atanmış bir değer.</span><span class="sxs-lookup"><span data-stu-id="08b11-215">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="08b11-216">CSByte örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-216">CSByte Example</span></span>  
 <span data-ttu-id="08b11-217">Aşağıdaki örnek kullanır `CSByte` sayısal değerine dönüştürmek için işlevi `SByte`.</span><span class="sxs-lookup"><span data-stu-id="08b11-217">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="08b11-218">CShort örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-218">CShort Example</span></span>  
 <span data-ttu-id="08b11-219">Aşağıdaki örnek kullanır `CShort` sayısal değerine dönüştürmek için işlevi `Short`.</span><span class="sxs-lookup"><span data-stu-id="08b11-219">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="08b11-220">CSng örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-220">CSng Example</span></span>  
 <span data-ttu-id="08b11-221">Aşağıdaki örnek kullanır `CSng` değerine dönüştürmek için işlevi `Single`.</span><span class="sxs-lookup"><span data-stu-id="08b11-221">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="08b11-222">CStr örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-222">CStr Example</span></span>  
 <span data-ttu-id="08b11-223">Aşağıdaki örnek kullanır `CStr` sayısal değerine dönüştürmek için işlevi `String`.</span><span class="sxs-lookup"><span data-stu-id="08b11-223">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="08b11-224">Aşağıdaki örnek kullanır `CStr` dönüştürmek için işlevi `Date` değerler `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="08b11-224">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="08b11-225">`CStr` her zaman işleyen bir `Date` geçerli yerel ayar için örneğin, standart kısa biçimindeki değerini "15/6/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="08b11-225">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="08b11-226">Ancak, `CStr` bastırır *nötr değerleri* 1/1/0001 için tarih ve saat için 00:00:00.</span><span class="sxs-lookup"><span data-stu-id="08b11-226">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="08b11-227">Tarafından döndürülen değerleri hakkında daha fazla ayrıntı için `CStr`, bkz: [CStr işlevinin dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="08b11-227">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="08b11-228">Cuınt örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-228">CUInt Example</span></span>  
 <span data-ttu-id="08b11-229">Aşağıdaki örnek kullanır `CUInt` sayısal değerine dönüştürmek için işlevi `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="08b11-229">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="08b11-230">CULng örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-230">CULng Example</span></span>  
 <span data-ttu-id="08b11-231">Aşağıdaki örnek kullanır `CULng` sayısal değerine dönüştürmek için işlevi `ULong`.</span><span class="sxs-lookup"><span data-stu-id="08b11-231">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="08b11-232">CUShort örneği</span><span class="sxs-lookup"><span data-stu-id="08b11-232">CUShort Example</span></span>  
 <span data-ttu-id="08b11-233">Aşağıdaki örnek kullanır `CUShort` sayısal değerine dönüştürmek için işlevi `UShort`.</span><span class="sxs-lookup"><span data-stu-id="08b11-233">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="08b11-234">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08b11-234">See Also</span></span>  
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
 [<span data-ttu-id="08b11-235">Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="08b11-235">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="08b11-236">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="08b11-236">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
