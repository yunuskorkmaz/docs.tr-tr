---
title: C# içinde LINQ sorguları yazma
description: C# içinde LINQ sorguları yazma hakkında bilgi edinin.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: df77326b921d22d90cf90c12e9c0f472d808ed95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981341"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="c6e52-103">C'de LINQ sorguları yazma\#</span><span class="sxs-lookup"><span data-stu-id="c6e52-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="c6e52-104">Bu makalede, C# LINQ sorgusu yazma kullandığı üç yöntem açıklanır:</span><span class="sxs-lookup"><span data-stu-id="c6e52-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="c6e52-105">Sorgu söz dizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6e52-105">Use query syntax.</span></span>

2. <span data-ttu-id="c6e52-106">Yöntem sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6e52-106">Use method syntax.</span></span>

3. <span data-ttu-id="c6e52-107">Sorgu sözdizimi ve yöntem sözdizimi bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6e52-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="c6e52-108">Aşağıdaki örnekler, daha önce listelenen her bir yaklaşım kullanarak bazı basit LINQ sorguları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="c6e52-109">Genel olarak, kullanım (1) mümkün olduğunda ve Kullan (2) ve (3) gerektiğinde kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="c6e52-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e52-110">Bu sorgular, basit bir bellek içi koleksiyonlarda çalışır; Ancak, temel sözdizimi, LINQ to Entities ve LINQ to XML kullanılıyor aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c6e52-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="c6e52-111">Örnek - sorgu söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c6e52-111">Example - Query syntax</span></span>

<span data-ttu-id="c6e52-112">Çoğu sorguları yazma için önerilen yöntem kullanmaktır *sorgu söz dizimi* oluşturmak için *sorgu ifadelerinde*.</span><span class="sxs-lookup"><span data-stu-id="c6e52-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="c6e52-113">Aşağıdaki örnek, üç sorgu ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-113">The following example shows three query expressions.</span></span> <span data-ttu-id="c6e52-114">İlk sorgu ifadesi filtreleyin veya koşullarla uygulayarak, sonuçları kısıtlama yapmayı gösteren bir `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c6e52-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="c6e52-115">Değerleri 7 veya 3'ten az büyük olan kaynak dizisindeki tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6e52-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="c6e52-116">İkinci deyim, döndürülen sonuçların nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="c6e52-117">Üçüncü ifade, sonuçları bir anahtar göre gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="c6e52-118">Bu sorgu, sözcüğün ilk harfini üzerinde alan iki gruplar döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6e52-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="c6e52-119">Sorgu türü olduğuna dikkat edin <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c6e52-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="c6e52-120">Tüm bu sorguları kullanarak yazılabilir `var` aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c6e52-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="c6e52-121">İçindeki sorgu değişkeni üzerinde yineleme kadar her önceki örnekte sorgular gerçekten Yürütülmeyen bir `foreach` deyimi veya diğer deyimi.</span><span class="sxs-lookup"><span data-stu-id="c6e52-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="c6e52-122">Daha fazla bilgi için [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c6e52-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="c6e52-123">Örnek - yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6e52-123">Example - Method syntax</span></span>

<span data-ttu-id="c6e52-124">Bazı sorgu işlemlerinin bir yöntem çağrısının ifade edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="c6e52-125">En yaygın tür yöntemler gibi tekil sayısal değerler döndüren olanlardır <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="c6e52-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="c6e52-126">Yalnızca tek bir değeri temsil eder ve bir ek sorgu işlemi kaynağı olarak hizmet veremez bu yöntemlerin her zaman içinde herhangi bir sorgu son çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6e52-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="c6e52-127">Aşağıdaki örnek bir sorgu ifadesinde yöntem çağrısı gösterir:</span><span class="sxs-lookup"><span data-stu-id="c6e52-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="c6e52-128">Yöntem bir eylem veya Func parametrelere sahipse, bunlar biçiminde sağlanır bir [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi ifade:</span><span class="sxs-lookup"><span data-stu-id="c6e52-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="c6e52-129">Önceki sorgular, yalnızca sorgu #4 hemen yürütür.</span><span class="sxs-lookup"><span data-stu-id="c6e52-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="c6e52-130">Tek bir değer ve bir genel döndürür olmasıdır <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c6e52-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="c6e52-131">Yöntemin kendisi kullanması gereken `foreach` değerini hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="c6e52-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="c6e52-132">Her biri, önceki sorgular ile örtülü yazma'yı kullanarak yazılabilir [var](../language-reference/keywords/var.md), aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c6e52-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="c6e52-133">Örnek - karma sorgu ve yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6e52-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="c6e52-134">Bu örnek, bir sorgu yan tümcesinin sonuçlarını temel yöntem sözdizimi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="c6e52-135">Yalnızca sorgu ifadesi, parantez içine ve ardından nokta işleci uygulamak ve yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="c6e52-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="c6e52-136">Aşağıdaki örnekte, sorgu #7, 3 ve 7 arasında bir değeri olan sayıların sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6e52-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="c6e52-137">Genel olarak, ancak bu ikinci bir değişkene yöntem çağrısının sonucunu depolamak için kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="c6e52-138">Bu şekilde, sorgu sorgu sonuçlarını kafanız olma olasılığı daha gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6e52-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="c6e52-139">Sorgu, sorgu #7 tek bir değer ve bir koleksiyonu döndürdüğünden, hemen yürütür.</span><span class="sxs-lookup"><span data-stu-id="c6e52-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="c6e52-140">Önceki sorguya ile örtülü yazma'yı kullanarak yazılabilir `var`gibi:</span><span class="sxs-lookup"><span data-stu-id="c6e52-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="c6e52-141">Bunu şu şekilde yöntemi sözdiziminde yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="c6e52-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="c6e52-142">Açık, şu şekilde yazım kullanarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="c6e52-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="c6e52-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6e52-143">See also</span></span>

- [<span data-ttu-id="c6e52-144">İzlenecek yol: Sorguları yazmaC#</span><span class="sxs-lookup"><span data-stu-id="c6e52-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="c6e52-145">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c6e52-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="c6e52-146">where yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c6e52-146">where clause</span></span>](../language-reference/keywords/where-clause.md)