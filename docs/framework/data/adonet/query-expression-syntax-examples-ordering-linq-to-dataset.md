---
description: 'Hakkında daha fazla bilgi edinin: sorgu Ifadesi sözdizimi örnekleri: sıralama (LINQ to DataSet)'
title: 'Sorgu Ifadesi söz dizimi örnekleri: sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: e47685e2aee8aae544a48c8e41eb99a1b76dd85a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663605"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="d1a24-103">Sorgu Ifadesi söz dizimi örnekleri: sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d1a24-103">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="d1a24-104">Bu konudaki örneklerde,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.Reverse%2A> ve <xref:System.Linq.Enumerable.ThenByDescending%2A> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak sonuçları sıralamak ve,,, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1a24-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="d1a24-105">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1a24-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d1a24-106">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1a24-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d1a24-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="d1a24-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d1a24-108">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d1a24-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="d1a24-109">OrderBy</span><span class="sxs-lookup"><span data-stu-id="d1a24-109">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="d1a24-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1a24-110">Example</span></span>  

 <span data-ttu-id="d1a24-111">Bu örnek <xref:System.Linq.Enumerable.OrderBy%2A> , son ada göre sıralanan kişilerin listesini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1a24-111">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="d1a24-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1a24-112">Example</span></span>  

 <span data-ttu-id="d1a24-113">Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> bir kişi listesini son ad uzunluğuna göre sıralamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1a24-113">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="d1a24-114">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="d1a24-114">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="d1a24-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1a24-115">Example</span></span>  

 <span data-ttu-id="d1a24-116">Bu örnekte, `orderby… descending` `Order By … Descending` <xref:System.Linq.Enumerable.OrderByDescending%2A> Fiyat listesini en yüksekten en düşüğe sıralamak için yöntemine eşdeğer olan () kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1a24-116">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="d1a24-117">Reverse</span><span class="sxs-lookup"><span data-stu-id="d1a24-117">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="d1a24-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1a24-118">Example</span></span>  

 <span data-ttu-id="d1a24-119">Bu örnek, <xref:System.Linq.Enumerable.Reverse%2A> `OrderDate` 20 Şubat 2002 ' den önceki bir siparişlerin listesini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1a24-119">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="d1a24-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="d1a24-120">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="d1a24-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1a24-121">Example</span></span>  

 <span data-ttu-id="d1a24-122">Bu örnekte, `OrderBy… Descending` <xref:System.Linq.Enumerable.ThenByDescending%2A> bir ürün listesini öncelikle ada ve sonra listenin fiyatını en yüksekten en düşüğe göre sıralamak için yöntemi ile eşdeğer olan bu örnek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1a24-122">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="d1a24-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1a24-123">See also</span></span>

- [<span data-ttu-id="d1a24-124">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="d1a24-124">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="d1a24-125">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d1a24-125">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="d1a24-126">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d1a24-126">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d1a24-127">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1a24-127">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
