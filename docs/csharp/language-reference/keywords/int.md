---
title: int - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 3436d2ceeec9eed80f346c28231ba376cf6d5fb6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243822"
---
# <a name="int-c-reference"></a><span data-ttu-id="a58cd-102">int (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a58cd-102">int (C# Reference)</span></span>

<span data-ttu-id="a58cd-103">`int` boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a58cd-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="a58cd-104">Tür</span><span class="sxs-lookup"><span data-stu-id="a58cd-104">Type</span></span>|<span data-ttu-id="a58cd-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="a58cd-105">Range</span></span>|<span data-ttu-id="a58cd-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="a58cd-106">Size</span></span>|<span data-ttu-id="a58cd-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="a58cd-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`int`|<span data-ttu-id="a58cd-108">-2.147.483.648 için 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="a58cd-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="a58cd-109">İşaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="a58cd-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="a58cd-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a58cd-110">Literals</span></span>  
 
<span data-ttu-id="a58cd-111">Bildirmek ve başlatmak bir `int` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="a58cd-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="a58cd-112">Tamsayı sabit değeri aralığının dışında ise `int` (diğer bir deyişle, bu ise kısa <xref:System.Int32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="a58cd-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="a58cd-113">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 90,946 eşit ve ikili sabit değerler atanır `int` değerleri.</span><span class="sxs-lookup"><span data-stu-id="a58cd-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="a58cd-114">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a58cd-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="a58cd-115">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="a58cd-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="a58cd-116">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="a58cd-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="a58cd-117">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="a58cd-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="a58cd-118">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="a58cd-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="a58cd-119">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="a58cd-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="a58cd-120">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a58cd-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="a58cd-121">Tamsayı sabit değerlerinde de bulunabilir, türü gösteren bir sonek gösteren sonek olsa `int` türü.</span><span class="sxs-lookup"><span data-stu-id="a58cd-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="a58cd-122">Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a58cd-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="a58cd-123">uint</span><span class="sxs-lookup"><span data-stu-id="a58cd-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="a58cd-124">long</span><span class="sxs-lookup"><span data-stu-id="a58cd-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="a58cd-125">ulong</span><span class="sxs-lookup"><span data-stu-id="a58cd-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="a58cd-126">Bu örneklerde, değişmez değer 90946 türünde `int`.</span><span class="sxs-lookup"><span data-stu-id="a58cd-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="a58cd-127">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="a58cd-127">Conversions</span></span>  
 <span data-ttu-id="a58cd-128">Önceden tanımlanmış bir örtük dönüştürme vardır `int` için [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="a58cd-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="a58cd-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a58cd-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="a58cd-130">Önceden tanımlanmış bir örtük dönüştürme vardır [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `int`.</span><span class="sxs-lookup"><span data-stu-id="a58cd-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="a58cd-131">Örneğin, aşağıdaki atama deyimi, bir yayın olmadan bir derleme hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="a58cd-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="a58cd-132">Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `int`.</span><span class="sxs-lookup"><span data-stu-id="a58cd-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="a58cd-133">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a58cd-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="a58cd-134">Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz. [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="a58cd-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a58cd-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a58cd-135">C# Language Specification</span></span>  

<span data-ttu-id="a58cd-136">Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a58cd-136">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="a58cd-137">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="a58cd-137">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a58cd-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a58cd-138">See Also</span></span>

- <xref:System.Int32>  
- [<span data-ttu-id="a58cd-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a58cd-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a58cd-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a58cd-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a58cd-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a58cd-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a58cd-142">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="a58cd-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="a58cd-143">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="a58cd-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="a58cd-144">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="a58cd-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="a58cd-145">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="a58cd-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
