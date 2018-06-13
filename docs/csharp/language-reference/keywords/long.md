---
title: long (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: f2bdc34400215ad24d5dcec2e1e9f314a01430d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288460"
---
# <a name="long-c-reference"></a><span data-ttu-id="2cd5f-102">long (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2cd5f-102">long (C# Reference)</span></span>

<span data-ttu-id="2cd5f-103">`long` Aşağıdaki tabloda gösterilen aralığı ve boyutu göre değerleri depolayan tamsayı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="2cd5f-104">Tür</span><span class="sxs-lookup"><span data-stu-id="2cd5f-104">Type</span></span>|<span data-ttu-id="2cd5f-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="2cd5f-105">Range</span></span>|<span data-ttu-id="2cd5f-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="2cd5f-106">Size</span></span>|<span data-ttu-id="2cd5f-107">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="2cd5f-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="2cd5f-108">-9,223,372,036,854,775,808 için 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="2cd5f-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="2cd5f-109">işaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="2cd5f-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="2cd5f-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="2cd5f-110">Literals</span></span> 

<span data-ttu-id="2cd5f-111">Bildirme ve başlatma bir `long` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="2cd5f-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="2cd5f-112">Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 4,294,967,296 tamsayılar eşit ve ikili değişmez değerler atanır `long` değerleri.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> <span data-ttu-id="2cd5f-113">Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="2cd5f-114">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-114">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="2cd5f-115">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="2cd5f-116">C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="2cd5f-117">C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="2cd5f-118">Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="2cd5f-119">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="2cd5f-120">Tamsayı değişmez değerleri türü gösterir bir sonek de içerir.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="2cd5f-121">Sonek `L` gösterir bir `long`.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="2cd5f-122">Aşağıdaki örnek kullanır `L` uzun tamsayı belirtmek için soneki:</span><span class="sxs-lookup"><span data-stu-id="2cd5f-122">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="2cd5f-123">Bu gibi durumlarda, küçük harf "m" de sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="2cd5f-124">Ancak, bu derleyici uyarısı oluşturur harf "l" kolay "1." rakamla karıştırılır çünkü</span><span class="sxs-lookup"><span data-stu-id="2cd5f-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="2cd5f-125">"M" daha anlaşılır olması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-125">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="2cd5f-126">Sonek kullandığınızda `L`, sabit değeri Tamsayı türünde ya da olduğu belirlenir `long` veya [ulong](../../../csharp/language-reference/keywords/ulong.md)boyutuna bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="2cd5f-127">Bu durumda olan `long` olduğundan, aralığı'den [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="2cd5f-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="2cd5f-128">Bir ortak soneki aşırı yüklenmiş yöntemleri çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="2cd5f-129">Örneğin, aşağıdaki aşırı yüklenmiş yöntemler türü parametrelerine sahip `long` ve [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="2cd5f-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="2cd5f-130">`L` Soneki garanti doğru aşırı adı verilir:</span><span class="sxs-lookup"><span data-stu-id="2cd5f-130">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="2cd5f-131">Değişmez değer bir tamsayı sonek türünü ilk değerini gösterilebilir aşağıdaki türlerde ise:</span><span class="sxs-lookup"><span data-stu-id="2cd5f-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="2cd5f-132">int</span><span class="sxs-lookup"><span data-stu-id="2cd5f-132">int</span></span>](int.md)
2. [<span data-ttu-id="2cd5f-133">uint</span><span class="sxs-lookup"><span data-stu-id="2cd5f-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="2cd5f-134">ulong</span><span class="sxs-lookup"><span data-stu-id="2cd5f-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="2cd5f-135">Önceki örneklerde değişmez değer 4294967296 türünde `long`, aralığı aştığından [uint](../../../csharp/language-reference/keywords/uint.md) (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).</span><span class="sxs-lookup"><span data-stu-id="2cd5f-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="2cd5f-136">Kullanırsanız `long` ifadesi aynı ifadedeki diğer tam sayı türleri türüyle olarak değerlendirildiği `long` (veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadeleri söz konusu olduğunda).</span><span class="sxs-lookup"><span data-stu-id="2cd5f-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="2cd5f-137">Örneğin, olarak aşağıdaki ifadeyi hesaplar `long`:</span><span class="sxs-lookup"><span data-stu-id="2cd5f-137">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="2cd5f-138">Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="2cd5f-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="2cd5f-139">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2cd5f-139">Conversions</span></span>  
 <span data-ttu-id="2cd5f-140">Önceden tanımlanmış bir örtük dönüştürme `long` için [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="2cd5f-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="2cd5f-141">Aksi halde bir cast kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="2cd5f-142">Örneğin, aşağıdaki deyim derleme hatası açık atama olmadan üretir:</span><span class="sxs-lookup"><span data-stu-id="2cd5f-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="2cd5f-143">Önceden tanımlanmış bir örtük dönüştürme [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), veya [char](../../../csharp/language-reference/keywords/char.md) için `long`.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="2cd5f-144">Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `long`.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="2cd5f-145">Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2cd5f-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="2cd5f-146">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2cd5f-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2cd5f-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd5f-147">See Also</span></span>  
 <xref:System.Int64>  
 [<span data-ttu-id="2cd5f-148">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2cd5f-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2cd5f-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2cd5f-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2cd5f-150">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2cd5f-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2cd5f-151">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="2cd5f-151">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="2cd5f-152">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="2cd5f-152">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="2cd5f-153">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="2cd5f-153">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="2cd5f-154">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="2cd5f-154">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
