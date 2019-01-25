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
ms.openlocfilehash: ea20569b207100886ddd4b40c8d4c86c55d5ddf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743549"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="61e05-102">Tür Dönüştürme İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61e05-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="61e05-103">Bu da dönüştürme kodunun ifadeyi değerlendiren kodun bir parçası olduğu anlamına derlenmiş satır içi işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="61e05-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="61e05-104">Bazen bir yordam performansı artıran dönüştürme gerçekleştirmek için hiçbir çağrı yoktur.</span><span class="sxs-lookup"><span data-stu-id="61e05-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="61e05-105">Her işlev bir özel veri türü için bir ifade olacak şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="61e05-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e05-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61e05-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="61e05-107">Bölümü</span><span class="sxs-lookup"><span data-stu-id="61e05-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="61e05-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="61e05-108">Required.</span></span> <span data-ttu-id="61e05-109">Herhangi bir ifade kaynak veri türü.</span><span class="sxs-lookup"><span data-stu-id="61e05-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="61e05-110">Dönüş değeri veri türü</span><span class="sxs-lookup"><span data-stu-id="61e05-110">Return Value Data Type</span></span>  
 <span data-ttu-id="61e05-111">İşlev adı, aşağıdaki tabloda gösterildiği gibi döndürür, değeri veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="61e05-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="61e05-112">İşlev adı</span><span class="sxs-lookup"><span data-stu-id="61e05-112">Function name</span></span>|<span data-ttu-id="61e05-113">Dönüş veri türü</span><span class="sxs-lookup"><span data-stu-id="61e05-113">Return data type</span></span>|<span data-ttu-id="61e05-114">İçin aralık `expression` bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="61e05-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="61e05-115">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="61e05-116">Herhangi bir geçerli `Char` veya `String` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="61e05-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="61e05-117">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="61e05-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-119">Visual Basic 15,8 ile başlayarak, Visual Basic ile bayt dönüştürme kayan nokta performansını iyileştirir `CByte` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-120">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="61e05-121">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="61e05-122">Herhangi bir geçerli `Char` veya `String` ifadesi; yalnızca ilk karakteri bir `String` dönüştürülür; değeri 0-65535 (işaretsiz) olabilir.</span><span class="sxs-lookup"><span data-stu-id="61e05-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="61e05-123">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="61e05-124">Tüm geçerli temsili bir tarih ve saat.</span><span class="sxs-lookup"><span data-stu-id="61e05-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="61e05-125">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="61e05-126">-1.79769313486231570E + 308 - aracılığıyla 4.94065645841246544E-324; negatif değerleri 4.94065645841246544E-324 1.79769313486231570E + 308 pozitif değerler için aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="61e05-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="61e05-127">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="61e05-128">sıfır ölçeklendirilmiş sayılar için diğer bir deyişle, ondalık konumu olmayan sayılar 79,228,162,514,264,337,593,543,950,335 +/-.</span><span class="sxs-lookup"><span data-stu-id="61e05-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="61e05-129">28 ondalık basamaklı sayılar için +/-7.9228162514264337593543950335 aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="61e05-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="61e05-130">En küçük olası sıfır olmayan 0.0000000000000000000000000001 (+/-1E-28) sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="61e05-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="61e05-131">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="61e05-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) aracılığıyla <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="61e05-133">Visual Basic 15,8 ile başlayarak, Visual Basic ile tamsayı dönüştürmesi için kayan nokta performansını iyileştirir `CInt` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-134">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="61e05-135">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="61e05-136"><xref:System.Int64.MaxValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) aracılığıyla <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-136"><xref:System.Int64.MaxValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-137">Visual Basic 15,8 ile başlayarak, Visual Basic ile 64-bit tamsayıya dönüştürme kayan nokta performansını iyileştirir `CLng` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-138">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="61e05-139">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="61e05-140">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="61e05-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="61e05-141">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="61e05-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) aracılığıyla <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-143">Visual Basic 15,8 ile başlayarak, Visual Basic ile işaretli bayt dönüştürme kayan nokta performansını iyileştirir `CSByte` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-144">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="61e05-145">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="61e05-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) aracılığıyla <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-147">Visual Basic 15,8 ile başlayarak, Visual Basic ile 16 bit tam sayı dönüşümü kayan nokta performansını iyileştirir `CShort` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-148">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="61e05-149">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="61e05-150">-3.402823E + 38 ile - 1.401298E-45 negatif değerleri; 1.401298E-45 3.402823E + 38 pozitif değerler için aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="61e05-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="61e05-151">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="61e05-152">Döndüren `CStr` bağımlı `expression` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="61e05-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="61e05-153">Bkz: [CStr işlevi dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="61e05-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="61e05-154">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="61e05-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295'e) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-156">Visual Basic 15,8 ile başlayarak, Visual Basic ile işaretsiz tamsayı dönüştürme kayan nokta performansını iyileştirir `CUInt` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-157">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="61e05-158">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="61e05-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-160">Visual Basic 15,8 ile başlayarak, Visual Basic ile işaretsiz uzun tamsayı dönüştürmesi için kayan nokta performansını iyileştirir `CULng` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-161">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="61e05-162">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="61e05-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="61e05-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) aracılığıyla <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (işaretsiz); kesirli bölümleri yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="61e05-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="61e05-164">Visual Basic 15,8 ile başlayarak, Visual Basic ile 16 bit işaretsiz tamsayı dönüştürme kayan nokta performansını iyileştirir `CUShort` işlev; bkz [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="61e05-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="61e05-165">Bkz: [CInt örnek](#cint-example) bölüm bir örnek.</span><span class="sxs-lookup"><span data-stu-id="61e05-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="61e05-166"><sup>1</sup> kesirli bölümleri çağrılan yuvarlama özel bir tür tabi olabilir *banker yuvarlama*.</span><span class="sxs-lookup"><span data-stu-id="61e05-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="61e05-167">"Açıklamalar" daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="61e05-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61e05-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61e05-168">Remarks</span></span>  
 <span data-ttu-id="61e05-169">Bir kural olarak, .NET Framework yöntemlerini değişkenden Visual Basic tür dönüştürme işlevleri gibi kullanmalısınız `ToString()`, ya da üzerinde <xref:System.Convert> sınıfı veya tek tek tür yapı ya da sınıfı.</span><span class="sxs-lookup"><span data-stu-id="61e05-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="61e05-170">Visual Basic işlevleri, Visual Basic kod ile en iyi etkileşim sağlamak için tasarlanmıştır ve ayrıca kaynak kodunuzu daha kısa ve kolay okunur hale.</span><span class="sxs-lookup"><span data-stu-id="61e05-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="61e05-171">Ayrıca, .NET Framework dönüştürme yöntemleri her zaman aynı sonucu dönüştürülürken bir örnek için Visual Basic işlevleri olarak vermez `Boolean` için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="61e05-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="61e05-172">Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="61e05-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  


<span data-ttu-id="61e05-173">Geçirdiğinizde, Visual Basic 15,8 ile başlayarak, kayan-noktaya-boolean'dan tamsayıya dönüştürmeyi performansını optimize edilmiştir <xref:System.Single> veya <xref:System.Double> değeri bir tamsayı dönüştürme işlevleri aşağıdaki yöntemlerle döndürdü (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="61e05-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

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

<span data-ttu-id="61e05-174">Bu iyileştirme, çok sayıda iki kat daha hızlı şekilde çalışması için tamsayı dönüştürmeleri yapan kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="61e05-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="61e05-175">Aşağıdaki örnekte, bu en iyi duruma getirilmiş kayan-noktaya boolean'dan tamsayıya dönüştürme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="61e05-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="61e05-176">Davranış</span><span class="sxs-lookup"><span data-stu-id="61e05-176">Behavior</span></span>  
  
-   <span data-ttu-id="61e05-177">**Zorlama.**</span><span class="sxs-lookup"><span data-stu-id="61e05-177">**Coercion.**</span></span> <span data-ttu-id="61e05-178">Genel olarak, varsayılan veri türü yerine belirli bir veri türüne bir işlemin sonucunu coerce için veri türü dönüştürme işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61e05-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="61e05-179">Örneğin, `CDec` burada tek duyarlıklı, çift duyarlıklı veya tamsayı aritmetik normalde geçtiğine durumlarda ondalık aritmetik zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="61e05-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="61e05-180">**Dönüştürme başarısız.**</span><span class="sxs-lookup"><span data-stu-id="61e05-180">**Failed Conversions.**</span></span> <span data-ttu-id="61e05-181">Varsa `expression` işleve geçirilen için hangi BT dönüştürülmekte olan veri türü aralığının dışında olduğundan bir <xref:System.OverflowException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="61e05-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="61e05-182">**Kesirli bölümleri.**</span><span class="sxs-lookup"><span data-stu-id="61e05-182">**Fractional Parts.**</span></span> <span data-ttu-id="61e05-183">Bir tam sayıya nonintegral değeri dönüştürdüğünüzde türü, tamsayı dönüştürme işlevleri (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, ve `CUShort`) Kaldır kesirli bölümü ve değeri en yakın tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="61e05-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="61e05-184">Kesirli bölümü tam olarak ise 0,5, tamsayı dönüştürme işlevleri yuvarlak kendisine en yakın çift tamsayıya.</span><span class="sxs-lookup"><span data-stu-id="61e05-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="61e05-185">Örneğin, 0 ve 1.5 hem de 2 yuvarlak 2.5 0,5 yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="61e05-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="61e05-186">Bazen adlandırılır *banker yuvarlama*, ve amacı dengelemek birlikte birçok sayı eklerken birikebilir sapması.</span><span class="sxs-lookup"><span data-stu-id="61e05-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="61e05-187">`CInt` ve `CLng` farklı <xref:Microsoft.VisualBasic.Conversion.Int%2A> ve <xref:Microsoft.VisualBasic.Conversion.Fix%2A> hangi round, bir sayının kesirli kısmını yerine truncate işlevleri.</span><span class="sxs-lookup"><span data-stu-id="61e05-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="61e05-188">Ayrıca, `Fix` ve `Int` , geçirdiğiniz her zaman aynı veri türünde bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="61e05-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="61e05-189">**Tarih/saat dönüştürme.**</span><span class="sxs-lookup"><span data-stu-id="61e05-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="61e05-190">Kullanım <xref:Microsoft.VisualBasic.Information.IsDate%2A> işlevi bir tarih ve saat değeri dönüştürülebilir ise belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="61e05-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="61e05-191">`CDate` Tarih değişmez değerleri ve zaman değişmez ancak sayısal değerleri algılar.</span><span class="sxs-lookup"><span data-stu-id="61e05-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="61e05-192">Visual Basic 6.0 dönüştürülecek `Date` değerini bir `Date` değer Visual Basic 2005 veya sonraki sürümler, kullanabileceğiniz <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61e05-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="61e05-193">**Nötr tarih/saat değerleri.**</span><span class="sxs-lookup"><span data-stu-id="61e05-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="61e05-194">[Date veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md) her zaman tarih ve saat bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="61e05-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="61e05-195">Tür dönüştürme amacı doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *bağımsız değer* tarihini ve 00:00:00 (gece yarısı) süresi için bağımsız bir değer olarak.</span><span class="sxs-lookup"><span data-stu-id="61e05-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="61e05-196">Dönüştürürseniz, bir `Date` bir dize değerine `CStr` nötr değerlerini sonuç dizesindeki içermez.</span><span class="sxs-lookup"><span data-stu-id="61e05-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="61e05-197">Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dize, "9:30:00 AM" sonucudur; tarih bilgisi bastırılır.</span><span class="sxs-lookup"><span data-stu-id="61e05-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="61e05-198">Ancak, tarih bilgileri özgün hala mevcut `Date` değeri ve işlevlerinde aşağıdaki gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> işlevi.</span><span class="sxs-lookup"><span data-stu-id="61e05-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="61e05-199">**Kültür duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="61e05-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="61e05-200">Dizeleri içeren tür dönüştürme işlevleri, uygulama için geçerli kültür ayarlara dayanan dönüştürmeler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="61e05-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="61e05-201">Örneğin, `CDate` tarih biçimleri sisteminizin yerel ayarına göre tanır.</span><span class="sxs-lookup"><span data-stu-id="61e05-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="61e05-202">Gün, ay ve yıl bölgeniz için doğru sırada sağlamanız gerekir ya da tarih doğru şekilde yorumlanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="61e05-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="61e05-203">"Çarşamba" gibi bir haftanın gün dize içeriyorsa, uzun tarih biçimi tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="61e05-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="61e05-204">İçin veya bir biçimde, yerel ayar tarafından belirtilen dışında bir değer bir dize gösterimini dönüştürmek istiyorsanız, Visual Basic tür dönüştürme işlevleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61e05-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="61e05-205">Bunu yapmak için `ToString(IFormatProvider)` ve `Parse(String, IFormatProvider)` yöntemleri bu değerin türü.</span><span class="sxs-lookup"><span data-stu-id="61e05-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="61e05-206">Örneğin, <xref:System.Double.Parse%2A?displayProperty=nameWithType> bir dizeye dönüştürürken bir `Double`ve <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` bir dize.</span><span class="sxs-lookup"><span data-stu-id="61e05-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="61e05-207">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="61e05-207">CType Function</span></span>  
 <span data-ttu-id="61e05-208">[CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ikinci bağımsız değişken `typename`ve olacak şekilde zorlar `expression` için `typename`burada `typename` veri türü, yapı, sınıf veya arabirim için hangi verilmesiyle geçerli bir dönüşümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="61e05-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="61e05-209">Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="61e05-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="61e05-210">CBool örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-210">CBool Example</span></span>  
 <span data-ttu-id="61e05-211">Aşağıdaki örnekte `CBool` ifadeleri dönüştürmek için işlevi `Boolean` değerleri.</span><span class="sxs-lookup"><span data-stu-id="61e05-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="61e05-212">Bir ifade sıfır olmayan bir değer olarak değerlendirilirse `CBool` döndürür `True`; Aksi halde döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="61e05-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="61e05-213">CByte örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-213">CByte Example</span></span>  
 <span data-ttu-id="61e05-214">Aşağıdaki örnekte `CByte` bir ifadeye dönüştürmek için işlevi bir `Byte`.</span><span class="sxs-lookup"><span data-stu-id="61e05-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="61e05-215">CChar örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-215">CChar Example</span></span>  
 <span data-ttu-id="61e05-216">Aşağıdaki örnekte `CChar` ilk karakteri dönüştürmek için işlevi bir `String` ifade bir `Char` türü.</span><span class="sxs-lookup"><span data-stu-id="61e05-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="61e05-217">Giriş bağımsız değişkeni için `CChar` veri türünde olmalıdır `Char` veya `String`.</span><span class="sxs-lookup"><span data-stu-id="61e05-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="61e05-218">Kullanamazsınız `CChar` çünkü bir karakter, bir sayı dönüştürmek için `CChar` bir sayısal veri türü kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="61e05-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="61e05-219">Aşağıdaki örnek, bir kod noktası (karakter kodu) temsil eden bir sayı alır ve karşılık gelen karaktere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="61e05-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="61e05-220">Kullandığı <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> basamak dizisini elde etmek için işlevi `CInt` dize türüne dönüştürmek için `Integer`, ve `ChrW` sayı türüne dönüştürmek için `Char`.</span><span class="sxs-lookup"><span data-stu-id="61e05-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="61e05-221">CDate örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-221">CDate Example</span></span>  
 <span data-ttu-id="61e05-222">Aşağıdaki örnekte `CDate` dizelere dönüştürmek için işlevi `Date` değerleri.</span><span class="sxs-lookup"><span data-stu-id="61e05-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="61e05-223">Genel olarak, kodlama sabit tarih ve saat dizeleri (Bu örnekte gösterildiği gibi) önerilmez.</span><span class="sxs-lookup"><span data-stu-id="61e05-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="61e05-224">Tarih değişmez değerleri ve #Feb 12 1969 # gibi zaman değişmez değerleri kullanın ve # 4:45:23 PM #, bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="61e05-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="61e05-225">CDbl örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="61e05-226">CDec örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-226">CDec Example</span></span>  
 <span data-ttu-id="61e05-227">Aşağıdaki örnekte `CDec` sayısal bir değere dönüştürmek için işlevi `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="61e05-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="61e05-228">CInt örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-228">CInt Example</span></span>  
 <span data-ttu-id="61e05-229">Aşağıdaki örnekte `CInt` değerine dönüştürmek için işlevi `Integer`.</span><span class="sxs-lookup"><span data-stu-id="61e05-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  

## <a name="clng-example"></a><span data-ttu-id="61e05-230">CLng örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-230">CLng Example</span></span>
 <span data-ttu-id="61e05-231">Aşağıdaki örnekte `CLng` değerlerine dönüştürmek için işlevi `Long`.</span><span class="sxs-lookup"><span data-stu-id="61e05-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="61e05-232">CObj örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-232">CObj Example</span></span>  
 <span data-ttu-id="61e05-233">Aşağıdaki örnekte `CObj` sayısal bir değere dönüştürmek için işlevi `Object`.</span><span class="sxs-lookup"><span data-stu-id="61e05-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="61e05-234">`Object` Değişkenin kendisine işaret yalnızca dört bayt işaretçi içeren `Double` atanmış değer.</span><span class="sxs-lookup"><span data-stu-id="61e05-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="61e05-235">CSByte örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-235">CSByte Example</span></span>  
 <span data-ttu-id="61e05-236">Aşağıdaki örnekte `CSByte` sayısal bir değere dönüştürmek için işlevi `SByte`.</span><span class="sxs-lookup"><span data-stu-id="61e05-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="61e05-237">CShort örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-237">CShort Example</span></span>  
 <span data-ttu-id="61e05-238">Aşağıdaki örnekte `CShort` sayısal bir değere dönüştürmek için işlevi `Short`.</span><span class="sxs-lookup"><span data-stu-id="61e05-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="61e05-239">CSng örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-239">CSng Example</span></span>  
 <span data-ttu-id="61e05-240">Aşağıdaki örnekte `CSng` değerlerine dönüştürmek için işlevi `Single`.</span><span class="sxs-lookup"><span data-stu-id="61e05-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="61e05-241">CStr örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-241">CStr Example</span></span>  
 <span data-ttu-id="61e05-242">Aşağıdaki örnekte `CStr` sayısal bir değere dönüştürmek için işlevi `String`.</span><span class="sxs-lookup"><span data-stu-id="61e05-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="61e05-243">Aşağıdaki örnekte `CStr` dönüştürmek için işlevi `Date` değerler `String` değerleri.</span><span class="sxs-lookup"><span data-stu-id="61e05-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="61e05-244">`CStr` her zaman oluşturur bir `Date` geçerli yerel ayar için örneğin, standart kısa biçiminde bir değer "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="61e05-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="61e05-245">Ancak, `CStr` bastırır *nötr değerleri* , 1/1/0001 tarih ve saat için 00:00:00 için.</span><span class="sxs-lookup"><span data-stu-id="61e05-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="61e05-246">Tarafından döndürülen değerleri hakkında daha fazla ayrıntı için `CStr`, bkz: [CStr işlevinin dönüş değerleri](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="61e05-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="61e05-247">Cuınt örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-247">CUInt Example</span></span>  
 <span data-ttu-id="61e05-248">Aşağıdaki örnekte `CUInt` sayısal bir değere dönüştürmek için işlevi `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="61e05-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="61e05-249">CULng örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-249">CULng Example</span></span>  
 <span data-ttu-id="61e05-250">Aşağıdaki örnekte `CULng` sayısal bir değere dönüştürmek için işlevi `ULong`.</span><span class="sxs-lookup"><span data-stu-id="61e05-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="61e05-251">CUShort örneği</span><span class="sxs-lookup"><span data-stu-id="61e05-251">CUShort Example</span></span>  
 <span data-ttu-id="61e05-252">Aşağıdaki örnekte `CUShort` sayısal bir değere dönüştürmek için işlevi `UShort`.</span><span class="sxs-lookup"><span data-stu-id="61e05-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="61e05-253">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61e05-253">See also</span></span>
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
- [<span data-ttu-id="61e05-254">Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="61e05-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="61e05-255">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="61e05-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
