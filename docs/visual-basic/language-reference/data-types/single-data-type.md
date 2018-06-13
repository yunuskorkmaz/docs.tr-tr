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
ms.openlocfilehash: 770961f225b139aaddf34b42327bca63638c725d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590792"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="21e06-102">Single Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21e06-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="21e06-103">Ayrı tutma imzalı IEEE 32-bit (4-bayt) tek duyarlıklı kayan nokta sayıları değerinden - 3.4028235E + 38 arasında değişen ile - 1.401298E-45 negatif değerler ve 1.401298E-45 3.4028235E + 38 pozitif değerler için aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="21e06-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="21e06-104">Tek duyarlıklı sayılar yaklaşık gerçek bir sayı olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="21e06-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e06-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21e06-105">Remarks</span></span>  
 <span data-ttu-id="21e06-106">Kullanım `Single` veri türü tam veri genişliği gerektirmeyen kayan nokta değerlerini içeren `Double`.</span><span class="sxs-lookup"><span data-stu-id="21e06-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="21e06-107">Bazı durumlarda ortak dil çalışma zamanı paketi olabilir, `Single` değişkenleri yakın işbirliği içinde ve bellek tüketimi.</span><span class="sxs-lookup"><span data-stu-id="21e06-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="21e06-108">Varsayılan değer olan `Single` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="21e06-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="21e06-109">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="21e06-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="21e06-110">**Hassasiyet.**</span><span class="sxs-lookup"><span data-stu-id="21e06-110">**Precision.**</span></span> <span data-ttu-id="21e06-111">Kayan nokta sayıları ile çalışırken, her zaman kesin gösterimi bellekte olmadığı olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="21e06-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="21e06-112">Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve `Mod` işleci.</span><span class="sxs-lookup"><span data-stu-id="21e06-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="21e06-113">Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="21e06-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="21e06-114">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="21e06-114">**Widening.**</span></span> <span data-ttu-id="21e06-115">`Single` Veri türü widens için `Double`.</span><span class="sxs-lookup"><span data-stu-id="21e06-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="21e06-116">Bu dönüştürebilirsiniz anlamına gelir `Single` için `Double` karşılaşmadan olmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="21e06-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="21e06-117">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="21e06-117">**Trailing Zeros.**</span></span> <span data-ttu-id="21e06-118">Kayan nokta veri türleri sondaki 0 karakterleri iç herhangi gösterimi yok.</span><span class="sxs-lookup"><span data-stu-id="21e06-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="21e06-119">Örneğin, bunlar 4.2000 4.2 arasında ayrım değil.</span><span class="sxs-lookup"><span data-stu-id="21e06-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="21e06-120">Sonuç olarak, görüntülediğinizde veya kayan nokta değerlerini yazdırmak sondaki 0 karakterleri görünmez.</span><span class="sxs-lookup"><span data-stu-id="21e06-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="21e06-121">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="21e06-121">**Type Characters.**</span></span> <span data-ttu-id="21e06-122">Değişmez değer türü karakteri ekleme `F` bir hazır değer zorlar `Single` veri türü.</span><span class="sxs-lookup"><span data-stu-id="21e06-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="21e06-123">Tanımlayıcı türü karakteri ekleme `!` herhangi bir tanımlayıcı zorlar `Single`.</span><span class="sxs-lookup"><span data-stu-id="21e06-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="21e06-124">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="21e06-124">**Framework Type.**</span></span> <span data-ttu-id="21e06-125">.NET Framework'teki karşılık gelen tür <xref:System.Single?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="21e06-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e06-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21e06-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="21e06-127">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="21e06-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="21e06-128">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="21e06-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="21e06-129">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="21e06-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="21e06-130">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="21e06-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="21e06-131">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="21e06-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="21e06-132">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="21e06-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="21e06-133">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="21e06-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
