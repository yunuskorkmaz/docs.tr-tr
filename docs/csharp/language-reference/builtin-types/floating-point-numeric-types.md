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
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236056"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="b3e96-103">Kayan nokta sayısal türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b3e96-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="b3e96-104">**Kayan nokta türleri** bir alt kümesidir **basit türler** ve ile başlatılabilir [ *değişmez değerleri*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="b3e96-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="b3e96-105">Tüm kayan nokta türleri de değer türleridir.</span><span class="sxs-lookup"><span data-stu-id="b3e96-105">All floating-point types are also value types.</span></span> <span data-ttu-id="b3e96-106">Tüm kayan nokta sayısal türleri desteği [aritmetik](../operators/arithmetic-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="b3e96-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="b3e96-107">Kayan nokta türleri özellikleri</span><span class="sxs-lookup"><span data-stu-id="b3e96-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="b3e96-108">C#Aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="b3e96-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="b3e96-109">C#anahtar yazın</span><span class="sxs-lookup"><span data-stu-id="b3e96-109">C# type/keyword</span></span>|<span data-ttu-id="b3e96-110">Yaklaşık aralık</span><span class="sxs-lookup"><span data-stu-id="b3e96-110">Approximate range</span></span>|<span data-ttu-id="b3e96-111">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="b3e96-111">Precision</span></span>|<span data-ttu-id="b3e96-112">.NET türü</span><span class="sxs-lookup"><span data-stu-id="b3e96-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="b3e96-113">±1.5 x 10<sup>−45</sup> ±3.4 x 10 için<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="b3e96-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="b3e96-114">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="b3e96-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="b3e96-115">±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="b3e96-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="b3e96-116">yaklaşık 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="b3e96-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="b3e96-117">±1.0 x 10<sup>-28</sup> ±7.9228 x 10 için<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="b3e96-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="b3e96-118">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="b3e96-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="b3e96-119">Önceki tabloda her C# en soldaki sütun türü anahtar kelimedir karşılık gelen .NET türü için bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="b3e96-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="b3e96-120">Birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3e96-120">They are interchangeable.</span></span> <span data-ttu-id="b3e96-121">Örneğin, aşağıdaki bildirimleri aynı türde değişkenleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="b3e96-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="b3e96-122">Her bir kayan nokta türünün varsayılan değeri sıfırdır `0`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="b3e96-123">Kayan nokta türlerinden her birinin sahip `MinValue` ve `MaxValue` türü minimum ve maksimum sonlu değeri sağlayan sabitler.</span><span class="sxs-lookup"><span data-stu-id="b3e96-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="b3e96-124">`float` Ve `double` türleri temsil eden bir sayı değil ve sonsuz değerler sabitleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3e96-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="b3e96-125">Örneğin, `double` türü aşağıdaki sabitler sunar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3e96-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b3e96-126">Çünkü `decimal` türünde daha fazla duyarlık ve hem de daha küçük bir aralığı `float` ve `double`, finansal ve parasal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="b3e96-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="b3e96-127">Karıştırabilir miyim [integral](integral-numeric-types.md) türleri ve kayan nokta türlerinde bir ifade.</span><span class="sxs-lookup"><span data-stu-id="b3e96-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="b3e96-128">Bu durumda, tamsayı türleri için kayan nokta türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="b3e96-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="b3e96-129">İfadenin değerlendirilmesi aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="b3e96-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="b3e96-130">Kayan nokta türlerinden biri ise `double`, ifadenin değerlendirdiği `double`, veya [bool](../keywords/bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="b3e96-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="b3e96-131">Yoksa hiçbir `double` değerlendirilen ifade ifadenin türü `float`, veya [bool](../keywords/bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="b3e96-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="b3e96-132">Bir kayan nokta ifadesi, aşağıdaki adımlardan birini değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="b3e96-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="b3e96-133">Pozitif ve negatif sıfırı</span><span class="sxs-lookup"><span data-stu-id="b3e96-133">Positive and negative zero</span></span>
- <span data-ttu-id="b3e96-134">Pozitif ve negatif sonsuz</span><span class="sxs-lookup"><span data-stu-id="b3e96-134">Positive and negative infinity</span></span>
- <span data-ttu-id="b3e96-135">Bir sayı değil değeri (NaN)</span><span class="sxs-lookup"><span data-stu-id="b3e96-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="b3e96-136">Sıfır olmayan değerler sınırlı kümesi</span><span class="sxs-lookup"><span data-stu-id="b3e96-136">The finite set of nonzero values</span></span>

<span data-ttu-id="b3e96-137">Bu değerler hakkında daha fazla bilgi için bkz. IEEE standardı ikili Floating-Point aritmetik, kullanılabilir [IEEE](https://www.ieee.org) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="b3e96-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="b3e96-138">Kullanabilirsiniz [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizeleri](../../../standard/base-types/custom-numeric-format-strings.md) bir kayan nokta değeri olarak biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="b3e96-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="b3e96-139">Kayan nokta değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="b3e96-139">Floating-point literals</span></span>

<span data-ttu-id="b3e96-140">Varsayılan olarak, bir kayan nokta sayısal sabit değer atama işlecinin sağ tarafında kabul `double`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="b3e96-141">Bir kayan veya tamsayı sabit belirli bir türe dönüştürmek için sonekleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3e96-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="b3e96-142">`d` Veya `D` soneki için bir sabit değer dönüştürür bir `double`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="b3e96-143">`f` Veya `F` soneki için bir sabit değer dönüştürür bir `float`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="b3e96-144">`m` Veya `M` soneki için bir sabit değer dönüştürür bir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="b3e96-145">Aşağıdaki örnekler, her sonek gösterir:</span><span class="sxs-lookup"><span data-stu-id="b3e96-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="b3e96-146">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="b3e96-146">Conversions</span></span>

<span data-ttu-id="b3e96-147">Örtük bir dönüştürme (adlı bir *dönüştürme genişletme*) öğesinden `float` için `double` çünkü aralığını `float` değerleri olan uygun bir alt kümesini `double` ve Duyarlılıkkaybıolmadan`float` için `double`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="b3e96-148">Örtük bir dönüştürme kaynak türden hedef türe tanımlı değil, bir kayan nokta türü başka bir kayan nokta türüne dönüştürmek için açık bir tür dönüştürme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3e96-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="b3e96-149">Bu adlı bir *daraltma dönüştürmesi*.</span><span class="sxs-lookup"><span data-stu-id="b3e96-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="b3e96-150">Dönüştürme veri kaybıyla sonuçlanabildiğinden açık durumda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b3e96-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="b3e96-151">Diğer kayan nokta türleri arasında örtük dönüştürme vardır ve `decimal` türü için `decimal` türünde daha da fazla duyarlığa `float` veya `double`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="b3e96-152">Örtük sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="b3e96-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="b3e96-153">Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="b3e96-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e96-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3e96-154">See also</span></span>

- [<span data-ttu-id="b3e96-155">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b3e96-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b3e96-156">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="b3e96-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="b3e96-157">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="b3e96-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="b3e96-158">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="b3e96-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="b3e96-159">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b3e96-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="b3e96-160">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="b3e96-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="b3e96-161">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="b3e96-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="b3e96-162">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b3e96-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="b3e96-163">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="b3e96-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
