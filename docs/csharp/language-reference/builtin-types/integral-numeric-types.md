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
ms.openlocfilehash: 0a1ed01d9e6cb86ea177e8b947627f9dc02eedae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744219"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="65d6f-103">Tamsayı sayısal türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="65d6f-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="65d6f-104">**Tamsayı sayısal türleri** bir alt kümesidir **basit türler** ve ile başlatılabilir [ *değişmez değerleri*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="65d6f-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="65d6f-105">Tüm tamsayı türleri de değer türleridir.</span><span class="sxs-lookup"><span data-stu-id="65d6f-105">All integral types are also value types.</span></span>

<span data-ttu-id="65d6f-106">Tüm tamsayı sayısal türleri desteği [aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma ve eşitlik](../operators/equality-operators.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="65d6f-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="sizes-and-ranges"></a><span data-ttu-id="65d6f-107">Boyutları ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="65d6f-107">Sizes and ranges</span></span>

<span data-ttu-id="65d6f-108">Aşağıdaki tabloda, boyutları ve tam sayı türleri aralığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="65d6f-108">The following table shows the sizes and ranges of the integral types:</span></span>

|<span data-ttu-id="65d6f-109">Tür</span><span class="sxs-lookup"><span data-stu-id="65d6f-109">Type</span></span>|<span data-ttu-id="65d6f-110">Aralık</span><span class="sxs-lookup"><span data-stu-id="65d6f-110">Range</span></span>|<span data-ttu-id="65d6f-111">Boyut</span><span class="sxs-lookup"><span data-stu-id="65d6f-111">Size</span></span>|  
|----------|-----------|----------|  
|`sbyte`|<span data-ttu-id="65d6f-112">-128 ila 127 arasında</span><span class="sxs-lookup"><span data-stu-id="65d6f-112">-128 to 127</span></span>|<span data-ttu-id="65d6f-113">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-113">Signed 8-bit integer</span></span>|  
|`byte`|<span data-ttu-id="65d6f-114">0 ile 255 arasında</span><span class="sxs-lookup"><span data-stu-id="65d6f-114">0 to 255</span></span>|<span data-ttu-id="65d6f-115">İmzalanmamış 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-115">Unsigned 8-bit integer</span></span>|  
|`short`|<span data-ttu-id="65d6f-116">-32.768 için 32.767</span><span class="sxs-lookup"><span data-stu-id="65d6f-116">-32,768 to 32,767</span></span>|<span data-ttu-id="65d6f-117">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-117">Signed 16-bit integer</span></span>|  
|`ushort`|<span data-ttu-id="65d6f-118">0 ile 65.535 arasındaki</span><span class="sxs-lookup"><span data-stu-id="65d6f-118">0 to 65,535</span></span>|<span data-ttu-id="65d6f-119">16 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-119">Unsigned 16-bit integer</span></span>|  
|`int`|<span data-ttu-id="65d6f-120">-2.147.483.648 için 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="65d6f-120">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="65d6f-121">İşaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-121">Signed 32-bit integer</span></span>|  
|`uint`|<span data-ttu-id="65d6f-122">0 için 4.294.967.295'e</span><span class="sxs-lookup"><span data-stu-id="65d6f-122">0 to 4,294,967,295</span></span>|<span data-ttu-id="65d6f-123">32-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-123">Unsigned 32-bit integer</span></span>|  
|`long`|<span data-ttu-id="65d6f-124">-9,223,372,036,854,775,808 için 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="65d6f-124">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="65d6f-125">İşaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-125">Signed 64-bit integer</span></span>|  
|`ulong`|<span data-ttu-id="65d6f-126">0 için 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="65d6f-126">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="65d6f-127">64-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="65d6f-127">Unsigned 64-bit integer</span></span>|  

<span data-ttu-id="65d6f-128">Tüm tamsayı türleri için varsayılan değerdir `0`.</span><span class="sxs-lookup"><span data-stu-id="65d6f-128">The default value for all integral types is `0`.</span></span> <span data-ttu-id="65d6f-129">Her bir integral türü sabitleri adlı sahip `MinValue` ve `MaxValue` türü için minimum ve maksimum değeri.</span><span class="sxs-lookup"><span data-stu-id="65d6f-129">Each of the integral types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span>

<span data-ttu-id="65d6f-130">Kullanım <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısı hiçbir üst işaretli bir tam sayı veya alt sınırlarını temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="65d6f-130">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="65d6f-131">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="65d6f-131">Integral literals</span></span>

<span data-ttu-id="65d6f-132">Tamsayı sabit değerleri olarak belirtilebilir *ondalık sabit değerleri*, *onaltılık değişmez değerler*, veya *ikili sabit dizeler*.</span><span class="sxs-lookup"><span data-stu-id="65d6f-132">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="65d6f-133">Her bir örneği aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="65d6f-133">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="65d6f-134">Ondalık sabit değerleri herhangi bir önek gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="65d6f-134">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="65d6f-135">`x` Veya `X` önek belirten bir *onaltılık değişmez değeri*.</span><span class="sxs-lookup"><span data-stu-id="65d6f-135">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="65d6f-136">`b` Veya `B` önek belirten bir *ikili değişmez değer*.</span><span class="sxs-lookup"><span data-stu-id="65d6f-136">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="65d6f-137">Bildirimi `binaryLiteral` kullanımını gösteren `_` olarak bir *basamak ayıracı*.</span><span class="sxs-lookup"><span data-stu-id="65d6f-137">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="65d6f-138">Basamak ayırıcı, tüm sayısal değişmez değerleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65d6f-138">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="65d6f-139">İkili sabit değerler ve basamak ayıracı `_` başlayarak desteklenir C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="65d6f-139">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="65d6f-140">Değişmez değer soneki</span><span class="sxs-lookup"><span data-stu-id="65d6f-140">Literal suffixes</span></span> 

<span data-ttu-id="65d6f-141">`l` Veya `L` sonekini belirtir, tam sayı sabiti olmalıdır `long` türü.</span><span class="sxs-lookup"><span data-stu-id="65d6f-141">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="65d6f-142">`ul` Veya `UL` sonekini belirtir `ulong` türü.</span><span class="sxs-lookup"><span data-stu-id="65d6f-142">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="65d6f-143">Varsa `L` soneki 9.223.372.036.854.775.807 büyük bir sabit değer ınternationalized (en büyük değerini `long`), değeri dönüştürülür `ulong` türü.</span><span class="sxs-lookup"><span data-stu-id="65d6f-143">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="65d6f-144">Bir tamsayı sabit değeri tarafından temsil edilen değeri aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, bir derleyici hatası [CS1021](../../misc/cs1021.md) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="65d6f-144">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="65d6f-145">Küçük harf "l" sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d6f-145">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="65d6f-146">Ancak, bu bir derleyici uyarısı oluşturur çünkü "m" harfinin basamağı "1" ile kolaylıkla karıştırılır</span><span class="sxs-lookup"><span data-stu-id="65d6f-146">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="65d6f-147">"M" daha anlaşılır olması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="65d6f-147">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="65d6f-148">Bir integral sabit değerinin türü</span><span class="sxs-lookup"><span data-stu-id="65d6f-148">Type of an integral literal</span></span>

<span data-ttu-id="65d6f-149">Bir tamsayı sabit değeri sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:</span><span class="sxs-lookup"><span data-stu-id="65d6f-149">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="65d6f-150">Bir integral sabit değer atama ya da bir tür dönüştürme kullanarak varsayılandan daha küçük bir aralık türüyle dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65d6f-150">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="65d6f-151">Bir integral sabit hazır değeri üzerinden ataması, bir tür dönüştürme veya son ekini kullanarak varsayılan değerinden daha büyük bir aralıkla türüne dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65d6f-151">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="65d6f-152">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="65d6f-152">Conversions</span></span>

<span data-ttu-id="65d6f-153">Örtük bir dönüştürme (adlı bir *dönüştürme genişletme*) hedef türüne kaynak türündeki tüm değerleri depolayabileceği herhangi iki tamsayı türleri arasında.</span><span class="sxs-lookup"><span data-stu-id="65d6f-153">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="65d6f-154">Örneğin, örtük bir dönüştürme yoktur `int` için `long` çünkü aralığını `int` değerleri olan uygun bir alt kümesini `long`.</span><span class="sxs-lookup"><span data-stu-id="65d6f-154">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="65d6f-155">Bir küçük işeritsiz tamsayı türünü daha büyük bir işaretli tamsayı türüne örtük dönüşümlere vardır.</span><span class="sxs-lookup"><span data-stu-id="65d6f-155">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="65d6f-156">Herhangi bir kayan nokta türü için herhangi bir tamsayı türü arasında'örtük bir dönüştürme yoktur.</span><span class="sxs-lookup"><span data-stu-id="65d6f-156">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="65d6f-157">Herhangi işaretli integral türünden herhangi bir işaretsiz tamsayı türü için örtük dönüştürme vardır.</span><span class="sxs-lookup"><span data-stu-id="65d6f-157">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="65d6f-158">Örtük bir dönüştürme kaynak türden hedef türe tanımlı değil, bir tamsayı türü başka bir integral türe dönüştürmek için açık bir tür dönüştürme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65d6f-158">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="65d6f-159">Bu adlı bir *daraltma dönüştürmesi*.</span><span class="sxs-lookup"><span data-stu-id="65d6f-159">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="65d6f-160">Dönüştürme veri kaybıyla sonuçlanabildiğinden açık durumda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="65d6f-160">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="65d6f-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65d6f-161">See also</span></span>

- [<span data-ttu-id="65d6f-162">C#dil belirtimi - tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="65d6f-162">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="65d6f-163">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="65d6f-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="65d6f-164">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="65d6f-164">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="65d6f-165">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="65d6f-165">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="65d6f-166">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="65d6f-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="65d6f-167">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="65d6f-167">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="65d6f-168">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="65d6f-168">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
