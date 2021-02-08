---
description: 'Hakkında daha fazla bilgi edinin: tek veri türü (Visual Basic)'
title: Single Veri Türü
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
ms.openlocfilehash: f30e21d3b2d2960a040609a9422ec71cc029f5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792134"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="b0a03-103">Single Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0a03-103">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="b0a03-104">, Negatif değerler için-3.4028235 E + 38 ila-1.401298 E-45 değerindeki ve pozitif değerler için 3.4028235 E + 38 ile 1.401298 E-45 arasında değişen, imzalanan IEEE 32-bit (4 baytlık) tek duyarlıklı kayan nokta sayılarını barındırır.</span><span class="sxs-lookup"><span data-stu-id="b0a03-104">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="b0a03-105">Tek duyarlıklı sayılar gerçek bir sayının yaklaşık bir kısmını depolar.</span><span class="sxs-lookup"><span data-stu-id="b0a03-105">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0a03-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0a03-106">Remarks</span></span>  

 <span data-ttu-id="b0a03-107">`Single`Tam veri genişliğini gerektirmeyen kayan nokta değerlerini içermesi için veri türünü kullanın `Double` .</span><span class="sxs-lookup"><span data-stu-id="b0a03-107">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="b0a03-108">Bazı durumlarda, ortak dil çalışma zamanı `Single` değişkenlerinizi birbirine yakından paketlenebilir ve bellek tüketimini kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="b0a03-108">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="b0a03-109">Varsayılan değeri 0 ' `Single` dır.</span><span class="sxs-lookup"><span data-stu-id="b0a03-109">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b0a03-110">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="b0a03-110">Programming Tips</span></span>  
  
- <span data-ttu-id="b0a03-111">**Duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="b0a03-111">**Precision.**</span></span> <span data-ttu-id="b0a03-112">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimine sahip olmadıkları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b0a03-112">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="b0a03-113">Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir `Mod` .</span><span class="sxs-lookup"><span data-stu-id="b0a03-113">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="b0a03-114">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="b0a03-114">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="b0a03-115">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="b0a03-115">**Widening.**</span></span> <span data-ttu-id="b0a03-116">`Single`Widens veri türü `Double` .</span><span class="sxs-lookup"><span data-stu-id="b0a03-116">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="b0a03-117">Bu, `Single` `Double` bir hatayla karşılaşmadan ' a dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b0a03-117">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="b0a03-118">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="b0a03-118">**Trailing Zeros.**</span></span> <span data-ttu-id="b0a03-119">Kayan nokta veri türlerinde sondaki 0 karakterden oluşan iç temsili yok.</span><span class="sxs-lookup"><span data-stu-id="b0a03-119">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="b0a03-120">Örneğin, 4,2000 ve 4,2 arasında ayrım yapmazlar.</span><span class="sxs-lookup"><span data-stu-id="b0a03-120">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="b0a03-121">Sonuç olarak, kayan nokta değerlerini görüntülerken veya yazdırdığınızda sondaki 0 karakter görünmez.</span><span class="sxs-lookup"><span data-stu-id="b0a03-121">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="b0a03-122">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="b0a03-122">**Type Characters.**</span></span> <span data-ttu-id="b0a03-123">Değişmez değer türü karakterini `F` bir sabit değere eklemek, `Single` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="b0a03-123">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="b0a03-124">Tanımlayıcı türü karakteri `!` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Single` .</span><span class="sxs-lookup"><span data-stu-id="b0a03-124">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="b0a03-125">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="b0a03-125">**Framework Type.**</span></span> <span data-ttu-id="b0a03-126">.NET Framework karşılık gelen tür <xref:System.Single?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="b0a03-126">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a03-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a03-127">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="b0a03-128">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b0a03-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="b0a03-129">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="b0a03-129">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="b0a03-130">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="b0a03-130">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="b0a03-131">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b0a03-131">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="b0a03-132">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="b0a03-132">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="b0a03-133">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b0a03-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="b0a03-134">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="b0a03-134">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
