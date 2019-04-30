---
title: Zincirleme sorgular (LINQ to XML) performansını (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8634ca224f5892918721996114649c392a5080a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665877"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="5b18e-102">Zincirleme sorgular (LINQ to XML) performansını (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b18e-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="5b18e-103">LINQ (ve LINQ to XML) en önemli avantajlarından biri, zincir sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirilebiliyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5b18e-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="5b18e-104">Zincirleme bir sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur.</span><span class="sxs-lookup"><span data-stu-id="5b18e-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="5b18e-105">Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:</span><span class="sxs-lookup"><span data-stu-id="5b18e-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="5b18e-106">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5b18e-106">This example produces the following output:</span></span>

```
4
```

<span data-ttu-id="5b18e-107">Bu Zincirli sorgu ile bağlantılı bir liste yineleme aynı performans profili sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b18e-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="5b18e-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Eksen sahip bir bağlantılı listede yineleme olarak temelde aynı performans.</span><span class="sxs-lookup"><span data-stu-id="5b18e-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="5b18e-109"><xref:System.Xml.Linq.XContainer.Elements%2A> Ertelenmiş yürütme ile bir yineleyici olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5b18e-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="5b18e-110">Bu, bazı iş Ayrıca bağlantılı liste yineleme gibi yineleyici nesnesinden ayırma ve yürütme durumunu izlemek için yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b18e-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="5b18e-111">Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından zamanda ve her yinelemede bitti iş bitti iş.</span><span class="sxs-lookup"><span data-stu-id="5b18e-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="5b18e-112">İş küçük, sabit bir miktarda Kurulum çalışmadır ve her yineleme sırasında çalışmanın kaynak koleksiyondaki öğe sayısı ile orantılıdır.</span><span class="sxs-lookup"><span data-stu-id="5b18e-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="5b18e-113">İçinde `query1`, `Where` çağırmak sorgu yan tümcesi neden <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b18e-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="5b18e-114">Bu yöntem aynı zamanda bir yineleyici uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5b18e-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="5b18e-115">Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum Bakacağınız temsilci örnekleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="5b18e-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="5b18e-116">Her yineleme ile koşul yürütmek için temsilci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5b18e-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="5b18e-117">Kurulum çalışması ve her yineleme sırasında çalışmanın benzer çalışmanın eksen yineleme sırasında.</span><span class="sxs-lookup"><span data-stu-id="5b18e-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="5b18e-118">İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b18e-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="5b18e-119">Bu yöntem aynı performans profili sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b18e-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="5b18e-120">İçinde `query2`hem `Where` yan tümcesi ve `Select` yan tümcesine sahip olarak aynı performans profili `query1`.</span><span class="sxs-lookup"><span data-stu-id="5b18e-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="5b18e-121">Üzerinden yineleme `query2` ilk kaynak öğe sayısını orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman, bu nedenle olur.</span><span class="sxs-lookup"><span data-stu-id="5b18e-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b18e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b18e-122">See also</span></span>

- [<span data-ttu-id="5b18e-123">Performans (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b18e-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
