---
title: ushort (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 03638893978779fcfd34544363d935fa5e609481
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288830"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="95702-102">ushort (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="95702-102">ushort (C# Reference)</span></span>

<span data-ttu-id="95702-103">`ushort` Anahtar sözcüğü değerleri aşağıdaki tabloda gösterilen aralığı ve boyutu göre depolayan bir tam sayı veri türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="95702-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="95702-104">Tür</span><span class="sxs-lookup"><span data-stu-id="95702-104">Type</span></span>|<span data-ttu-id="95702-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="95702-105">Range</span></span>|<span data-ttu-id="95702-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="95702-106">Size</span></span>|<span data-ttu-id="95702-107">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="95702-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="95702-108">0 ile 65.535 arasındaki</span><span class="sxs-lookup"><span data-stu-id="95702-108">0 to 65,535</span></span>|<span data-ttu-id="95702-109">İmzasız 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="95702-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="95702-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="95702-110">Literals</span></span>  

<span data-ttu-id="95702-111">Bildirme ve başlatma bir `ushort` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="95702-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="95702-112">Değişmez değer tamsayı aralığı dışında ise `ushort` (diğer bir deyişle, bu ise değerinden <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="95702-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="95702-113">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 65,034 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `ushort` değerleri.</span><span class="sxs-lookup"><span data-stu-id="95702-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="95702-114">Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="95702-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="95702-115">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="95702-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="95702-116">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="95702-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="95702-117">C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="95702-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="95702-118">C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="95702-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="95702-119">Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="95702-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="95702-120">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="95702-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="95702-121">Derleyici aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="95702-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="95702-122">Aşırı yüklenmiş yöntemler çağırdığınızda bir cast kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95702-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="95702-123">Örneğin, aşağıdaki aşırı kullanan yöntemleri düşünün `ushort` ve [int](../../../csharp/language-reference/keywords/int.md) Parametreler:</span><span class="sxs-lookup"><span data-stu-id="95702-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="95702-124">Kullanarak `ushort` cast garanti doğru türde, örneğin çağrıldığından emin:</span><span class="sxs-lookup"><span data-stu-id="95702-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="95702-125">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="95702-125">Conversions</span></span>  
 <span data-ttu-id="95702-126">Önceden tanımlanmış bir örtük dönüştürme `ushort` için [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float ](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="95702-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="95702-127">Önceden tanımlanmış bir örtük dönüştürme [bayt](../../../csharp/language-reference/keywords/byte.md) veya [char](../../../csharp/language-reference/keywords/char.md) için `ushort`.</span><span class="sxs-lookup"><span data-stu-id="95702-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="95702-128">Aksi halde bir cast açık bir dönüştürme gerçekleştirmek için kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95702-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="95702-129">Örneğin, aşağıdaki iki göz önünde bulundurun `ushort` değişkenleri `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="95702-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="95702-130">Atama işlecinin sağ tarafında aritmetik ifade değerlendiren çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="95702-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="95702-131">Bu sorunu gidermek için bir atama kullanın:</span><span class="sxs-lookup"><span data-stu-id="95702-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="95702-132">Ancak hedef değişkeni depolama boyutu ile aynı veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak için mümkündür:</span><span class="sxs-lookup"><span data-stu-id="95702-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="95702-133">Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `ushort`.</span><span class="sxs-lookup"><span data-stu-id="95702-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="95702-134">Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="95702-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="95702-135">Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="95702-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="95702-136">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="95702-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="95702-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="95702-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95702-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95702-138">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="95702-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="95702-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="95702-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95702-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95702-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95702-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="95702-142">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="95702-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="95702-143">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="95702-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="95702-144">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="95702-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="95702-145">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="95702-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
