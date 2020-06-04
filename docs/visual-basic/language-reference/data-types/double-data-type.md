---
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
ms.openlocfilehash: 899554f427ac77ead465752c35e51ca88d045763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415640"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="43344-102">Double Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43344-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="43344-103">Negatif değerler için-1.79769313486231570 E + 308 ile-4.94065645841246544 E-324 arasında ve pozitif değerler için 1.79769313486231570 E + 308 ile 4.94065645841246544 E-324 arasında yer alan imzalanmış IEEE 64-bit (8 baytlık) çift duyarlıklı kayan nokta sayılarını barındırır.</span><span class="sxs-lookup"><span data-stu-id="43344-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="43344-104">Çift duyarlıklı sayılar gerçek bir sayının yaklaşık bir kısmını depolar.</span><span class="sxs-lookup"><span data-stu-id="43344-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="43344-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43344-105">Remarks</span></span>

<span data-ttu-id="43344-106">`Double`Veri türü, bir sayı için en büyük ve en küçük olası magnitudes sağlar.</span><span class="sxs-lookup"><span data-stu-id="43344-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="43344-107">Varsayılan değeri 0 ' `Double` dır.</span><span class="sxs-lookup"><span data-stu-id="43344-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="43344-108">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="43344-108">Programming Tips</span></span>

- <span data-ttu-id="43344-109">**Duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="43344-109">**Precision.**</span></span> <span data-ttu-id="43344-110">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir gösterimin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="43344-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="43344-111">Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmedik sonuçlara neden olabilir `Mod` .</span><span class="sxs-lookup"><span data-stu-id="43344-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="43344-112">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="43344-112">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="43344-113">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="43344-113">**Trailing Zeros.**</span></span> <span data-ttu-id="43344-114">Kayan nokta veri türlerinde sondaki sıfır karakteri iç temsili yok.</span><span class="sxs-lookup"><span data-stu-id="43344-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="43344-115">Örneğin, 4,2000 ve 4,2 arasında ayrım yapmazlar.</span><span class="sxs-lookup"><span data-stu-id="43344-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="43344-116">Sonuç olarak, kayan nokta değerlerini görüntülerken veya yazdırdığınızda sondaki sıfır karakter görünmez.</span><span class="sxs-lookup"><span data-stu-id="43344-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="43344-117">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="43344-117">**Type Characters.**</span></span> <span data-ttu-id="43344-118">Değişmez değer türü karakterini `R` bir sabit değere eklemek, `Double` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="43344-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="43344-119">Örneğin, bir tamsayı değerinin arkasından `R` , değer bir olarak değiştirilir `Double` .</span><span class="sxs-lookup"><span data-stu-id="43344-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="43344-120">Tanımlayıcı türü karakteri `#` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Double` .</span><span class="sxs-lookup"><span data-stu-id="43344-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="43344-121">Aşağıdaki örnekte, değişkeni `num` şöyle yazılır `Double` :</span><span class="sxs-lookup"><span data-stu-id="43344-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="43344-122">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="43344-122">**Framework Type.**</span></span> <span data-ttu-id="43344-123">.NET Framework karşılık gelen tür <xref:System.Double?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="43344-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="43344-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43344-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="43344-125">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="43344-125">Data Types</span></span>](index.md)
- [<span data-ttu-id="43344-126">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="43344-126">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="43344-127">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="43344-127">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="43344-128">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="43344-128">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="43344-129">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="43344-129">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="43344-130">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="43344-130">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="43344-131">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="43344-131">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="43344-132">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="43344-132">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
