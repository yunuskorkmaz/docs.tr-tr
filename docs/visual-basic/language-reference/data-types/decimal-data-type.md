---
title: Decimal Veri Türü
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
ms.openlocfilehash: 690c8061b6df1115aa24668520170b44edfa8287
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415653"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="cea63-102">Onluk Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cea63-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="cea63-103">, 10 ' un bir değişken gücüne göre ölçeklendirilmiş 96 bit (12 baytlık) tamsayı sayılarını temsil eden imzalı 128 bitlik (16 baytlık) değerleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="cea63-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="cea63-104">Ölçeklendirme faktörü, ondalık noktanın sağ tarafındaki basamak sayısını belirtir; 0 ile 28 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="cea63-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="cea63-105">0 ölçeğinde (ondalık basamak yok), olası en büyük değer +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28) olur.</span><span class="sxs-lookup"><span data-stu-id="cea63-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="cea63-106">28 ondalık basamakla, en büyük değer +/-7.9228162514264337593543950335 ve sıfır olmayan en küçük değer +/-0,0000000000000000000000000001 (+/-1E-28) olur.</span><span class="sxs-lookup"><span data-stu-id="cea63-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="cea63-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cea63-107">Remarks</span></span>

<span data-ttu-id="cea63-108">`Decimal`Veri türü, bir sayı için en fazla sayıda önemli basamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cea63-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="cea63-109">29 ' dan fazla önemli basamağı destekler ve 7,9228 x 10 ^ 28 değerinden fazla değeri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="cea63-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="cea63-110">Çok sayıda basamak gerektiren, ancak yuvarlama hatalarını kabul edemeyecek finansal gibi hesaplamalar için özellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="cea63-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="cea63-111">Varsayılan değeri 0 ' `Decimal` dır.</span><span class="sxs-lookup"><span data-stu-id="cea63-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="cea63-112">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="cea63-112">Programming Tips</span></span>

- <span data-ttu-id="cea63-113">**Duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="cea63-113">**Precision.**</span></span> <span data-ttu-id="cea63-114">`Decimal`kayan nokta veri türü değil.</span><span class="sxs-lookup"><span data-stu-id="cea63-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="cea63-115">`Decimal`Yapı bir ikili tamsayı değerini, bir işaret biti ve değerin hangi kısmının ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörüyle birlikte tutar.</span><span class="sxs-lookup"><span data-stu-id="cea63-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="cea63-116">Bu nedenle, `Decimal` sayıların, kayan nokta türlerinden (ve) daha kesin bir temsili vardır `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="cea63-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="cea63-117">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="cea63-117">**Performance.**</span></span> <span data-ttu-id="cea63-118">`Decimal`Veri türü, tüm sayısal türlerin en yavaş türüdür.</span><span class="sxs-lookup"><span data-stu-id="cea63-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="cea63-119">Veri türü seçmeden önce, performans için duyarlık önem derecesine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cea63-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="cea63-120">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="cea63-120">**Widening.**</span></span> <span data-ttu-id="cea63-121">`Decimal`Veya için widens veri türü `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="cea63-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="cea63-122">Bu, `Decimal` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cea63-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="cea63-123">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="cea63-123">**Trailing Zeros.**</span></span> <span data-ttu-id="cea63-124">Visual Basic sondaki sıfırları bir sabit değer içinde depolamaz `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="cea63-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="cea63-125">Ancak, bir `Decimal` değişken sondaki tüm sıfırları elde edilen hesaplama sırasında korur.</span><span class="sxs-lookup"><span data-stu-id="cea63-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="cea63-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cea63-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="cea63-127">`MsgBox`Önceki örnekteki çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cea63-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="cea63-128">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="cea63-128">**Type Characters.**</span></span> <span data-ttu-id="cea63-129">Değişmez değer türü karakterini `D` bir sabit değere eklemek, `Decimal` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="cea63-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="cea63-130">Tanımlayıcı türü karakteri `@` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="cea63-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="cea63-131">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="cea63-131">**Framework Type.**</span></span> <span data-ttu-id="cea63-132">.NET Framework karşılık gelen tür <xref:System.Decimal?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="cea63-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="cea63-133">Aralık</span><span class="sxs-lookup"><span data-stu-id="cea63-133">Range</span></span>

 <span data-ttu-id="cea63-134">`D`Bir `Decimal` değişkene veya sabitine büyük bir değer atamak için tür karakterini kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cea63-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="cea63-135">Bu gereksinim, derleyicinin bir sabit değer türü karakteri değişmez değer olarak değişmez ve `Long` Aşağıdaki örnekte gösterildiği gibi değişmez.</span><span class="sxs-lookup"><span data-stu-id="cea63-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="cea63-136">`bigDec1`Öğesine atanan değer için aralığında yer aldığından, için bildirimi bir taşma oluşturmaz `Long` .</span><span class="sxs-lookup"><span data-stu-id="cea63-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="cea63-137">`Long`Değer `Decimal` değişkene atanabilir.</span><span class="sxs-lookup"><span data-stu-id="cea63-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="cea63-138">`bigDec2`Öğesine atanan değer için çok büyük olduğundan, için bildirimi bir taşma hatası oluşturur `Long` .</span><span class="sxs-lookup"><span data-stu-id="cea63-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="cea63-139">Sayısal sabit değer önce bir olarak yorumlanamadığından `Long` `Decimal` değişkenine atanamaz.</span><span class="sxs-lookup"><span data-stu-id="cea63-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="cea63-140">İçin `bigDec3` , değişmez değer türü karakteri, `D` derleyicinin sabit `Decimal` değerini a yerine bir olarak yorumlamasını zorlayarak sorunu çözer `Long` .</span><span class="sxs-lookup"><span data-stu-id="cea63-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cea63-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cea63-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cea63-142">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="cea63-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="cea63-143">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="cea63-143">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="cea63-144">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="cea63-144">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="cea63-145">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cea63-145">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="cea63-146">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="cea63-146">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="cea63-147">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="cea63-147">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
