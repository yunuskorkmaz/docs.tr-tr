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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 608587080cfbcfe7c5b2b16235a540c0711f7c3c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="5e8e4-102">Sorgu ifade sözdizimi örnekleri: Birleştirme işleçleri (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="5e8e4-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="5e8e4-103">Birleştirme, birbirlerine, gezinebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi sahip veri kaynaklarına hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="5e8e4-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağının diğer veri kaynağındaki ortak bir özniteliği paylaşan nesnelerle ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="5e8e4-105">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="5e8e4-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="5e8e4-107">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="5e8e4-108">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5e8e4-109">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="5e8e4-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="5e8e4-110">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5e8e4-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="5e8e4-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="5e8e4-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e8e4-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e8e4-112">Example</span></span>  
 <span data-ttu-id="5e8e4-113">Bu örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> üzerinden `SalesOrderHeader` ve `SalesOrderDetail` tabloları başına müşteri siparişi sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="5e8e4-114">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="5e8e4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e8e4-115">Example</span></span>  
 <span data-ttu-id="5e8e4-116">Bu örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> üzerinden `Contact` ve `SalesOrderHeader` tabloları.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="5e8e4-117">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="5e8e4-118">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="5e8e4-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e8e4-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e8e4-119">Example</span></span>  
 <span data-ttu-id="5e8e4-120">Bu örnek üzerinde birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` Ağustos, month çevrimiçi olarak sipariş almak için tablo.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="5e8e4-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e8e4-121">See Also</span></span>  
 [<span data-ttu-id="5e8e4-122">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="5e8e4-122">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="5e8e4-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="5e8e4-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="5e8e4-124">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e8e4-124">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
