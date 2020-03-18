---
title: C# içinde LINQ sorguları yazma
description: C#'da LINQ sorguları nasıl yazılanın öğrenin.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632885"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="53d7b-103">C'ye LINQ sorguları yazın\#</span><span class="sxs-lookup"><span data-stu-id="53d7b-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="53d7b-104">Bu makalede, C#'da bir LINQ sorgusu yazabileceğiniz üç yol gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="53d7b-105">Sorgu sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="53d7b-105">Use query syntax.</span></span>

2. <span data-ttu-id="53d7b-106">Yöntem sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="53d7b-106">Use method syntax.</span></span>

3. <span data-ttu-id="53d7b-107">Sorgu sözdizimi ve yöntem sözdizimi nin bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="53d7b-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="53d7b-108">Aşağıdaki örnekler, daha önce listelenen her yaklaşımı kullanarak bazı basit LINQ sorgularını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="53d7b-109">Genel olarak, kural (1) mümkün olduğunca kullanmak ve (2) ve (3) gerektiğinde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="53d7b-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="53d7b-110">Bu sorgular basit bellek içi koleksiyonlarda çalışır; ancak, temel sözdizimi Linq'de Kullanılanvarlıklarla ve LINQ'dan XML'e aynıdır.</span><span class="sxs-lookup"><span data-stu-id="53d7b-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="53d7b-111">Örnek - Sözdizimini sorgula</span><span class="sxs-lookup"><span data-stu-id="53d7b-111">Example - Query syntax</span></span>

<span data-ttu-id="53d7b-112">Çoğu sorgu yazmanın önerilen yolu sorgu *ifadeleri*oluşturmak için *sorgu sözdizimini* kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="53d7b-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="53d7b-113">Aşağıdaki örnekte üç sorgu ifadesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-113">The following example shows three query expressions.</span></span> <span data-ttu-id="53d7b-114">İlk sorgu ifadesi, bir `where` yan tümceyle koşullar uygulayarak sonuçların nasıl filtrelenebildiğini veya kısıtlanın.</span><span class="sxs-lookup"><span data-stu-id="53d7b-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="53d7b-115">Değerleri 7'den büyük veya 3'ten küçük olan kaynak dizisindeki tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="53d7b-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="53d7b-116">İkinci ifade, döndürülen sonuçların nasıl sıralanın gösterildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="53d7b-117">Üçüncü ifade, sonuçların bir anahtara göre nasıl gruplatını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="53d7b-118">Bu sorgu, sözcüğün ilk harfini temel alan iki grubu döndürür.</span><span class="sxs-lookup"><span data-stu-id="53d7b-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="53d7b-119">Sorguların türü . <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="53d7b-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="53d7b-120">Tüm bu sorgular aşağıdaki `var` örnekte gösterildiği gibi kullanılarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="53d7b-121">Önceki her örnekte, bir deyimveya başka bir `foreach` deyimdeki sorgu değişkeni üzerinde yinelene kadar sorgular gerçekten yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="53d7b-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="53d7b-122">Daha fazla bilgi için [LINQ Sorgularına Giriş'e](../programming-guide/concepts/linq/introduction-to-linq-queries.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="53d7b-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="53d7b-123">Örnek - Yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53d7b-123">Example - Method syntax</span></span>

<span data-ttu-id="53d7b-124">Bazı sorgu işlemleri bir yöntem çağrısı olarak ifade edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="53d7b-125">En yaygın bu tür yöntemler, singleton sayısal değerleri <xref:System.Linq.Enumerable.Sum%2A>döndüren yöntemlerdir, , , <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Average%2A>, ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="53d7b-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="53d7b-126">Bu yöntemler, yalnızca tek bir değeri temsil ettikleri ve ek bir sorgu işlemi için kaynak olarak hizmet veremedikleri nden, her zaman herhangi bir sorguda sonuncu olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53d7b-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="53d7b-127">Aşağıdaki örnekte sorgu ifadesinde bir yöntem çağrısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="53d7b-128">Yöntemde Action veya Func parametreleri varsa, bunlar aşağıdaki örnekte gösterildiği gibi [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) ifadesi biçiminde sağlanır:</span><span class="sxs-lookup"><span data-stu-id="53d7b-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="53d7b-129">Önceki sorgularda, yalnızca Sorgu #4 hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="53d7b-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="53d7b-130">Bunun nedeni, genel <xref:System.Collections.Generic.IEnumerable%601> bir koleksiyon değil, tek bir değer döndürmesidir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="53d7b-131">Yöntemin değerini hesaplamak için kendisi kullanmak `foreach` zorundadır.</span><span class="sxs-lookup"><span data-stu-id="53d7b-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="53d7b-132">Önceki sorguların her biri aşağıdaki örnekte gösterildiği [gibi, var](../language-reference/keywords/var.md)ile örtük yazarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="53d7b-133">Örnek - Karma sorgu ve yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53d7b-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="53d7b-134">Bu örnek, bir sorgu yan tümcesinin sonuçlarında yöntem sözdiziminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="53d7b-135">Sorgu ifadesini parantez içine eklemeniz ve nokta işlecini uygulayın ve yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="53d7b-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="53d7b-136">Aşağıdaki örnekte, sorgu #7 değeri 3 ile 7 arasında olan sayıların sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="53d7b-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="53d7b-137">Genel olarak, ancak, yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="53d7b-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="53d7b-138">Bu şekilde, sorgunun sorgu sonuçlarıyla karıştırılma olasılığı daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="53d7b-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="53d7b-139">Sorgu #7 bir koleksiyon değil, tek bir değer döndürdüğünden, sorgu hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="53d7b-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="53d7b-140">Önceki sorgu, aşağıdaki gibi örtülü `var`yazarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="53d7b-141">Yöntem sözdiziminde aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="53d7b-142">Aşağıdaki gibi, açık yazarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="53d7b-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="53d7b-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53d7b-143">See also</span></span>

- [<span data-ttu-id="53d7b-144">Walkthrough: C'de Sorgu Yazma #</span><span class="sxs-lookup"><span data-stu-id="53d7b-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="53d7b-145">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="53d7b-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="53d7b-146">where tümcesi</span><span class="sxs-lookup"><span data-stu-id="53d7b-146">where clause</span></span>](../language-reference/keywords/where-clause.md)
