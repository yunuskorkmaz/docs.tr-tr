---
title: Performans zincirleme sorgu (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336371"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="715ea-102">Performans zincirleme sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="715ea-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="715ea-103">LINQ (ve LINQ-XML) en önemli avantajları zincirleme sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirebilirsiniz biridir.</span><span class="sxs-lookup"><span data-stu-id="715ea-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="715ea-104">Başka bir sorgu, kaynağı olarak kullanan bir sorgu bir zincirleme sorgudur.</span><span class="sxs-lookup"><span data-stu-id="715ea-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="715ea-105">Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:</span><span class="sxs-lookup"><span data-stu-id="715ea-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
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
  
 <span data-ttu-id="715ea-106">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="715ea-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="715ea-107">Bu zincirleme sorgu bağlantılı listesini yineleme olarak aynı performans profili sağlar.</span><span class="sxs-lookup"><span data-stu-id="715ea-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="715ea-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Eksen bağlantılı listesini yineleme olarak temelde aynı performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="715ea-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="715ea-109"><xref:System.Xml.Linq.XContainer.Elements%2A> Ertelenmiş yürütme ile yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="715ea-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="715ea-110">Bu, bazı iş Ayrıca bağlantılı liste yineleme yapma gibi yineleyici nesne ayırma ve yürütme durumu izlemek için yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="715ea-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="715ea-111">Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından saat ve her yinelemede yapılır iş yapılan iş.</span><span class="sxs-lookup"><span data-stu-id="715ea-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="715ea-112">Kurulum çalışması küçük, sabit bir tutar iş ve her yinelemede çalışmanın kaynak koleksiyondaki öğe sayısını doğru orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="715ea-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="715ea-113">İçinde `query1`, `where` yan tümcesi neden çağırmak sorgu <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="715ea-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="715ea-114">Bu yöntem aynı zamanda yineleyici uygulanır.</span><span class="sxs-lookup"><span data-stu-id="715ea-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="715ea-115">Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum başvurur temsilci başlatmasını oluşur.</span><span class="sxs-lookup"><span data-stu-id="715ea-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="715ea-116">Her bir yineleme, koşul yürütmek için temsilci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="715ea-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="715ea-117">Kurulum çalışması ve her yinelemede çalışmanın benzer çalışmanın eksen yineleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="715ea-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="715ea-118">İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="715ea-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="715ea-119">Bu yöntem olarak aynı performans profiline sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="715ea-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="715ea-120">İçinde `query2`, her iki `where` yan tümcesi ve `select` yan tümcesi bulunan aynı performans profili olarak `query1`.</span><span class="sxs-lookup"><span data-stu-id="715ea-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="715ea-121">Üzerinden yineleme `query2` ilk kaynağındaki öğelerin sayısı orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman bu nedenle olur.</span><span class="sxs-lookup"><span data-stu-id="715ea-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="715ea-122">Karşılık gelen bir Visual Basic örnek aynı performans profili olması.</span><span class="sxs-lookup"><span data-stu-id="715ea-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="715ea-123">Yineleyiciler hakkında daha fazla bilgi için bkz: [verim](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="715ea-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="715ea-124">Sorguları birlikte zincirleme üzerinde daha ayrıntılı öğretici için bkz [Öğreticisi: sorguları birlikte zincirleme](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span><span class="sxs-lookup"><span data-stu-id="715ea-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715ea-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="715ea-125">See Also</span></span>  
 [<span data-ttu-id="715ea-126">Performans (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="715ea-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
