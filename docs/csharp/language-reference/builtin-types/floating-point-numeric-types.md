---
title: Kayan nokta sayısal türleri- C# başvuru
description: Yerleşik C# kayan nokta türlerine genel bakış
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002200"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="0d925-103">Kayan nokta sayısal türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="0d925-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="0d925-104">**Kayan nokta türleri** **basit türlerin** bir alt kümesidir ve [*değişmez değerler*](#floating-point-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d925-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="0d925-105">Tüm kayan nokta türleri de değer türlerdir.</span><span class="sxs-lookup"><span data-stu-id="0d925-105">All floating-point types are also value types.</span></span> <span data-ttu-id="0d925-106">Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="0d925-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="0d925-107">Kayan nokta türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="0d925-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="0d925-108">C#aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="0d925-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="0d925-109">C#tür/anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="0d925-109">C# type/keyword</span></span>|<span data-ttu-id="0d925-110">Yaklaşık Aralık</span><span class="sxs-lookup"><span data-stu-id="0d925-110">Approximate range</span></span>|<span data-ttu-id="0d925-111">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="0d925-111">Precision</span></span>|<span data-ttu-id="0d925-112">Boyut</span><span class="sxs-lookup"><span data-stu-id="0d925-112">Size</span></span>|<span data-ttu-id="0d925-113">.NET türü</span><span class="sxs-lookup"><span data-stu-id="0d925-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="0d925-114">± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="0d925-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="0d925-115">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="0d925-115">~6-9 digits</span></span>|<span data-ttu-id="0d925-116">4 bayt</span><span class="sxs-lookup"><span data-stu-id="0d925-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="0d925-117">± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="0d925-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="0d925-118">~ 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="0d925-118">~15-17 digits</span></span>|<span data-ttu-id="0d925-119">8 bayt</span><span class="sxs-lookup"><span data-stu-id="0d925-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="0d925-120">± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="0d925-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="0d925-121">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="0d925-121">28-29 digits</span></span>|<span data-ttu-id="0d925-122">16 bayt</span><span class="sxs-lookup"><span data-stu-id="0d925-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="0d925-123">Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="0d925-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="0d925-124">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d925-124">They are interchangeable.</span></span> <span data-ttu-id="0d925-125">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="0d925-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="0d925-126">Her kayan nokta türünün varsayılan değeri sıfır, `0` ' dır.</span><span class="sxs-lookup"><span data-stu-id="0d925-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="0d925-127">Kayan nokta türlerinin her biri, bu türün minimum ve maksimum sonlu değerini sağlayan `MinValue` ve `MaxValue` sabitleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0d925-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="0d925-128">@No__t-0 ve `double` türleri ayrıca sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d925-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="0d925-129">Örneğin, `double` türü şu sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d925-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0d925-130">@No__t-0 türü daha fazla duyarlık ve `float` ve `double` ' den daha küçük bir aralığa sahip olduğundan, finansal ve parasal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="0d925-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="0d925-131">Bir ifadede [integral](integral-numeric-types.md) türlerini ve kayan nokta türlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d925-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="0d925-132">Bu durumda, integral türler kayan nokta türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="0d925-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="0d925-133">İfadenin değerlendirmesi aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="0d925-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="0d925-134">Kayan nokta türlerinden biri `double` ise, ifade `double` ' i veya ilişkisel karşılaştırmalarda [bool](../keywords/bool.md) ya da eşitlik karşılaştırmaları ' ne göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0d925-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="0d925-135">İfadede `double` türü yoksa, ifade `float` ' i veya ilişkisel karşılaştırmalar ya da eşitlik karşılaştırmaları için [bool](../keywords/bool.md) değerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0d925-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="0d925-136">Kayan nokta ifadesi aşağıdaki değer kümelerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="0d925-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="0d925-137">Pozitif ve negatif sıfır</span><span class="sxs-lookup"><span data-stu-id="0d925-137">Positive and negative zero</span></span>
- <span data-ttu-id="0d925-138">Pozitif ve negatif sonsuzluk</span><span class="sxs-lookup"><span data-stu-id="0d925-138">Positive and negative infinity</span></span>
- <span data-ttu-id="0d925-139">Sayı olmayan değer (NaN)</span><span class="sxs-lookup"><span data-stu-id="0d925-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="0d925-140">Sınırlı olmayan değerler kümesi</span><span class="sxs-lookup"><span data-stu-id="0d925-140">The finite set of nonzero values</span></span>

<span data-ttu-id="0d925-141">Bu değerler hakkında daha fazla bilgi için, [IEEE](https://www.ieee.org) Web sitesinde kullanılabilen Ikili kayan nokta ARITMETIĞI Için IEEE Standard ' a bakın.</span><span class="sxs-lookup"><span data-stu-id="0d925-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="0d925-142">Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d925-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="0d925-143">Kayan nokta sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="0d925-143">Floating-point literals</span></span>

<span data-ttu-id="0d925-144">Varsayılan olarak, atama işlecinin sağ tarafındaki kayan nokta sayısal değişmez değeri `double` olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0d925-144">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="0d925-145">Bir kayan nokta veya integral sabit değerini belirli bir türe dönüştürmek için son ekleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d925-145">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="0d925-146">@No__t-0 veya `D` soneki, bir sabit değeri `double` ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0d925-146">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="0d925-147">@No__t-0 veya `F` soneki, bir sabit değeri `float` ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0d925-147">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="0d925-148">@No__t-0 veya `M` soneki, bir sabit değeri `decimal` ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0d925-148">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="0d925-149">Aşağıdaki örneklerde her bir sonek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0d925-149">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="0d925-150">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="0d925-150">Conversions</span></span>

<span data-ttu-id="0d925-151">@No__t-1 ' den `double` ' ye ait `float` değerlerinin doğru bir alt @no__t kümesi olduğundan ve `float` ' e `double` ' a bir duyarlık kaybı olmadığı için,-1 ' den-2 ' den örtük bir dönüştürme ( *genişleyen dönüştürme*denir) vardır.</span><span class="sxs-lookup"><span data-stu-id="0d925-151">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="0d925-152">Örtük bir dönüştürme, kaynak türünden hedef türüne tanımlanmamışsa, bir kayan nokta türünü başka bir kayan nokta türüne dönüştürmek için açık bir atama kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d925-152">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="0d925-153">Bu, *daraltma dönüştürmesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0d925-153">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="0d925-154">Dönüştürme işlemi veri kaybına neden olabileceğinden açık durum gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0d925-154">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="0d925-155">@No__t-1 türü `float` veya `double` ' ten daha büyük bir duyarlık içerdiğinden, diğer kayan nokta türleri ve `decimal` türü arasında örtük dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d925-155">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="0d925-156">Örtük Sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [örtük sayısal dönüştürmeler tablosu](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="0d925-156">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="0d925-157">Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Açık Sayısal Dönüşümler Tablosu](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="0d925-157">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d925-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d925-158">See also</span></span>

- [<span data-ttu-id="0d925-159">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="0d925-159">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d925-160">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="0d925-160">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="0d925-161">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="0d925-161">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="0d925-162">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="0d925-162">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="0d925-163">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0d925-163">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="0d925-164">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0d925-164">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="0d925-165">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0d925-165">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="0d925-166">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="0d925-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="0d925-167">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="0d925-167">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
