---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Birleşim (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 6ec65cad0070bdbd1d510bcc822f3b71f9cf69dc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195299"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="2cff8-102">Metot tabanlı sorgu söz dizimi örnekleri: Birleşim (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2cff8-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="2cff8-103">Birleştirme, birbiriyle gezilebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi veri kaynakları hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2cff8-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="2cff8-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı ile bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerin ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="2cff8-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="2cff8-105">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="2cff8-105">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="2cff8-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Join%2A> sorgu yöntemine bir <xref:System.Data.DataSet> yöntemi sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2cff8-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="2cff8-107">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2cff8-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2cff8-108">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2cff8-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2cff8-109">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="2cff8-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="2cff8-110">Daha fazla bilgi için [nasıl yapılır: bir LINQ to DataSet proje Visual Studio'da oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2cff8-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="2cff8-111">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="2cff8-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="2cff8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cff8-112">Example</span></span>  
 <span data-ttu-id="2cff8-113">Bu örnek üzerinde birleştirme gerçekleştirir `Contact` ve `SalesOrderHeader` tablolar.</span><span class="sxs-lookup"><span data-stu-id="2cff8-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="2cff8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cff8-114">Example</span></span>  
 <span data-ttu-id="2cff8-115">Bu örnek üzerinde birleştirme gerçekleştirir `Contact` ve `SalesOrderHeader` sonuçlarına göre gruplandırma tablolar, bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="2cff8-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2cff8-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cff8-116">See Also</span></span>  
 [<span data-ttu-id="2cff8-117">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="2cff8-117">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="2cff8-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="2cff8-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="2cff8-119">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2cff8-119">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [<span data-ttu-id="2cff8-120">Örnekleri katılın</span><span class="sxs-lookup"><span data-stu-id="2cff8-120">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)  
 [<span data-ttu-id="2cff8-121">Veri kümesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="2cff8-121">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
