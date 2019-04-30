---
title: ushort anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660404"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="335ce-102">ushort (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="335ce-102">ushort (C# Reference)</span></span>

<span data-ttu-id="335ce-103">`ushort` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tam sayı veri türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="335ce-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="335ce-104">Tür</span><span class="sxs-lookup"><span data-stu-id="335ce-104">Type</span></span>|<span data-ttu-id="335ce-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="335ce-105">Range</span></span>|<span data-ttu-id="335ce-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="335ce-106">Size</span></span>|<span data-ttu-id="335ce-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="335ce-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ushort`|<span data-ttu-id="335ce-108">0 ile 65.535 arasındaki</span><span class="sxs-lookup"><span data-stu-id="335ce-108">0 to 65,535</span></span>|<span data-ttu-id="335ce-109">16 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="335ce-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="335ce-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="335ce-110">Literals</span></span>

<span data-ttu-id="335ce-111">Bildirmek ve başlatmak bir `ushort` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="335ce-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="335ce-112">Tamsayı sabit değeri aralığının dışında ise `ushort` (diğer bir deyişle, bu ise kısa <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="335ce-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="335ce-113">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 65,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](int.md) için `ushort` değerleri.</span><span class="sxs-lookup"><span data-stu-id="335ce-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `ushort` values.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> <span data-ttu-id="335ce-114">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="335ce-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="335ce-115">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="335ce-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="335ce-116">İle başlayarak C# 7.0, birkaç özellik eklenmiştir okunabilirliği artırmak için:</span><span class="sxs-lookup"><span data-stu-id="335ce-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="335ce-117">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="335ce-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="335ce-118">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="335ce-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="335ce-119">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="335ce-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="335ce-120">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="335ce-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="335ce-121">Derleyici aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="335ce-121">Compiler overload resolution</span></span>

<span data-ttu-id="335ce-122">Aşırı yüklenmiş yöntemler çağırdığınızda, bir yayın kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="335ce-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="335ce-123">Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ushort` ve [int](int.md) parametreleri:</span><span class="sxs-lookup"><span data-stu-id="335ce-123">Consider, for example, the following overloaded methods that use `ushort` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

<span data-ttu-id="335ce-124">Kullanarak `ushort` atama doğru tür, örneğin çağrıldığını güvence altına alır:</span><span class="sxs-lookup"><span data-stu-id="335ce-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a><span data-ttu-id="335ce-125">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="335ce-125">Conversions</span></span>

<span data-ttu-id="335ce-126">Önceden tanımlanmış bir örtük dönüştürme vardır `ushort` için [int](int.md), [uint](uint.md), [uzun](long.md), [ulong](ulong.md), [float ](float.md), [çift](double.md), veya [ondalık](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="335ce-126">There is a predefined implicit conversion from `ushort` to [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="335ce-127">Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](byte.md) veya [char](char.md) için `ushort`.</span><span class="sxs-lookup"><span data-stu-id="335ce-127">There is a predefined implicit conversion from [byte](byte.md) or [char](char.md) to `ushort`.</span></span> <span data-ttu-id="335ce-128">Aksi halde bir tür dönüştürme açık bir dönüştürme gerçekleştirmek için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="335ce-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="335ce-129">Örneğin, aşağıdaki iki göz önünde bulundurun `ushort` değişkenleri `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="335ce-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>

```csharp
ushort x = 5, y = 12;
```

<span data-ttu-id="335ce-130">Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="335ce-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

<span data-ttu-id="335ce-131">Bu sorunu gidermek için bir tür dönüştürme kullanın:</span><span class="sxs-lookup"><span data-stu-id="335ce-131">To fix this problem, use a cast:</span></span>

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

<span data-ttu-id="335ce-132">Ancak hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:</span><span class="sxs-lookup"><span data-stu-id="335ce-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="335ce-133">Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `ushort`.</span><span class="sxs-lookup"><span data-stu-id="335ce-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="335ce-134">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="335ce-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

<span data-ttu-id="335ce-135">Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](float.md) ve [çift](double.md).</span><span class="sxs-lookup"><span data-stu-id="335ce-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="335ce-136">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="335ce-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="335ce-137">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="335ce-137">C# language specification</span></span>

<span data-ttu-id="335ce-138">Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="335ce-138">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="335ce-139">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="335ce-139">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="335ce-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="335ce-140">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="335ce-141">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="335ce-141">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="335ce-142">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="335ce-142">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="335ce-143">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="335ce-143">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="335ce-144">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="335ce-144">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="335ce-145">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="335ce-145">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="335ce-146">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="335ce-146">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="335ce-147">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="335ce-147">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
