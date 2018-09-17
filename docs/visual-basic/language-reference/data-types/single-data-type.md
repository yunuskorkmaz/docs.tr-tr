---
title: Single Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746919"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="d241b-102">Single Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d241b-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="d241b-103">Ayrı tutma IEEE 32-bit (4-bayt) tek duyarlıklı kayan nokta sayı değerini - 3.4028235E + 38 arasında değişen imzalı ile - 1.401298E-45 negatif değerleri ve 1.401298E-45 3.4028235E + 38 pozitif değerler için aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="d241b-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="d241b-104">Tek duyarlıklı sayılar yaklaşık bir gerçek sayı olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="d241b-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d241b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d241b-105">Remarks</span></span>  
 <span data-ttu-id="d241b-106">Kullanım `Single` veri türü, tam veri genişliği gerektirmeyen kayan nokta değerleri içerecek şekilde `Double`.</span><span class="sxs-lookup"><span data-stu-id="d241b-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="d241b-107">Bazı durumlarda ortak dil çalışma zamanı paketi mümkün olabilir, `Single` değişkenleri yakından birlikte ve bellek tüketimi.</span><span class="sxs-lookup"><span data-stu-id="d241b-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="d241b-108">Varsayılan değer olan `Single` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="d241b-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="d241b-109">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="d241b-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="d241b-110">**Duyarlık.**</span><span class="sxs-lookup"><span data-stu-id="d241b-110">**Precision.**</span></span> <span data-ttu-id="d241b-111">Kayan noktalı sayı ile çalıştığınızda, bunlar her zaman kesin bir gösterimi bellekte olmadığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d241b-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="d241b-112">Değer karşılaştırması gibi bazı işlemleri öğesinden bu beklenmeyen sonuçlara neden olabilir ve `Mod` işleci.</span><span class="sxs-lookup"><span data-stu-id="d241b-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="d241b-113">Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="d241b-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="d241b-114">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="d241b-114">**Widening.**</span></span> <span data-ttu-id="d241b-115">`Single` Widens veri türü için `Double`.</span><span class="sxs-lookup"><span data-stu-id="d241b-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="d241b-116">Yani dönüştürebilirsiniz `Single` için `Double` karşılaşmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="d241b-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="d241b-117">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="d241b-117">**Trailing Zeros.**</span></span> <span data-ttu-id="d241b-118">Kayan nokta veri türleri, sondaki 0 karakterleri, herhangi bir iç gösterimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d241b-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="d241b-119">Örneğin, bunlar 4.2 4.2000 arasında ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d241b-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="d241b-120">Sonuç olarak, sondaki 0 karakterleri görüntülediğinizde veya kayan nokta değerlerini yazdırma görünmez.</span><span class="sxs-lookup"><span data-stu-id="d241b-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="d241b-121">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="d241b-121">**Type Characters.**</span></span> <span data-ttu-id="d241b-122">Değişmez değer türü karakterinin `F` sabit değerine zorlar `Single` veri türü.</span><span class="sxs-lookup"><span data-stu-id="d241b-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="d241b-123">Tanımlayıcı türü karakteri ekleme `!` herhangi bir tanımlayıcı zorlar `Single`.</span><span class="sxs-lookup"><span data-stu-id="d241b-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="d241b-124">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="d241b-124">**Framework Type.**</span></span> <span data-ttu-id="d241b-125">.NET Framework içinde karşılık gelen türü <xref:System.Single?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="d241b-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d241b-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d241b-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="d241b-127">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d241b-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="d241b-128">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d241b-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="d241b-129">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d241b-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="d241b-130">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d241b-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="d241b-131">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="d241b-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="d241b-132">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d241b-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="d241b-133">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="d241b-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
