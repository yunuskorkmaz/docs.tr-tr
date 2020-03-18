---
title: Kayan nokta sayısal türleri - C# referansı
description: 'Yerleşik C# kayan nokta türleri hakkında bilgi edinin: float, double ve ondalık'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77215247"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="a47e0-103">Kayan nokta sayısal türleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a47e0-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="a47e0-104">*Kayan nokta sayısal türleri* gerçek sayıları temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="a47e0-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="a47e0-105">Tüm kayan nokta sayısal türleri [değer türleridir.](value-types.md)</span><span class="sxs-lookup"><span data-stu-id="a47e0-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="a47e0-106">Onlar da [basit türleri](value-types.md#built-in-value-types) ve [literals](#real-literals)ile başharfolabilir.</span><span class="sxs-lookup"><span data-stu-id="a47e0-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="a47e0-107">Tüm kayan nokta sayısal türleri [aritmetik,](../operators/arithmetic-operators.md) [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a47e0-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="a47e0-108">Kayan nokta türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="a47e0-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="a47e0-109">C# aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="a47e0-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="a47e0-110">C# türü/anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="a47e0-110">C# type/keyword</span></span>|<span data-ttu-id="a47e0-111">Yaklaşık aralık</span><span class="sxs-lookup"><span data-stu-id="a47e0-111">Approximate range</span></span>|<span data-ttu-id="a47e0-112">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="a47e0-112">Precision</span></span>|<span data-ttu-id="a47e0-113">Boyut</span><span class="sxs-lookup"><span data-stu-id="a47e0-113">Size</span></span>|<span data-ttu-id="a47e0-114">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a47e0-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="a47e0-115">±1,5 x 10<sup>−45</sup> ila ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="a47e0-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="a47e0-116">~6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="a47e0-116">~6-9 digits</span></span>|<span data-ttu-id="a47e0-117">4 bayt</span><span class="sxs-lookup"><span data-stu-id="a47e0-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="a47e0-118">±5,0 × 10<sup>−324</sup> ile ±1,7 ×<sup>10 308</sup></span><span class="sxs-lookup"><span data-stu-id="a47e0-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="a47e0-119">~15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="a47e0-119">~15-17 digits</span></span>|<span data-ttu-id="a47e0-120">8 bayt</span><span class="sxs-lookup"><span data-stu-id="a47e0-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="a47e0-121">±1,0 x 10<sup>-28</sup> ile ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="a47e0-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="a47e0-122">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="a47e0-122">28-29 digits</span></span>|<span data-ttu-id="a47e0-123">16 bayt</span><span class="sxs-lookup"><span data-stu-id="a47e0-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="a47e0-124">Önceki tabloda, soldaki sütundaki her C# türü anahtar sözcüğü karşılık gelen .NET türüiçin bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="a47e0-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="a47e0-125">Değiştirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="a47e0-125">They are interchangeable.</span></span> <span data-ttu-id="a47e0-126">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="a47e0-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="a47e0-127">Her kayan nokta türünün varsayılan değeri `0`sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="a47e0-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="a47e0-128">Kayan nokta türlerinin her `MinValue` biri, bu türün minimum ve maksimum sonlu değerini sağlayan sabitlere `MaxValue` sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a47e0-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="a47e0-129">`float` Ve `double` türleri de değil-a-sayı ve sonsuz değerleri temsil eden sabitler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a47e0-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="a47e0-130">`double` Örneğin, tür aşağıdaki sabitleri <xref:System.Double.NaN?displayProperty=nameWithType>sağlar: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, ve .</span><span class="sxs-lookup"><span data-stu-id="a47e0-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a47e0-131">`decimal` Türü her ikisinden `float` de daha hassas ve daha küçük bir aralıkta olduğundan ve `double`finansal ve parasal hesaplamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="a47e0-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="a47e0-132">Bir ifadede [integral](integral-numeric-types.md) `float` türlerini ve türleri `double` karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47e0-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="a47e0-133">Bu durumda, integral türleri örtülü olarak kayan nokta türlerinden birine dönüştürülür `float` ve gerekirse tür örtülü `double`olarak .</span><span class="sxs-lookup"><span data-stu-id="a47e0-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="a47e0-134">İfade, aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="a47e0-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="a47e0-135">İfadede `double` tür varsa, ifade ilişkisel `double`ve eşitlik [`bool`](bool.md) karşılaştırmalarını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a47e0-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="a47e0-136">İfadede bir `double` tür yoksa, ifade ilişkisel `float`ve `bool` eşitlik karşılaştırmalarını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a47e0-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="a47e0-137">Ayrıca, bir ifadedeki `decimal` integral türlerini ve türünü de karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47e0-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="a47e0-138">Bu durumda, integral türleri örtülü olarak `decimal` türe dönüştürülür ve `decimal`ifade, `bool` ilişkisel ve eşitlik karşılaştırmaları için veya değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a47e0-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="a47e0-139">Bir ifadedeki `decimal` türü `float` ve `double` türleri karıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="a47e0-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="a47e0-140">Bu durumda, aritmetik, karşılaştırma veya eşitlik işlemleri gerçekleştirmek istiyorsanız, aşağıdaki örnekte görüldüğü gibi, operandları açıkça türe `decimal` dönüştürmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a47e0-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="a47e0-141">Kayan nokta değerini biçimlendirmek için [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizeleri](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47e0-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="a47e0-142">Gerçek edebi</span><span class="sxs-lookup"><span data-stu-id="a47e0-142">Real literals</span></span>

<span data-ttu-id="a47e0-143">Gerçek bir edebi türü, sonek tarafından aşağıdaki gibi belirlenir:</span><span class="sxs-lookup"><span data-stu-id="a47e0-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="a47e0-144">Sonek olmayan veya `d` `D` sonek olan edebi`double`</span><span class="sxs-lookup"><span data-stu-id="a47e0-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="a47e0-145">Veya `F` sonek `f` ile literal türü`float`</span><span class="sxs-lookup"><span data-stu-id="a47e0-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="a47e0-146">Veya `M` sonek `m` ile literal türü`decimal`</span><span class="sxs-lookup"><span data-stu-id="a47e0-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="a47e0-147">Aşağıdaki kod her birinin bir örneğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="a47e0-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="a47e0-148">Yukarıdaki örnek, C# 7.0 ile başlayan desteklenen bir basamak `_` *ayırıcısı*olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a47e0-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="a47e0-149">Sayısal literals her türlü ile basamak ayırıcı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47e0-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="a47e0-150">Aşağıdaki örnekte görüldüğü gibi, bilimsel gösterimi, diğer bir şekilde gerçek bir edebi bölümün üslü bir bölümünü belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a47e0-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="a47e0-151">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="a47e0-151">Conversions</span></span>

<span data-ttu-id="a47e0-152">Kayan nokta sayısal türleri arasında yalnızca bir örtük `float` `double`dönüştürme vardır: .'a kadar</span><span class="sxs-lookup"><span data-stu-id="a47e0-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="a47e0-153">Ancak, herhangi bir kayan nokta türünü [açık dökümle](../operators/type-testing-and-cast.md#cast-operator-)başka bir kayan nokta türüne dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47e0-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="a47e0-154">Daha fazla bilgi için yerleşik [sayısal dönüşümlere](numeric-conversions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a47e0-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a47e0-155">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a47e0-155">C# language specification</span></span>

<span data-ttu-id="a47e0-156">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="a47e0-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a47e0-157">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="a47e0-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="a47e0-158">Ondalık tür</span><span class="sxs-lookup"><span data-stu-id="a47e0-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="a47e0-159">Gerçek edebi</span><span class="sxs-lookup"><span data-stu-id="a47e0-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="a47e0-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a47e0-160">See also</span></span>

- [<span data-ttu-id="a47e0-161">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a47e0-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a47e0-162">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="a47e0-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="a47e0-163">İntegral tipleri</span><span class="sxs-lookup"><span data-stu-id="a47e0-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="a47e0-164">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="a47e0-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="a47e0-165">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="a47e0-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
