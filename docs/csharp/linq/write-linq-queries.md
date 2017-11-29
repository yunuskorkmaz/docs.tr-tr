---
title: "C# içinde LINQ sorguları yazma"
description: "Nasıl yazılacağını sorgular."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: f3efbfd232bd7e19d3db56289f57724c71dca064
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="7674b-104">C# içinde LINQ sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="7674b-104">Write LINQ queries in C#</span></span>

<span data-ttu-id="7674b-105">Bu konu, C# üzerinde LINQ sorgu yazabilirsiniz üç şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="7674b-105">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="7674b-106">Sorgu sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7674b-106">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="7674b-107">Yöntemi sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7674b-107">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="7674b-108">Sorgu sözdizimi ve yöntem sözdizimi bileşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7674b-108">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="7674b-109">Aşağıdaki örnekler, daha önce listelenen her bir yaklaşım kullanarak bazı basit LINQ sorgularını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7674b-109">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="7674b-110">Genel olarak, kullanım (1) mümkün olduğunda ve Kullan (2) ve (3) gerektiğinde kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="7674b-110">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7674b-111">Bu sorguları basit bellek içi koleksiyonlar üzerinde çalışır; Ancak, temel sözdizimi LINQ to Entities ve LINQ-XML kullanılan aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7674b-111">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7674b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7674b-112">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="7674b-113">Sorgu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7674b-113">Query syntax</span></span>  
 <span data-ttu-id="7674b-114">Sorguların çoğu yazmak için önerilen yöntem kullanmaktır *sorgu sözdizimi* oluşturmak için *sorgu ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="7674b-114">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="7674b-115">Aşağıdaki örnekte, üç sorgu ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="7674b-115">The following example shows three query expressions.</span></span> <span data-ttu-id="7674b-116">Filtre veya koşullar uygulayarak sonuçları kısıtlamak nasıl ilk sorgu ifadesi gösteren bir `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7674b-116">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="7674b-117">Değerleri 7 veya 3'ten az büyük olan kaynak dizisindeki tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7674b-117">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="7674b-118">İkinci ifade döndürülen sonuçların sipariş gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7674b-118">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="7674b-119">Üçüncü ifade, sonuçları bir anahtar göre gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7674b-119">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="7674b-120">Bu sorgu sözcüğün ilk harfini göre iki grupları döndürür.</span><span class="sxs-lookup"><span data-stu-id="7674b-120">This query returns two groups based on the first letter of the word.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 <span data-ttu-id="7674b-121">Sorguları türünde Not <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7674b-121">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="7674b-122">Tüm bu sorguları kullanarak yazılabilir `var` aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="7674b-122">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="7674b-123">Sorgu değişkeninde üzerinden yineleme kadar her önceki örnekte sorguları gerçekte yürütmeme bir `foreach` deyimi veya diğer deyimi.</span><span class="sxs-lookup"><span data-stu-id="7674b-123">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="7674b-124">Daha fazla bilgi için bkz: [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="7674b-124">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7674b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="7674b-125">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="7674b-126">Yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7674b-126">Method syntax</span></span>  
 <span data-ttu-id="7674b-127">Bazı sorgu işlemleri bir yöntem çağrısı ifade edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7674b-127">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="7674b-128">En yaygın tür yöntem dönüş singleton sayısal değerleri gibi izinlerdir <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="7674b-128">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="7674b-129">Yalnızca tek bir değeri temsil eder ve bir ek sorgu işlemi için kaynak olarak sunulamıyor olduğundan bu yöntemlerin her zaman içinde herhangi bir sorgu son çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7674b-129">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="7674b-130">Aşağıdaki örnek, sorgu ifadesinde bir yöntem çağrısı gösterir:</span><span class="sxs-lookup"><span data-stu-id="7674b-130">The following example shows a method call in a query expression:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="7674b-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="7674b-131">Example</span></span>  
 <span data-ttu-id="7674b-132">Yöntem bir eylem veya Func parametrelere sahipse, bunlar biçiminde sağlanan bir [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi ifade:</span><span class="sxs-lookup"><span data-stu-id="7674b-132">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 <span data-ttu-id="7674b-133">Önceki sorgularında yalnızca sorgu #4 hemen yürütür.</span><span class="sxs-lookup"><span data-stu-id="7674b-133">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="7674b-134">Tek bir değer ve bir genel döndürür olmasıdır <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7674b-134">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="7674b-135">Yöntemin kendisi kullanması gereken `foreach` değerini hesaplamak üzere.</span><span class="sxs-lookup"><span data-stu-id="7674b-135">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="7674b-136">Her bir önceki sorgu ile örtük yazarak kullanarak yazılabilir [var](../language-reference/keywords/var.md), aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="7674b-136">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="7674b-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="7674b-137">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="7674b-138">Karma sorgu ve yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7674b-138">Mixed query and method syntax</span></span>  
 <span data-ttu-id="7674b-139">Bu örnek bir sorgu yan tümcesinin sonuçlarını temel yöntem sözdizimi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7674b-139">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="7674b-140">Yalnızca sorgu ifadesi parantez içine alın ve ardından nokta işleci uygulamak ve yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7674b-140">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="7674b-141">Aşağıdaki örnekte, sorgu #7 değeri 3 ile 7 arasında olan sayıları sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7674b-141">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="7674b-142">Genel olarak, ancak bu yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="7674b-142">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="7674b-143">Bu şekilde, sorgu sorgu sonuçlarını kafası olması daha az olasıdır.</span><span class="sxs-lookup"><span data-stu-id="7674b-143">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 <span data-ttu-id="7674b-144">Sorgu #7 tek bir değer ve bir koleksiyon döndürdüğünden, sorguyu hemen yürütür.</span><span class="sxs-lookup"><span data-stu-id="7674b-144">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="7674b-145">Önceki sorgu ile örtük yazarak kullanarak yazılabilir `var`aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="7674b-145">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="7674b-146">Bunu şu şekilde yöntemi sözdiziminde yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="7674b-146">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="7674b-147">Açık, aşağıdaki gibi yazarak kullanarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="7674b-147">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="7674b-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7674b-148">See Also</span></span>  
  <span data-ttu-id="7674b-149">[İzlenecek yol: Sorguları C# ile yazma](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="7674b-149">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 [<span data-ttu-id="7674b-150">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7674b-150">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="7674b-151">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="7674b-151">where clause</span></span>](../language-reference/keywords/where-clause.md)
