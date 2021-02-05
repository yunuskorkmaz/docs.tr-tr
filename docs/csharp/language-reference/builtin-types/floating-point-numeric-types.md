---
title: Kayan nokta sayısal türleri-C# başvurusu
description: 'Yerleşik C# kayan nokta türleri hakkında bilgi edinin: float, Double ve Decimal'
ms.date: 02/04/2021
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
ms.openlocfilehash: a086e8de60bbb63408c3f2cd557feb36c4baa0f8
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585760"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="3f79e-103">Kayan nokta sayısal türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3f79e-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="3f79e-104">*Kayan nokta sayısal türleri* gerçek sayıları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3f79e-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="3f79e-105">Tüm kayan nokta sayısal türleri [değer türlerdir](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="3f79e-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="3f79e-106">Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#real-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="3f79e-107">Tüm kayan nokta sayısal türleri [Aritmetik](../operators/arithmetic-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="3f79e-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="3f79e-108">Kayan nokta türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="3f79e-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="3f79e-109">C#, aşağıdaki önceden tanımlanmış kayan nokta türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="3f79e-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="3f79e-110">C# türü/anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="3f79e-110">C# type/keyword</span></span>|<span data-ttu-id="3f79e-111">Yaklaşık Aralık</span><span class="sxs-lookup"><span data-stu-id="3f79e-111">Approximate range</span></span>|<span data-ttu-id="3f79e-112">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="3f79e-112">Precision</span></span>|<span data-ttu-id="3f79e-113">Boyut</span><span class="sxs-lookup"><span data-stu-id="3f79e-113">Size</span></span>|<span data-ttu-id="3f79e-114">.NET türü</span><span class="sxs-lookup"><span data-stu-id="3f79e-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="3f79e-115">± 1,5 x 10<sup>− 45</sup> ila ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="3f79e-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="3f79e-116">~ 6-9 basamak</span><span class="sxs-lookup"><span data-stu-id="3f79e-116">~6-9 digits</span></span>|<span data-ttu-id="3f79e-117">4 bayt</span><span class="sxs-lookup"><span data-stu-id="3f79e-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="3f79e-118">± 5,0 × 10<sup>− 324</sup> ila ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="3f79e-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="3f79e-119">~ 15-17 basamak</span><span class="sxs-lookup"><span data-stu-id="3f79e-119">~15-17 digits</span></span>|<span data-ttu-id="3f79e-120">8 bayt</span><span class="sxs-lookup"><span data-stu-id="3f79e-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="3f79e-121">± 1,0 x 10<sup>-28</sup> ila ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="3f79e-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="3f79e-122">28-29 basamak</span><span class="sxs-lookup"><span data-stu-id="3f79e-122">28-29 digits</span></span>|<span data-ttu-id="3f79e-123">16 bayt</span><span class="sxs-lookup"><span data-stu-id="3f79e-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="3f79e-124">Yukarıdaki tabloda, en soldaki sütundan her C# tür anahtar sözcüğü, karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="3f79e-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="3f79e-125">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-125">They are interchangeable.</span></span> <span data-ttu-id="3f79e-126">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="3f79e-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="3f79e-127">Her kayan nokta türünün varsayılan değeri sıfırdır `0` .</span><span class="sxs-lookup"><span data-stu-id="3f79e-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="3f79e-128">Kayan nokta türlerinin her biri, `MinValue` `MaxValue` Bu türün minimum ve maksimum sonlu değerini sağlayan ve sabitleridir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="3f79e-129">`float`Ve `double` türleri ayrıca, sayı olmayan ve sonsuz değerleri temsil eden sabitleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f79e-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="3f79e-130">Örneğin, `double` türü aşağıdaki sabitleri sağlar: <xref:System.Double.NaN?displayProperty=nameWithType> , <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ve <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3f79e-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3f79e-131">`decimal`Gerekli duyarlık derecesi, ondalık noktanın sağ tarafındaki basamak sayısına göre belirleniyorsa, tür uygundur.</span><span class="sxs-lookup"><span data-stu-id="3f79e-131">The `decimal` type is appropriate when the required degree of precision is determined by the number of digits to the right of the decimal point.</span></span> <span data-ttu-id="3f79e-132">Bu sayılar genellikle finansal uygulamalarda, para birimi miktarları (örneğin, $1,00), faiz oranları (örneğin,% 2,625) için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f79e-132">Such numbers are commonly used in financial applications, for currency amounts (for example, $1.00), interest rates (for example, 2.625%), and so forth.</span></span> <span data-ttu-id="3f79e-133">Yalnızca bir ondalık basamak için kesin olan sayılar, tür tarafından daha doğru işlenir `decimal` : 0,1, örneğin, tam olarak 0,1 ' i `decimal` `double` temsil eden bir veya örnek olarak, bir örnek tarafından tam olarak temsil edilebilir `float` .</span><span class="sxs-lookup"><span data-stu-id="3f79e-133">Even numbers that are precise to only one decimal digit are handled more accurately by the `decimal` type: 0.1, for example, can be exactly represented by a `decimal` instance, while there's no `double` or `float` instance that exactly represents 0.1.</span></span> <span data-ttu-id="3f79e-134">Sayısal türlerde bu fark nedeniyle, `double` veya ondalık veriler için kullandığınızda aritmetik hesaplamalarda beklenmedik yuvarlama hataları oluşabilir `float` .</span><span class="sxs-lookup"><span data-stu-id="3f79e-134">Because of this difference in numeric types, unexpected rounding errors can occur in arithmetic calculations when you use `double` or `float` for decimal data.</span></span> <span data-ttu-id="3f79e-135">`double` `decimal` Performansı en iyi duruma getirmeye kıyasla bunun yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-135">You can use `double` instead of `decimal` when optimizing performance is more important than ensuring accuracy.</span></span> <span data-ttu-id="3f79e-136">Ancak, performansla ilgili herhangi bir farklılık, en fazla hesaplama yoğun uygulamalar tarafından açıklanabilecek.</span><span class="sxs-lookup"><span data-stu-id="3f79e-136">However, any difference in performance would go unnoticed by all but the most calculation-intensive applications.</span></span> <span data-ttu-id="3f79e-137">Kaçınmanın olası bir nedeni `decimal` , depolama gereksinimlerini en aza indirmektir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-137">Another possible reason to avoid `decimal` is to minimize storage requirements.</span></span> <span data-ttu-id="3f79e-138">Örneğin, [ml.net](../../../machine-learning/how-does-mldotnet-work.md) , `float` 4 bayt ve 16 bayt arasındaki fark çok büyük veri kümeleri için eklediği için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f79e-138">For example, [ML.NET](../../../machine-learning/how-does-mldotnet-work.md) uses `float` because the difference between 4 bytes and 16 bytes adds up for very large data sets.</span></span> <span data-ttu-id="3f79e-139">Daha fazla bilgi için bkz. <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f79e-139">For more information, see <xref:System.Decimal?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3f79e-140">Bir ifadede [integral](integral-numeric-types.md) türlerini ve `float` ve türlerini karıştırabilirsiniz `double` .</span><span class="sxs-lookup"><span data-stu-id="3f79e-140">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="3f79e-141">Bu durumda, integral türler örtük olarak kayan nokta türlerinden birine dönüştürülür ve gerekirse `float` tür örtülü olarak dönüştürülür `double` .</span><span class="sxs-lookup"><span data-stu-id="3f79e-141">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="3f79e-142">İfade, aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="3f79e-142">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="3f79e-143">`double`İfadede tür varsa, ifade olarak `double` veya [`bool`](bool.md) ilişkisel ve eşitlik karşılaştırmaları olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-143">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="3f79e-144">İfadede hiçbir tür yoksa `double` , ifade olarak `float` veya `bool` ilişkisel ve eşitlik karşılaştırmaları olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-144">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="3f79e-145">Ayrıca integral türlerini ve `decimal` bir ifadede türü karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-145">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="3f79e-146">Bu durumda, integral türleri örtük olarak `decimal` türüne dönüştürülür ve ifade olarak `decimal` veya `bool` ilişkisel ve eşitlik karşılaştırmaları olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-146">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="3f79e-147">`decimal`Türü `float` `double` bir ifadede ve türleriyle karıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-147">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="3f79e-148">Bu durumda, aritmetik, karşılaştırma veya eşitlik işlemleri gerçekleştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi, işlenenleri ya da türünden türüne açıkça dönüştürmeniz gerekir `decimal` :</span><span class="sxs-lookup"><span data-stu-id="3f79e-148">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="3f79e-149">Kayan noktalı bir değeri biçimlendirmek için [Standart sayısal biçim dizelerini](../../../standard/base-types/standard-numeric-format-strings.md) veya [özel sayısal biçim dizelerini](../../../standard/base-types/custom-numeric-format-strings.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-149">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="3f79e-150">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="3f79e-150">Real literals</span></span>

<span data-ttu-id="3f79e-151">Gerçek bir sabit değerin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="3f79e-151">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="3f79e-152">Sonek olmadan veya veya sonekine sahip sabit `d` değer `D` türü `double`</span><span class="sxs-lookup"><span data-stu-id="3f79e-152">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="3f79e-153">Veya sonekine sahip sabit `f` değer `F` tür `float`</span><span class="sxs-lookup"><span data-stu-id="3f79e-153">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="3f79e-154">Veya sonekine sahip sabit `m` değer `M` tür `decimal`</span><span class="sxs-lookup"><span data-stu-id="3f79e-154">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="3f79e-155">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="3f79e-155">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="3f79e-156">Yukarıdaki örnek ayrıca `_` C# 7,0 ile başlayarak desteklenen bir *rakam ayırıcısı* olarak kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f79e-156">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="3f79e-157">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-157">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="3f79e-158">Ayrıca, aşağıdaki örnekte gösterildiği gibi bilimsel gösterim kullanabilirsiniz, yani gerçek bir sabit değerin üs bir kısmını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3f79e-158">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="3f79e-159">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="3f79e-159">Conversions</span></span>

<span data-ttu-id="3f79e-160">Kayan nokta sayısal türleri arasında yalnızca bir örtük dönüşüm vardır: öğesinden `float` öğesine `double` .</span><span class="sxs-lookup"><span data-stu-id="3f79e-160">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="3f79e-161">Ancak, herhangi bir kayan nokta türünü [açık atama](../operators/type-testing-and-cast.md#cast-expression)ile başka bir kayan nokta türüne dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-161">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="3f79e-162">Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3f79e-162">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3f79e-163">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3f79e-163">C# language specification</span></span>

<span data-ttu-id="3f79e-164">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="3f79e-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3f79e-165">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="3f79e-165">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="3f79e-166">Ondalık tür</span><span class="sxs-lookup"><span data-stu-id="3f79e-166">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="3f79e-167">Gerçek sabit değerler</span><span class="sxs-lookup"><span data-stu-id="3f79e-167">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="3f79e-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f79e-168">See also</span></span>

- [<span data-ttu-id="3f79e-169">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f79e-169">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3f79e-170">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="3f79e-170">Value types</span></span>](value-types.md)
- [<span data-ttu-id="3f79e-171">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="3f79e-171">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="3f79e-172">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="3f79e-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="3f79e-173">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="3f79e-173">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
