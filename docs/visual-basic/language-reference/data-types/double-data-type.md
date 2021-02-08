---
description: 'Hakkında daha fazla bilgi edinin: Double veri türü (Visual Basic)'
title: Double Veri Türü
ms.date: 07/20/2015
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
ms.openlocfilehash: ae7b87b392038c67ba47e09d7ca995562bf06c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792225"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="58f63-103">Double Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58f63-103">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="58f63-104">Negatif değerler için-1.79769313486231570 E + 308 ile-4.94065645841246544 E-324 arasında ve pozitif değerler için 1.79769313486231570 E + 308 ile 4.94065645841246544 E-324 arasında yer alan imzalanmış IEEE 64-bit (8 baytlık) çift duyarlıklı kayan nokta sayılarını barındırır.</span><span class="sxs-lookup"><span data-stu-id="58f63-104">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="58f63-105">Çift duyarlıklı sayılar gerçek bir sayının yaklaşık bir kısmını depolar.</span><span class="sxs-lookup"><span data-stu-id="58f63-105">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="58f63-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58f63-106">Remarks</span></span>

<span data-ttu-id="58f63-107">`Double`Veri türü, bir sayı için en büyük ve en küçük olası magnitudes sağlar.</span><span class="sxs-lookup"><span data-stu-id="58f63-107">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="58f63-108">Varsayılan değeri 0 ' `Double` dır.</span><span class="sxs-lookup"><span data-stu-id="58f63-108">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="58f63-109">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="58f63-109">Programming Tips</span></span>

- <span data-ttu-id="58f63-110">**Duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="58f63-110">**Precision.**</span></span> <span data-ttu-id="58f63-111">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="58f63-111">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="58f63-112">Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir `Mod` .</span><span class="sxs-lookup"><span data-stu-id="58f63-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="58f63-113">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="58f63-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="58f63-114">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="58f63-114">**Trailing Zeros.**</span></span> <span data-ttu-id="58f63-115">Kayan nokta veri türlerinde sondaki sıfır karakteri iç temsili yok.</span><span class="sxs-lookup"><span data-stu-id="58f63-115">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="58f63-116">Örneğin, 4,2000 ve 4,2 arasında ayrım yapmazlar.</span><span class="sxs-lookup"><span data-stu-id="58f63-116">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="58f63-117">Sonuç olarak, kayan nokta değerlerini görüntülerken veya yazdırdığınızda sondaki sıfır karakter görünmez.</span><span class="sxs-lookup"><span data-stu-id="58f63-117">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="58f63-118">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="58f63-118">**Type Characters.**</span></span> <span data-ttu-id="58f63-119">Değişmez değer türü karakterini `R` bir sabit değere eklemek, `Double` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="58f63-119">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="58f63-120">Örneğin, bir tamsayı değerinin arkasından `R` , değer bir olarak değiştirilir `Double` .</span><span class="sxs-lookup"><span data-stu-id="58f63-120">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="58f63-121">Tanımlayıcı türü karakteri `#` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Double` .</span><span class="sxs-lookup"><span data-stu-id="58f63-121">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="58f63-122">Aşağıdaki örnekte, değişkeni `num` şöyle yazılır `Double` :</span><span class="sxs-lookup"><span data-stu-id="58f63-122">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="58f63-123">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="58f63-123">**Framework Type.**</span></span> <span data-ttu-id="58f63-124">.NET Framework karşılık gelen tür <xref:System.Double?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="58f63-124">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="58f63-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58f63-125">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="58f63-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="58f63-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="58f63-127">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="58f63-127">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="58f63-128">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="58f63-128">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="58f63-129">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="58f63-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="58f63-130">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="58f63-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="58f63-131">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="58f63-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="58f63-132">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="58f63-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="58f63-133">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="58f63-133">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
