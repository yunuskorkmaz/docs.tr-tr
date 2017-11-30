---
title: "double (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords: double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 232dd97e152f943137604074f24b5de779168e59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="double-c-reference"></a><span data-ttu-id="7c19b-102">double (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7c19b-102">double (C# Reference)</span></span>
<span data-ttu-id="7c19b-103">`double` Anahtar sözcüğü 64-bit kayan nokta değerlerini depolayan basit bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c19b-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="7c19b-104">Aşağıdaki tabloda duyarlık ve yaklaşık aralığının gösterir `double` türü.</span><span class="sxs-lookup"><span data-stu-id="7c19b-104">The following table shows the precision and approximate range for the `double` type.</span></span>  
  
|<span data-ttu-id="7c19b-105">Tür</span><span class="sxs-lookup"><span data-stu-id="7c19b-105">Type</span></span>|<span data-ttu-id="7c19b-106">Yaklaşık aralığı</span><span class="sxs-lookup"><span data-stu-id="7c19b-106">Approximate range</span></span>|<span data-ttu-id="7c19b-107">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="7c19b-107">Precision</span></span>|<span data-ttu-id="7c19b-108">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="7c19b-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|<span data-ttu-id="7c19b-109">±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="7c19b-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="7c19b-110">15-16 basamak</span><span class="sxs-lookup"><span data-stu-id="7c19b-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="7c19b-111">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="7c19b-111">Literals</span></span>  
 <span data-ttu-id="7c19b-112">Varsayılan olarak, gerçek tamsayısal bir hazır değer atama işlecinin sağ tarafında olarak işlem görür `double`.</span><span class="sxs-lookup"><span data-stu-id="7c19b-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="7c19b-113">Ancak, kabul edilmesi için bir tamsayı isteyip istemediğinizi `double`, sonek d veya D, örneğin kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c19b-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>  
  
```  
double x = 3D;  
```  
  
## <a name="conversions"></a><span data-ttu-id="7c19b-114">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="7c19b-114">Conversions</span></span>  
 <span data-ttu-id="7c19b-115">Sayısal tam sayı türleri ve bir ifadede kayan nokta türleri karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c19b-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="7c19b-116">Bu durumda, tam sayı türleri için kayan nokta türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="7c19b-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="7c19b-117">İfade değerlendirme aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="7c19b-117">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="7c19b-118">Kayan nokta türlerinden birini ise `double`, için ifadeyi hesaplar `double`, veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadelerde.</span><span class="sxs-lookup"><span data-stu-id="7c19b-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="7c19b-119">Varsa hiçbir `double` türü için değerlendirir ifadesinde [float](../../../csharp/language-reference/keywords/float.md), veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadelerde.</span><span class="sxs-lookup"><span data-stu-id="7c19b-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="7c19b-120">Kayan nokta ifade aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="7c19b-120">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="7c19b-121">Pozitif ve negatif sıfır.</span><span class="sxs-lookup"><span data-stu-id="7c19b-121">Positive and negative zero.</span></span>  
  
-   <span data-ttu-id="7c19b-122">Pozitif ve negatif sonsuzluk.</span><span class="sxs-lookup"><span data-stu-id="7c19b-122">Positive and negative infinity.</span></span>  
  
-   <span data-ttu-id="7c19b-123">Değer bir sayı değil (NaN).</span><span class="sxs-lookup"><span data-stu-id="7c19b-123">Not-a-Number value (NaN).</span></span>  
  
-   <span data-ttu-id="7c19b-124">Sıfır olmayan değerler sınırlı kümesi.</span><span class="sxs-lookup"><span data-stu-id="7c19b-124">The finite set of nonzero values.</span></span>  
  
 <span data-ttu-id="7c19b-125">Bu değerler hakkında daha fazla bilgi için ikili Floating-Point aritmetik, kullanılabilir IEEE standardı bkz [IEEE](http://www.ieee.org) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="7c19b-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c19b-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c19b-126">Example</span></span>  
 <span data-ttu-id="7c19b-127">Aşağıdaki örnekte, bir [int](../../../csharp/language-reference/keywords/int.md), [kısa](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)ve bir `double` birlikte vermiş eklenen bir `double` sonucu.</span><span class="sxs-lookup"><span data-stu-id="7c19b-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7c19b-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7c19b-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c19b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c19b-129">See Also</span></span>  
 [<span data-ttu-id="7c19b-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7c19b-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7c19b-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7c19b-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7c19b-132">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7c19b-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7c19b-133">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="7c19b-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="7c19b-134">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="7c19b-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="7c19b-135">Kayan nokta türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="7c19b-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [<span data-ttu-id="7c19b-136">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="7c19b-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="7c19b-137">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="7c19b-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
