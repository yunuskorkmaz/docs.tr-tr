---
title: Onluk Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 4d530a8c1f85d2f0045184c05df63849047a8204
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834107"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="dd8de-102">Onluk Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd8de-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="dd8de-103">Ayrı tutma 128-bit (16 baytlık) değerler tarafından 10 değişken güç ölçeği 96 bit (12-bayt) tamsayıları temsil eden imzalı.</span><span class="sxs-lookup"><span data-stu-id="dd8de-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="dd8de-104">Ölçeklendirme çarpanı ondalık noktasının sağındaki basamak sayısını belirtir; 0 ile 28 arasında çeşitlilik gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd8de-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="dd8de-105">İle bir ölçek 0 (ondalık basamak) 79,228,162,514,264,337,593,543,950,335 +/-olası en büyük değer olan (7 +/-.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="dd8de-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="dd8de-106">28 ondalık basamakları olan en büyük değeri 7.9228162514264337593543950335 +/-, ise sıfır olmayan en küçük değeri +/-0.0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="dd8de-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd8de-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd8de-107">Remarks</span></span>  
 <span data-ttu-id="dd8de-108">`Decimal` Veri türü, bir sayı için en fazla belirtici basamak sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd8de-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="dd8de-109">29 önemli basamak destekler ve 7.9228 x 10 aşan değerleri temsil edebilen ^ 28.</span><span class="sxs-lookup"><span data-stu-id="dd8de-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="dd8de-110">Gibi özellikle hesaplamalar için uygun Finans, çok sayıda basamak gerektirir ancak yuvarlama hataları tolere olamaz.</span><span class="sxs-lookup"><span data-stu-id="dd8de-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="dd8de-111">Varsayılan değer olan `Decimal` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="dd8de-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="dd8de-112">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="dd8de-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="dd8de-113">**Duyarlık.**</span><span class="sxs-lookup"><span data-stu-id="dd8de-113">**Precision.**</span></span> <span data-ttu-id="dd8de-114">`Decimal` bir kayan nokta veri türü değil.</span><span class="sxs-lookup"><span data-stu-id="dd8de-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="dd8de-115">`Decimal` Yapısı tutan bir imza biti ve Ölçeklendirme çarpanı ondalık kesir değeri hangi kısmı olduğunu belirten bir tamsayı ile birlikte bir ikili tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="dd8de-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="dd8de-116">Bu nedenle, `Decimal` numarasına sahip daha kesin bir gösterimi kayan nokta türleri daha bellekte (`Single` ve `Double`).</span><span class="sxs-lookup"><span data-stu-id="dd8de-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="dd8de-117">**Performans.**</span><span class="sxs-lookup"><span data-stu-id="dd8de-117">**Performance.**</span></span> <span data-ttu-id="dd8de-118">`Decimal` Veri türü, tüm sayısal türlerin en yavaş.</span><span class="sxs-lookup"><span data-stu-id="dd8de-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="dd8de-119">Bir veri türü seçmeden önce performans karşı duyarlılığı önemini tartmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd8de-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="dd8de-120">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="dd8de-120">**Widening.**</span></span> <span data-ttu-id="dd8de-121">`Decimal` Widens veri türü için `Single` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="dd8de-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="dd8de-122">Yani dönüştürebilirsiniz `Decimal` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="dd8de-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="dd8de-123">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="dd8de-123">**Trailing Zeros.**</span></span> <span data-ttu-id="dd8de-124">Visual Basic sıfırları depolamaz bir `Decimal` değişmez.</span><span class="sxs-lookup"><span data-stu-id="dd8de-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="dd8de-125">Ancak, bir `Decimal` değişkeni hesaplama açısından alınan sonundaki sıfırları korur.</span><span class="sxs-lookup"><span data-stu-id="dd8de-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="dd8de-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dd8de-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="dd8de-127">Çıkışı `MsgBox` önceki örnekte aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dd8de-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="dd8de-128">D1 2.375, d2 = 1.625, d3 = 4.000, d4 = 4 =</span><span class="sxs-lookup"><span data-stu-id="dd8de-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="dd8de-129">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="dd8de-129">**Type Characters.**</span></span> <span data-ttu-id="dd8de-130">Değişmez değer türü karakterinin `D` sabit değerine zorlar `Decimal` veri türü.</span><span class="sxs-lookup"><span data-stu-id="dd8de-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="dd8de-131">Tanımlayıcı türü karakteri ekleme `@` herhangi bir tanımlayıcı zorlar `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dd8de-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="dd8de-132">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="dd8de-132">**Framework Type.**</span></span> <span data-ttu-id="dd8de-133">.NET Framework içinde karşılık gelen türü <xref:System.Decimal?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="dd8de-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="dd8de-134">Aralık</span><span class="sxs-lookup"><span data-stu-id="dd8de-134">Range</span></span>  
 <span data-ttu-id="dd8de-135">Kullanmanız gerekebilir `D` türü için büyük bir değer atamak için karakteri bir `Decimal` değişken veya sabit.</span><span class="sxs-lookup"><span data-stu-id="dd8de-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="dd8de-136">Bu gereksinim olduğundan derleyici değişmez değer olarak yorumlar `Long` sürece bir değişmez değer türü karakteri aşağıdaki örnekte gösterildiği gibi değişmez değer izler.</span><span class="sxs-lookup"><span data-stu-id="dd8de-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="dd8de-137">Bildirimi `bigDec1` kendisine atanmış değer aralığında kaldığından taşma üretemez `Long`.</span><span class="sxs-lookup"><span data-stu-id="dd8de-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="dd8de-138">`Long` Değer atanabilen `Decimal` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="dd8de-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="dd8de-139">Bildirimi `bigDec2` kendisine atanmış değer için çok büyük olduğundan overflow hata üretir `Long`.</span><span class="sxs-lookup"><span data-stu-id="dd8de-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="dd8de-140">Sayısal sabit değer ilk olarak yorumlanamıyor çünkü bir `Long`, için atanamaz `Decimal` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="dd8de-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="dd8de-141">İçin `bigDec3`, değişmez değer türü karakteri `D` değişmez değer olarak yorumlamak üzere zorlayarak sorunu çözer bir `Decimal` yerine olarak bir `Long`.</span><span class="sxs-lookup"><span data-stu-id="dd8de-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8de-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd8de-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dd8de-143">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="dd8de-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="dd8de-144">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="dd8de-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="dd8de-145">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="dd8de-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="dd8de-146">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="dd8de-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="dd8de-147">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="dd8de-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="dd8de-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dd8de-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
