---
title: "sbyte (C# Başvurusu)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 010ac98f523eca5929100f7c51b8b6ef5d11de30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="2b98c-102">sbyte (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b98c-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="2b98c-103">`sbyte`Aşağıdaki tabloda gösterilen aralığı ve boyutu göre değerleri depolayan tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b98c-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="2b98c-104">Tür</span><span class="sxs-lookup"><span data-stu-id="2b98c-104">Type</span></span>|<span data-ttu-id="2b98c-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="2b98c-105">Range</span></span>|<span data-ttu-id="2b98c-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="2b98c-106">Size</span></span>|<span data-ttu-id="2b98c-107">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="2b98c-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="2b98c-108">-128 ile 127</span><span class="sxs-lookup"><span data-stu-id="2b98c-108">-128 to 127</span></span>|<span data-ttu-id="2b98c-109">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="2b98c-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="2b98c-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="2b98c-110">Literals</span></span>  

<span data-ttu-id="2b98c-111">Bildirme ve başlatma bir `sbyte` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# 7 için değişmez değer bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="2b98c-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="2b98c-112">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil-102 tamsayılar eşit ve ikili değişmez değerleri, gelen dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `sbyte` değerleri.</span><span class="sxs-lookup"><span data-stu-id="2b98c-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="2b98c-113">Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="2b98c-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="2b98c-114">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="2b98c-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2b98c-115">C# 7 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="2b98c-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="2b98c-116">C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="2b98c-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="2b98c-117">C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2b98c-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="2b98c-118">Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="2b98c-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="2b98c-119">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b98c-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="2b98c-120">Değişmez değer tamsayı aralığı dışında ise `sbyte` (diğer bir deyişle, bu ise değerinden <xref:System.SByte.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.SByte.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="2b98c-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="2b98c-121">Değişmez değer bir tamsayı sonek olduğunda, kendi içinde değerini temsil bu tür ilk türüdür: [int](int.md), [uint](uint.md), [uzun](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="2b98c-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="2b98c-122">Bu, bu örnekte, sayısal değişmez değerleri anlamına `0x9A` ve `0b10011010` 32 bit imzalı tamsayılar aşıyor 156, değerini olarak yorumlanır <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b98c-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2b98c-123">Bu nedenle atama işleci gerekli değildir ve atama oluşması gereken bir [denetlenmeyen](unchecked.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="2b98c-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="2b98c-124">Derleyici aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="2b98c-124">Compiler overload resolution</span></span>

 <span data-ttu-id="2b98c-125">Arama aşırı yüklenmiş yöntemler bir cast kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b98c-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="2b98c-126">Örneğin, aşağıdaki aşırı kullanan yöntemleri düşünün `sbyte` ve [int](../../../csharp/language-reference/keywords/int.md) Parametreler:</span><span class="sxs-lookup"><span data-stu-id="2b98c-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="2b98c-127">Kullanarak `sbyte` cast garanti doğru türde, örneğin çağrıldığından emin:</span><span class="sxs-lookup"><span data-stu-id="2b98c-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="2b98c-128">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2b98c-128">Conversions</span></span>  
 <span data-ttu-id="2b98c-129">Önceden tanımlanmış bir örtük dönüştürme `sbyte` için [kısa](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift ](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="2b98c-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="2b98c-130">Daha büyük depolama boyutu nonliteral sayısal türlerini örtük olarak dönüştürülemiyor `sbyte` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).</span><span class="sxs-lookup"><span data-stu-id="2b98c-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="2b98c-131">Örneğin, aşağıdaki iki göz önünde bulundurun `sbyte` değişkenleri `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="2b98c-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="2b98c-132">Atama işlecinin sağ tarafında aritmetik ifade değerlendiren çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="2b98c-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="2b98c-133">Bu sorunu gidermek için aşağıdaki örnekteki gibi ifade atayın:</span><span class="sxs-lookup"><span data-stu-id="2b98c-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="2b98c-134">Ancak hedef değişkeni depolama boyutu ile aynı veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak için mümkündür:</span><span class="sxs-lookup"><span data-stu-id="2b98c-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="2b98c-135">Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="2b98c-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="2b98c-136">Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2b98c-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="2b98c-137">Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="2b98c-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="2b98c-138">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="2b98c-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2b98c-139">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2b98c-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b98c-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b98c-140">See Also</span></span>  
 <xref:System.SByte>  
 [<span data-ttu-id="2b98c-141">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b98c-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2b98c-142">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b98c-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b98c-143">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2b98c-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2b98c-144">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="2b98c-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="2b98c-145">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="2b98c-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="2b98c-146">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="2b98c-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="2b98c-147">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="2b98c-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
