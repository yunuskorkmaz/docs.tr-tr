---
title: "float (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846f132812fe90a285c81a020d440fc846f88b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="float-c-reference"></a><span data-ttu-id="1894c-102">float (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1894c-102">float (C# Reference)</span></span>
<span data-ttu-id="1894c-103">`float` Anahtar sözcüğü 32 bit kayan nokta değerlerini depolayan basit bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="1894c-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="1894c-104">Aşağıdaki tabloda duyarlık ve yaklaşık aralığının gösterir `float` türü.</span><span class="sxs-lookup"><span data-stu-id="1894c-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="1894c-105">Tür</span><span class="sxs-lookup"><span data-stu-id="1894c-105">Type</span></span>|<span data-ttu-id="1894c-106">Yaklaşık aralığı</span><span class="sxs-lookup"><span data-stu-id="1894c-106">Approximate range</span></span>|<span data-ttu-id="1894c-107">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="1894c-107">Precision</span></span>|<span data-ttu-id="1894c-108">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="1894c-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="1894c-109">-3.4 × 10<sup>38</sup>+3.4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="1894c-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="1894c-110">7 basamağa</span><span class="sxs-lookup"><span data-stu-id="1894c-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="1894c-111">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="1894c-111">Literals</span></span>  
 <span data-ttu-id="1894c-112">Varsayılan olarak, gerçek tamsayısal bir hazır değer atama işlecinin sağ tarafında olarak işlem görür [çift](double.md).</span><span class="sxs-lookup"><span data-stu-id="1894c-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="1894c-113">Bu nedenle, bir float değişkeni başlatmak için sonekini kullan `f` veya `F`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="1894c-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="1894c-114">Önceki bildiriminde soneki kullanmıyorsanız depolamak çalıştığınız için bir derleme hatası alırsınız bir [çift](double.md) içine değeri bir `float` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="1894c-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="1894c-115">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="1894c-115">Conversions</span></span>  
 <span data-ttu-id="1894c-116">Sayısal tam sayı türleri ve bir ifadede kayan nokta türleri karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1894c-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="1894c-117">Bu durumda, tam sayı türleri için kayan nokta türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="1894c-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="1894c-118">İfade değerlendirme aşağıdaki kurallara göre gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="1894c-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="1894c-119">Kayan nokta türlerinden birini ise [çift](double.md), için ifadeyi hesaplar [çift](double.md) veya [bool](bool.md) ilişkisel ya da Boole ifadelerde.</span><span class="sxs-lookup"><span data-stu-id="1894c-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="1894c-120">Varsa hiçbir [çift](double.md) ifadede, ifade türü hesaplar için `float` veya [bool](bool.md) ilişkisel ya da Boole ifadelerde.</span><span class="sxs-lookup"><span data-stu-id="1894c-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="1894c-121">Kayan nokta ifade aşağıdaki değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="1894c-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="1894c-122">Pozitif ve negatif sıfır</span><span class="sxs-lookup"><span data-stu-id="1894c-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="1894c-123">Pozitif ve negatif sonsuzluk</span><span class="sxs-lookup"><span data-stu-id="1894c-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="1894c-124">Bir sayı değil değeri (NaN)</span><span class="sxs-lookup"><span data-stu-id="1894c-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="1894c-125">Sıfır olmayan değerler sınırlı kümesi</span><span class="sxs-lookup"><span data-stu-id="1894c-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="1894c-126">Bu değerler hakkında daha fazla bilgi için ikili Floating-Point aritmetik, kullanılabilir IEEE standardı bkz [IEEE](http://www.ieee.org) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="1894c-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1894c-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1894c-127">Example</span></span>  
 <span data-ttu-id="1894c-128">Aşağıdaki örnekte, bir [int](int.md), [kısa](short.md)ve bir `float` bir matematik ifadesindeki vermiş bulunan bir `float` sonucu.</span><span class="sxs-lookup"><span data-stu-id="1894c-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="1894c-129">(Unutmayın `float` için diğer ad olduğu <xref:System.Single?displayProperty=nameWithType> türü.) Var olduğuna dikkat edin hiçbir [çift](double.md) ifadesinde.</span><span class="sxs-lookup"><span data-stu-id="1894c-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1894c-130">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="1894c-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1894c-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1894c-131">See Also</span></span>  
 <xref:System.Single>  
 [<span data-ttu-id="1894c-132">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1894c-132">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1894c-133">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1894c-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1894c-134">Atama ve tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="1894c-134">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="1894c-135">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1894c-135">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="1894c-136">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="1894c-136">Integral Types Table</span></span>](integral-types-table.md)  
 [<span data-ttu-id="1894c-137">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="1894c-137">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="1894c-138">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="1894c-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="1894c-139">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="1894c-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
