---
title: Kayan nokta sayısal türleri- C# başvuru
description: Yerleşik C# kayan nokta türlerine genel bakış
ms.date: 10/18/2019
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
ms.openlocfilehash: fa6cbb869d90113414cc6f8ffe231386c3596b1d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579376"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="a61a1-103">Kayan nokta sayısal türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="a61a1-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="a61a1-104">**Kayan nokta türleri** **basit türlerin** bir alt kümesidir ve [*değişmez değerler*](#real-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#real-literals).</span></span> <span data-ttu-id="a61a1-105">Tüm kayan nokta türleri de değer türlerdir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-105">All floating-point types are also value types.</span></span> <span data-ttu-id="a61a1-106">Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a61a1-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="a61a1-107">Kayan nokta türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="a61a1-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="a61a1-108">C#aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="a61a1-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="a61a1-109">C#tür/anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="a61a1-109">C# type/keyword</span></span>|<span data-ttu-id="a61a1-110">Yaklaşık Aralık</span><span class="sxs-lookup"><span data-stu-id="a61a1-110">Approximate range</span></span>|<span data-ttu-id="a61a1-111">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="a61a1-111">Precision</span></span>|<span data-ttu-id="a61a1-112">Boyut</span><span class="sxs-lookup"><span data-stu-id="a61a1-112">Size</span></span>|<span data-ttu-id="a61a1-113">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a61a1-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="a61a1-114">± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="a61a1-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="a61a1-115">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="a61a1-115">~6-9 digits</span></span>|<span data-ttu-id="a61a1-116">4 bayt</span><span class="sxs-lookup"><span data-stu-id="a61a1-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="a61a1-117">± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="a61a1-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="a61a1-118">~ 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="a61a1-118">~15-17 digits</span></span>|<span data-ttu-id="a61a1-119">8 bayt</span><span class="sxs-lookup"><span data-stu-id="a61a1-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="a61a1-120">± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="a61a1-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="a61a1-121">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="a61a1-121">28-29 digits</span></span>|<span data-ttu-id="a61a1-122">16 bayt</span><span class="sxs-lookup"><span data-stu-id="a61a1-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="a61a1-123">Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="a61a1-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="a61a1-124">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-124">They are interchangeable.</span></span> <span data-ttu-id="a61a1-125">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="a61a1-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="a61a1-126">Her kayan nokta türünün varsayılan değeri sıfır, `0` ' dır.</span><span class="sxs-lookup"><span data-stu-id="a61a1-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="a61a1-127">Kayan nokta türlerinin her biri, bu türün minimum ve maksimum sonlu değerini sağlayan `MinValue` ve `MaxValue` sabitleri vardır.</span><span class="sxs-lookup"><span data-stu-id="a61a1-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="a61a1-128">@No__t_0 ve `double` türleri, sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="a61a1-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="a61a1-129">Örneğin, `double` türü şu sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a61a1-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a61a1-130">@No__t_0 türü daha fazla kesinlik ve `float` ve `double` daha küçük bir aralığa sahip olduğundan, finansal ve parasal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="a61a1-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="a61a1-131">Bir ifadede [integral](integral-numeric-types.md) türlerini ve kayan nokta türlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a61a1-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="a61a1-132">Bu durumda, integral türler kayan nokta türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a61a1-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="a61a1-133">İfadenin değerlendirmesi aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="a61a1-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="a61a1-134">Kayan nokta türlerinden biri `double`, ifade `double` veya ilişkisel ve eşitlik karşılaştırmalarında [bool](../keywords/bool.md) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="a61a1-135">İfadede `double` tür yoksa, ifade `float` veya ilişkisel ve eşitlik karşılaştırmalarında [bool](../keywords/bool.md) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="a61a1-136">Kayan nokta ifadesi aşağıdaki değer kümelerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="a61a1-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="a61a1-137">Pozitif ve negatif sıfır</span><span class="sxs-lookup"><span data-stu-id="a61a1-137">Positive and negative zero</span></span>
- <span data-ttu-id="a61a1-138">Pozitif ve negatif sonsuzluk</span><span class="sxs-lookup"><span data-stu-id="a61a1-138">Positive and negative infinity</span></span>
- <span data-ttu-id="a61a1-139">Sayı olmayan değer (NaN)</span><span class="sxs-lookup"><span data-stu-id="a61a1-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="a61a1-140">Sınırlı olmayan değerler kümesi</span><span class="sxs-lookup"><span data-stu-id="a61a1-140">The finite set of nonzero values</span></span>

<span data-ttu-id="a61a1-141">Bu değerler hakkında daha fazla bilgi için, [IEEE](https://www.ieee.org) Web sitesinde kullanılabilen Ikili kayan nokta ARITMETIĞI Için IEEE Standard ' a bakın.</span><span class="sxs-lookup"><span data-stu-id="a61a1-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="a61a1-142">Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a61a1-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="a61a1-143">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a61a1-143">Real literals</span></span>

<span data-ttu-id="a61a1-144">Gerçek bir sabit değerin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="a61a1-144">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="a61a1-145">Sonek olmadan veya `d` ya da `D` sonekine sahip sabit değer `double` türündedir</span><span class="sxs-lookup"><span data-stu-id="a61a1-145">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="a61a1-146">@No__t_0 veya `F` sonekine sahip sabit değer `float` türündedir</span><span class="sxs-lookup"><span data-stu-id="a61a1-146">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="a61a1-147">@No__t_0 veya `M` sonekine sahip sabit değer `decimal` türündedir</span><span class="sxs-lookup"><span data-stu-id="a61a1-147">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="a61a1-148">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="a61a1-148">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="a61a1-149">Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-149">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="a61a1-150">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a61a1-150">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="a61a1-151">Ayrıca, aşağıdaki örnekte gösterildiği gibi bilimsel gösterim kullanabilirsiniz, yani gerçek bir sabit değerin üs bir kısmını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a61a1-151">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="a61a1-152">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="a61a1-152">Conversions</span></span>

<span data-ttu-id="a61a1-153">@No__t_3 değerler `double` uygun bir alt kümesi olduğundan ve `float` ile `double` arasında bir duyarlık kaybı olmadığından, `float` 'den `double` örtük bir dönüştürme ( *genişleyen dönüştürme*denir) vardır.</span><span class="sxs-lookup"><span data-stu-id="a61a1-153">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="a61a1-154">Örtük bir dönüştürme, kaynak türünden hedef türüne tanımlanmamışsa, bir kayan nokta türünü başka bir kayan nokta türüne dönüştürmek için açık bir atama kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-154">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="a61a1-155">Bu, *daraltma dönüştürmesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a61a1-155">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="a61a1-156">Dönüştürme işlemi veri kaybına neden olabileceğinden açık durum gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a61a1-156">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="a61a1-157">@No__t_1 türü `float` ya da `double` göre daha fazla duyarlığa sahip olduğundan, diğer kayan nokta türleri ve `decimal` türü arasında örtük dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="a61a1-157">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="a61a1-158">Örtük Sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [örtük sayısal dönüştürmeler tablosu](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="a61a1-158">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="a61a1-159">Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Açık Sayısal Dönüşümler Tablosu](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="a61a1-159">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a61a1-160">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a61a1-160">C# language specification</span></span>

<span data-ttu-id="a61a1-161">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="a61a1-161">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a61a1-162">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="a61a1-162">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="a61a1-163">Ondalık tür</span><span class="sxs-lookup"><span data-stu-id="a61a1-163">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="a61a1-164">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a61a1-164">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="a61a1-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a61a1-165">See also</span></span>

- [<span data-ttu-id="a61a1-166">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="a61a1-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a61a1-167">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="a61a1-167">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="a61a1-168">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="a61a1-168">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="a61a1-169">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="a61a1-169">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="a61a1-170">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="a61a1-170">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="a61a1-171">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="a61a1-171">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="a61a1-172">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="a61a1-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
