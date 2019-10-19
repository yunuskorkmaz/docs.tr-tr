---
title: Integral sayısal türleri- C# başvuru
description: İntegral sayısal türlerin her biri için aralığı, depolama boyutunu ve kullanımları öğrenin.
ms.date: 10/18/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579189"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="855f0-103">Integral sayısal türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="855f0-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="855f0-104">**İntegral sayısal türleri** **basit türlerin** bir alt kümesidir ve [*değişmez değerler*](#integer-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="855f0-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="855f0-105">Tüm integral türleri de değer türlerdir.</span><span class="sxs-lookup"><span data-stu-id="855f0-105">All integral types are also value types.</span></span> <span data-ttu-id="855f0-106">Tüm integral sayısal türler [Aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="855f0-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="855f0-107">İntegral türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="855f0-107">Characteristics of the integral types</span></span>

<span data-ttu-id="855f0-108">C#aşağıdaki önceden tanımlanmış integral türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="855f0-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="855f0-109">C#tür/anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="855f0-109">C# type/keyword</span></span>|<span data-ttu-id="855f0-110">Aralık</span><span class="sxs-lookup"><span data-stu-id="855f0-110">Range</span></span>|<span data-ttu-id="855f0-111">Boyut</span><span class="sxs-lookup"><span data-stu-id="855f0-111">Size</span></span>|<span data-ttu-id="855f0-112">.NET türü</span><span class="sxs-lookup"><span data-stu-id="855f0-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="855f0-113">-128-127</span><span class="sxs-lookup"><span data-stu-id="855f0-113">-128 to 127</span></span>|<span data-ttu-id="855f0-114">İmzalanan 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="855f0-115">0-255</span><span class="sxs-lookup"><span data-stu-id="855f0-115">0 to 255</span></span>|<span data-ttu-id="855f0-116">İşaretsiz 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="855f0-117">-32.768-32.767</span><span class="sxs-lookup"><span data-stu-id="855f0-117">-32,768 to 32,767</span></span>|<span data-ttu-id="855f0-118">İmzalanan 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="855f0-119">0-65.535</span><span class="sxs-lookup"><span data-stu-id="855f0-119">0 to 65,535</span></span>|<span data-ttu-id="855f0-120">İşaretsiz 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="855f0-121">-2.147.483.648-2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="855f0-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="855f0-122">İmzalanan 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="855f0-123">0-4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="855f0-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="855f0-124">İşaretsiz 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="855f0-125">-9223372036854775808-9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="855f0-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="855f0-126">İmzalanan 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="855f0-127">0-18446744073709551615</span><span class="sxs-lookup"><span data-stu-id="855f0-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="855f0-128">İşaretsiz 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="855f0-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="855f0-129">Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="855f0-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="855f0-130">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="855f0-130">They are interchangeable.</span></span> <span data-ttu-id="855f0-131">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="855f0-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="855f0-132">Her integral türünün varsayılan değeri sıfırdır `0`.</span><span class="sxs-lookup"><span data-stu-id="855f0-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="855f0-133">İntegral türlerinin her biri, bu türün en düşük ve en büyük değerini sağlayan `MinValue` ve `MaxValue` sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="855f0-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="855f0-134">Büyük veya alt sınır olmadan işaretli bir tamsayıyı temsil etmek için <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="855f0-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="855f0-135">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="855f0-135">Integer literals</span></span>

<span data-ttu-id="855f0-136">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="855f0-136">Integer literals can be</span></span>

- <span data-ttu-id="855f0-137">*Decimal*: herhangi bir ön ek olmadan</span><span class="sxs-lookup"><span data-stu-id="855f0-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="855f0-138">*onaltılı*: `0x` veya `0X` ön eki ile</span><span class="sxs-lookup"><span data-stu-id="855f0-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="855f0-139">*ikili*: `0b` veya `0B` önekiyle ( C# 7,0 ve üzeri sürümlerde mevcuttur)</span><span class="sxs-lookup"><span data-stu-id="855f0-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="855f0-140">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="855f0-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="855f0-141">Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="855f0-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="855f0-142">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="855f0-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="855f0-143">Bir tamsayı sabit değerinin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="855f0-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="855f0-144">Değişmez değer için bir sonek yoksa, türü, değerinin gösterilebileceği aşağıdaki türlerin birincsahiptir: `int`, `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="855f0-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="855f0-145">Sabit değer `U` veya `u` ile sondiçeriyorsa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="855f0-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="855f0-146">Sabit değer `L` veya `l` ile sondiçeriyorsa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="855f0-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="855f0-147">Küçük harf `l` bir sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="855f0-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="855f0-148">Ancak, harf `l` `1` basamak ile karıştırıabileceğinden bu bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="855f0-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="855f0-149">Açıklık için `L` kullanın.</span><span class="sxs-lookup"><span data-stu-id="855f0-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="855f0-150">Sabit değer `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` veya `lu` tarafından düzeltildiğinde, türü `ulong` olur.</span><span class="sxs-lookup"><span data-stu-id="855f0-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="855f0-151">Bir tamsayı değişmez değeri ile temsil edilen değer <xref:System.UInt64.MaxValue?displayProperty=nameWithType> aşarsa, bir derleyici hatası [CS1021](../../misc/cs1021.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="855f0-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="855f0-152">Bir tamsayı değişmez değeri tarafından temsil edilen değer, örtük olarak, sabit değer türü tarafından belirlenen değerden daha küçük bir aralığa dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="855f0-152">The value represented by an integer literal can be implicitly converted to a type with a smaller range than the determined type of the literal.</span></span> <span data-ttu-id="855f0-153">Bu, değer hedef türünün aralığı dahilinde olduğunda mümkündür:</span><span class="sxs-lookup"><span data-stu-id="855f0-153">That's possible when the value is within the range of the destination type:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="855f0-154">Yukarıdaki örnekte gösterildiği gibi, değişmez değerin değeri hedef türü Aralık içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="855f0-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="855f0-155">Ayrıca, bir tamsayı değişmez değeri ile temsil edilen değeri, değişmez değerin belirlenen türü dışında bir türe dönüştürmek için bir cast kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="855f0-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="855f0-156">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="855f0-156">Conversions</span></span>

<span data-ttu-id="855f0-157">Hedef türün kaynak türünün tüm değerlerini depolayabileceği iki integral tür arasında örtük bir dönüştürme ( *genişleyen dönüştürme*denir) vardır.</span><span class="sxs-lookup"><span data-stu-id="855f0-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="855f0-158">Örneğin, `int` değerlerinin aralığı `long` uygun bir alt kümesi olduğundan, `int` `long` ' den örtük bir dönüştürme vardır.</span><span class="sxs-lookup"><span data-stu-id="855f0-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="855f0-159">Daha küçük bir işaretsiz integral türünden daha büyük bir işaretli integral türüne örtük dönüştürmeler vardır.</span><span class="sxs-lookup"><span data-stu-id="855f0-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="855f0-160">Ayrıca herhangi bir integral türünden herhangi bir kayan nokta türüne örtük bir dönüştürme de vardır.</span><span class="sxs-lookup"><span data-stu-id="855f0-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="855f0-161">Herhangi bir imzalı integral türünden hiçbir işaretsiz integral türüne örtülü dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="855f0-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="855f0-162">Örtük bir dönüştürme, kaynak türünden hedef türüne tanımlanmadığında, bir integral türünü başka bir integral türüne dönüştürmek için açık bir atama kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="855f0-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="855f0-163">Bu, *daraltma dönüştürmesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="855f0-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="855f0-164">Dönüştürme işlemi veri kaybına neden olabileceğinden açık durum gereklidir.</span><span class="sxs-lookup"><span data-stu-id="855f0-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="855f0-165">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="855f0-165">C# language specification</span></span>

<span data-ttu-id="855f0-166">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="855f0-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="855f0-167">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="855f0-167">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="855f0-168">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="855f0-168">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="855f0-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="855f0-169">See also</span></span>

- [<span data-ttu-id="855f0-170">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="855f0-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="855f0-171">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="855f0-171">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="855f0-172">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="855f0-172">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="855f0-173">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="855f0-173">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="855f0-174">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="855f0-174">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="855f0-175">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="855f0-175">Numerics in .NET</span></span>](../../../standard/numerics.md)
