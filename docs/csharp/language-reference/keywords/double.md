---
title: double (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 3683b51dfd0ef653ab8bfff6705b96a37e21a10a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="double-c-reference"></a><span data-ttu-id="e3de4-102">double (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e3de4-102">double (C# Reference)</span></span>
<span data-ttu-id="e3de4-103">`double` Anahtar sözcüğü 64-bit kayan nokta değerlerini depolayan basit bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3de4-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="e3de4-104">Aşağıdaki tabloda duyarlık ve yaklaşık aralığının gösterir `double` türü.</span><span class="sxs-lookup"><span data-stu-id="e3de4-104">The following table shows the precision and approximate range for the `double` type.</span></span>  
  
|<span data-ttu-id="e3de4-105">Tür</span><span class="sxs-lookup"><span data-stu-id="e3de4-105">Type</span></span>|<span data-ttu-id="e3de4-106">Yaklaşık aralığı</span><span class="sxs-lookup"><span data-stu-id="e3de4-106">Approximate range</span></span>|<span data-ttu-id="e3de4-107">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="e3de4-107">Precision</span></span>|<span data-ttu-id="e3de4-108">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="e3de4-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|<span data-ttu-id="e3de4-109">±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="e3de4-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="e3de4-110">15-16 basamak</span><span class="sxs-lookup"><span data-stu-id="e3de4-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="e3de4-111">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="e3de4-111">Literals</span></span>  
 <span data-ttu-id="e3de4-112">Varsayılan olarak, gerçek tamsayısal bir hazır değer atama işlecinin sağ tarafında olarak işlem görür `double`.</span><span class="sxs-lookup"><span data-stu-id="e3de4-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="e3de4-113">Ancak, kabul edilmesi için bir tamsayı isteyip istemediğinizi `double`, sonek d veya D, örneğin kullanın:</span><span class="sxs-lookup"><span data-stu-id="e3de4-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>  
  
```csharp  
double x = 3D;  
```  
  
## <a name="conversions"></a><span data-ttu-id="e3de4-114">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="e3de4-114">Conversions</span></span>  
 <span data-ttu-id="e3de4-115">Sayısal tam sayı türleri ve bir ifadede kayan nokta türleri karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3de4-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="e3de4-116">Bu durumda, tam sayı türleri için kayan nokta türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e3de4-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="e3de4-117">İfade değerlendirme aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="e3de4-117">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="e3de4-118">Kayan nokta türlerinden birini ise `double`, için ifadeyi hesaplar `double`, veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadelerde.</span><span class="sxs-lookup"><span data-stu-id="e3de4-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="e3de4-119">Varsa hiçbir `double` türü için değerlendirir ifadesinde [float](../../../csharp/language-reference/keywords/float.md), veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadelerde.</span><span class="sxs-lookup"><span data-stu-id="e3de4-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="e3de4-120">Kayan nokta ifade aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="e3de4-120">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="e3de4-121">Pozitif ve negatif sıfır.</span><span class="sxs-lookup"><span data-stu-id="e3de4-121">Positive and negative zero.</span></span>  
  
-   <span data-ttu-id="e3de4-122">Pozitif ve negatif sonsuzluk.</span><span class="sxs-lookup"><span data-stu-id="e3de4-122">Positive and negative infinity.</span></span>  
  
-   <span data-ttu-id="e3de4-123">Değer bir sayı değil (NaN).</span><span class="sxs-lookup"><span data-stu-id="e3de4-123">Not-a-Number value (NaN).</span></span>  
  
-   <span data-ttu-id="e3de4-124">Sıfır olmayan değerler sınırlı kümesi.</span><span class="sxs-lookup"><span data-stu-id="e3de4-124">The finite set of nonzero values.</span></span>  
  
 <span data-ttu-id="e3de4-125">Bu değerler hakkında daha fazla bilgi için ikili Floating-Point aritmetik, kullanılabilir IEEE standardı bkz [IEEE](http://www.ieee.org) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="e3de4-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3de4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3de4-126">Example</span></span>  
 <span data-ttu-id="e3de4-127">Aşağıdaki örnekte, bir [int](../../../csharp/language-reference/keywords/int.md), [kısa](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)ve bir `double` birlikte vermiş eklenen bir `double` sonucu.</span><span class="sxs-lookup"><span data-stu-id="e3de4-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e3de4-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e3de4-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3de4-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3de4-129">See Also</span></span>  
 [<span data-ttu-id="e3de4-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e3de4-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e3de4-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e3de4-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3de4-132">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e3de4-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e3de4-133">Varsayılan Değerler Tablosu</span><span class="sxs-lookup"><span data-stu-id="e3de4-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="e3de4-134">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="e3de4-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="e3de4-135">Kayan Nokta Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="e3de4-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [<span data-ttu-id="e3de4-136">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="e3de4-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="e3de4-137">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="e3de4-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
