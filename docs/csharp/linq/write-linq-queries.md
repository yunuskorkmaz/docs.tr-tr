---
title: C# içinde LINQ sorguları yazma
description: C# dilinde LINQ sorguları yazmayı öğrenin.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: bd7da81f2873c6a25570cab32fafecc66fd98be4
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063451"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="af1a0-103">C 'de LINQ sorguları yazma\#</span><span class="sxs-lookup"><span data-stu-id="af1a0-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="af1a0-104">Bu makalede C# dilinde LINQ sorgusu yazabileceğiniz üç yol gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="af1a0-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="af1a0-105">Sorgu söz dizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="af1a0-105">Use query syntax.</span></span>

2. <span data-ttu-id="af1a0-106">Yöntem sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="af1a0-106">Use method syntax.</span></span>

3. <span data-ttu-id="af1a0-107">Sorgu söz dizimi ve Yöntem sözdizimi birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="af1a0-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="af1a0-108">Aşağıdaki örneklerde, daha önce listelenen her yaklaşımı kullanarak bazı basit LINQ sorguları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="af1a0-109">Genel olarak, kural mümkün olduğunca (1) kullanılır ve gerektiğinde (2) ve (3) kullanır.</span><span class="sxs-lookup"><span data-stu-id="af1a0-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="af1a0-110">Bu sorgular, basit bellek içi koleksiyonlar üzerinde çalışır; Ancak, temel sözdizimi LINQ to Entities ve LINQ to XML ' de kullanılan ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="af1a0-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="af1a0-111">Örnek-sorgu söz dizimi</span><span class="sxs-lookup"><span data-stu-id="af1a0-111">Example - Query syntax</span></span>

<span data-ttu-id="af1a0-112">Çoğu sorgu yazmak için önerilen yol sorgu *ifadelerini*oluşturmak için *sorgu sözdizimini* kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="af1a0-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="af1a0-113">Aşağıdaki örnek, üç sorgu ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-113">The following example shows three query expressions.</span></span> <span data-ttu-id="af1a0-114">İlk sorgu ifadesi, bir yan tümcesiyle koşulları uygulayarak sonuçların nasıl filtreleneceğini veya kısıtlanacağını gösterir `where` .</span><span class="sxs-lookup"><span data-stu-id="af1a0-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="af1a0-115">Kaynak dizisindeki, değerleri 7 ' den büyük veya 3 ' ten küçük olan tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="af1a0-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="af1a0-116">İkinci ifade, döndürülen sonuçların nasıl sıraya alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="af1a0-117">Üçüncü ifade, sonuçların bir anahtara göre nasıl gruplandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="af1a0-118">Bu sorgu, sözcüğün ilk harfine göre iki grup döndürür.</span><span class="sxs-lookup"><span data-stu-id="af1a0-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="af1a0-119">Sorguların türünün olduğunu unutmayın <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="af1a0-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="af1a0-120">Bu sorguların hepsi `var` , aşağıdaki örnekte gösterildiği gibi kullanılarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="af1a0-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="af1a0-121">Bir önceki örnekte, sorgu değişkeni üzerinde veya başka bir bildirimde yineleme yapana kadar sorgular aslında yürütülmez `foreach` .</span><span class="sxs-lookup"><span data-stu-id="af1a0-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="af1a0-122">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="af1a0-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="af1a0-123">Örnek yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af1a0-123">Example - Method syntax</span></span>

<span data-ttu-id="af1a0-124">Bazı sorgu işlemleri bir yöntem çağrısı olarak ifade edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="af1a0-125">En sık kullanılan yöntemler,,,, vb. gibi tekil sayısal değerler döndüren <xref:System.Linq.Enumerable.Sum%2A> olanlardır <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Average%2A> .</span><span class="sxs-lookup"><span data-stu-id="af1a0-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="af1a0-126">Yalnızca tek bir değeri temsil ettiğinden ve ek bir sorgu işlemi için kaynak olarak işlev veremediği için, bu yöntemlerin her zaman herhangi bir sorguda en son çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="af1a0-127">Aşağıdaki örnek bir sorgu ifadesinde bir yöntem çağrısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="af1a0-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="af1a0-128">Yöntemin Action veya Func parametreleri varsa, bunlar aşağıdaki örnekte gösterildiği gibi bir [lambda](../language-reference/operators/lambda-expressions.md) ifadesi biçiminde sağlanır:</span><span class="sxs-lookup"><span data-stu-id="af1a0-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../language-reference/operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="af1a0-129">Önceki sorgularda yalnızca Query #4 hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="af1a0-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="af1a0-130">Bunun nedeni, genel bir koleksiyon değil tek bir değer döndürmektedir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="af1a0-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="af1a0-131">Metodun kendi `foreach` değerini hesaplamak için kullanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="af1a0-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="af1a0-132">Önceki sorguların her biri, aşağıdaki örnekte gösterildiği gibi, [var](../language-reference/keywords/var.md)ile örtük yazma kullanılarak yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="af1a0-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="af1a0-133">Örnek-karışık sorgu ve Yöntem sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af1a0-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="af1a0-134">Bu örnek, bir sorgu yan tümcesinin sonuçlarında Yöntem sözdiziminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="af1a0-135">Sorgu ifadesini parantez içine almalısınız ve sonra nokta işlecini uygulayıp yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="af1a0-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="af1a0-136">Aşağıdaki örnekte, Query #7 değeri 3 ile 7 arasında olan sayıların sayımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="af1a0-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="af1a0-137">Ancak genel olarak, yöntem çağrısının sonucunu depolamak için ikinci bir değişken kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="af1a0-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="af1a0-138">Bu şekilde sorgunun sonuçlarıyla karışması daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="af1a0-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="af1a0-139">Sorgu #7 bir koleksiyon değil tek bir değer döndürdüğünden sorgu hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="af1a0-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="af1a0-140">Önceki sorgu, aşağıdaki gibi örtük yazma kullanılarak yazılabilir `var` :</span><span class="sxs-lookup"><span data-stu-id="af1a0-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="af1a0-141">Yöntem sözdiziminde aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="af1a0-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="af1a0-142">Açık yazma kullanılarak şu şekilde yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="af1a0-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="af1a0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1a0-143">See also</span></span>

- [<span data-ttu-id="af1a0-144">İzlenecek yol: C 'de sorgu yazma #</span><span class="sxs-lookup"><span data-stu-id="af1a0-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="af1a0-145">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="af1a0-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="af1a0-146">where tümcesi</span><span class="sxs-lookup"><span data-stu-id="af1a0-146">where clause</span></span>](../language-reference/keywords/where-clause.md)
