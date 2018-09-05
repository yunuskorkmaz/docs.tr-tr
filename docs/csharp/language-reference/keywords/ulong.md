---
title: ulong (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: a68ebe1d382bf39e945d333a728fad66934fd286
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505183"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="892fe-102">ulong (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="892fe-102">ulong (C# Reference)</span></span>

<span data-ttu-id="892fe-103">`ulong` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="892fe-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="892fe-104">Tür</span><span class="sxs-lookup"><span data-stu-id="892fe-104">Type</span></span>|<span data-ttu-id="892fe-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="892fe-105">Range</span></span>|<span data-ttu-id="892fe-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="892fe-106">Size</span></span>|<span data-ttu-id="892fe-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="892fe-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="892fe-108">0 için 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="892fe-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="892fe-109">64-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="892fe-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="892fe-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="892fe-110">Literals</span></span>  

<span data-ttu-id="892fe-111">Bildirmek ve başlatmak bir `ulong` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="892fe-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="892fe-112">Tamsayı sabit değeri aralığının dışında ise `ulong` (diğer bir deyişle, bu ise kısa <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="892fe-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="892fe-113">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 7,934,076,125 eşit ve ikili sabit değerler atanır `ulong` değerleri.</span><span class="sxs-lookup"><span data-stu-id="892fe-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> <span data-ttu-id="892fe-114">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="892fe-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="892fe-115">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="892fe-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="892fe-116">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="892fe-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="892fe-117">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="892fe-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="892fe-118">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="892fe-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="892fe-119">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="892fe-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="892fe-120">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="892fe-120">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="892fe-121">Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="892fe-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="892fe-122">Sonek `UL` veya `ul` sayısal bir değişmez değer olarak kesin bir şekilde tanımlayan bir `ulong` değeri.</span><span class="sxs-lookup"><span data-stu-id="892fe-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="892fe-123">`L` Soneki gösterir bir `ulong` değişmez değer aşarsa <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="892fe-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="892fe-124">Ve `U` veya `u` soneki gösterir bir `ulong` değişmez değer aşarsa <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="892fe-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="892fe-125">Aşağıdaki örnekte `ul` sonek uzun tamsayı belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="892fe-125">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="892fe-126">Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="892fe-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="892fe-127">int</span><span class="sxs-lookup"><span data-stu-id="892fe-127">int</span></span>](int.md)
2. [<span data-ttu-id="892fe-128">uint</span><span class="sxs-lookup"><span data-stu-id="892fe-128">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="892fe-129">long</span><span class="sxs-lookup"><span data-stu-id="892fe-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="892fe-130">Derleyici aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="892fe-130">Compiler overload resolution</span></span>
  
 <span data-ttu-id="892fe-131">Bir ortak soneki aşırı yüklenmiş yöntem çağırma işleviyle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="892fe-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="892fe-132">Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ulong` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:</span><span class="sxs-lookup"><span data-stu-id="892fe-132">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="892fe-133">Bir sonek ile kullanarak `ulong` parametresi doğru türde, örneğin çağrıldığını güvence altına alır:</span><span class="sxs-lookup"><span data-stu-id="892fe-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="892fe-134">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="892fe-134">Conversions</span></span>  
 <span data-ttu-id="892fe-135">Önceden tanımlanmış bir örtük dönüştürme vardır `ulong` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="892fe-135">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="892fe-136">Örtülü dönüştürme olmaz yoktur `ulong` için herhangi bir tamsayı türü.</span><span class="sxs-lookup"><span data-stu-id="892fe-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="892fe-137">Örneğin, aşağıdaki deyim, açık atama olmadan bir derleme hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="892fe-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="892fe-138">Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `ulong`.</span><span class="sxs-lookup"><span data-stu-id="892fe-138">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="892fe-139">Ayrıca, kayan nokta türlerinden örtük dönüştürme vardır `ulong`.</span><span class="sxs-lookup"><span data-stu-id="892fe-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="892fe-140">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="892fe-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="892fe-141">Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="892fe-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="892fe-142">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="892fe-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="892fe-143">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="892fe-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="892fe-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="892fe-144">See Also</span></span>

- <xref:System.UInt64>  
- [<span data-ttu-id="892fe-145">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="892fe-145">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="892fe-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="892fe-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="892fe-147">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="892fe-147">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="892fe-148">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="892fe-148">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="892fe-149">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="892fe-149">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="892fe-150">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="892fe-150">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="892fe-151">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="892fe-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
