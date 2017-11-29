---
title: "Sorgu ifade sözdizimi örnekleri: Birleştirme işleçleri (LINQ-DataSet)"
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
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 28f2627e991d6761306d6655ad4b2e3c0f61ebfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="6a24a-102">Sorgu ifade sözdizimi örnekleri: Birleştirme işleçleri (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="6a24a-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="6a24a-103">Birleştirme, birbirlerine, gezinebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi sahip veri kaynaklarına hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="6a24a-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="6a24a-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağının diğer veri kaynağındaki ortak bir özniteliği paylaşan nesnelerle ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="6a24a-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="6a24a-105">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="6a24a-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="6a24a-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6a24a-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="6a24a-107">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="6a24a-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6a24a-108">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a24a-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6a24a-109">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="6a24a-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="6a24a-110">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6a24a-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="6a24a-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="6a24a-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="6a24a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a24a-112">Example</span></span>  
 <span data-ttu-id="6a24a-113">Bu örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> üzerinden `SalesOrderHeader` ve `SalesOrderDetail` tabloları başına müşteri siparişi sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="6a24a-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="6a24a-114">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="6a24a-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="6a24a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a24a-115">Example</span></span>  
 <span data-ttu-id="6a24a-116">Bu örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> üzerinden `Contact` ve `SalesOrderHeader` tabloları.</span><span class="sxs-lookup"><span data-stu-id="6a24a-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="6a24a-117">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="6a24a-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="6a24a-118">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="6a24a-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="6a24a-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a24a-119">Example</span></span>  
 <span data-ttu-id="6a24a-120">Bu örnek üzerinde birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` Ağustos, month çevrimiçi olarak sipariş almak için tablo.</span><span class="sxs-lookup"><span data-stu-id="6a24a-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="6a24a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a24a-121">See Also</span></span>  
 [<span data-ttu-id="6a24a-122">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="6a24a-122">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="6a24a-123">LINQ-DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="6a24a-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="6a24a-124">Standart sorgu işleçlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="6a24a-124">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
