---
title: Zincirleme sorgularının performansı-LINQ to XML
description: Zincirleme sorguları ve tek bir daha karmaşık sorgu hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553093"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a><span data-ttu-id="24ff4-103">Zincirleme sorguların performansı (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="24ff4-103">Performance of chained queries (LINQ to XML)</span></span>

<span data-ttu-id="24ff4-104">LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincirlenmiş sorguların yanı sıra zincirleme sorgulardan daha büyük ve daha karmaşık tek bir sorgu gerçekleştirebildiği bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="24ff4-104">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single query that is larger and more complicated than the chained queries.</span></span>

<span data-ttu-id="24ff4-105">Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="24ff4-105">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="24ff4-106">Örneğin, aşağıdaki basit kodda `query2` `query1` kaynağına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="24ff4-106">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="24ff4-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="24ff4-107">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="24ff4-108">Bu zincirleme sorgu, bağlantılı bir liste ile yineleme ile aynı performans profilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="24ff4-108">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="24ff4-109"><xref:System.Xml.Linq.XContainer.Elements%2A>Eksen temelde, bağlantılı bir liste ile yineleme ile aynı performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="24ff4-109">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="24ff4-110"><xref:System.Xml.Linq.XContainer.Elements%2A> , ertelenmiş yürütme ile bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="24ff4-110"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="24ff4-111">Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="24ff4-111">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="24ff4-112">Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş.</span><span class="sxs-lookup"><span data-stu-id="24ff4-112">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="24ff4-113">Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="24ff4-113">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>
- <span data-ttu-id="24ff4-114">`query1`' De, `where` yan tümce ( `Where` Visual Basic) sorgunun yöntemi çağırmasını sağlar <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="24ff4-114">In `query1`, the `where` clause (`Where` in Visual Basic) causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="24ff4-115">Bu yöntem ayrıca bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="24ff4-115">This method is also implemented as an iterator.</span></span> <span data-ttu-id="24ff4-116">Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur.</span><span class="sxs-lookup"><span data-stu-id="24ff4-116">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="24ff4-117">Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="24ff4-117">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="24ff4-118">Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="24ff4-118">The setup work and the work done during each iteration is similar to the work done while iterating through the axis.</span></span>
- <span data-ttu-id="24ff4-119">`query1`' De, select yan tümcesi sorgunun yöntemi çağırmasını sağlar <xref:System.Linq.Enumerable.Select%2A> .</span><span class="sxs-lookup"><span data-stu-id="24ff4-119">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="24ff4-120">Bu yöntem, yöntemiyle aynı performans profiline sahiptir <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="24ff4-120">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>
- <span data-ttu-id="24ff4-121">' De `query2` , `where` yan tümcesinin ( `Where` Visual Basic) ve `select` yan tümcesindeki ' de ile aynı performans profili vardır `query1` .</span><span class="sxs-lookup"><span data-stu-id="24ff4-121">In `query2`, both the `where` clause (`Where` in Visual Basic) and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="24ff4-122">`query2`Bu nedenle yineleme, diğer bir deyişle, doğrusal saat olan ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="24ff4-122">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

<span data-ttu-id="24ff4-123">Yineleyiciler hakkında daha fazla bilgi için bkz. [yield](../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="24ff4-123">For more information on iterators, see [yield](../../csharp/language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="24ff4-124">Sorguları birlikte zincirlemeye yönelik daha ayrıntılı bir öğretici için bkz. [öğretici: birlikte zinciri sorguları (C#)](chain-queries-example.md).</span><span class="sxs-lookup"><span data-stu-id="24ff4-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chain queries together (C#)](chain-queries-example.md).</span></span>
