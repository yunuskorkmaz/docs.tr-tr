---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 932f5e4f6073844a951d06dabec45e5ff3e743bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782998"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="0b26d-102">Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0b26d-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="0b26d-103">Bu konudaki örneklerde,, ve sorgu ifadesi söz dizimini <xref:System.Linq.Enumerable.OrderBy%2A>kullanarak <xref:System.Linq.Enumerable.OrderByDescending%2A>sonuçları <xref:System.Linq.Enumerable.Reverse%2A>sıralamak <xref:System.Data.DataSet> ve <xref:System.Linq.Enumerable.ThenByDescending%2A> ,,, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b26d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="0b26d-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b26d-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0b26d-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b26d-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0b26d-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="0b26d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0b26d-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b26d-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="0b26d-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="0b26d-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b26d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b26d-109">Example</span></span>  
 <span data-ttu-id="0b26d-110">Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> son ada göre sıralanan kişilerin listesini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b26d-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="0b26d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b26d-111">Example</span></span>  
 <span data-ttu-id="0b26d-112">Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> bir kişi listesini son ad uzunluğuna göre sıralamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b26d-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="0b26d-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="0b26d-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b26d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b26d-114">Example</span></span>  
 <span data-ttu-id="0b26d-115">Bu örnekte, `orderby… descending` fiyat`Order By … Descending`listesini en yüksekten en düşüğe <xref:System.Linq.Enumerable.OrderByDescending%2A> sıralamak için yöntemine eşdeğer olan () kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b26d-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="0b26d-116">Tersini</span><span class="sxs-lookup"><span data-stu-id="0b26d-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b26d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b26d-117">Example</span></span>  
 <span data-ttu-id="0b26d-118">Bu örnek, <xref:System.Linq.Enumerable.Reverse%2A> 20 Şubat 2002 ' den önceki bir `OrderDate` siparişlerin listesini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b26d-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="0b26d-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="0b26d-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="0b26d-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b26d-120">Example</span></span>  
 <span data-ttu-id="0b26d-121">Bu örnekte, `OrderBy… Descending` bir ürün listesini öncelikle ada ve <xref:System.Linq.Enumerable.ThenByDescending%2A> sonra listenin fiyatını en yüksekten en düşüğe göre sıralamak için yöntemi ile eşdeğer olan bu örnek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b26d-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="0b26d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b26d-122">See also</span></span>

- [<span data-ttu-id="0b26d-123">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="0b26d-123">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0b26d-124">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0b26d-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0b26d-125">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="0b26d-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0b26d-126">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b26d-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
