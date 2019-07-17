---
title: Tamsayı sayısal türleri - C# başvurusu
description: Aralık, depolama boyutu ve kullandığı her tamsayı sayısal türleri için öğrenin.
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236083"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="e0d42-103">Tamsayı sayısal türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0d42-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="e0d42-104">**Tamsayı sayısal türleri** bir alt kümesidir **basit türler** ve ile başlatılabilir [ *değişmez değerleri*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="e0d42-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="e0d42-105">Tüm tamsayı türleri de değer türleridir.</span><span class="sxs-lookup"><span data-stu-id="e0d42-105">All integral types are also value types.</span></span> <span data-ttu-id="e0d42-106">Tüm tamsayı sayısal türleri desteği [aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="e0d42-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="e0d42-107">İntegral türündeki özellikleri</span><span class="sxs-lookup"><span data-stu-id="e0d42-107">Characteristics of the integral types</span></span>

<span data-ttu-id="e0d42-108">C#Aşağıdaki önceden tanımlanmış tamsayı türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="e0d42-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="e0d42-109">C#anahtar yazın</span><span class="sxs-lookup"><span data-stu-id="e0d42-109">C# type/keyword</span></span>|<span data-ttu-id="e0d42-110">Aralık</span><span class="sxs-lookup"><span data-stu-id="e0d42-110">Range</span></span>|<span data-ttu-id="e0d42-111">Boyut</span><span class="sxs-lookup"><span data-stu-id="e0d42-111">Size</span></span>|<span data-ttu-id="e0d42-112">.NET türü</span><span class="sxs-lookup"><span data-stu-id="e0d42-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="e0d42-113">-128 ila 127 arasında</span><span class="sxs-lookup"><span data-stu-id="e0d42-113">-128 to 127</span></span>|<span data-ttu-id="e0d42-114">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="e0d42-115">0 ile 255 arasında</span><span class="sxs-lookup"><span data-stu-id="e0d42-115">0 to 255</span></span>|<span data-ttu-id="e0d42-116">İmzalanmamış 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="e0d42-117">-32.768 için 32.767</span><span class="sxs-lookup"><span data-stu-id="e0d42-117">-32,768 to 32,767</span></span>|<span data-ttu-id="e0d42-118">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="e0d42-119">0 ile 65.535 arasındaki</span><span class="sxs-lookup"><span data-stu-id="e0d42-119">0 to 65,535</span></span>|<span data-ttu-id="e0d42-120">16 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="e0d42-121">-2.147.483.648 için 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="e0d42-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="e0d42-122">İşaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="e0d42-123">0 için 4.294.967.295'e</span><span class="sxs-lookup"><span data-stu-id="e0d42-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="e0d42-124">32-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="e0d42-125">-9,223,372,036,854,775,808 için 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="e0d42-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="e0d42-126">İşaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="e0d42-127">0 için 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="e0d42-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="e0d42-128">64-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="e0d42-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="e0d42-129">Önceki tabloda her C# en soldaki sütun türü anahtar kelimedir karşılık gelen .NET türü için bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="e0d42-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="e0d42-130">Birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d42-130">They are interchangeable.</span></span> <span data-ttu-id="e0d42-131">Örneğin, aşağıdaki bildirimleri aynı türde değişkenleri bildirin:</span><span class="sxs-lookup"><span data-stu-id="e0d42-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="e0d42-132">Her bir integral türünün varsayılan değeri sıfırdır `0`.</span><span class="sxs-lookup"><span data-stu-id="e0d42-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="e0d42-133">Her bir integral türü olan `MinValue` ve `MaxValue` minimum ve maksimum değerin türü sağlayan sabitler.</span><span class="sxs-lookup"><span data-stu-id="e0d42-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="e0d42-134">Kullanım <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısı hiçbir üst işaretli bir tam sayı veya alt sınırlarını temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="e0d42-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="e0d42-135">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="e0d42-135">Integral literals</span></span>

<span data-ttu-id="e0d42-136">Tamsayı sabit değerleri olarak belirtilebilir *ondalık sabit değerleri*, *onaltılık değişmez değerler*, veya *ikili sabit dizeler*.</span><span class="sxs-lookup"><span data-stu-id="e0d42-136">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="e0d42-137">Her bir örneği aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0d42-137">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="e0d42-138">Ondalık sabit değerleri herhangi bir önek gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e0d42-138">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="e0d42-139">`x` Veya `X` önek belirten bir *onaltılık değişmez değeri*.</span><span class="sxs-lookup"><span data-stu-id="e0d42-139">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="e0d42-140">`b` Veya `B` önek belirten bir *ikili değişmez değer*.</span><span class="sxs-lookup"><span data-stu-id="e0d42-140">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="e0d42-141">Bildirimi `binaryLiteral` kullanımını gösteren `_` olarak bir *basamak ayıracı*.</span><span class="sxs-lookup"><span data-stu-id="e0d42-141">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="e0d42-142">Basamak ayırıcı, tüm sayısal değişmez değerleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d42-142">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="e0d42-143">İkili sabit değerler ve basamak ayıracı `_` başlayarak desteklenir C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="e0d42-143">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="e0d42-144">Değişmez değer soneki</span><span class="sxs-lookup"><span data-stu-id="e0d42-144">Literal suffixes</span></span>

<span data-ttu-id="e0d42-145">`l` Veya `L` sonekini belirtir, tam sayı sabiti olmalıdır `long` türü.</span><span class="sxs-lookup"><span data-stu-id="e0d42-145">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="e0d42-146">`ul` Veya `UL` sonekini belirtir `ulong` türü.</span><span class="sxs-lookup"><span data-stu-id="e0d42-146">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="e0d42-147">Varsa `L` soneki 9.223.372.036.854.775.807 büyük bir sabit değer ınternationalized (en büyük değerini `long`), değeri dönüştürülür `ulong` türü.</span><span class="sxs-lookup"><span data-stu-id="e0d42-147">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="e0d42-148">Bir tamsayı sabit değeri tarafından temsil edilen değeri aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, bir derleyici hatası [CS1021](../../misc/cs1021.md) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e0d42-148">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="e0d42-149">Küçük harf "l" sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0d42-149">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="e0d42-150">Ancak, bu bir derleyici uyarısı oluşturur çünkü "m" harfinin basamağı "1" ile kolaylıkla karıştırılır</span><span class="sxs-lookup"><span data-stu-id="e0d42-150">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="e0d42-151">"M" daha anlaşılır olması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0d42-151">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="e0d42-152">Bir integral sabit değerinin türü</span><span class="sxs-lookup"><span data-stu-id="e0d42-152">Type of an integral literal</span></span>

<span data-ttu-id="e0d42-153">Bir tamsayı sabit değeri sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:</span><span class="sxs-lookup"><span data-stu-id="e0d42-153">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="e0d42-154">Bir integral sabit değer atama ya da bir tür dönüştürme kullanarak varsayılandan daha küçük bir aralık türüyle dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0d42-154">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="e0d42-155">Bir integral sabit hazır değeri üzerinden ataması, bir tür dönüştürme veya son ekini kullanarak varsayılan değerinden daha büyük bir aralıkla türüne dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0d42-155">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="e0d42-156">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="e0d42-156">Conversions</span></span>

<span data-ttu-id="e0d42-157">Örtük bir dönüştürme (adlı bir *dönüştürme genişletme*) hedef türüne kaynak türündeki tüm değerleri depolayabileceği herhangi iki tamsayı türleri arasında.</span><span class="sxs-lookup"><span data-stu-id="e0d42-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="e0d42-158">Örneğin, örtük bir dönüştürme yoktur `int` için `long` çünkü aralığını `int` değerleri olan uygun bir alt kümesini `long`.</span><span class="sxs-lookup"><span data-stu-id="e0d42-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="e0d42-159">Bir küçük işeritsiz tamsayı türünü daha büyük bir işaretli tamsayı türüne örtük dönüşümlere vardır.</span><span class="sxs-lookup"><span data-stu-id="e0d42-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="e0d42-160">Herhangi bir kayan nokta türü için herhangi bir tamsayı türü arasında'örtük bir dönüştürme yoktur.</span><span class="sxs-lookup"><span data-stu-id="e0d42-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="e0d42-161">Herhangi işaretli integral türünden herhangi bir işaretsiz tamsayı türü için örtük dönüştürme vardır.</span><span class="sxs-lookup"><span data-stu-id="e0d42-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="e0d42-162">Örtük bir dönüştürme kaynak türden hedef türe tanımlı değil, bir tamsayı türü başka bir integral türe dönüştürmek için açık bir tür dönüştürme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0d42-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="e0d42-163">Bu adlı bir *daraltma dönüştürmesi*.</span><span class="sxs-lookup"><span data-stu-id="e0d42-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="e0d42-164">Dönüştürme veri kaybıyla sonuçlanabildiğinden açık durumda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0d42-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0d42-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d42-165">See also</span></span>

- [<span data-ttu-id="e0d42-166">C#dil belirtimi - tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="e0d42-166">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="e0d42-167">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="e0d42-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0d42-168">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="e0d42-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="e0d42-169">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="e0d42-169">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="e0d42-170">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e0d42-170">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="e0d42-171">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="e0d42-171">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="e0d42-172">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="e0d42-172">Numerics in .NET</span></span>](../../../standard/numerics.md)
