---
title: int (C# Başvurusu)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3e82dd195252a8c55e4ba7b18b657b341553047
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="int-c-reference"></a><span data-ttu-id="d1cd2-102">int (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d1cd2-102">int (C# Reference)</span></span>

<span data-ttu-id="d1cd2-103">`int` Aşağıdaki tabloda gösterilen aralığı ve boyutu göre değerleri depolayan tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="d1cd2-104">Tür</span><span class="sxs-lookup"><span data-stu-id="d1cd2-104">Type</span></span>|<span data-ttu-id="d1cd2-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="d1cd2-105">Range</span></span>|<span data-ttu-id="d1cd2-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="d1cd2-106">Size</span></span>|<span data-ttu-id="d1cd2-107">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="d1cd2-107">.NET Framework type</span></span>|<span data-ttu-id="d1cd2-108">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="d1cd2-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="d1cd2-109">-2,147,483,648 için 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="d1cd2-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="d1cd2-110">işaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="d1cd2-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="d1cd2-111">0</span><span class="sxs-lookup"><span data-stu-id="d1cd2-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="d1cd2-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="d1cd2-112">Literals</span></span>  
 
<span data-ttu-id="d1cd2-113">Bildirme ve başlatma bir `int` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="d1cd2-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="d1cd2-114">Değişmez değer tamsayı aralığı dışında ise `int` (diğer bir deyişle, bu ise değerinden <xref:System.Int32.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="d1cd2-115">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 90,946 tamsayılar eşit ve ikili değişmez değerler atanır `int` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="d1cd2-116">Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="d1cd2-117">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="d1cd2-118">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-118">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="d1cd2-119">C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="d1cd2-120">C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="d1cd2-121">Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="d1cd2-122">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-122">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="d1cd2-123">Tamsayı değişmez değerleri de dahil edebilirsiniz tür gösterir bir sonek gösterir hiçbir soneki olsa `int` türü.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-123">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="d1cd2-124">Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:</span><span class="sxs-lookup"><span data-stu-id="d1cd2-124">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="d1cd2-125">uint</span><span class="sxs-lookup"><span data-stu-id="d1cd2-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="d1cd2-126">long</span><span class="sxs-lookup"><span data-stu-id="d1cd2-126">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="d1cd2-127">ulong</span><span class="sxs-lookup"><span data-stu-id="d1cd2-127">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="d1cd2-128">Bu örneklerde, değişmez değer 90946 türüdür `int`.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-128">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="d1cd2-129">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="d1cd2-129">Conversions</span></span>  
 <span data-ttu-id="d1cd2-130">Önceden tanımlanmış bir örtük dönüştürme `int` için [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="d1cd2-130">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="d1cd2-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d1cd2-131">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="d1cd2-132">Önceden tanımlanmış bir örtük dönüştürme [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `int`.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-132">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="d1cd2-133">Örneğin, aşağıdaki atama deyimi bir cast derleme hatasız üretir:</span><span class="sxs-lookup"><span data-stu-id="d1cd2-133">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="d1cd2-134">Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `int`.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-134">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="d1cd2-135">Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d1cd2-135">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="d1cd2-136">Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="d1cd2-136">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d1cd2-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d1cd2-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1cd2-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1cd2-138">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="d1cd2-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d1cd2-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d1cd2-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d1cd2-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d1cd2-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d1cd2-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d1cd2-142">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="d1cd2-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="d1cd2-143">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="d1cd2-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="d1cd2-144">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="d1cd2-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d1cd2-145">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="d1cd2-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
