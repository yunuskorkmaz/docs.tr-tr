---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleştirme (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 84bd5f48c993dc5b15104b70081f739a1bec2e5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152483"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="d9a10-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleştirme (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d9a10-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="d9a10-103">Birleştirme, birbiriyle gezilebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi veri kaynakları hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d9a10-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="d9a10-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı ile bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerin ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="d9a10-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="d9a10-105">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9a10-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="d9a10-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Join%2A> sorgu yöntemine bir <xref:System.Data.DataSet> yöntemi sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d9a10-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="d9a10-107">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="d9a10-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d9a10-108">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9a10-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d9a10-109">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="d9a10-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d9a10-110">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d9a10-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="d9a10-111">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="d9a10-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="d9a10-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9a10-112">Example</span></span>  
 <span data-ttu-id="d9a10-113">Bu örnek üzerinde birleştirme gerçekleştirir `Contact` ve `SalesOrderHeader` tablolar.</span><span class="sxs-lookup"><span data-stu-id="d9a10-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="d9a10-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9a10-114">Example</span></span>  
 <span data-ttu-id="d9a10-115">Bu örnek üzerinde birleştirme gerçekleştirir `Contact` ve `SalesOrderHeader` sonuçlarına göre gruplandırma tablolar, bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="d9a10-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d9a10-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9a10-116">See also</span></span>

- [<span data-ttu-id="d9a10-117">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="d9a10-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="d9a10-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d9a10-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="d9a10-119">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d9a10-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d9a10-120">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9a10-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d9a10-121">Örnekleri katılın</span><span class="sxs-lookup"><span data-stu-id="d9a10-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="d9a10-122">Veri kümesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="d9a10-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
