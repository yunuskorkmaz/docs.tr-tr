---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: JOIN (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 8bfcd8ae5d81c0d04ca7a43e6d5b25a492266605
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189350"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="05484-102">Yöntem tabanlı sorgu söz dizimi örnekleri: JOIN (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="05484-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>

<span data-ttu-id="05484-103">Birleştirme, ilişkisel veritabanı tabloları gibi birbirleriyle gezinebilir ilişki bulunmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="05484-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="05484-104">İki veri kaynağının birleşimi, bir veri kaynağındaki nesnelerin diğer veri kaynağında ortak bir özniteliği paylaşan nesneler ile ilişkilendirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="05484-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="05484-105">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="05484-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="05484-106">Bu konudaki örneklerde, yönteminin <xref:System.Linq.Enumerable.Join%2A> <xref:System.Data.DataSet> sorgu söz dizimini kullanarak sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05484-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="05484-107">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05484-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="05484-108">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05484-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="05484-109">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="05484-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="05484-110">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="05484-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="05484-111">Birleştir</span><span class="sxs-lookup"><span data-stu-id="05484-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="05484-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="05484-112">Example</span></span>  

 <span data-ttu-id="05484-113">Bu örnek, ve tabloları üzerinde bir JOIN gerçekleştirir `Contact` `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="05484-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="05484-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="05484-114">Example</span></span>  

 <span data-ttu-id="05484-115">Bu örnek, ve tabloları üzerinde bir JOIN gerçekleştirerek `Contact` `SalesOrderHeader` sonuçları ılgılı kişi kimliğine göre gruplandırıyor.</span><span class="sxs-lookup"><span data-stu-id="05484-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="05484-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05484-116">See also</span></span>

- [<span data-ttu-id="05484-117">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="05484-117">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="05484-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="05484-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="05484-119">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="05484-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="05484-120">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05484-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="05484-121">Örneklere katılarak</span><span class="sxs-lookup"><span data-stu-id="05484-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="05484-122">Veri kümesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="05484-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
