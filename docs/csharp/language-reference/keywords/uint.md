---
title: uint anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: e22468eea63ce082f2e9842e6ec307aba1888964
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660443"
---
# <a name="uint-c-reference"></a><span data-ttu-id="5b41e-102">uint (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b41e-102">uint (C# Reference)</span></span>

<span data-ttu-id="5b41e-103">`uint` Anahtar sözcüğü, boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="5b41e-104">Tür</span><span class="sxs-lookup"><span data-stu-id="5b41e-104">Type</span></span>|<span data-ttu-id="5b41e-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="5b41e-105">Range</span></span>|<span data-ttu-id="5b41e-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="5b41e-106">Size</span></span>|<span data-ttu-id="5b41e-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="5b41e-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`uint`|<span data-ttu-id="5b41e-108">0 için 4.294.967.295'e</span><span class="sxs-lookup"><span data-stu-id="5b41e-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="5b41e-109">32-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="5b41e-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|

<span data-ttu-id="5b41e-110">**Not** `uint` türü CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="5b41e-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="5b41e-111">Kullanım `int` mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="5b41e-111">Use `int` whenever possible.</span></span>

## <a name="literals"></a><span data-ttu-id="5b41e-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="5b41e-112">Literals</span></span>

<span data-ttu-id="5b41e-113">Bildirmek ve başlatmak bir `uint` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="5b41e-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="5b41e-114">Tamsayı sabit değeri aralığının dışında ise `uint` (diğer bir deyişle, bu ise kısa <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="5b41e-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="5b41e-115">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 3,000,000,000 eşit ve ikili sabit değerler atanır `uint` değerleri.</span><span class="sxs-lookup"><span data-stu-id="5b41e-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> <span data-ttu-id="5b41e-116">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="5b41e-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="5b41e-117">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="5b41e-117">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5b41e-118">İle başlayarak C# 7.0, birkaç özellik eklenmiştir okunabilirliği artırmak için:</span><span class="sxs-lookup"><span data-stu-id="5b41e-118">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="5b41e-119">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="5b41e-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="5b41e-120">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="5b41e-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="5b41e-121">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="5b41e-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="5b41e-122">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-122">Some examples are shown below.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

<span data-ttu-id="5b41e-123">Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="5b41e-124">Sonek `U` veya 'u' gösterir ya da bir `uint` veya `ulong`sayısal değerine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="5b41e-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="5b41e-125">Aşağıdaki örnekte `u` sonek işaretsiz bir tamsayı her iki türdeki belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="5b41e-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="5b41e-126">İlk değişmez değer olduğunu unutmayın bir `uint` değeri olduğundan küçüktür <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ikinci olmakla birlikte bir `ulong` değeri büyük olduğundan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b41e-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

<span data-ttu-id="5b41e-127">Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5b41e-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="5b41e-128">int</span><span class="sxs-lookup"><span data-stu-id="5b41e-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="5b41e-129">long</span><span class="sxs-lookup"><span data-stu-id="5b41e-129">long</span></span>](long.md)
4. [<span data-ttu-id="5b41e-130">ulong</span><span class="sxs-lookup"><span data-stu-id="5b41e-130">ulong</span></span>](ulong.md)

## <a name="conversions"></a><span data-ttu-id="5b41e-131">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="5b41e-131">Conversions</span></span>

<span data-ttu-id="5b41e-132">Önceden tanımlanmış bir örtük dönüştürme vardır `uint` için [uzun](long.md), [ulong](ulong.md), [float](float.md), [çift](double.md), veya [ ondalık](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="5b41e-132">There is a predefined implicit conversion from `uint` to [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span> <span data-ttu-id="5b41e-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5b41e-133">For example:</span></span>

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

<span data-ttu-id="5b41e-134">Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](byte.md), [ushort](ushort.md), veya [char](char.md) için `uint`.</span><span class="sxs-lookup"><span data-stu-id="5b41e-134">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), or [char](char.md) to `uint`.</span></span> <span data-ttu-id="5b41e-135">Aksi takdirde, bir dönüştürme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b41e-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="5b41e-136">Örneğin, aşağıdaki atama deyimi, bir yayın olmadan bir derleme hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="5b41e-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

<span data-ttu-id="5b41e-137">Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `uint`.</span><span class="sxs-lookup"><span data-stu-id="5b41e-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="5b41e-138">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5b41e-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

<span data-ttu-id="5b41e-139">Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](float.md) ve [çift](double.md).</span><span class="sxs-lookup"><span data-stu-id="5b41e-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="5b41e-140">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="5b41e-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5b41e-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5b41e-141">C# language specification</span></span>

<span data-ttu-id="5b41e-142">Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b41e-142">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="5b41e-143">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="5b41e-143">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b41e-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b41e-144">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="5b41e-145">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5b41e-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5b41e-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5b41e-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5b41e-147">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5b41e-147">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5b41e-148">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="5b41e-148">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="5b41e-149">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="5b41e-149">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="5b41e-150">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="5b41e-150">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="5b41e-151">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="5b41e-151">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)