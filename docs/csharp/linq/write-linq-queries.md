---
title: C# içinde LINQ sorguları yazma
description: Nasıl yazılacağını sorgular.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: a9683dbf3c4101829054477824ccc7135f20f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288843"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="d7e83-103">C# içinde LINQ sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="d7e83-103">Write LINQ queries in C#</span></span>

<span data-ttu-id="d7e83-104">Bu konu, C# üzerinde LINQ sorgu yazabilirsiniz üç şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="d7e83-104">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="d7e83-105">Sorgu sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7e83-105">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="d7e83-106">Yöntemi sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7e83-106">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="d7e83-107">Sorgu sözdizimi ve yöntem sözdizimi bileşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7e83-107">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="d7e83-108">Aşağıdaki örnekler, daha önce listelenen her bir yaklaşım kullanarak bazı basit LINQ sorgularını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="d7e83-109">Genel olarak, kullanım (1) mümkün olduğunda ve Kullan (2) ve (3) gerektiğinde kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="d7e83-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7e83-110">Bu sorguları basit bellek içi koleksiyonlar üzerinde çalışır; Ancak, temel sözdizimi LINQ to Entities ve LINQ-XML kullanılan aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d7e83-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7e83-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7e83-111">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="d7e83-112">Sorgu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e83-112">Query syntax</span></span>  
 <span data-ttu-id="d7e83-113">Sorguların çoğu yazmak için önerilen yöntem kullanmaktır *sorgu sözdizimi* oluşturmak için *sorgu ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="d7e83-113">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="d7e83-114">Aşağıdaki örnekte, üç sorgu ifadeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-114">The following example shows three query expressions.</span></span> <span data-ttu-id="d7e83-115">Filtre veya koşullar uygulayarak sonuçları kısıtlamak nasıl ilk sorgu ifadesi gösteren bir `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d7e83-115">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="d7e83-116">Değerleri 7 veya 3'ten az büyük olan kaynak dizisindeki tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d7e83-116">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="d7e83-117">İkinci ifade döndürülen sonuçların sipariş gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-117">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="d7e83-118">Üçüncü ifade, sonuçları bir anahtar göre gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-118">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="d7e83-119">Bu sorgu sözcüğün ilk harfini göre iki grupları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d7e83-119">This query returns two groups based on the first letter of the word.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 <span data-ttu-id="d7e83-120">Sorguları türünde Not <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d7e83-120">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d7e83-121">Tüm bu sorguları kullanarak yazılabilir `var` aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d7e83-121">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="d7e83-122">Sorgu değişkeninde üzerinden yineleme kadar her önceki örnekte sorguları gerçekte yürütmeme bir `foreach` deyimi veya diğer deyimi.</span><span class="sxs-lookup"><span data-stu-id="d7e83-122">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="d7e83-123">Daha fazla bilgi için bkz: [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d7e83-123">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7e83-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7e83-124">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="d7e83-125">Yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e83-125">Method syntax</span></span>  
 <span data-ttu-id="d7e83-126">Bazı sorgu işlemleri bir yöntem çağrısı ifade edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-126">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="d7e83-127">En yaygın tür yöntem dönüş singleton sayısal değerleri gibi izinlerdir <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="d7e83-127">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="d7e83-128">Yalnızca tek bir değeri temsil eder ve bir ek sorgu işlemi için kaynak olarak sunulamıyor olduğundan bu yöntemlerin her zaman içinde herhangi bir sorgu son çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7e83-128">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="d7e83-129">Aşağıdaki örnek, sorgu ifadesinde bir yöntem çağrısı gösterir:</span><span class="sxs-lookup"><span data-stu-id="d7e83-129">The following example shows a method call in a query expression:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="d7e83-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7e83-130">Example</span></span>  
 <span data-ttu-id="d7e83-131">Yöntem bir eylem veya Func parametrelere sahipse, bunlar biçiminde sağlanan bir [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi ifade:</span><span class="sxs-lookup"><span data-stu-id="d7e83-131">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 <span data-ttu-id="d7e83-132">Önceki sorgularında yalnızca sorgu #4 hemen yürütür.</span><span class="sxs-lookup"><span data-stu-id="d7e83-132">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="d7e83-133">Tek bir değer ve bir genel döndürür olmasıdır <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d7e83-133">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="d7e83-134">Yöntemin kendisi kullanması gereken `foreach` değerini hesaplamak üzere.</span><span class="sxs-lookup"><span data-stu-id="d7e83-134">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="d7e83-135">Her bir önceki sorgu ile örtük yazarak kullanarak yazılabilir [var](../language-reference/keywords/var.md), aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d7e83-135">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="d7e83-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7e83-136">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="d7e83-137">Karma sorgu ve yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e83-137">Mixed query and method syntax</span></span>  
 <span data-ttu-id="d7e83-138">Bu örnek bir sorgu yan tümcesinin sonuçlarını temel yöntem sözdizimi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-138">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="d7e83-139">Yalnızca sorgu ifadesi parantez içine alın ve ardından nokta işleci uygulamak ve yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d7e83-139">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="d7e83-140">Aşağıdaki örnekte, sorgu #7 değeri 3 ile 7 arasında olan sayıları sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d7e83-140">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="d7e83-141">Genel olarak, ancak bu yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="d7e83-141">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="d7e83-142">Bu şekilde, sorgu sorgu sonuçlarını kafası olması daha az olasıdır.</span><span class="sxs-lookup"><span data-stu-id="d7e83-142">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 <span data-ttu-id="d7e83-143">Sorgu #7 tek bir değer ve bir koleksiyon döndürdüğünden, sorguyu hemen yürütür.</span><span class="sxs-lookup"><span data-stu-id="d7e83-143">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="d7e83-144">Önceki sorgu ile örtük yazarak kullanarak yazılabilir `var`aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="d7e83-144">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="d7e83-145">Bunu şu şekilde yöntemi sözdiziminde yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d7e83-145">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="d7e83-146">Açık, aşağıdaki gibi yazarak kullanarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d7e83-146">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7e83-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e83-147">See Also</span></span>  
  <span data-ttu-id="d7e83-148">[İzlenecek yol: Sorguları C# ile yazma](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d7e83-148">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 [<span data-ttu-id="d7e83-149">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d7e83-149">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="d7e83-150">where yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d7e83-150">where clause</span></span>](../language-reference/keywords/where-clause.md)
