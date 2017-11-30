---
title: "Zincirleme sorgu (LINQ-XML) performansını (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 281eb8ea62760507da991ea878270befe458bb38
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="52353-102">Zincirleme sorgu (LINQ-XML) performansını (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52353-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="52353-103">LINQ (ve LINQ-XML) en önemli avantajları zincirleme sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirebilirsiniz biridir.</span><span class="sxs-lookup"><span data-stu-id="52353-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="52353-104">Başka bir sorgu, kaynağı olarak kullanan bir sorgu bir zincirleme sorgudur.</span><span class="sxs-lookup"><span data-stu-id="52353-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="52353-105">Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:</span><span class="sxs-lookup"><span data-stu-id="52353-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 <span data-ttu-id="52353-106">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="52353-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="52353-107">Bu zincirleme sorgu bağlantılı listesini yineleme olarak aynı performans profili sağlar.</span><span class="sxs-lookup"><span data-stu-id="52353-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="52353-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Eksen bağlantılı listesini yineleme olarak temelde aynı performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="52353-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="52353-109"><xref:System.Xml.Linq.XContainer.Elements%2A>Ertelenmiş yürütme ile yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="52353-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="52353-110">Bu, bazı iş Ayrıca bağlantılı liste yineleme yapma gibi yineleyici nesne ayırma ve yürütme durumu izlemek için yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52353-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="52353-111">Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından saat ve her yinelemede yapılır iş yapılan iş.</span><span class="sxs-lookup"><span data-stu-id="52353-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="52353-112">Kurulum çalışması küçük, sabit bir tutar iş ve her yinelemede çalışmanın kaynak koleksiyondaki öğe sayısını doğru orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="52353-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="52353-113">İçinde `query1`, `Where` yan tümcesi neden çağırmak sorgu <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52353-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="52353-114">Bu yöntem aynı zamanda yineleyici uygulanır.</span><span class="sxs-lookup"><span data-stu-id="52353-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="52353-115">Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum başvurur temsilci başlatmasını oluşur.</span><span class="sxs-lookup"><span data-stu-id="52353-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="52353-116">Her bir yineleme, koşul yürütmek için temsilci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="52353-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="52353-117">Kurulum çalışması ve her yinelemede çalışmanın benzer çalışmanın eksen yineleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="52353-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="52353-118">İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52353-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="52353-119">Bu yöntem olarak aynı performans profiline sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52353-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="52353-120">İçinde `query2`, her iki `Where` yan tümcesi ve `Select` yan tümcesi bulunan aynı performans profili olarak `query1`.</span><span class="sxs-lookup"><span data-stu-id="52353-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="52353-121">Üzerinden yineleme `query2` ilk kaynağındaki öğelerin sayısı orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman bu nedenle olur.</span><span class="sxs-lookup"><span data-stu-id="52353-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52353-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52353-122">See Also</span></span>  
 [<span data-ttu-id="52353-123">Performans (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52353-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
