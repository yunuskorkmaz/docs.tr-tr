---
title: short (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: f402b9d2d62bcc3ba265755d59a657b88c197482
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660049"
---
# <a name="short-c-reference"></a><span data-ttu-id="abe44-102">short (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="abe44-102">short (C# Reference)</span></span>

<span data-ttu-id="abe44-103">`short` boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tam sayı veri türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="abe44-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="abe44-104">Tür</span><span class="sxs-lookup"><span data-stu-id="abe44-104">Type</span></span>|<span data-ttu-id="abe44-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="abe44-105">Range</span></span>|<span data-ttu-id="abe44-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="abe44-106">Size</span></span>|<span data-ttu-id="abe44-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="abe44-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="abe44-108">-32.768 için 32.767</span><span class="sxs-lookup"><span data-stu-id="abe44-108">-32,768 to 32,767</span></span>|<span data-ttu-id="abe44-109">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="abe44-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="abe44-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="abe44-110">Literals</span></span>  

<span data-ttu-id="abe44-111">Bildirmek ve başlatmak bir `short` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).</span><span class="sxs-lookup"><span data-stu-id="abe44-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="abe44-112">Tamsayı sabit değeri aralığının dışında ise `short` (diğer bir deyişle, bu ise kısa <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="abe44-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="abe44-113">Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 1,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `short` değerleri.</span><span class="sxs-lookup"><span data-stu-id="abe44-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> <span data-ttu-id="abe44-114">Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="abe44-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="abe44-115">Ondalık değişmez değerler, önek vardır.</span><span class="sxs-lookup"><span data-stu-id="abe44-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="abe44-116">C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="abe44-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="abe44-117">C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="abe44-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="abe44-118">C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="abe44-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="abe44-119">Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.</span><span class="sxs-lookup"><span data-stu-id="abe44-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="abe44-120">Aşağıda bazı örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="abe44-120">Some examples are shown below.</span></span>

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="abe44-121">Derleyici aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="abe44-121">Compiler overload resolution</span></span>

 <span data-ttu-id="abe44-122">Çağırma yöntemleri aşırı yüklendiğinde bir yayın kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abe44-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="abe44-123">Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `short` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:</span><span class="sxs-lookup"><span data-stu-id="abe44-123">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="abe44-124">Kullanarak `short` atama doğru tür, örneğin çağrıldığını güvence altına alır:</span><span class="sxs-lookup"><span data-stu-id="abe44-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="abe44-125">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="abe44-125">Conversions</span></span>  

 <span data-ttu-id="abe44-126">Önceden tanımlanmış bir örtük dönüştürme vardır `short` için [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="abe44-126">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="abe44-127">Daha büyük depolama boyutu için sabit değerli olmayan sayısal türleri örtülü olarak dönüştürülemiyor `short` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için).</span><span class="sxs-lookup"><span data-stu-id="abe44-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="abe44-128">Örneğin, aşağıdaki iki göz önünde bulundurun `short` değişkenleri `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="abe44-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="abe44-129">Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="abe44-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="abe44-130">Bu sorunu gidermek için bir tür dönüştürme kullanın:</span><span class="sxs-lookup"><span data-stu-id="abe44-130">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="abe44-131">Ayrıca, hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak da mümkündür:</span><span class="sxs-lookup"><span data-stu-id="abe44-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="abe44-132">Kayan nokta türlerinden hiç örtük dönüştürme `short`.</span><span class="sxs-lookup"><span data-stu-id="abe44-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="abe44-133">Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="abe44-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="abe44-134">Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="abe44-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="abe44-135">Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="abe44-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="abe44-136">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="abe44-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="abe44-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abe44-137">See Also</span></span>

- <xref:System.Int16>  
- [<span data-ttu-id="abe44-138">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="abe44-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="abe44-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="abe44-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="abe44-140">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="abe44-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="abe44-141">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="abe44-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="abe44-142">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="abe44-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="abe44-143">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="abe44-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="abe44-144">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="abe44-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
