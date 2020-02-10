---
title: Integral sayısal türleri- C# başvuru
description: İntegral sayısal türlerin her biri için aralığı, depolama boyutunu ve kullanımları öğrenin.
ms.date: 10/22/2019
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
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093207"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="977a1-103">Integral sayısal türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="977a1-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="977a1-104">*İntegral sayısal türleri* tamsayı sayılarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="977a1-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="977a1-105">Tüm integral sayısal türleri [değer türlerdir](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="977a1-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="977a1-106">Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#integer-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="977a1-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="977a1-107">Tüm integral sayısal türler [Aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="977a1-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="977a1-108">İntegral türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="977a1-108">Characteristics of the integral types</span></span>

<span data-ttu-id="977a1-109">C#aşağıdaki önceden tanımlanmış integral türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="977a1-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="977a1-110">C#tür/anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="977a1-110">C# type/keyword</span></span>|<span data-ttu-id="977a1-111">Aralık</span><span class="sxs-lookup"><span data-stu-id="977a1-111">Range</span></span>|<span data-ttu-id="977a1-112">Boyut</span><span class="sxs-lookup"><span data-stu-id="977a1-112">Size</span></span>|<span data-ttu-id="977a1-113">.NET türü</span><span class="sxs-lookup"><span data-stu-id="977a1-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="977a1-114">-128-127</span><span class="sxs-lookup"><span data-stu-id="977a1-114">-128 to 127</span></span>|<span data-ttu-id="977a1-115">İmzalanan 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="977a1-116">0-255</span><span class="sxs-lookup"><span data-stu-id="977a1-116">0 to 255</span></span>|<span data-ttu-id="977a1-117">İşaretsiz 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="977a1-118">-32.768-32.767</span><span class="sxs-lookup"><span data-stu-id="977a1-118">-32,768 to 32,767</span></span>|<span data-ttu-id="977a1-119">İmzalanan 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="977a1-120">0-65.535</span><span class="sxs-lookup"><span data-stu-id="977a1-120">0 to 65,535</span></span>|<span data-ttu-id="977a1-121">İşaretsiz 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="977a1-122">-2.147.483.648-2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="977a1-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="977a1-123">İmzalanan 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="977a1-124">0-4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="977a1-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="977a1-125">İşaretsiz 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="977a1-126">-9223372036854775808-9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="977a1-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="977a1-127">İmzalanan 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="977a1-128">0-18446744073709551615</span><span class="sxs-lookup"><span data-stu-id="977a1-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="977a1-129">İşaretsiz 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="977a1-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="977a1-130">Yukarıdaki tabloda, en soldaki sütundan C# her tür anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="977a1-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="977a1-131">Bunlar arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="977a1-131">They are interchangeable.</span></span> <span data-ttu-id="977a1-132">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="977a1-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="977a1-133">Her integral türünün varsayılan değeri sıfırdır `0`.</span><span class="sxs-lookup"><span data-stu-id="977a1-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="977a1-134">İntegral türlerinin her biri, bu türün en düşük ve en büyük değerini sağlayan `MinValue` ve `MaxValue` sabitlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="977a1-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="977a1-135">Büyük veya alt sınır olmadan işaretli bir tamsayıyı temsil etmek için <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="977a1-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="977a1-136">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="977a1-136">Integer literals</span></span>

<span data-ttu-id="977a1-137">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="977a1-137">Integer literals can be</span></span>

- <span data-ttu-id="977a1-138">*Decimal*: herhangi bir ön ek olmadan</span><span class="sxs-lookup"><span data-stu-id="977a1-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="977a1-139">*onaltılı*: `0x` veya `0X` ön eki ile</span><span class="sxs-lookup"><span data-stu-id="977a1-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="977a1-140">*ikili*: `0b` veya `0B` önekiyle ( C# 7,0 ve üzeri sürümlerde mevcuttur)</span><span class="sxs-lookup"><span data-stu-id="977a1-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="977a1-141">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="977a1-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="977a1-142">Yukarıdaki örnek ayrıca, 7,0 ile C# başlayarak desteklenen bir *rakam ayırıcısı*olarak `_` kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="977a1-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="977a1-143">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="977a1-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="977a1-144">Bir tamsayı sabit değerinin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="977a1-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="977a1-145">Değişmez değer için bir sonek yoksa, türü, değerinin gösterilebileceği aşağıdaki türlerin birincsahiptir: `int`, `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="977a1-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="977a1-146">Sabit değer `U` veya `u`ile sondiçeriyorsa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="977a1-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="977a1-147">Sabit değer `L` veya `l`ile sondiçeriyorsa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="977a1-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="977a1-148">Küçük harf `l` bir sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="977a1-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="977a1-149">Ancak, harf `l` `1`basamak ile karıştırıabileceğinden bu bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="977a1-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="977a1-150">Açıklık için `L` kullanın.</span><span class="sxs-lookup"><span data-stu-id="977a1-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="977a1-151">Sabit değer `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`veya `lu`tarafından düzeltildiğinde, türü `ulong`olur.</span><span class="sxs-lookup"><span data-stu-id="977a1-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="977a1-152">Bir tamsayı değişmez değeri ile temsil edilen değer <xref:System.UInt64.MaxValue?displayProperty=nameWithType>aşarsa, bir derleyici hatası [CS1021](../../misc/cs1021.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="977a1-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="977a1-153">Bir tamsayı değişmez değerinin belirlenen türü `int` ise ve değişmez değer tarafından temsil edilen değer hedef türünün aralığı içindeyse, değer örtük olarak `sbyte`, `byte`, `short`, `ushort`, `uint`veya `ulong`dönüştürülebilir:</span><span class="sxs-lookup"><span data-stu-id="977a1-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="977a1-154">Yukarıdaki örnekte gösterildiği gibi, değişmez değerin değeri hedef türü Aralık içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="977a1-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="977a1-155">Ayrıca, bir tamsayı değişmez değeri ile temsil edilen değeri, değişmez değerin belirlenen türü dışında bir türe dönüştürmek için bir cast kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="977a1-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="977a1-156">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="977a1-156">Conversions</span></span>

<span data-ttu-id="977a1-157">Herhangi bir integral sayısal türü diğer tüm integral sayısal türlerine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="977a1-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="977a1-158">Hedef türü kaynak türünün tüm değerlerini depolayabiliyorsanız, dönüştürme örtük olur.</span><span class="sxs-lookup"><span data-stu-id="977a1-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="977a1-159">Aksi takdirde, açık bir dönüştürme çağırmak için [`()`cast işlecini](../operators/type-testing-and-cast.md#cast-operator-) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="977a1-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="977a1-160">Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="977a1-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="977a1-161">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="977a1-161">C# language specification</span></span>

<span data-ttu-id="977a1-162">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="977a1-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="977a1-163">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="977a1-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="977a1-164">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="977a1-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="977a1-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="977a1-165">See also</span></span>

- [<span data-ttu-id="977a1-166">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="977a1-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="977a1-167">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="977a1-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="977a1-168">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="977a1-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="977a1-169">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="977a1-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="977a1-170">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="977a1-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
