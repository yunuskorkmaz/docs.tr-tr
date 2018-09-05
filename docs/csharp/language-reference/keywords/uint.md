---
title: uint (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
ms.openlocfilehash: e75abf8ac356eaed6c54dd0309316fb6755bf635
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661275"
---
# <a name="uint-c-reference"></a><span data-ttu-id="76265-102">uint (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="76265-102">uint (C# Reference)</span></span>

<span data-ttu-id="76265-103">`uint` Anahtar sözcüğü, boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="76265-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="76265-104">Tür</span><span class="sxs-lookup"><span data-stu-id="76265-104">Type</span></span>|<span data-ttu-id="76265-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="76265-105">Range</span></span>|<span data-ttu-id="76265-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="76265-106">Size</span></span>|<span data-ttu-id="76265-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="76265-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="76265-108">0 için 4.294.967.295'e</span><span class="sxs-lookup"><span data-stu-id="76265-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="76265-109">32-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="76265-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="76265-110">**Not** `uint` türü CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="76265-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="76265-111">Kullanım `int` mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="76265-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="76265-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="76265-112">Literals</span></span>  

<span data-ttu-id="76265-113">Bildirmek ve başlatmak bir `uint` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="76265-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="76265-114">Tamsayı sabit değeri aralığının dışında ise `uint` (diğer bir deyişle, bu ise kısa <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="76265-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="76265-115">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 3,000,000,000 eşit ve ikili sabit değerler atanır `uint` değerleri.</span><span class="sxs-lookup"><span data-stu-id="76265-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="76265-116">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="76265-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="76265-117">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="76265-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="76265-118">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="76265-118">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="76265-119">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="76265-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="76265-120">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="76265-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="76265-121">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="76265-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="76265-122">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="76265-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="76265-123">Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="76265-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="76265-124">Sonek `U` veya 'u' gösterir ya da bir `uint` veya `ulong`sayısal değerine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="76265-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="76265-125">Aşağıdaki örnekte `u` sonek işaretsiz bir tamsayı her iki türdeki belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="76265-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="76265-126">İlk değişmez değer olduğunu unutmayın bir `uint` değeri olduğundan küçüktür <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ikinci olmakla birlikte bir `ulong` değeri büyük olduğundan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76265-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="76265-127">Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="76265-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="76265-128">int</span><span class="sxs-lookup"><span data-stu-id="76265-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="76265-129">long</span><span class="sxs-lookup"><span data-stu-id="76265-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="76265-130">ulong</span><span class="sxs-lookup"><span data-stu-id="76265-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="76265-131">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="76265-131">Conversions</span></span>  
 <span data-ttu-id="76265-132">Önceden tanımlanmış bir örtük dönüştürme vardır `uint` için [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="76265-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="76265-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="76265-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="76265-134">Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `uint`.</span><span class="sxs-lookup"><span data-stu-id="76265-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="76265-135">Aksi takdirde, bir dönüştürme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="76265-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="76265-136">Örneğin, aşağıdaki atama deyimi, bir yayın olmadan bir derleme hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="76265-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="76265-137">Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `uint`.</span><span class="sxs-lookup"><span data-stu-id="76265-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="76265-138">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="76265-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="76265-139">Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="76265-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="76265-140">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="76265-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="76265-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="76265-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76265-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76265-142">See Also</span></span>

- <xref:System.UInt32>  
- [<span data-ttu-id="76265-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="76265-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="76265-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="76265-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="76265-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="76265-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="76265-146">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="76265-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="76265-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="76265-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="76265-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="76265-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="76265-149">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="76265-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
