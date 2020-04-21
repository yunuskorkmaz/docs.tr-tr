---
title: İntegral sayısal türleri - C# referansı
description: İntegral sayısal türlerinher biri için aralığı, depolama boyutunu ve kullanımlarını öğrenin.
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
ms.openlocfilehash: 51ea64065ea8422e5885022105545780bc916f06
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739013"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="d24ba-103">İntegral sayısal türleri (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="d24ba-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="d24ba-104">*İntegral sayısal türleri,* tümsel sayılarını temsil emzdir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="d24ba-105">Tüm integral sayısal türleri [değer türleridir.](value-types.md)</span><span class="sxs-lookup"><span data-stu-id="d24ba-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="d24ba-106">Onlar da [basit türleri](value-types.md#built-in-value-types) ve [literals](#integer-literals)ile başharfolabilir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="d24ba-107">Tüm integral sayısal türleri [aritmetik,](../operators/arithmetic-operators.md) [bitwise mantıksal,](../operators/bitwise-and-shift-operators.md) [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d24ba-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="d24ba-108">İntegral türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="d24ba-108">Characteristics of the integral types</span></span>

<span data-ttu-id="d24ba-109">C# aşağıdaki önceden tanımlanmış integral türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="d24ba-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="d24ba-110">C# türü/anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="d24ba-110">C# type/keyword</span></span>|<span data-ttu-id="d24ba-111">Aralık</span><span class="sxs-lookup"><span data-stu-id="d24ba-111">Range</span></span>|<span data-ttu-id="d24ba-112">Boyut</span><span class="sxs-lookup"><span data-stu-id="d24ba-112">Size</span></span>|<span data-ttu-id="d24ba-113">.NET türü</span><span class="sxs-lookup"><span data-stu-id="d24ba-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="d24ba-114">-128 ile 127 arası</span><span class="sxs-lookup"><span data-stu-id="d24ba-114">-128 to 127</span></span>|<span data-ttu-id="d24ba-115">İmzalı 8 bit'lik bir sayı</span><span class="sxs-lookup"><span data-stu-id="d24ba-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="d24ba-116">0 ile 255 arasında</span><span class="sxs-lookup"><span data-stu-id="d24ba-116">0 to 255</span></span>|<span data-ttu-id="d24ba-117">İmzasız 8 bit'lik tümseci</span><span class="sxs-lookup"><span data-stu-id="d24ba-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="d24ba-118">-32.768 ile 32.767 arası</span><span class="sxs-lookup"><span data-stu-id="d24ba-118">-32,768 to 32,767</span></span>|<span data-ttu-id="d24ba-119">İmzalı 16 bit'lik bir sayı</span><span class="sxs-lookup"><span data-stu-id="d24ba-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="d24ba-120">0 ile 65.535 arası</span><span class="sxs-lookup"><span data-stu-id="d24ba-120">0 to 65,535</span></span>|<span data-ttu-id="d24ba-121">İmzasız 16 bit'lik bir sayı</span><span class="sxs-lookup"><span data-stu-id="d24ba-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="d24ba-122">-2.147.483.648 ila 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="d24ba-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="d24ba-123">İmzalı 32 bit'lik bir sayı</span><span class="sxs-lookup"><span data-stu-id="d24ba-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="d24ba-124">0 ile 4.294.967.295 arası</span><span class="sxs-lookup"><span data-stu-id="d24ba-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="d24ba-125">İmzasız 32 bit'lik tümseci</span><span class="sxs-lookup"><span data-stu-id="d24ba-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="d24ba-126">-9.223.372.036.854.775.808 ila 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="d24ba-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="d24ba-127">İmzalı 64 bit'lik bir sayı</span><span class="sxs-lookup"><span data-stu-id="d24ba-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="d24ba-128">0 ila 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="d24ba-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="d24ba-129">İmzasız 64 bit'lik bir sayı</span><span class="sxs-lookup"><span data-stu-id="d24ba-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="d24ba-130">Önceki tabloda, soldaki sütundaki her C# türü anahtar sözcüğü karşılık gelen .NET türüiçin bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="d24ba-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="d24ba-131">Değiştirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="d24ba-131">They are interchangeable.</span></span> <span data-ttu-id="d24ba-132">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="d24ba-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="d24ba-133">Her integral türünün varsayılan değeri `0`sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d24ba-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="d24ba-134">İntegral türlerinin `MinValue` `MaxValue` her biri, bu türün minimum ve maksimum değerini sağlayan sabitlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="d24ba-135">Üst <xref:System.Numerics.BigInteger?displayProperty=nameWithType> veya alt sınırları olmayan imzalı bir tamsayıyı temsil etmek için yapıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d24ba-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="d24ba-136">Sonda lı edebi</span><span class="sxs-lookup"><span data-stu-id="d24ba-136">Integer literals</span></span>

<span data-ttu-id="d24ba-137">İnteger literals olabilir</span><span class="sxs-lookup"><span data-stu-id="d24ba-137">Integer literals can be</span></span>

- <span data-ttu-id="d24ba-138">*ondalık*: herhangi bir önek olmadan</span><span class="sxs-lookup"><span data-stu-id="d24ba-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="d24ba-139">*hexadecimal*: `0x` veya `0X` önek ile</span><span class="sxs-lookup"><span data-stu-id="d24ba-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="d24ba-140">*ikili*: `0b` veya `0B` önek ile (C# 7.0 ve sonrası mevcuttur)</span><span class="sxs-lookup"><span data-stu-id="d24ba-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="d24ba-141">Aşağıdaki kod her birinin bir örneğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d24ba-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="d24ba-142">Yukarıdaki örnek, C# 7.0 ile başlayan desteklenen bir basamak `_` *ayırıcısı*olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d24ba-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="d24ba-143">Sayısal literals her türlü ile basamak ayırıcı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d24ba-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="d24ba-144">Bir sonda sının yazımı, sonek tarafından aşağıdaki gibi belirlenir:</span><span class="sxs-lookup"><span data-stu-id="d24ba-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="d24ba-145">Literal'ın sonekyoksa, türü, değerinin temsil edilebildiği aşağıdaki türlerden `int`ilkidir: , , `uint` `long`. `ulong`</span><span class="sxs-lookup"><span data-stu-id="d24ba-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="d24ba-146">`U` Eğer literal tarafından suffixed `u`veya , türü değeri temsil edilebilir aşağıdaki türlerden ilki: `uint`. `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d24ba-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="d24ba-147">`L` Eğer literal tarafından suffixed `l`veya , türü değeri temsil edilebilir aşağıdaki türlerden ilki: `long`. `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d24ba-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d24ba-148">Küçük harfi `l` sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d24ba-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="d24ba-149">Ancak, bu bir derleyici uyarısı `l` oluşturur, çünkü harf `1`basamakla karıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="d24ba-150">Netlik için kullanın. `L`</span><span class="sxs-lookup"><span data-stu-id="d24ba-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="d24ba-151">Eğer edebi olarak `UL`, , `Ul` `uL` `ul` `LU`, , `Lu`, `lU`, `lu`, , `ulong`veya , türü .</span><span class="sxs-lookup"><span data-stu-id="d24ba-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="d24ba-152">Bir tamsayı ile temsil edilen değer gerçek <xref:System.UInt64.MaxValue?displayProperty=nameWithType>değeri aşıyorsa, [cs1021](../../misc/cs1021.md) derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d24ba-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="d24ba-153">Bir bir insalı literal'In belirlenen `int` türü ve gerçek tarafından temsil edilen değer hedef türün aralığındaysa, `sbyte`değer `byte` `short`dolaylı `ushort` `uint`olarak `ulong`, , , , , veya :</span><span class="sxs-lookup"><span data-stu-id="d24ba-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="d24ba-154">Yukarıdaki örnekte de görüldüğü gibi, literal değeri hedef türü aralığında değilse, [cs0031](../../misc/cs0031.md) derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d24ba-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="d24ba-155">Bir tamsayı tarafından temsil edilen değeri, belirlenen edebi tür dışında türe dönüştürmek için bir döküm de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d24ba-155">You can also use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="d24ba-156">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="d24ba-156">Conversions</span></span>

<span data-ttu-id="d24ba-157">Herhangi bir integral sayısal türü diğer integral sayısal türe dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d24ba-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="d24ba-158">Hedef türü kaynak türün tüm değerlerini depolayabiliyorsa, dönüştürme örtülüdür.</span><span class="sxs-lookup"><span data-stu-id="d24ba-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="d24ba-159">Aksi takdirde, açık bir dönüştürme gerçekleştirmek için [bir döküm ifadesi](../operators/type-testing-and-cast.md#cast-expression) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d24ba-159">Otherwise, you need to use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span> <span data-ttu-id="d24ba-160">Daha fazla bilgi için yerleşik [sayısal dönüşümlere](numeric-conversions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d24ba-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d24ba-161">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d24ba-161">C# language specification</span></span>

<span data-ttu-id="d24ba-162">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="d24ba-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d24ba-163">İntegral tipleri</span><span class="sxs-lookup"><span data-stu-id="d24ba-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="d24ba-164">Sonda lı edebi</span><span class="sxs-lookup"><span data-stu-id="d24ba-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="d24ba-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d24ba-165">See also</span></span>

- [<span data-ttu-id="d24ba-166">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d24ba-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d24ba-167">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="d24ba-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d24ba-168">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="d24ba-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="d24ba-169">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="d24ba-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="d24ba-170">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="d24ba-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
