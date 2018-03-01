---
title: "long (C# Başvurusu)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f18bed80550b293195961fd9d42491dd571cbaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="long-c-reference"></a><span data-ttu-id="ba7e3-102">long (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ba7e3-102">long (C# Reference)</span></span>

<span data-ttu-id="ba7e3-103">`long`Aşağıdaki tabloda gösterilen aralığı ve boyutu göre değerleri depolayan tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="ba7e3-104">Tür</span><span class="sxs-lookup"><span data-stu-id="ba7e3-104">Type</span></span>|<span data-ttu-id="ba7e3-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="ba7e3-105">Range</span></span>|<span data-ttu-id="ba7e3-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="ba7e3-106">Size</span></span>|<span data-ttu-id="ba7e3-107">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="ba7e3-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="ba7e3-108">-9,223,372,036,854,775,808 için 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="ba7e3-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="ba7e3-109">işaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="ba7e3-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="ba7e3-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="ba7e3-110">Literals</span></span> 

<span data-ttu-id="ba7e3-111">Bildirme ve başlatma bir `long` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# 7 için değişmez değer bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="ba7e3-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="ba7e3-112">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 4,294,967,296 tamsayılar eşit ve ikili değişmez değerler atanır `long` değerleri.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> <span data-ttu-id="ba7e3-113">Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="ba7e3-114">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-114">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="ba7e3-115">C# 7 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="ba7e3-116">C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="ba7e3-117">C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="ba7e3-118">Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="ba7e3-119">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="ba7e3-120">Tamsayı değişmez değerleri türü gösterir bir sonek de içerir.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="ba7e3-121">Sonek `L` gösterir bir `long`.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="ba7e3-122">Aşağıdaki örnek kullanır `L` uzun tamsayı belirtmek için soneki:</span><span class="sxs-lookup"><span data-stu-id="ba7e3-122">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="ba7e3-123">Bu gibi durumlarda, küçük harf "m" de sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="ba7e3-124">Ancak, bu derleyici uyarısı oluşturur harf "l" kolay "1." rakamla karıştırılır çünkü</span><span class="sxs-lookup"><span data-stu-id="ba7e3-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="ba7e3-125">"M" daha anlaşılır olması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-125">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="ba7e3-126">Sonek kullandığınızda `L`, sabit değeri Tamsayı türünde ya da olduğu belirlenir `long` veya [ulong](../../../csharp/language-reference/keywords/ulong.md)boyutuna bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="ba7e3-127">Bu durumda olan `long` olduğundan, aralığı'den [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="ba7e3-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="ba7e3-128">Bir ortak soneki aşırı yüklenmiş yöntemleri çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="ba7e3-129">Örneğin, aşağıdaki aşırı yüklenmiş yöntemler türü parametrelerine sahip `long` ve [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="ba7e3-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="ba7e3-130">`L` Soneki garanti doğru aşırı adı verilir:</span><span class="sxs-lookup"><span data-stu-id="ba7e3-130">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="ba7e3-131">Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:</span><span class="sxs-lookup"><span data-stu-id="ba7e3-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="ba7e3-132">int</span><span class="sxs-lookup"><span data-stu-id="ba7e3-132">int</span></span>](int.md)
2. [<span data-ttu-id="ba7e3-133">uint</span><span class="sxs-lookup"><span data-stu-id="ba7e3-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="ba7e3-134">ulong</span><span class="sxs-lookup"><span data-stu-id="ba7e3-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="ba7e3-135">Önceki örneklerde değişmez değer 4294967296 türünde `long`, aralığı aştığından [uint](../../../csharp/language-reference/keywords/uint.md) (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).</span><span class="sxs-lookup"><span data-stu-id="ba7e3-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="ba7e3-136">Kullanırsanız `long` ifadesi aynı ifadedeki diğer tam sayı türleri türüyle olarak değerlendirildiği `long` (veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadeleri söz konusu olduğunda).</span><span class="sxs-lookup"><span data-stu-id="ba7e3-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="ba7e3-137">Örneğin, olarak aşağıdaki ifadeyi hesaplar `long`:</span><span class="sxs-lookup"><span data-stu-id="ba7e3-137">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="ba7e3-138">Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="ba7e3-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="ba7e3-139">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="ba7e3-139">Conversions</span></span>  
 <span data-ttu-id="ba7e3-140">Önceden tanımlanmış bir örtük dönüştürme `long` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="ba7e3-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="ba7e3-141">Aksi halde bir cast kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="ba7e3-142">Örneğin, aşağıdaki deyim derleme hatası açık atama olmadan üretir:</span><span class="sxs-lookup"><span data-stu-id="ba7e3-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="ba7e3-143">Önceden tanımlanmış bir örtük dönüştürme [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `long`.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="ba7e3-144">Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `long`.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="ba7e3-145">Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ba7e3-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="ba7e3-146">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ba7e3-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba7e3-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba7e3-147">See Also</span></span>  
 <xref:System.Int64>  
 [<span data-ttu-id="ba7e3-148">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ba7e3-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ba7e3-149">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ba7e3-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ba7e3-150">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ba7e3-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ba7e3-151">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="ba7e3-151">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="ba7e3-152">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="ba7e3-152">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="ba7e3-153">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="ba7e3-153">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="ba7e3-154">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="ba7e3-154">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
