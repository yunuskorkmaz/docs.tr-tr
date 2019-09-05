---
title: Zincirleme sorgularının performansı (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253117"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="5b7c7-102">Zincirleme sorgularının performansı (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5b7c7-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="5b7c7-103">LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincir sorgularının ve çok daha karmaşık bir sorgunun gerçekleştirebildiği bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="5b7c7-104">Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="5b7c7-105">Örneğin, aşağıdaki basit kodda `query2` kaynağına sahiptir: `query1`</span><span class="sxs-lookup"><span data-stu-id="5b7c7-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="5b7c7-106">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5b7c7-106">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="5b7c7-107">Bu zincirleme sorgu, bağlantılı bir liste ile yineleme ile aynı performans profilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="5b7c7-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Eksen temelde, bağlantılı bir liste ile yineleme ile aynı performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="5b7c7-109"><xref:System.Xml.Linq.XContainer.Elements%2A>, ertelenmiş yürütme ile bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="5b7c7-110">Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="5b7c7-111">Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="5b7c7-112">Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="5b7c7-113">İçinde `query1` <xref:System.Linq.Enumerable.Where%2A> , yantümcesorgununyöntemiçağırmasınısağlar.`where`</span><span class="sxs-lookup"><span data-stu-id="5b7c7-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="5b7c7-114">Bu yöntem ayrıca bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="5b7c7-115">Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="5b7c7-116">Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="5b7c7-117">Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzer.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="5b7c7-118">' `query1`De, select yan tümcesi sorgunun <xref:System.Linq.Enumerable.Select%2A> yöntemi çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="5b7c7-119">Bu yöntem, <xref:System.Linq.Enumerable.Where%2A> yöntemiyle aynı performans profiline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="5b7c7-120">' `query2`De, `where` yan tümcesi ve `select` `query1`yan tümcesi, ile aynı performans profiline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="5b7c7-121">Bu nedenle yineleme `query2` , diğer bir deyişle, doğrusal saat olan ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="5b7c7-122">Karşılık gelen bir Visual Basic örneği aynı performans profiline sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="5b7c7-123">Yineleyiciler hakkında daha fazla bilgi için bkz. [yield](../../../language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="5b7c7-123">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="5b7c7-124">Sorguları birlikte zincirlemeye yönelik daha ayrıntılı bir öğretici için bkz [. Öğretici: Sorguları birlikte](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)zincirleme.</span><span class="sxs-lookup"><span data-stu-id="5b7c7-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
