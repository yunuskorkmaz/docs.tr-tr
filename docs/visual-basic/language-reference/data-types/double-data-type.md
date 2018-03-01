---
title: "Double Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad0e8082edfb7b7d96b0ca2019da88514e5b3b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="6841e-102">Double Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6841e-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="6841e-103">Ayrı tutma imzalı değerinden - 1.79769313486231570E + 308 ile - değişen IEEE 64-bit (8-bayt) çift duyarlıklı kayan nokta sayıları 4.94065645841246544E-324 negatif değerler ve 4.94065645841246544E-324 1.79769313486231570E + 308 aracılığıyla pozitif değerler.</span><span class="sxs-lookup"><span data-stu-id="6841e-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="6841e-104">Çift duyarlıklı sayılar yaklaşık gerçek bir sayı olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="6841e-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6841e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6841e-105">Remarks</span></span>  
 <span data-ttu-id="6841e-106">`Double` Veri türü için bir sayı en büyük ve küçük olası magnitudes sağlar.</span><span class="sxs-lookup"><span data-stu-id="6841e-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="6841e-107">Varsayılan değer olan `Double` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="6841e-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="6841e-108">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="6841e-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="6841e-109">**Hassasiyet.**</span><span class="sxs-lookup"><span data-stu-id="6841e-109">**Precision.**</span></span> <span data-ttu-id="6841e-110">Kayan nokta sayıları ile çalışırken, bunlar her zaman kesin bir gösterimi belleğe sahip olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6841e-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="6841e-111">Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve `Mod` işleci.</span><span class="sxs-lookup"><span data-stu-id="6841e-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="6841e-112">Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="6841e-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="6841e-113">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="6841e-113">**Trailing Zeros.**</span></span> <span data-ttu-id="6841e-114">Kayan nokta veri türleri sondaki sıfır karakterleri herhangi iç temsilini gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6841e-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="6841e-115">Örneğin, bunlar 4.2000 4.2 arasında ayrım değil.</span><span class="sxs-lookup"><span data-stu-id="6841e-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="6841e-116">Sonuç olarak, sondaki sıfır karakterleri görünmez görüntülediğinizde veya yazdırma kayan nokta değerleri.</span><span class="sxs-lookup"><span data-stu-id="6841e-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="6841e-117">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="6841e-117">**Type Characters.**</span></span> <span data-ttu-id="6841e-118">Değişmez değer türü karakteri ekleme `R` bir hazır değer zorlar `Double` veri türü.</span><span class="sxs-lookup"><span data-stu-id="6841e-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="6841e-119">Örneğin, bir tamsayı değeri tarafından izlediyseniz `R`, değeri değiştirilmiş olan bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="6841e-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="6841e-120">Tanımlayıcı türü karakteri ekleme `#` herhangi bir tanımlayıcı zorlar `Double`.</span><span class="sxs-lookup"><span data-stu-id="6841e-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="6841e-121">Aşağıdaki örnekte, değişken `num` olarak yazılan bir `Double`:</span><span class="sxs-lookup"><span data-stu-id="6841e-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="6841e-122">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="6841e-122">**Framework Type.**</span></span> <span data-ttu-id="6841e-123">.NET Framework'teki karşılık gelen tür <xref:System.Double?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="6841e-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6841e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6841e-124">See Also</span></span>  
 <xref:System.Double?displayProperty=nameWithType>  
 [<span data-ttu-id="6841e-125">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="6841e-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="6841e-126">Ondalık veri türü</span><span class="sxs-lookup"><span data-stu-id="6841e-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="6841e-127">Single veri türü</span><span class="sxs-lookup"><span data-stu-id="6841e-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="6841e-128">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="6841e-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="6841e-129">Dönüştürme özeti</span><span class="sxs-lookup"><span data-stu-id="6841e-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="6841e-130">Veri türlerinin etkili kullanımı</span><span class="sxs-lookup"><span data-stu-id="6841e-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="6841e-131">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="6841e-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="6841e-132">Tür karakterleri</span><span class="sxs-lookup"><span data-stu-id="6841e-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
