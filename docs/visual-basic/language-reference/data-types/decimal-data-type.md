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
ms.openlocfilehash: 892824b61cfb6a0172361d220c638cab0a78565d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700872"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="dee94-102">Onluk Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dee94-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="dee94-103">, 10 ' un bir değişken gücüne göre ölçeklendirilmiş 96 bit (12 baytlık) tamsayı sayılarını temsil eden imzalı 128 bitlik (16 baytlık) değerleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="dee94-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="dee94-104">Ölçeklendirme faktörü, ondalık noktanın sağ tarafındaki basamak sayısını belirtir; 0 ile 28 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="dee94-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="dee94-105">0 ölçeğinde (ondalık basamak yok), olası en büyük değer +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28) olur.</span><span class="sxs-lookup"><span data-stu-id="dee94-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="dee94-106">28 ondalık basamakla, en büyük değer +/-7.9228162514264337593543950335 ve sıfır olmayan en küçük değer +/-0,0000000000000000000000000001 (+/-1E-28) olur.</span><span class="sxs-lookup"><span data-stu-id="dee94-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="dee94-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dee94-107">Remarks</span></span>

<span data-ttu-id="dee94-108">@No__t-0 veri türü, bir sayı için en çok önemli basamak sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dee94-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="dee94-109">29 ' dan fazla önemli basamağı destekler ve 7,9228 x 10 ^ 28 değerinden fazla değeri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="dee94-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="dee94-110">Çok sayıda basamak gerektiren, ancak yuvarlama hatalarını kabul edemeyecek finansal gibi hesaplamalar için özellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="dee94-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="dee94-111">@No__t-0 ' ın varsayılan değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="dee94-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="dee94-112">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="dee94-112">Programming Tips</span></span>

- <span data-ttu-id="dee94-113">**Duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="dee94-113">**Precision.**</span></span> <span data-ttu-id="dee94-114">`Decimal` bir kayan nokta veri türü değil.</span><span class="sxs-lookup"><span data-stu-id="dee94-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="dee94-115">@No__t-0 yapısı bir ikili tamsayı değerini, bir işaret biti ve değerin hangi bölümünün ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörüyle birlikte tutar.</span><span class="sxs-lookup"><span data-stu-id="dee94-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="dee94-116">Bu nedenle, `Decimal` sayıları bellek içinde kayan nokta türlerinden daha kesin bir gösterimine sahiptir (`Single` ve `Double`).</span><span class="sxs-lookup"><span data-stu-id="dee94-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="dee94-117">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="dee94-117">**Performance.**</span></span> <span data-ttu-id="dee94-118">@No__t-0 veri türü, tüm sayısal türlerin en yavaş türüdür.</span><span class="sxs-lookup"><span data-stu-id="dee94-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="dee94-119">Veri türü seçmeden önce, performans için duyarlık önem derecesine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dee94-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="dee94-120">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="dee94-120">**Widening.**</span></span> <span data-ttu-id="dee94-121">@No__t-0 veri türü `Single` veya `Double` ' widens.</span><span class="sxs-lookup"><span data-stu-id="dee94-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="dee94-122">Bu, <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Decimal` ' y i bu türlerden birine dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dee94-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="dee94-123">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="dee94-123">**Trailing Zeros.**</span></span> <span data-ttu-id="dee94-124">Visual Basic sondaki sıfırları bir `Decimal` değişmez değerinde depolamaz.</span><span class="sxs-lookup"><span data-stu-id="dee94-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="dee94-125">Ancak, `Decimal` değişkeni sondaki tüm sıfırları elde edilen hesaplama sırasında korur.</span><span class="sxs-lookup"><span data-stu-id="dee94-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="dee94-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dee94-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="dee94-127">Yukarıdaki örnekte `MsgBox` çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dee94-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="dee94-128">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="dee94-128">**Type Characters.**</span></span> <span data-ttu-id="dee94-129">Değişmez değer türü karakterini bir hazır @no__t eklemek, `Decimal` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="dee94-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="dee94-130">Tanımlayıcı türü karakterini herhangi bir tanımlayıcıya eklemek @no__t `Decimal` ' e zorlar.</span><span class="sxs-lookup"><span data-stu-id="dee94-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="dee94-131">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="dee94-131">**Framework Type.**</span></span> <span data-ttu-id="dee94-132">.NET Framework karşılık gelen tür <xref:System.Decimal?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="dee94-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="dee94-133">Aralık</span><span class="sxs-lookup"><span data-stu-id="dee94-133">Range</span></span>
 <span data-ttu-id="dee94-134">Bir `Decimal` değişkenine veya sabitine büyük bir değer atamak için `D` tür karakterini kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="dee94-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="dee94-135">Bu gereksinim, bir sabit değer türü karakteri değişmez değer olarak, aşağıdaki örnekte gösterildiği gibi, bir sabit değerin `Long` olarak yorumlaması derleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="dee94-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="dee94-136">@No__t-0 ' a yönelik bildirim bir taşma oluşturmaz çünkü kendisine atanan değer `Long` aralığı içinde.</span><span class="sxs-lookup"><span data-stu-id="dee94-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="dee94-137">@No__t-0 değeri `Decimal` değişkenine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="dee94-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="dee94-138">@No__t-0 ' a yönelik bildirim, kendisine atanan değer `Long` için çok büyük olduğundan bir taşma hatası oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="dee94-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="dee94-139">Sayısal sabit değer öncelikle `Long` olarak yorumlanamadığından, `Decimal` değişkenine atanamaz.</span><span class="sxs-lookup"><span data-stu-id="dee94-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="dee94-140">@No__t-0 için, değişmez değer türü karakteri `D`, derleyicinin sabit değeri `Long` yerine `Decimal` olarak yorumlamasını zorlayarak sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="dee94-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="dee94-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dee94-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dee94-142">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="dee94-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="dee94-143">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="dee94-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="dee94-144">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="dee94-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="dee94-145">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="dee94-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="dee94-146">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="dee94-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="dee94-147">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dee94-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
