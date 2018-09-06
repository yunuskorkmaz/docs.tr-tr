---
title: ushort (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 2f038378e1af85520cea13d914da69dfcb054ac0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857306"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="a1402-102">ushort (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a1402-102">ushort (C# Reference)</span></span>

<span data-ttu-id="a1402-103">`ushort` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tam sayı veri türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1402-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="a1402-104">Tür</span><span class="sxs-lookup"><span data-stu-id="a1402-104">Type</span></span>|<span data-ttu-id="a1402-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="a1402-105">Range</span></span>|<span data-ttu-id="a1402-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="a1402-106">Size</span></span>|<span data-ttu-id="a1402-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a1402-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="a1402-108">0 ile 65.535 arasındaki</span><span class="sxs-lookup"><span data-stu-id="a1402-108">0 to 65,535</span></span>|<span data-ttu-id="a1402-109">16 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="a1402-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="a1402-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a1402-110">Literals</span></span>  

<span data-ttu-id="a1402-111">Bildirmek ve başlatmak bir `ushort` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="a1402-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="a1402-112">Tamsayı sabit değeri aralığının dışında ise `ushort` (diğer bir deyişle, bu ise kısa <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="a1402-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="a1402-113">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 65,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `ushort` değerleri.</span><span class="sxs-lookup"><span data-stu-id="a1402-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="a1402-114">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a1402-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="a1402-115">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="a1402-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a1402-116">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="a1402-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="a1402-117">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="a1402-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="a1402-118">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="a1402-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="a1402-119">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="a1402-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="a1402-120">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1402-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="a1402-121">Derleyici aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="a1402-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="a1402-122">Aşırı yüklenmiş yöntemler çağırdığınızda, bir yayın kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1402-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="a1402-123">Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ushort` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:</span><span class="sxs-lookup"><span data-stu-id="a1402-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="a1402-124">Kullanarak `ushort` atama doğru tür, örneğin çağrıldığını güvence altına alır:</span><span class="sxs-lookup"><span data-stu-id="a1402-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="a1402-125">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="a1402-125">Conversions</span></span>  
 <span data-ttu-id="a1402-126">Önceden tanımlanmış bir örtük dönüştürme vardır `ushort` için [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float ](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="a1402-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="a1402-127">Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](../../../csharp/language-reference/keywords/byte.md) veya [char](../../../csharp/language-reference/keywords/char.md) için `ushort`.</span><span class="sxs-lookup"><span data-stu-id="a1402-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="a1402-128">Aksi halde bir tür dönüştürme açık bir dönüştürme gerçekleştirmek için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1402-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="a1402-129">Örneğin, aşağıdaki iki göz önünde bulundurun `ushort` değişkenleri `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="a1402-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="a1402-130">Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="a1402-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="a1402-131">Bu sorunu gidermek için bir tür dönüştürme kullanın:</span><span class="sxs-lookup"><span data-stu-id="a1402-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="a1402-132">Ancak hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:</span><span class="sxs-lookup"><span data-stu-id="a1402-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="a1402-133">Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `ushort`.</span><span class="sxs-lookup"><span data-stu-id="a1402-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="a1402-134">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a1402-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="a1402-135">Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="a1402-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="a1402-136">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="a1402-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1402-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a1402-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1402-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1402-138">See Also</span></span>

- <xref:System.UInt16>  
- [<span data-ttu-id="a1402-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a1402-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a1402-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a1402-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a1402-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a1402-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a1402-142">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="a1402-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="a1402-143">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="a1402-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="a1402-144">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="a1402-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="a1402-145">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="a1402-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
