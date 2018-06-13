---
title: 'Sorgu ifade sözdizimi örnekleri: Sıralama (LINQ-DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 6df3e5f08e6f6a2058c44079c15da37ace3752c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352200"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="effce-102">Sorgu ifade sözdizimi örnekleri: Sıralama (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="effce-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="effce-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, ve <xref:System.Linq.Enumerable.ThenByDescending%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve sorgu ifade sözdizimi kullanarak sonuçları sıralayın.</span><span class="sxs-lookup"><span data-stu-id="effce-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="effce-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="effce-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="effce-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="effce-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="effce-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="effce-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="effce-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="effce-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="effce-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="effce-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="effce-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="effce-109">Example</span></span>  
 <span data-ttu-id="effce-110">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> kişiler son ada göre sıralanan listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="effce-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="effce-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="effce-111">Example</span></span>  
 <span data-ttu-id="effce-112">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> kişilerin listesini Soyadı uzunluğa göre sıralamak için.</span><span class="sxs-lookup"><span data-stu-id="effce-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="effce-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="effce-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="effce-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="effce-114">Example</span></span>  
 <span data-ttu-id="effce-115">Bu örnekte `orderby… descending` (`Order By … Descending`), eşdeğer olduğu <xref:System.Linq.Enumerable.OrderByDescending%2A> fiyat yüksekten en düşük sıralamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="effce-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="effce-116">Ters Çevir</span><span class="sxs-lookup"><span data-stu-id="effce-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="effce-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="effce-117">Example</span></span>  
 <span data-ttu-id="effce-118">Bu örnekte <xref:System.Linq.Enumerable.Reverse%2A> siparişleri listesini oluşturmak için burada `OrderDate` 20 Şub 2002'den daha eski.</span><span class="sxs-lookup"><span data-stu-id="effce-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="effce-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="effce-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="effce-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="effce-120">Example</span></span>  
 <span data-ttu-id="effce-121">Bu örnekte `OrderBy… Descending` , eşdeğer olduğu <xref:System.Linq.Enumerable.ThenByDescending%2A> ilk adı ve ardından göre yüksekten fiyat listesi, ürünlerin listesini düşük sıralamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="effce-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="effce-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="effce-122">See Also</span></span>  
 [<span data-ttu-id="effce-123">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="effce-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="effce-124">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="effce-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="effce-125">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="effce-125">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
