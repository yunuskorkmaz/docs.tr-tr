---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: b8f605eaa3a186ebb6bad7800d6576bd4d5a34b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203905"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="5ac05-102">Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5ac05-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="5ac05-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, ve <xref:System.Linq.Enumerable.ThenByDescending%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve sorgu ifadesi söz dizimi kullanarak sonuçları sıralayabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac05-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="5ac05-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5ac05-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="5ac05-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5ac05-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5ac05-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="5ac05-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="5ac05-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5ac05-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="5ac05-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="5ac05-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="5ac05-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac05-109">Example</span></span>  
 <span data-ttu-id="5ac05-110">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> kişileri soyadına göre sıralanmış bir listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="5ac05-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="5ac05-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac05-111">Example</span></span>  
 <span data-ttu-id="5ac05-112">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> Soyadı uzunluğuna kişilerin listesini sıralamak için.</span><span class="sxs-lookup"><span data-stu-id="5ac05-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="5ac05-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="5ac05-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="5ac05-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac05-114">Example</span></span>  
 <span data-ttu-id="5ac05-115">Bu örnekte `orderby… descending` (`Order By … Descending`), eşdeğer olan <xref:System.Linq.Enumerable.OrderByDescending%2A> fiyat listesinin en yüksekten en düşük sıralamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ac05-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="5ac05-116">geriye doğru</span><span class="sxs-lookup"><span data-stu-id="5ac05-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="5ac05-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac05-117">Example</span></span>  
 <span data-ttu-id="5ac05-118">Bu örnekte <xref:System.Linq.Enumerable.Reverse%2A> siparişlerinin listesi oluşturmak için burada `OrderDate` 20 Şubat 2002 ' daha eski.</span><span class="sxs-lookup"><span data-stu-id="5ac05-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="5ac05-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="5ac05-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="5ac05-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac05-120">Example</span></span>  
 <span data-ttu-id="5ac05-121">Bu örnekte `OrderBy… Descending` , eşdeğer olan <xref:System.Linq.Enumerable.ThenByDescending%2A> en düşük öncelikle adına ve ardından göre en yüksekten liste fiyatı, ürünlerin listesini sıralamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ac05-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="5ac05-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac05-122">See also</span></span>

- [<span data-ttu-id="5ac05-123">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="5ac05-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="5ac05-124">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="5ac05-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="5ac05-125">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="5ac05-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="5ac05-126">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ac05-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
