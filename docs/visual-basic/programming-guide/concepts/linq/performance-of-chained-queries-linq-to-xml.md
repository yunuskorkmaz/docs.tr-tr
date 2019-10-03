---
title: Zincirleme sorgularının performansı (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 69ed09addb50ac45e7b46cd0322d4df076b5875b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834960"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="9e6bd-102">Zincirleme sorgularının performansı (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e6bd-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="9e6bd-103">LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincir sorgularının ve çok daha karmaşık bir sorgunun gerçekleştirebildiği bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="9e6bd-104">Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="9e6bd-105">Örneğin, aşağıdaki basit kodda `query2`, kaynağı olarak `query1` ' dir:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="9e6bd-106">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="9e6bd-107">Bu zincirleme sorgu, bağlantılı bir liste ile yineleme ile aynı performans profilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="9e6bd-108">@No__t-0 ekseni temelde bağlı bir liste ile yineleme ile aynı performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="9e6bd-109"><xref:System.Xml.Linq.XContainer.Elements%2A>, ertelenmiş yürütme ile bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="9e6bd-110">Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="9e6bd-111">Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="9e6bd-112">Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="9e6bd-113">@No__t-0 ' da `Where` yan tümcesi sorgunun <xref:System.Linq.Enumerable.Where%2A> metodunu çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="9e6bd-114">Bu yöntem ayrıca bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="9e6bd-115">Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="9e6bd-116">Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="9e6bd-117">Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzer.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="9e6bd-118">@No__t-0 ' da, select yan tümcesi sorgunun <xref:System.Linq.Enumerable.Select%2A> metodunu çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="9e6bd-119">Bu yöntemin <xref:System.Linq.Enumerable.Where%2A> yöntemiyle aynı performans profili vardır.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="9e6bd-120">@No__t-0 ' da, hem `Where` yan tümcesi hem de `Select` yan tümcesi `query1` ' teki aynı performans profiline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="9e6bd-121">@No__t-0 ile yineleme, diğer bir deyişle, doğrusal bir süre içinde ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e6bd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-122">See also</span></span>

- [<span data-ttu-id="9e6bd-123">Performans (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e6bd-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
