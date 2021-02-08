---
description: 'Hakkında daha fazla bilgi edinin: Decimal veri türü (Visual Basic)'
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
ms.openlocfilehash: 5806041e7737b8fe0f1c7ffa63f6cbadcbf92e42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792238"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="ed28a-103">Onluk Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed28a-103">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="ed28a-104">, 10 ' un bir değişken gücüne göre ölçeklendirilmiş 96 bit (12 baytlık) tamsayı sayılarını temsil eden imzalı 128 bitlik (16 baytlık) değerleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="ed28a-104">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="ed28a-105">Ölçeklendirme faktörü, ondalık noktanın sağ tarafındaki basamak sayısını belirtir; 0 ile 28 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="ed28a-105">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="ed28a-106">0 ölçeğinde (ondalık basamak yok), olası en büyük değer +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28) olur.</span><span class="sxs-lookup"><span data-stu-id="ed28a-106">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="ed28a-107">28 ondalık basamakla, en büyük değer +/-7.9228162514264337593543950335 ve sıfır olmayan en küçük değer +/-0,0000000000000000000000000001 (+/-1E-28) olur.</span><span class="sxs-lookup"><span data-stu-id="ed28a-107">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="ed28a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed28a-108">Remarks</span></span>

<span data-ttu-id="ed28a-109">`Decimal`Veri türü, bir sayı için en fazla sayıda önemli basamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed28a-109">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="ed28a-110">29 ' dan fazla önemli basamağı destekler ve 7,9228 x 10 ^ 28 değerinden fazla değeri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="ed28a-110">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="ed28a-111">Çok sayıda basamak gerektiren, ancak yuvarlama hatalarını kabul edemeyecek finansal gibi hesaplamalar için özellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="ed28a-111">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="ed28a-112">Varsayılan değeri 0 ' `Decimal` dır.</span><span class="sxs-lookup"><span data-stu-id="ed28a-112">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="ed28a-113">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="ed28a-113">Programming Tips</span></span>

- <span data-ttu-id="ed28a-114">**Duyarlılık.**</span><span class="sxs-lookup"><span data-stu-id="ed28a-114">**Precision.**</span></span> <span data-ttu-id="ed28a-115">`Decimal` kayan nokta veri türü değil.</span><span class="sxs-lookup"><span data-stu-id="ed28a-115">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="ed28a-116">`Decimal`Yapı bir ikili tamsayı değerini, bir işaret biti ve değerin hangi kısmının ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörüyle birlikte tutar.</span><span class="sxs-lookup"><span data-stu-id="ed28a-116">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="ed28a-117">Bu nedenle, `Decimal` sayıların, kayan nokta türlerinden (ve) daha kesin bir temsili vardır `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-117">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="ed28a-118">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="ed28a-118">**Performance.**</span></span> <span data-ttu-id="ed28a-119">`Decimal`Veri türü, tüm sayısal türlerin en yavaş türüdür.</span><span class="sxs-lookup"><span data-stu-id="ed28a-119">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="ed28a-120">Veri türü seçmeden önce, performans için duyarlık önem derecesine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed28a-120">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="ed28a-121">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="ed28a-121">**Widening.**</span></span> <span data-ttu-id="ed28a-122">`Decimal`Veya için widens veri türü `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-122">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="ed28a-123">Bu, `Decimal` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ed28a-123">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="ed28a-124">**Sondaki sıfırlar.**</span><span class="sxs-lookup"><span data-stu-id="ed28a-124">**Trailing Zeros.**</span></span> <span data-ttu-id="ed28a-125">Visual Basic sondaki sıfırları bir sabit değer içinde depolamaz `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-125">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="ed28a-126">Ancak, bir `Decimal` değişken sondaki tüm sıfırları elde edilen hesaplama sırasında korur.</span><span class="sxs-lookup"><span data-stu-id="ed28a-126">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="ed28a-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ed28a-127">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="ed28a-128">`MsgBox`Önceki örnekteki çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ed28a-128">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="ed28a-129">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="ed28a-129">**Type Characters.**</span></span> <span data-ttu-id="ed28a-130">Değişmez değer türü karakterini `D` bir sabit değere eklemek, `Decimal` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="ed28a-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="ed28a-131">Tanımlayıcı türü karakteri `@` herhangi bir tanımlayıcıya eklemek bunu öğesine zorlar `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="ed28a-132">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="ed28a-132">**Framework Type.**</span></span> <span data-ttu-id="ed28a-133">.NET Framework karşılık gelen tür <xref:System.Decimal?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="ed28a-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="ed28a-134">Aralık</span><span class="sxs-lookup"><span data-stu-id="ed28a-134">Range</span></span>

 <span data-ttu-id="ed28a-135">`D`Bir `Decimal` değişkene veya sabitine büyük bir değer atamak için tür karakterini kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ed28a-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="ed28a-136">Bu gereksinim, derleyicinin bir sabit değer türü karakteri değişmez değer olarak değişmez ve `Long` Aşağıdaki örnekte gösterildiği gibi değişmez.</span><span class="sxs-lookup"><span data-stu-id="ed28a-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="ed28a-137">`bigDec1`Öğesine atanan değer için aralığında yer aldığından, için bildirimi bir taşma oluşturmaz `Long` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="ed28a-138">`Long`Değer `Decimal` değişkene atanabilir.</span><span class="sxs-lookup"><span data-stu-id="ed28a-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="ed28a-139">`bigDec2`Öğesine atanan değer için çok büyük olduğundan, için bildirimi bir taşma hatası oluşturur `Long` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="ed28a-140">Sayısal sabit değer önce bir olarak yorumlanamadığından `Long` `Decimal` değişkenine atanamaz.</span><span class="sxs-lookup"><span data-stu-id="ed28a-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="ed28a-141">İçin `bigDec3` , değişmez değer türü karakteri, `D` derleyicinin sabit `Decimal` değerini a yerine bir olarak yorumlamasını zorlayarak sorunu çözer `Long` .</span><span class="sxs-lookup"><span data-stu-id="ed28a-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed28a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed28a-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ed28a-143">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="ed28a-143">Data Types</span></span>](index.md)
- [<span data-ttu-id="ed28a-144">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ed28a-144">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="ed28a-145">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ed28a-145">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="ed28a-146">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ed28a-146">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ed28a-147">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="ed28a-147">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ed28a-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ed28a-148">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
