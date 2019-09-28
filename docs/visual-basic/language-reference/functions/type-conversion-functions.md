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
ms.openlocfilehash: 6b448fa23368f7a0848c44362337b0ccc70b6162
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592070"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="16359-102">Tür Dönüştürme İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16359-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="16359-103">Bu işlevler satır içi olarak derlenir, yani dönüştürme kodu, ifadeyi değerlendiren kodun bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="16359-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="16359-104">Bazen dönüştürmeyi gerçekleştirmek için bir yordam çağrısı yoktur ve bu da performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="16359-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="16359-105">Her işlev bir ifadeyi belirli bir veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="16359-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16359-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16359-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="16359-107">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="16359-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="16359-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="16359-108">Required.</span></span> <span data-ttu-id="16359-109">Kaynak veri türünün herhangi bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="16359-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="16359-110">Dönüş değeri veri türü</span><span class="sxs-lookup"><span data-stu-id="16359-110">Return Value Data Type</span></span>  
 <span data-ttu-id="16359-111">İşlev adı, aşağıdaki tabloda gösterildiği gibi, döndürdüğü değerin veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="16359-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="16359-112">İşlev adı</span><span class="sxs-lookup"><span data-stu-id="16359-112">Function name</span></span>|<span data-ttu-id="16359-113">Dönüş veri türü</span><span class="sxs-lookup"><span data-stu-id="16359-113">Return data type</span></span>|<span data-ttu-id="16359-114">@No__t-0 bağımsız değişkeni aralığı</span><span class="sxs-lookup"><span data-stu-id="16359-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="16359-115">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="16359-116">Geçerli @no__t 0 veya `String` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="16359-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="16359-117">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="16359-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0)-<xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-119">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CByte` işleviyle birlikte bayt dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-120">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="16359-121">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="16359-122">Geçerli `Char` veya `String` ifadesi; yalnızca bir `String` ' nin ilk karakteri dönüştürülür; değer 0 ile 65535 (işaretsiz) olabilir.</span><span class="sxs-lookup"><span data-stu-id="16359-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="16359-123">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="16359-124">Tarih ve saatin geçerli bir gösterimi.</span><span class="sxs-lookup"><span data-stu-id="16359-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="16359-125">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="16359-126">-1.79769313486231570 e + 308 ile-4.94065645841246544 E-324 arasında negatif değerler için; 4.94065645841246544 e-324-1.79769313486231570 E + 308 arası pozitif değerler için.</span><span class="sxs-lookup"><span data-stu-id="16359-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="16359-127">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="16359-128">+/-79228162514264337593543950335 sıfır ölçekli sayılar, diğer bir deyişle ondalık basamak içermeyen sayılar.</span><span class="sxs-lookup"><span data-stu-id="16359-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="16359-129">28 ondalık basamak içeren sayılar için, Aralık +/-7.9228162514264337593543950335 olur.</span><span class="sxs-lookup"><span data-stu-id="16359-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="16359-130">Olası en küçük sıfır olmayan sayı 0,0000000000000000000000000001 ' dir (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="16359-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="16359-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="16359-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) ile <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647) arasında; kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="16359-133">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CInt` işleviyle tamsayı dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-134">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="16359-135">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="16359-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) ile <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807) arasında; kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-137">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CLng` işleviyle 64 bit tamsayı dönüştürmeye iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-138">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="16359-139">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="16359-140">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="16359-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="16359-141">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="16359-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) ile <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127) arasında; kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-143">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktalı olarak işaretli bayt dönüştürme performansını `CSByte` işleviyle iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-144">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="16359-145">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="16359-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) ile <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767) arasında; kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-147">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CShort` işleviyle 16 bit tam sayı dönüştürmesi ile iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-148">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="16359-149">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="16359-150">-3.402823 e + 38 ila-1.401298 E-45 negatif değerler için; 1.401298 e-45 ile pozitif değerler için 3.402823 E + 38 arası.</span><span class="sxs-lookup"><span data-stu-id="16359-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="16359-151">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="16359-152">@No__t-0 `expression` bağımsız değişkenine göre değişir.</span><span class="sxs-lookup"><span data-stu-id="16359-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="16359-153">Bkz. [CStr işlevi Için dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="16359-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="16359-154">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="16359-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0)-<xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-156">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CUInt` işleviyle işaretsiz tamsayı dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-157">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="16359-158">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="16359-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0)-<xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-160">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CULng` işleviyle işaretsiz uzun tamsayı dönüştürmeye en iyi duruma getirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-161">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="16359-162">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="16359-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="16359-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0)-<xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (işaretsiz); kesirli parçalar yuvarlanır. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16359-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="16359-164">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını `CUShort` işleviyle işaretsiz 16 bit tam sayı dönüştürmesi ile iyileştirir; daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="16359-165">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="16359-166"><sup>1</sup> kesirli parçalar *banker 'in yuvarlanması*adlı özel bir yuvarlama türüne tabi olabilir.</span><span class="sxs-lookup"><span data-stu-id="16359-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="16359-167">Daha fazla bilgi için "açıklamalar" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16359-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16359-168">Remarks</span></span>  
 <span data-ttu-id="16359-169">Bir kural olarak, <xref:System.Convert> sınıfında veya tek bir tür yapısında ya da sınıfında `ToString()` gibi .NET Framework yöntemlere tercih olarak Visual Basic tür dönüştürme işlevlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="16359-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="16359-170">Visual Basic işlevleri Visual Basic kodla en iyi etkileşim için tasarlanmıştır ve ayrıca, kaynak kodunuzu daha kısa ve daha kolay okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="16359-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="16359-171">Ayrıca, .NET Framework dönüştürme yöntemleri her zaman Visual Basic işlevlerle aynı sonuçları oluşturmaz; Örneğin, `Boolean` ' ı `Integer` ' e dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="16359-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="16359-172">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="16359-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  

<span data-ttu-id="16359-173">Visual Basic 15,8 ' den itibaren, aşağıdaki yöntemler tarafından döndürülen <xref:System.Single> veya <xref:System.Double> değerini tamsayı dönüştürme işlevlerinden birine geçirdiğinizde (`CByte`, `CShort`, `CInt`, @no__) kayan noktalı tamsayı dönüştürme performansı en iyi duruma getirilmiştir. t-5, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="16359-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

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

<span data-ttu-id="16359-174">Bu iyileştirme, çok sayıda tamsayı dönüştürme yapan kodun hızlı bir şekilde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="16359-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="16359-175">Aşağıdaki örnekte, bu en iyileştirilmiş kayan noktadan tamsayı dönüştürmeleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="16359-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="16359-176">Davranış</span><span class="sxs-lookup"><span data-stu-id="16359-176">Behavior</span></span>  
  
- <span data-ttu-id="16359-177">**Zorlama.**</span><span class="sxs-lookup"><span data-stu-id="16359-177">**Coercion.**</span></span> <span data-ttu-id="16359-178">Genel olarak, bir işlemin sonucunu varsayılan veri türü yerine belirli bir veri türüne zorlamak için veri türü dönüştürme işlevlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16359-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="16359-179">Örneğin, tek duyarlıklı, çift duyarlıklı veya tamsayı aritmetiğinin normalde gerçekleştiği durumlarda ondalık aritmetiğini zorlamak için `CDec` kullanın.</span><span class="sxs-lookup"><span data-stu-id="16359-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
- <span data-ttu-id="16359-180">**Dönüştürme başarısız oldu.**</span><span class="sxs-lookup"><span data-stu-id="16359-180">**Failed Conversions.**</span></span> <span data-ttu-id="16359-181">İşleve geçirilen `expression`, dönüştürülecek veri türü aralığının dışındaysa, bir <xref:System.OverflowException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="16359-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
- <span data-ttu-id="16359-182">**Kesirli parçalar.**</span><span class="sxs-lookup"><span data-stu-id="16359-182">**Fractional Parts.**</span></span> <span data-ttu-id="16359-183">İntegral olmayan bir değeri integral türüne dönüştürdüğünüzde, tamsayı dönüştürme işlevleri (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` ve `CUShort`) Kesirli parçayı kaldırır ve değeri en yakın tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="16359-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="16359-184">Kesirli bölüm tam olarak 0,5 ise, tamsayı dönüştürme işlevleri onu en yakın çift tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="16359-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="16359-185">Örneğin, 0,5, 0, 1,5 ve 2,5 her ikisi de 2 ' ye yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="16359-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="16359-186">Bu bazen Banker yuvarlama olarak adlandırılır ve amacı, bu tür sayıları birlikte eklerken *birikmekte*olan bir sapma için telafi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="16359-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="16359-187">`CInt` ve `CLng` <xref:Microsoft.VisualBasic.Conversion.Int%2A> ve <xref:Microsoft.VisualBasic.Conversion.Fix%2A> işlevlerinden farklıdır, bu, sayının kesirli kısmını yuvarlayıp keser.</span><span class="sxs-lookup"><span data-stu-id="16359-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="16359-188">Ayrıca, `Fix` ve `Int` her zaman, geçirdiğiniz veri türünde bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="16359-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
- <span data-ttu-id="16359-189">**Tarih/saat dönüştürmeleri.**</span><span class="sxs-lookup"><span data-stu-id="16359-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="16359-190">Değerin tarih ve saate dönüştürülebileceğini öğrenmek için <xref:Microsoft.VisualBasic.Information.IsDate%2A> işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="16359-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="16359-191">`CDate`, tarih değişmez değerlerini ve zaman rakamlarını tanır, ancak sayısal değerleri tanımaz.</span><span class="sxs-lookup"><span data-stu-id="16359-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="16359-192">Visual Basic 6,0 `Date` değerini Visual Basic 2005 veya sonraki sürümlerde `Date` değerine dönüştürmek için <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16359-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="16359-193">**Bağımsız tarih/saat değerleri.**</span><span class="sxs-lookup"><span data-stu-id="16359-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="16359-194">[Tarih veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md) her zaman hem tarih hem de saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="16359-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="16359-195">Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="16359-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="16359-196">Bir `Date` değerini bir dizeye dönüştürürseniz, `CStr` sonuç dizesinde nötr değerler içermez.</span><span class="sxs-lookup"><span data-stu-id="16359-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="16359-197">Örneğin, `#January 1, 0001 9:30:00#` ' ı bir dizeye dönüştürürseniz, sonuç "9:30:00" olur; tarih bilgileri bastırılır.</span><span class="sxs-lookup"><span data-stu-id="16359-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="16359-198">Ancak, tarih bilgileri özgün `Date` değerinde hala vardır ve <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> işlevi gibi işlevlerle kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="16359-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
- <span data-ttu-id="16359-199">**Kültür duyarlılığı.**</span><span class="sxs-lookup"><span data-stu-id="16359-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="16359-200">Dizeleri içeren tür dönüştürme işlevleri, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüştürme işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="16359-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="16359-201">Örneğin, `CDate`, sisteminizin yerel ayara göre tarih biçimlerini tanır.</span><span class="sxs-lookup"><span data-stu-id="16359-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="16359-202">Yerel ayarınız için doğru sırada gün, ay ve yıl girmelisiniz veya tarih doğru şekilde yorumlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="16359-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="16359-203">Uzun tarih biçimi, "Çarşamba" gibi bir haftanın günü dizesi içeriyorsa tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="16359-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="16359-204">Bir değerin dize gösterimine ya da yerel ayarınız tarafından belirtilenden farklı bir biçimde dönüştürmeniz gerekiyorsa Visual Basic tür dönüştürme işlevlerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="16359-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="16359-205">Bunu yapmak için, bu değerin türünün `ToString(IFormatProvider)` ve `Parse(String, IFormatProvider)` yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="16359-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="16359-206">Örneğin, bir dizeyi `Double` ' e dönüştürürken <xref:System.Double.Parse%2A?displayProperty=nameWithType> kullanın ve `Double` türündeki bir değeri bir dizeye dönüştürürken <xref:System.Double.ToString%2A?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="16359-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="16359-207">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="16359-207">CType Function</span></span>  
 <span data-ttu-id="16359-208">[CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ikinci bir bağımsız değişken alır, `typename` ve `expression` ' yi `typename` ' e zorlar; burada `typename`, geçerli bir dönüştürme var olan herhangi bir veri türü, yapı, sınıf veya arabirim olabilir.</span><span class="sxs-lookup"><span data-stu-id="16359-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="16359-209">Diğer tür dönüştürme anahtar sözcükleriyle `CType` ' ı bir karşılaştırma için bkz. [DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="16359-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="16359-210">CBool örneği</span><span class="sxs-lookup"><span data-stu-id="16359-210">CBool Example</span></span>  
 <span data-ttu-id="16359-211">Aşağıdaki örnek, ifadeleri `Boolean` değerlerine dönüştürmek için `CBool` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="16359-212">Bir ifade sıfır dışında bir değer olarak değerlendirilirse, `CBool` döndürür `True`; Aksi takdirde, `False` döndürür.</span><span class="sxs-lookup"><span data-stu-id="16359-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="16359-213">CByte örneği</span><span class="sxs-lookup"><span data-stu-id="16359-213">CByte Example</span></span>  
 <span data-ttu-id="16359-214">Aşağıdaki örnek, bir ifadeyi `Byte` ' e dönüştürmek için `CByte` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a><span data-ttu-id="16359-215">CChar örneği</span><span class="sxs-lookup"><span data-stu-id="16359-215">CChar Example</span></span>  
 <span data-ttu-id="16359-216">Aşağıdaki örnek, bir `String` ifadesinin ilk karakterini `Char` türüne dönüştürmek için `CChar` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 <span data-ttu-id="16359-217">@No__t-0 ' a ait giriş bağımsız değişkeni `Char` veya `String` veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16359-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="16359-218">Bir sayıyı bir karaktere dönüştürmek için `CChar` ' ı kullanamazsınız, çünkü `CChar` sayısal bir veri türünü kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="16359-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="16359-219">Aşağıdaki örnek, bir kod noktasını temsil eden bir sayı edinir (karakter kodu) ve karşılık gelen karaktere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="16359-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="16359-220">@No__t-0 işlevini kullanarak, dizeyi `Integer` türüne dönüştürmek için `CInt` ve sayıyı `Char` türüne dönüştürmek için `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="16359-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a><span data-ttu-id="16359-221">CDate örneği</span><span class="sxs-lookup"><span data-stu-id="16359-221">CDate Example</span></span>  
 <span data-ttu-id="16359-222">Aşağıdaki örnek, `CDate` işlevini kullanarak dizeleri `Date` değerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="16359-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="16359-223">Genel olarak, sabit kodlama tarihleri ve saatleri dizeler (Bu örnekte gösterildiği gibi) önerilmez.</span><span class="sxs-lookup"><span data-stu-id="16359-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="16359-224">#Feb 12, 1969 # ve #4:45:23 PM # gibi tarih değişmez değerlerini ve zaman değişmez değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="16359-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="16359-225">CDbl örneği</span><span class="sxs-lookup"><span data-stu-id="16359-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a><span data-ttu-id="16359-226">CDec örneği</span><span class="sxs-lookup"><span data-stu-id="16359-226">CDec Example</span></span>  
 <span data-ttu-id="16359-227">Aşağıdaki örnek, sayısal bir değeri `Decimal` ' e dönüştürmek için `CDec` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a><span data-ttu-id="16359-228">CInt örneği</span><span class="sxs-lookup"><span data-stu-id="16359-228">CInt Example</span></span>  
 <span data-ttu-id="16359-229">Aşağıdaki örnek, bir değeri `Integer` ' e dönüştürmek için `CInt` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a><span data-ttu-id="16359-230">CLng örneği</span><span class="sxs-lookup"><span data-stu-id="16359-230">CLng Example</span></span>
 <span data-ttu-id="16359-231">Aşağıdaki örnek, değerleri `Long` ' e dönüştürmek için `CLng` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a><span data-ttu-id="16359-232">CObj örneği</span><span class="sxs-lookup"><span data-stu-id="16359-232">CObj Example</span></span>  
 <span data-ttu-id="16359-233">Aşağıdaki örnek, sayısal bir değeri `Object` ' e dönüştürmek için `CObj` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="16359-234">@No__t-0 değişkeni, kendisine atanan @no__t 1 değerini gösteren yalnızca dört baytlık bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="16359-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="16359-235">CSByte örneği</span><span class="sxs-lookup"><span data-stu-id="16359-235">CSByte Example</span></span>  
 <span data-ttu-id="16359-236">Aşağıdaki örnek, sayısal bir değeri `SByte` ' e dönüştürmek için `CSByte` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a><span data-ttu-id="16359-237">CShort örneği</span><span class="sxs-lookup"><span data-stu-id="16359-237">CShort Example</span></span>  
 <span data-ttu-id="16359-238">Aşağıdaki örnek, sayısal bir değeri `Short` ' e dönüştürmek için `CShort` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a><span data-ttu-id="16359-239">CSng örneği</span><span class="sxs-lookup"><span data-stu-id="16359-239">CSng Example</span></span>  
 <span data-ttu-id="16359-240">Aşağıdaki örnek, değerleri `Single` ' e dönüştürmek için `CSng` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a><span data-ttu-id="16359-241">CStr örneği</span><span class="sxs-lookup"><span data-stu-id="16359-241">CStr Example</span></span>  
 <span data-ttu-id="16359-242">Aşağıdaki örnek, sayısal bir değeri `String` ' e dönüştürmek için `CStr` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 <span data-ttu-id="16359-243">Aşağıdaki örnek, `Date` değerlerini `String` değerlerine dönüştürmek için `CStr` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="16359-244">`CStr`, geçerli yerel ayar için standart kısa biçimde her zaman bir `Date` değeri işler (örneğin, "6/15/2003 4:35:47 PM").</span><span class="sxs-lookup"><span data-stu-id="16359-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="16359-245">Ancak, `CStr`, tarih ve 00:00:00 için *bağımsız 1/1/0001 nötr değerlerini* saat için bastırır.</span><span class="sxs-lookup"><span data-stu-id="16359-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="16359-246">@No__t-0 tarafından döndürülen değerler hakkında daha fazla ayrıntı için bkz. [CStr işlevi Için dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="16359-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="16359-247">CUInt örneği</span><span class="sxs-lookup"><span data-stu-id="16359-247">CUInt Example</span></span>  
 <span data-ttu-id="16359-248">Aşağıdaki örnek, sayısal bir değeri `UInteger` ' e dönüştürmek için `CUInt` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a><span data-ttu-id="16359-249">Külörnek örneği</span><span class="sxs-lookup"><span data-stu-id="16359-249">CULng Example</span></span>  
 <span data-ttu-id="16359-250">Aşağıdaki örnek, sayısal bir değeri `ULong` ' e dönüştürmek için `CULng` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a><span data-ttu-id="16359-251">CUShort örneği</span><span class="sxs-lookup"><span data-stu-id="16359-251">CUShort Example</span></span>  
 <span data-ttu-id="16359-252">Aşağıdaki örnek, sayısal bir değeri `UShort` ' e dönüştürmek için `CUShort` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16359-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="16359-253">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16359-253">See also</span></span>

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
- [<span data-ttu-id="16359-254">Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="16359-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="16359-255">Visual Basic dönüşümler yazın</span><span class="sxs-lookup"><span data-stu-id="16359-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
