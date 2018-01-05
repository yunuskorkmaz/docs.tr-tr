---
title: "Sorgu ifade sözdizimi örnekleri: Sıralama (LINQ-DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a138580ba3111bd5706aa7b073755cb494ae96ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="30fdb-102">Sorgu ifade sözdizimi örnekleri: Sıralama (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="30fdb-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="30fdb-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, ve <xref:System.Linq.Enumerable.ThenByDescending%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve sorgu ifade sözdizimi kullanarak sonuçları sıralayın.</span><span class="sxs-lookup"><span data-stu-id="30fdb-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="30fdb-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="30fdb-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="30fdb-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="30fdb-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="30fdb-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="30fdb-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="30fdb-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="30fdb-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="30fdb-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="30fdb-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="30fdb-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fdb-109">Example</span></span>  
 <span data-ttu-id="30fdb-110">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> kişiler son ada göre sıralanan listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="30fdb-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="30fdb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fdb-111">Example</span></span>  
 <span data-ttu-id="30fdb-112">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> kişilerin listesini Soyadı uzunluğa göre sıralamak için.</span><span class="sxs-lookup"><span data-stu-id="30fdb-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="30fdb-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="30fdb-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="30fdb-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fdb-114">Example</span></span>  
 <span data-ttu-id="30fdb-115">Bu örnekte `orderby… descending` (`Order By … Descending`), eşdeğer olduğu <xref:System.Linq.Enumerable.OrderByDescending%2A> fiyat yüksekten en düşük sıralamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="30fdb-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="30fdb-116">Ters Çevir</span><span class="sxs-lookup"><span data-stu-id="30fdb-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="30fdb-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fdb-117">Example</span></span>  
 <span data-ttu-id="30fdb-118">Bu örnekte <xref:System.Linq.Enumerable.Reverse%2A> siparişleri listesini oluşturmak için burada `OrderDate` 20 Şub 2002'den daha eski.</span><span class="sxs-lookup"><span data-stu-id="30fdb-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="30fdb-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="30fdb-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="30fdb-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="30fdb-120">Example</span></span>  
 <span data-ttu-id="30fdb-121">Bu örnekte `OrderBy… Descending` , eşdeğer olduğu <xref:System.Linq.Enumerable.ThenByDescending%2A> ilk adı ve ardından göre yüksekten fiyat listesi, ürünlerin listesini düşük sıralamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="30fdb-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="30fdb-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30fdb-122">See Also</span></span>  
 [<span data-ttu-id="30fdb-123">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="30fdb-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="30fdb-124">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="30fdb-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="30fdb-125">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30fdb-125">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
