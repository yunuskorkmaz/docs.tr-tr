---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: JOIN Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: c150cb14c567590daa7ffb2ea77893598977bdf9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794868"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="e2331-102">Sorgu İfadesi Söz Dizimi Örnekleri: JOIN Işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e2331-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="e2331-103">Birleştirme, ilişkisel veritabanı tabloları gibi birbirleriyle gezinebilir ilişki bulunmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="e2331-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="e2331-104">İki veri kaynağının birleşimi, bir veri kaynağındaki nesnelerin diğer veri kaynağında ortak bir özniteliği paylaşan nesneler ile ilişkilendirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="e2331-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="e2331-105">Daha fazla bilgi için bkz. [Standart sorgu işleçlerineC#genel bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçleri genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2331-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="e2331-106">Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak bir <xref:System.Linq.Enumerable.GroupJoin%2A> <xref:System.Data.DataSet> sorgusu <xref:System.Linq.Enumerable.Join%2A> sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e2331-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="e2331-107">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2331-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e2331-108">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2331-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e2331-109">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="e2331-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="e2331-110">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2331-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="e2331-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="e2331-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="e2331-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2331-112">Example</span></span>  
 <span data-ttu-id="e2331-113">Bu örnek, `SalesOrderHeader` müşteri <xref:System.Linq.Enumerable.GroupJoin%2A> başına sipariş sayısını `SalesOrderDetail` bulmak için ve tabloları üzerinde bir gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e2331-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="e2331-114">Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="e2331-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="e2331-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2331-115">Example</span></span>  
 <span data-ttu-id="e2331-116">Bu örnek, `Contact` ve <xref:System.Linq.Enumerable.GroupJoin%2A> `SalesOrderHeader` tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="e2331-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="e2331-117">Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="e2331-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="e2331-118">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="e2331-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="e2331-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2331-119">Example</span></span>  
 <span data-ttu-id="e2331-120">Bu örnek, `SalesOrderHeader` Ağustos ayına ait çevrimiçi siparişleri `SalesOrderDetail` almak için ve tabloları üzerinde bir JOIN işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e2331-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="e2331-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2331-121">See also</span></span>

- [<span data-ttu-id="e2331-122">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="e2331-122">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="e2331-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e2331-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="e2331-124">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="e2331-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e2331-125">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2331-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
