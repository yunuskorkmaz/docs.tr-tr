---
title: Zincirli Sorguların Performansı (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253117"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="c81a6-102">Zincirli Sorguların Performansı (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c81a6-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>

<span data-ttu-id="c81a6-103">LINQ'un (ve LINQ'dan XML'e) en önemli avantajlarından biri, zincirli sorguların yanı sıra tek bir daha büyük, daha karmaşık sorguyu gerçekleştirebiliyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c81a6-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="c81a6-104">Zincirlenmiş sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="c81a6-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="c81a6-105">Örneğin, aşağıdaki basit kod, `query2` `query1` kaynağı olarak vardır:</span><span class="sxs-lookup"><span data-stu-id="c81a6-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

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

<span data-ttu-id="c81a6-106">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c81a6-106">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="c81a6-107">Bu zincirleme sorgu, bağlantılı bir liste üzerinden yinelenen aynı performans profilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c81a6-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="c81a6-108">Eksen, <xref:System.Xml.Linq.XContainer.Elements%2A> bağlantılı bir liste boyunca yinelenmeyle temelde aynı performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c81a6-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="c81a6-109"><xref:System.Xml.Linq.XContainer.Elements%2A>ertelenmiş yürütme ile bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c81a6-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="c81a6-110">Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı liste yi yinelemeye ek olarak bazı işler yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c81a6-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="c81a6-111">Bu çalışma iki kategoriye ayrılabilir: yineleyicinin ayarlandığı anda yapılan iş ve her yineleme sırasında yapılan iş.</span><span class="sxs-lookup"><span data-stu-id="c81a6-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="c81a6-112">Kurulum çalışması küçük, sabit bir çalışma miktarıdır ve her yineleme sırasında yapılan iş kaynak koleksiyonundaki madde sayısıyla orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="c81a6-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="c81a6-113">In `query1`, `where` yan tümcesi <xref:System.Linq.Enumerable.Where%2A> sorgu yöntemi aramak için neden olur.</span><span class="sxs-lookup"><span data-stu-id="c81a6-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="c81a6-114">Bu yöntem aynı zamanda bir yineleyici olarak da uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c81a6-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="c81a6-115">Kurulum çalışması, lambda ifadesine başvurulacak temsilcinin yanı sıra bir yineleyici için normal kurulumun anlık olarak düzenlenmesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c81a6-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="c81a6-116">Her yinelemede, temsilci yüklemi yürütmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c81a6-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="c81a6-117">Kurulum çalışması ve her yineleme sırasında yapılan iş, eksen üzerinden yineleme yaparken yapılan işe benzer.</span><span class="sxs-lookup"><span data-stu-id="c81a6-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="c81a6-118">'de, `query1`select yan tümcesi sorgunun yöntemi ni aramasına <xref:System.Linq.Enumerable.Select%2A> neden olur.</span><span class="sxs-lookup"><span data-stu-id="c81a6-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="c81a6-119">Bu yöntem, yöntemle aynı <xref:System.Linq.Enumerable.Where%2A> performans profiline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c81a6-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="c81a6-120">In `query2`, `where` hem yan `select` tümcesi hem `query1`de yan tümcesi aynı performans profiline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c81a6-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="c81a6-121">Bu nedenle yineleme, ilk sorgunun kaynağındaki madde sayısıyla, başka bir deyişle doğrusal zamanla doğrusal olarak doğrusal olarak `query2` orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="c81a6-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="c81a6-122">İlgili Visual Basic örneği aynı performans profiline sahip olur.</span><span class="sxs-lookup"><span data-stu-id="c81a6-122">A corresponding Visual Basic example would have the same performance profile.</span></span>

<span data-ttu-id="c81a6-123">Yineleyiciler hakkında daha fazla bilgi için [bkz.](../../../language-reference/keywords/yield.md)</span><span class="sxs-lookup"><span data-stu-id="c81a6-123">For more information on iterators, see [yield](../../../language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="c81a6-124">Sorguları birbirine zincirleme konusunda daha ayrıntılı bir öğretici için [Bkz. Öğretici: Sorguları Birlikte Zincirleme.](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="c81a6-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>
