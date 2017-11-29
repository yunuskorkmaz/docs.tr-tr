---
title: "uint (C# Başvurusu)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords: uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d32f7146d1f9e13d8cf0f275f4fd78b693b09d31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="uint-c-reference"></a><span data-ttu-id="38b90-102">uint (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="38b90-102">uint (C# Reference)</span></span>

<span data-ttu-id="38b90-103">`uint` Anahtar sözcüğü değerleri aşağıdaki tabloda gösterilen aralığı ve boyutu göre depolayan bir tam sayı türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="38b90-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="38b90-104">Tür</span><span class="sxs-lookup"><span data-stu-id="38b90-104">Type</span></span>|<span data-ttu-id="38b90-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="38b90-105">Range</span></span>|<span data-ttu-id="38b90-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="38b90-106">Size</span></span>|<span data-ttu-id="38b90-107">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="38b90-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="38b90-108">0 için 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="38b90-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="38b90-109">İmzasız 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="38b90-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="38b90-110">**Not** `uint` türü CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="38b90-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="38b90-111">Kullanım `int` mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="38b90-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="38b90-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="38b90-112">Literals</span></span>  

<span data-ttu-id="38b90-113">Bildirme ve başlatma bir `uint` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# 7 için değişmez değer bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="38b90-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="38b90-114">Değişmez değer tamsayı aralığı dışında ise `uint` (diğer bir deyişle, bu ise değerinden <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="38b90-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="38b90-115">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 3,000,000,000 tamsayılar eşit ve ikili değişmez değerler atanır `uint` değerleri.</span><span class="sxs-lookup"><span data-stu-id="38b90-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="38b90-116">Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="38b90-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="38b90-117">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="38b90-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="38b90-118">C# 7 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="38b90-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="38b90-119">C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="38b90-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="38b90-120">C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="38b90-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="38b90-121">Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="38b90-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="38b90-122">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38b90-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="38b90-123">Tamsayı değişmez değerleri türü gösterir bir sonek de içerir.</span><span class="sxs-lookup"><span data-stu-id="38b90-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="38b90-124">Sonek `U` veya 'u' gösterir ya da bir `uint` veya `ulong`değişmez değeri sayısal değerini bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="38b90-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="38b90-125">Aşağıdaki örnek kullanır `u` işaretsiz tamsayıya her iki türdeki belirtmek için soneki.</span><span class="sxs-lookup"><span data-stu-id="38b90-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="38b90-126">İlk sabit olduğuna dikkat edin bir `uint` değeri olduğu için değerinden <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ikinci bir `ulong` değerini daha büyük olduğu için <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38b90-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="38b90-127">Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:</span><span class="sxs-lookup"><span data-stu-id="38b90-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="38b90-128">int</span><span class="sxs-lookup"><span data-stu-id="38b90-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="38b90-129">uzun</span><span class="sxs-lookup"><span data-stu-id="38b90-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="38b90-130">ulong</span><span class="sxs-lookup"><span data-stu-id="38b90-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="38b90-131">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="38b90-131">Conversions</span></span>  
 <span data-ttu-id="38b90-132">Önceden tanımlanmış bir örtük dönüştürme `uint` için [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="38b90-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="38b90-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="38b90-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="38b90-134">Önceden tanımlanmış bir örtük dönüştürme [bayt](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `uint`.</span><span class="sxs-lookup"><span data-stu-id="38b90-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="38b90-135">Aksi halde, bir cast kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38b90-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="38b90-136">Örneğin, aşağıdaki atama deyimi bir cast derleme hatasız üretir:</span><span class="sxs-lookup"><span data-stu-id="38b90-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="38b90-137">Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `uint`.</span><span class="sxs-lookup"><span data-stu-id="38b90-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="38b90-138">Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="38b90-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="38b90-139">Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="38b90-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="38b90-140">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="38b90-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="38b90-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="38b90-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38b90-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38b90-142">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="38b90-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="38b90-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="38b90-144">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="38b90-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="38b90-145">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="38b90-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="38b90-146">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="38b90-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="38b90-147">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="38b90-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="38b90-148">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="38b90-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="38b90-149">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="38b90-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
