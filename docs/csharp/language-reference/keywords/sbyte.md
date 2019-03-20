---
title: sbyte - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: 124ff282fc354699c68e0a17c64f911db2e25869
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185525"
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="fae00-102">sbyte (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fae00-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="fae00-103">`sbyte` boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="fae00-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="fae00-104">Tür</span><span class="sxs-lookup"><span data-stu-id="fae00-104">Type</span></span>|<span data-ttu-id="fae00-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="fae00-105">Range</span></span>|<span data-ttu-id="fae00-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="fae00-106">Size</span></span>|<span data-ttu-id="fae00-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="fae00-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`sbyte`|<span data-ttu-id="fae00-108">-128 ila 127 arasında</span><span class="sxs-lookup"><span data-stu-id="fae00-108">-128 to 127</span></span>|<span data-ttu-id="fae00-109">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="fae00-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="fae00-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="fae00-110">Literals</span></span>

<span data-ttu-id="fae00-111">Bildirmek ve başlatmak bir `sbyte` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="fae00-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>

<span data-ttu-id="fae00-112">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen-102 eşit ve ikili sabit dizeler gelen dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `sbyte` değerleri.</span><span class="sxs-lookup"><span data-stu-id="fae00-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>

[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]

> [!NOTE]
> <span data-ttu-id="fae00-113">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="fae00-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="fae00-114">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="fae00-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fae00-115">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="fae00-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>
- <span data-ttu-id="fae00-116">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="fae00-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="fae00-117">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="fae00-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="fae00-118">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="fae00-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="fae00-119">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fae00-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]

<span data-ttu-id="fae00-120">Tamsayı sabit değeri aralığının dışında ise `sbyte` (diğer bir deyişle, bu ise kısa <xref:System.SByte.MinValue?displayProperty=nameWithType> veya ondan <xref:System.SByte.MaxValue?displayProperty=nameWithType>, bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="fae00-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="fae00-121">Değişmez değer bir tamsayı sonek varsa, kendi içinde değerini gösterilebileceği bu tür ilk türüdür: [int](int.md), [uint](uint.md), [uzun](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="fae00-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="fae00-122">Bu örnekte, sayısal değişmez değerleri, yani, `0x9A` ve `0b10011010` aşıyor 156, değerini 32-bit imzalı tamsayı olarak yorumlanır <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fae00-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fae00-123">Bu nedenle, yayım işleciyle gereklidir ve atama oluşması gereken bir [denetlenmeyen](unchecked.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="fae00-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span>

## <a name="compiler-overload-resolution"></a><span data-ttu-id="fae00-124">Derleyici aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="fae00-124">Compiler overload resolution</span></span>

<span data-ttu-id="fae00-125">Çağırma yöntemleri aşırı yüklendiğinde bir yayın kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fae00-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="fae00-126">Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `sbyte` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:</span><span class="sxs-lookup"><span data-stu-id="fae00-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(sbyte b) {}
```

<span data-ttu-id="fae00-127">Kullanarak `sbyte` atama doğru tür, örneğin çağrıldığını güvence altına alır:</span><span class="sxs-lookup"><span data-stu-id="fae00-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>

```csharp
// Calling the method with the int parameter:
SampleMethod(5);
// Calling the method with the sbyte parameter:
SampleMethod((sbyte)5);
```

## <a name="conversions"></a><span data-ttu-id="fae00-128">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="fae00-128">Conversions</span></span>

<span data-ttu-id="fae00-129">Önceden tanımlanmış bir örtük dönüştürme vardır `sbyte` için [kısa](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift ](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="fae00-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>

<span data-ttu-id="fae00-130">Daha büyük depolama boyutu için sabit değerli olmayan sayısal türleri örtülü olarak dönüştürülemiyor `sbyte` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).</span><span class="sxs-lookup"><span data-stu-id="fae00-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="fae00-131">Örneğin, aşağıdaki iki göz önünde bulundurun `sbyte` değişkenleri `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="fae00-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>

```csharp
sbyte x = 10, y = 20;
```

<span data-ttu-id="fae00-132">Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="fae00-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>

```csharp
sbyte z = x + y;   // Error: conversion from int to sbyte
```

<span data-ttu-id="fae00-133">Bu sorunu gidermek için aşağıdaki örnekte olduğu gibi ifade dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="fae00-133">To fix this problem, cast the expression as in the following example:</span></span>

```csharp
sbyte z = (sbyte)(x + y);   // OK: explicit conversion
```

<span data-ttu-id="fae00-134">Ancak hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:</span><span class="sxs-lookup"><span data-stu-id="fae00-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
sbyte x = 10, y = 20;
int m = x + y;
long n = x + y;
```

<span data-ttu-id="fae00-135">Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="fae00-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="fae00-136">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="fae00-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
sbyte x = 3.0;         // Error: no implicit conversion from double
sbyte y = (sbyte)3.0;  // OK: explicit conversion
```

<span data-ttu-id="fae00-137">Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="fae00-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>

<span data-ttu-id="fae00-138">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="fae00-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fae00-139">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fae00-139">C# Language Specification</span></span>

<span data-ttu-id="fae00-140">Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="fae00-140">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="fae00-141">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="fae00-141">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="fae00-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fae00-142">See also</span></span>

- <xref:System.SByte>
- [<span data-ttu-id="fae00-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fae00-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="fae00-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fae00-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fae00-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fae00-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="fae00-146">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="fae00-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="fae00-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="fae00-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="fae00-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="fae00-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="fae00-149">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="fae00-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
