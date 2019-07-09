---
title: Kayan nokta sayısal türleri - C# başvurusu
description: Yerleşik C# kayan nokta türleri'ne genel bakış
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664208"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="2b6ce-103">Kayan nokta sayısal türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b6ce-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="2b6ce-104">**Kayan nokta türleri** bir alt kümesidir **basit türler** ve ile başlatılabilir [ *değişmez değerleri*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="2b6ce-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="2b6ce-105">Tüm kayan nokta türleri de değer türleridir.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-105">All floating-point types are also value types.</span></span> <span data-ttu-id="2b6ce-106">Tüm kayan nokta sayısal türleri desteği [aritmetik](../operators/arithmetic-operators.md) [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md) [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

<span data-ttu-id="2b6ce-107">Kayan nokta türleri için yaklaşık aralık ve duyarlık aşağıdaki tabloda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2b6ce-107">The following table shows the precision and approximate ranges for the floating-point types:</span></span>
  
|<span data-ttu-id="2b6ce-108">Tür</span><span class="sxs-lookup"><span data-stu-id="2b6ce-108">Type</span></span>|<span data-ttu-id="2b6ce-109">Yaklaşık aralık</span><span class="sxs-lookup"><span data-stu-id="2b6ce-109">Approximate range</span></span>|<span data-ttu-id="2b6ce-110">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="2b6ce-110">Precision</span></span>|  
|----------|-----------------------|---------------|  
|`float`|<span data-ttu-id="2b6ce-111">±1.5 x 10<sup>−45</sup> ±3.4 x 10 için<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="2b6ce-111">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="2b6ce-112">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="2b6ce-112">~6-9 digits</span></span>|  
|`double`|<span data-ttu-id="2b6ce-113">±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="2b6ce-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="2b6ce-114">yaklaşık 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="2b6ce-114">~15-17 digits</span></span>|  
|`decimal`|<span data-ttu-id="2b6ce-115">±1.0 x 10<sup>-28</sup> ±7.9228 x 10 için<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="2b6ce-115">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="2b6ce-116">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="2b6ce-116">28-29 digits</span></span>|  

<span data-ttu-id="2b6ce-117">Tüm kayan nokta türleri için varsayılan değerdir `0`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-117">The default value for all floating-point types is `0`.</span></span> <span data-ttu-id="2b6ce-118">Her bir kayan nokta türleri adlandırılmış sabitler olan `MinValue` ve `MaxValue` türü için minimum ve maksimum değeri.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-118">Each of the floating-point types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span> <span data-ttu-id="2b6ce-119">`float` Ve `double` türleri için ek sabitler sahip `PositiveInfinity`, `NegativeInfinity`, ve `NaN` (için "bir sayı değil").</span><span class="sxs-lookup"><span data-stu-id="2b6ce-119">The `float` and `double` types have additional constants for `PositiveInfinity`, `NegativeInfinity`, and `NaN` (for "Not a Number").</span></span> <span data-ttu-id="2b6ce-120">`decimal` Türü için sabitler içerir `Zero`, `One`, ve `MinusOne`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-120">The `decimal` type includes constants for `Zero`, `One`, and `MinusOne`.</span></span>

<span data-ttu-id="2b6ce-121">`decimal` Türünde daha fazla duyarlık ve hem de daha küçük bir aralığı `float` ve `double`, getiren onu finansal ve parasal hesaplamalar için uygun.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-121">The `decimal` type has more precision and a smaller range than both `float` and `double`, which makes it appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="2b6ce-122">İntegral türleri ve kayan nokta türleri bir ifadede karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-122">You can mix integral types and floating-point types in an expression.</span></span> <span data-ttu-id="2b6ce-123">Bu durumda, tamsayı türleri için kayan nokta türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-123">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="2b6ce-124">İfadenin değerlendirilmesi aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="2b6ce-124">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="2b6ce-125">Kayan nokta türlerinden biri ise `double`, ifadenin değerlendirdiği `double`, veya [bool](../keywords/bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-125">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="2b6ce-126">Yoksa hiçbir `double` değerlendirilen ifade ifadenin türü `float`, veya [bool](../keywords/bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-126">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="2b6ce-127">Bir kayan nokta ifadesi, aşağıdaki adımlardan birini değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="2b6ce-127">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="2b6ce-128">Pozitif ve negatif sıfırı</span><span class="sxs-lookup"><span data-stu-id="2b6ce-128">Positive and negative zero</span></span>
- <span data-ttu-id="2b6ce-129">Pozitif ve negatif sonsuz</span><span class="sxs-lookup"><span data-stu-id="2b6ce-129">Positive and negative infinity</span></span>
- <span data-ttu-id="2b6ce-130">Bir sayı değil değeri (NaN)</span><span class="sxs-lookup"><span data-stu-id="2b6ce-130">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="2b6ce-131">Sıfır olmayan değerler sınırlı kümesi</span><span class="sxs-lookup"><span data-stu-id="2b6ce-131">The finite set of nonzero values</span></span>

<span data-ttu-id="2b6ce-132">Bu değerler hakkında daha fazla bilgi için bkz. IEEE standardı ikili Floating-Point aritmetik, kullanılabilir [IEEE](https://www.ieee.org) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-132">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="2b6ce-133">Kullanabilirsiniz [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizeleri](../../../standard/base-types/custom-numeric-format-strings.md) bir kayan nokta değeri olarak biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-133">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="2b6ce-134">Kayan nokta değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="2b6ce-134">Floating-point literals</span></span>

<span data-ttu-id="2b6ce-135">Varsayılan olarak, bir kayan nokta sayısal sabit değer atama işlecinin sağ tarafında kabul `double`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-135">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="2b6ce-136">Bir kayan veya tamsayı sabit belirli bir türe dönüştürmek için sonekleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b6ce-136">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="2b6ce-137">`d` Veya `D` soneki için bir sabit değer dönüştürür bir `double`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-137">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="2b6ce-138">`f` Veya `F` soneki için bir sabit değer dönüştürür bir `float`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-138">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="2b6ce-139">`m` Veya `M` soneki için bir sabit değer dönüştürür bir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-139">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="2b6ce-140">Aşağıdaki örnekler, her sonek gösterir:</span><span class="sxs-lookup"><span data-stu-id="2b6ce-140">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="2b6ce-141">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2b6ce-141">Conversions</span></span>

<span data-ttu-id="2b6ce-142">Örtük bir dönüştürme (adlı bir *dönüştürme genişletme*) öğesinden `float` için `double` çünkü aralığını `float` değerleri olan uygun bir alt kümesini `double` ve Duyarlılıkkaybıolmadan`float` için `double`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-142">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span> 

<span data-ttu-id="2b6ce-143">Örtük bir dönüştürme kaynak türden hedef türe tanımlı değil, bir kayan nokta türü başka bir kayan nokta türüne dönüştürmek için açık bir tür dönüştürme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-143">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="2b6ce-144">Bu adlı bir *daraltma dönüştürmesi*.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-144">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="2b6ce-145">Dönüştürme veri kaybıyla sonuçlanabildiğinden açık durumda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-145">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="2b6ce-146">Diğer kayan nokta türleri arasında örtük dönüştürme vardır ve `decimal` türü için `decimal` türünde daha da fazla duyarlığa `float` veya `double`.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-146">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="2b6ce-147">Örtük sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="2b6ce-147">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="2b6ce-148">Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="2b6ce-148">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b6ce-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b6ce-149">See also</span></span>

- [<span data-ttu-id="2b6ce-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b6ce-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2b6ce-151">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="2b6ce-151">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="2b6ce-152">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="2b6ce-152">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="2b6ce-153">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="2b6ce-153">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="2b6ce-154">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="2b6ce-154">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="2b6ce-155">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="2b6ce-155">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="2b6ce-156">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="2b6ce-156">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="2b6ce-157">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="2b6ce-157">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="2b6ce-158">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="2b6ce-158">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="2b6ce-159">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="2b6ce-159">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
