---
title: Onluk Veri Türü
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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243329"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="9ff1a-102">Onluk Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ff1a-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="9ff1a-103">10 değişken gücüyle ölçeklenmiş 96 bit (12 bayt) tamsayı numaralarını temsil eden imzalı 128 bit (16 bayt) değerleri tutar.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="9ff1a-104">Ölçekleme faktörü ondalık noktanın sağındaki basamak sayısını belirtir; 0 ile 28 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="9ff1a-105">0 ölçeği (ondalık basamak yok) ile, mümkün olan en büyük değer +/-79.228.162.514.264.337.593.543.950.335 (+/-7228162514264337593544395035E+28' dir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="9ff1a-106">28 ondalık basamakile en büyük değer +/-7228162514264337593543950335 ve en küçük sıfır olmayan değer +/-0.0000000000000000000000000000000000000000000000 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="9ff1a-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="9ff1a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ff1a-107">Remarks</span></span>

<span data-ttu-id="9ff1a-108">Veri `Decimal` türü, bir sayı için en çok önemli basamak sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="9ff1a-109">29'a kadar önemli basamağı destekler ve 7,9228 x 10^28'i aşan değerleri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="9ff1a-110">Özellikle çok sayıda basamak gerektiren ancak yuvarlama hatalarını tolere edemeyen finansal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="9ff1a-111">Varsayılan değeri `Decimal` 0'dır.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="9ff1a-112">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="9ff1a-112">Programming Tips</span></span>

- <span data-ttu-id="9ff1a-113">**Hassas.**</span><span class="sxs-lookup"><span data-stu-id="9ff1a-113">**Precision.**</span></span> <span data-ttu-id="9ff1a-114">`Decimal`kayan nokta veri türü değildir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="9ff1a-115">Yapı, `Decimal` bir işaret biti ve değerin hangi bölümünün ondalık kesir olduğunu belirten bir tamsayı ölçeklendirme faktörüyle birlikte ikili bir tamsayı değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="9ff1a-116">Bu nedenle, `Decimal` sayılar kayan nokta türlerine göre bellekte`Single` `Double`daha kesin bir gösterime sahiptir ( ve).</span><span class="sxs-lookup"><span data-stu-id="9ff1a-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="9ff1a-117">**Performans.**</span><span class="sxs-lookup"><span data-stu-id="9ff1a-117">**Performance.**</span></span> <span data-ttu-id="9ff1a-118">Veri `Decimal` türü tüm sayısal türlerin en yavaşıdır.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="9ff1a-119">Bir veri türünü seçmeden önce performansın performansını tartmalısınız.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="9ff1a-120">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="9ff1a-120">**Widening.**</span></span> <span data-ttu-id="9ff1a-121">Veri `Decimal` türü `Single` genişletir `Double`veya .</span><span class="sxs-lookup"><span data-stu-id="9ff1a-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="9ff1a-122">Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Decimal` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="9ff1a-123">**Sıfırları Takip Ediyor.**</span><span class="sxs-lookup"><span data-stu-id="9ff1a-123">**Trailing Zeros.**</span></span> <span data-ttu-id="9ff1a-124">Visual Basic, sondaki sıfırları `Decimal` gerçek bir şekilde depolamaz.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="9ff1a-125">Ancak, `Decimal` bir değişken hesaplamalı olarak edinilen sondaki sıfırları korur.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="9ff1a-126">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="9ff1a-127">Önceki `MsgBox` örnekte çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9ff1a-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="9ff1a-128">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="9ff1a-128">**Type Characters.**</span></span> <span data-ttu-id="9ff1a-129">Gerçek tür karakterini `D` bir edebi karaktere ekler, `Decimal` onu veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="9ff1a-130">Tanımlayıcı türü karakterini `@` herhangi bir tanımlayıcıya `Decimal`ekolarak .</span><span class="sxs-lookup"><span data-stu-id="9ff1a-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="9ff1a-131">**Çerçeve Türü.**</span><span class="sxs-lookup"><span data-stu-id="9ff1a-131">**Framework Type.**</span></span> <span data-ttu-id="9ff1a-132">.NET Framework'de karşılık gelen <xref:System.Decimal?displayProperty=nameWithType> tür yapıdır.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="9ff1a-133">Aralık</span><span class="sxs-lookup"><span data-stu-id="9ff1a-133">Range</span></span>

 <span data-ttu-id="9ff1a-134">Bir `Decimal` değişkene veya `D` sabite büyük bir değer atamak için tür karakterini kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="9ff1a-135">Derleyici, aşağıdaki örnekte görüldüğü gibi, `Long` edebi türü bir karakter aşağıdaki gibi, bir edebi karakter aşağıdaki gibi aşağıdaki gibi değilse, bir literal olarak yorumluyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="9ff1a-136">Buna atanan `bigDec1` değer `Long`için aralık içinde düştüğünden, taşma oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="9ff1a-137">Değer `Long` `Decimal` değişkene atanabilir.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="9ff1a-138">Ona atanan `bigDec2` değer `Long`için çok büyük olduğundan, bir taşma hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="9ff1a-139">Sayısal edebi ilk olarak `Long`yorumlanamayacağıiçin, `Decimal` değişkene atanamaz.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="9ff1a-140">Çünkü, `bigDec3`edebi türde `D` karakter derleyiciyi literal'ı bir ' `Decimal` yerine "" `Long`olarak yorumlamaya zorlayarak sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ff1a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ff1a-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9ff1a-142">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9ff1a-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="9ff1a-143">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9ff1a-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="9ff1a-144">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9ff1a-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="9ff1a-145">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9ff1a-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9ff1a-146">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="9ff1a-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="9ff1a-147">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9ff1a-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
