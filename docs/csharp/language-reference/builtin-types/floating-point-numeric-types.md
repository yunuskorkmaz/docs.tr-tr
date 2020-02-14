---
title: Kayan nokta sayısal türleri- C# başvuru
description: 'Yerleşik C# kayan nokta türleri hakkında bilgi edinin: float, Double ve Decimal'
ms.date: 02/10/2020
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
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215247"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="2f4d6-103">Kayan nokta sayısal türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="2f4d6-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="2f4d6-104">*Kayan nokta sayısal türleri* gerçek sayıları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="2f4d6-105">Tüm kayan nokta sayısal türleri [değer türlerdir](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="2f4d6-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="2f4d6-106">Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#real-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="2f4d6-107">Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="2f4d6-108">Kayan nokta türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="2f4d6-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="2f4d6-109">C#aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="2f4d6-110">C#tür/anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2f4d6-110">C# type/keyword</span></span>|<span data-ttu-id="2f4d6-111">Yaklaşık Aralık</span><span class="sxs-lookup"><span data-stu-id="2f4d6-111">Approximate range</span></span>|<span data-ttu-id="2f4d6-112">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="2f4d6-112">Precision</span></span>|<span data-ttu-id="2f4d6-113">Boyut</span><span class="sxs-lookup"><span data-stu-id="2f4d6-113">Size</span></span>|<span data-ttu-id="2f4d6-114">.NET türü</span><span class="sxs-lookup"><span data-stu-id="2f4d6-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="2f4d6-115">± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="2f4d6-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="2f4d6-116">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="2f4d6-116">~6-9 digits</span></span>|<span data-ttu-id="2f4d6-117">4 bayt</span><span class="sxs-lookup"><span data-stu-id="2f4d6-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="2f4d6-118">± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="2f4d6-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="2f4d6-119">~ 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="2f4d6-119">~15-17 digits</span></span>|<span data-ttu-id="2f4d6-120">8 bayt</span><span class="sxs-lookup"><span data-stu-id="2f4d6-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="2f4d6-121">± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="2f4d6-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="2f4d6-122">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="2f4d6-122">28-29 digits</span></span>|<span data-ttu-id="2f4d6-123">16 bayt</span><span class="sxs-lookup"><span data-stu-id="2f4d6-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="2f4d6-124">Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="2f4d6-125">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-125">They are interchangeable.</span></span> <span data-ttu-id="2f4d6-126">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="2f4d6-127">Her kayan nokta türünün varsayılan değeri sıfırdır `0`.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="2f4d6-128">Kayan nokta türlerinin her biri, bu türün minimum ve maksimum sonlu değerini sağlayan `MinValue` ve `MaxValue` sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="2f4d6-129">`float` ve `double` türleri, sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="2f4d6-130">Örneğin, `double` türü şu sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2f4d6-131">`decimal` türü daha fazla kesinlik ve `float` ve `double`daha küçük bir aralığa sahip olduğundan, finansal ve parasal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="2f4d6-132">Bir ifadede [integral](integral-numeric-types.md) türlerini ve `float` ve `double` türlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="2f4d6-133">Bu durumda, integral türler örtük olarak kayan nokta türlerinden birine dönüştürülür ve gerekirse `float` türü örtük olarak `double`dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="2f4d6-134">İfade, aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="2f4d6-135">İfadede `double` tür varsa, ifade `double`veya ilişkisel ve eşitlik karşılaştırmalarında [`bool`](bool.md) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="2f4d6-136">İfadede `double` tür yoksa, ifade `float`veya ilişkisel ve eşitlik karşılaştırmalarında `bool` olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="2f4d6-137">Ayrıca, tamsayı türlerini ve `decimal` türünü bir ifadede karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="2f4d6-138">Bu durumda, tam sayı türleri örtülü olarak `decimal` türüne dönüştürülür ve ifade `decimal`veya ilişkisel ve eşitlik karşılaştırmaları `bool` olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="2f4d6-139">`decimal` türünü bir ifadede `float` ve `double` türleriyle karıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="2f4d6-140">Bu durumda, aritmetik, karşılaştırma veya eşitlik işlemleri gerçekleştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi, işlenenleri ya da `decimal` türüne açıkça dönüştürmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="2f4d6-141">Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="2f4d6-142">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="2f4d6-142">Real literals</span></span>

<span data-ttu-id="2f4d6-143">Gerçek bir sabit değerin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="2f4d6-144">Sonek olmadan veya `d` ya da `D` sonekine sahip sabit değer `double` türündedir</span><span class="sxs-lookup"><span data-stu-id="2f4d6-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="2f4d6-145">`f` veya `F` sonekine sahip sabit değer `float` türündedir</span><span class="sxs-lookup"><span data-stu-id="2f4d6-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="2f4d6-146">`m` veya `M` sonekine sahip sabit değer `decimal` türündedir</span><span class="sxs-lookup"><span data-stu-id="2f4d6-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="2f4d6-147">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="2f4d6-148">Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="2f4d6-149">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="2f4d6-150">Ayrıca, aşağıdaki örnekte gösterildiği gibi bilimsel gösterim kullanabilirsiniz, yani gerçek bir sabit değerin üs bir kısmını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="2f4d6-151">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2f4d6-151">Conversions</span></span>

<span data-ttu-id="2f4d6-152">Kayan nokta sayısal türleri arasında yalnızca bir örtük dönüşüm vardır: `float` 'den `double`.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="2f4d6-153">Ancak, herhangi bir kayan nokta türünü [açık atama](../operators/type-testing-and-cast.md#cast-operator-)ile başka bir kayan nokta türüne dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="2f4d6-154">Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2f4d6-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2f4d6-155">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2f4d6-155">C# language specification</span></span>

<span data-ttu-id="2f4d6-156">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="2f4d6-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2f4d6-157">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="2f4d6-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="2f4d6-158">Ondalık tür</span><span class="sxs-lookup"><span data-stu-id="2f4d6-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="2f4d6-159">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="2f4d6-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="2f4d6-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f4d6-160">See also</span></span>

- [<span data-ttu-id="2f4d6-161">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="2f4d6-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2f4d6-162">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="2f4d6-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="2f4d6-163">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="2f4d6-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="2f4d6-164">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="2f4d6-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="2f4d6-165">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="2f4d6-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
