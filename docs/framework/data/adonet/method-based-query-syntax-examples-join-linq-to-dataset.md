---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleştir (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: ba6e33f98e063aab946db27b97106272c5adef63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783667"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="6e1fa-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleştir (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6e1fa-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="6e1fa-103">Birleştirme, ilişkisel veritabanı tabloları gibi birbirleriyle gezinebilir ilişki bulunmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="6e1fa-104">İki veri kaynağının birleşimi, bir veri kaynağındaki nesnelerin diğer veri kaynağında ortak bir özniteliği paylaşan nesneler ile ilişkilendirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="6e1fa-105">Daha fazla bilgi için bkz. [Standart sorgu işleçlerineC#genel bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçleri genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6e1fa-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="6e1fa-106">Bu konudaki örneklerde, yönteminin sorgu söz dizimini <xref:System.Linq.Enumerable.Join%2A> <xref:System.Data.DataSet> kullanarak sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="6e1fa-107">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6e1fa-108">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6e1fa-109">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="6e1fa-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="6e1fa-110">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="6e1fa-111">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="6e1fa-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="6e1fa-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e1fa-112">Example</span></span>  
 <span data-ttu-id="6e1fa-113">Bu örnek, `Contact` ve `SalesOrderHeader` tabloları üzerinde bir JOIN gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="6e1fa-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e1fa-114">Example</span></span>  
 <span data-ttu-id="6e1fa-115">Bu örnek, `Contact` ve `SalesOrderHeader` tabloları üzerinde bir JOIN gerçekleştirerek sonuçları ilgili kişi kimliğine göre gruplandırıyor.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6e1fa-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e1fa-116">See also</span></span>

- [<span data-ttu-id="6e1fa-117">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="6e1fa-117">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="6e1fa-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6e1fa-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="6e1fa-119">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="6e1fa-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6e1fa-120">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e1fa-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6e1fa-121">Örneklere katılarak</span><span class="sxs-lookup"><span data-stu-id="6e1fa-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="6e1fa-122">Veri kümesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="6e1fa-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
