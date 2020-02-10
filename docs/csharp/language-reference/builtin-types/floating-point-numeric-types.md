---
title: Kayan nokta sayısal türleri- C# başvuru
description: Yerleşik C# kayan nokta türlerine genel bakış
ms.date: 10/22/2019
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
ms.openlocfilehash: 9c8b11f9337ee9de90f2d4d96b5be162713bfcbd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093220"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="d57db-103">Kayan nokta sayısal türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="d57db-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="d57db-104">*Kayan nokta sayısal türleri* gerçek sayıları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d57db-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="d57db-105">Tüm kayan nokta sayısal türleri [değer türlerdir](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="d57db-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="d57db-106">Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#real-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="d57db-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="d57db-107">Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="d57db-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="d57db-108">Kayan nokta türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="d57db-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="d57db-109">C#aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="d57db-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="d57db-110">C#tür/anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="d57db-110">C# type/keyword</span></span>|<span data-ttu-id="d57db-111">Yaklaşık Aralık</span><span class="sxs-lookup"><span data-stu-id="d57db-111">Approximate range</span></span>|<span data-ttu-id="d57db-112">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="d57db-112">Precision</span></span>|<span data-ttu-id="d57db-113">Boyut</span><span class="sxs-lookup"><span data-stu-id="d57db-113">Size</span></span>|<span data-ttu-id="d57db-114">.NET türü</span><span class="sxs-lookup"><span data-stu-id="d57db-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="d57db-115">± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="d57db-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="d57db-116">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="d57db-116">~6-9 digits</span></span>|<span data-ttu-id="d57db-117">4 bayt</span><span class="sxs-lookup"><span data-stu-id="d57db-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="d57db-118">± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="d57db-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="d57db-119">~ 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="d57db-119">~15-17 digits</span></span>|<span data-ttu-id="d57db-120">8 bayt</span><span class="sxs-lookup"><span data-stu-id="d57db-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="d57db-121">± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="d57db-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="d57db-122">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="d57db-122">28-29 digits</span></span>|<span data-ttu-id="d57db-123">16 bayt</span><span class="sxs-lookup"><span data-stu-id="d57db-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="d57db-124">Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="d57db-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="d57db-125">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d57db-125">They are interchangeable.</span></span> <span data-ttu-id="d57db-126">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="d57db-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="d57db-127">Her kayan nokta türünün varsayılan değeri sıfırdır `0`.</span><span class="sxs-lookup"><span data-stu-id="d57db-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="d57db-128">Kayan nokta türlerinin her biri, bu türün minimum ve maksimum sonlu değerini sağlayan `MinValue` ve `MaxValue` sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d57db-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="d57db-129">`float` ve `double` türleri, sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="d57db-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="d57db-130">Örneğin, `double` türü şu sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d57db-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d57db-131">`decimal` türü daha fazla kesinlik ve `float` ve `double`daha küçük bir aralığa sahip olduğundan, finansal ve parasal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="d57db-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="d57db-132">Bir ifadede [integral](integral-numeric-types.md) türlerini ve kayan nokta türlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d57db-132">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="d57db-133">Bu durumda, integral türler kayan nokta türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d57db-133">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="d57db-134">İfadenin değerlendirmesi aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="d57db-134">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="d57db-135">Kayan nokta türlerinden biri `double`, ifade `double`veya ilişkisel ve eşitlik karşılaştırmalarında [bool](bool.md) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d57db-135">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="d57db-136">İfadede `double` tür yoksa, ifade `float`veya ilişkisel ve eşitlik karşılaştırmalarında [bool](bool.md) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d57db-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="d57db-137">Kayan nokta ifadesi aşağıdaki değer kümelerini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="d57db-137">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="d57db-138">Pozitif ve negatif sıfır</span><span class="sxs-lookup"><span data-stu-id="d57db-138">Positive and negative zero</span></span>
- <span data-ttu-id="d57db-139">Pozitif ve negatif sonsuzluk</span><span class="sxs-lookup"><span data-stu-id="d57db-139">Positive and negative infinity</span></span>
- <span data-ttu-id="d57db-140">Sayı olmayan değer (NaN)</span><span class="sxs-lookup"><span data-stu-id="d57db-140">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="d57db-141">Sınırlı olmayan değerler kümesi</span><span class="sxs-lookup"><span data-stu-id="d57db-141">The finite set of nonzero values</span></span>

<span data-ttu-id="d57db-142">Bu değerler hakkında daha fazla bilgi için, [IEEE](https://www.ieee.org) Web sitesinde kullanılabilen Ikili kayan nokta ARITMETIĞI Için IEEE Standard ' a bakın.</span><span class="sxs-lookup"><span data-stu-id="d57db-142">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="d57db-143">Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d57db-143">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="d57db-144">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="d57db-144">Real literals</span></span>

<span data-ttu-id="d57db-145">Gerçek bir sabit değerin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="d57db-145">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="d57db-146">Sonek olmadan veya `d` ya da `D` sonekine sahip sabit değer `double` türündedir</span><span class="sxs-lookup"><span data-stu-id="d57db-146">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="d57db-147">`f` veya `F` sonekine sahip sabit değer `float` türündedir</span><span class="sxs-lookup"><span data-stu-id="d57db-147">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="d57db-148">`m` veya `M` sonekine sahip sabit değer `decimal` türündedir</span><span class="sxs-lookup"><span data-stu-id="d57db-148">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="d57db-149">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="d57db-149">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="d57db-150">Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="d57db-150">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="d57db-151">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d57db-151">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="d57db-152">Ayrıca, aşağıdaki örnekte gösterildiği gibi bilimsel gösterim kullanabilirsiniz, yani gerçek bir sabit değerin üs bir kısmını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d57db-152">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="d57db-153">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="d57db-153">Conversions</span></span>

<span data-ttu-id="d57db-154">Kayan nokta sayısal türleri arasında yalnızca bir örtük dönüşüm vardır: `float` 'den `double`.</span><span class="sxs-lookup"><span data-stu-id="d57db-154">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="d57db-155">Ancak, herhangi bir kayan nokta türünü [açık atama](../operators/type-testing-and-cast.md#cast-operator-)ile başka bir kayan nokta türüne dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d57db-155">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="d57db-156">Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="d57db-156">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d57db-157">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d57db-157">C# language specification</span></span>

<span data-ttu-id="d57db-158">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="d57db-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d57db-159">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="d57db-159">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="d57db-160">Ondalık tür</span><span class="sxs-lookup"><span data-stu-id="d57db-160">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="d57db-161">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="d57db-161">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="d57db-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d57db-162">See also</span></span>

- [<span data-ttu-id="d57db-163">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="d57db-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d57db-164">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="d57db-164">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d57db-165">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="d57db-165">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="d57db-166">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="d57db-166">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="d57db-167">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="d57db-167">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
