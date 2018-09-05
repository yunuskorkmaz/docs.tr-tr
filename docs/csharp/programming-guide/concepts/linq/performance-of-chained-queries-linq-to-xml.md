---
title: Performans zincirleme sorgu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 6f127f14a488158d219f37ccd467543be1c86bde
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530295"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="cffda-102">Performans zincirleme sorgu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cffda-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="cffda-103">LINQ (ve LINQ to XML) en önemli avantajlarından biri, zincir sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirilebiliyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="cffda-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="cffda-104">Zincirleme bir sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="cffda-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="cffda-105">Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:</span><span class="sxs-lookup"><span data-stu-id="cffda-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
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
  
 <span data-ttu-id="cffda-106">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cffda-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="cffda-107">Bu Zincirli sorgu ile bağlantılı bir liste yineleme aynı performans profili sağlar.</span><span class="sxs-lookup"><span data-stu-id="cffda-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="cffda-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Eksen sahip bir bağlantılı listede yineleme olarak temelde aynı performans.</span><span class="sxs-lookup"><span data-stu-id="cffda-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="cffda-109"><xref:System.Xml.Linq.XContainer.Elements%2A> Ertelenmiş yürütme ile bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cffda-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="cffda-110">Bu, bazı iş Ayrıca bağlantılı liste yineleme gibi yineleyici nesnesinden ayırma ve yürütme durumunu izlemek için yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cffda-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="cffda-111">Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından zamanda ve her yinelemede bitti iş bitti iş.</span><span class="sxs-lookup"><span data-stu-id="cffda-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="cffda-112">İş küçük, sabit bir miktarda Kurulum çalışmadır ve her yineleme sırasında çalışmanın kaynak koleksiyondaki öğe sayısı ile orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="cffda-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="cffda-113">İçinde `query1`, `where` çağırmak sorgu yan tümcesi neden <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cffda-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="cffda-114">Bu yöntem aynı zamanda bir yineleyici uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cffda-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="cffda-115">Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum Bakacağınız temsilci örnekleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="cffda-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="cffda-116">Her yineleme ile koşul yürütmek için temsilci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cffda-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="cffda-117">Kurulum çalışması ve her yineleme sırasında çalışmanın benzer çalışmanın eksen yineleme sırasında.</span><span class="sxs-lookup"><span data-stu-id="cffda-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="cffda-118">İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cffda-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="cffda-119">Bu yöntem aynı performans profili sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cffda-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="cffda-120">İçinde `query2`hem `where` yan tümcesi ve `select` yan tümcesine sahip olarak aynı performans profili `query1`.</span><span class="sxs-lookup"><span data-stu-id="cffda-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="cffda-121">Üzerinden yineleme `query2` ilk kaynak öğe sayısını orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman, bu nedenle olur.</span><span class="sxs-lookup"><span data-stu-id="cffda-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="cffda-122">Karşılık gelen bir Visual Basic örneği aynı performans profili gerekir.</span><span class="sxs-lookup"><span data-stu-id="cffda-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="cffda-123">Yineleyiciler hakkında daha fazla bilgi için bkz. [yield](../../../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="cffda-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="cffda-124">Daha ayrıntılı bir eğitim sorguları birbirine zincirleme hakkında bilgi için bkz [öğretici: sorguları birbirine zincirleme](https://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span><span class="sxs-lookup"><span data-stu-id="cffda-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](https://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cffda-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cffda-125">See Also</span></span>

- [<span data-ttu-id="cffda-126">Performans (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cffda-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
