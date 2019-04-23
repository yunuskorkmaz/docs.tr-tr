---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Ayarlama işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 48aa6044f39be93f144b6c4af5137b131dda0b30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085824"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="69450-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Ayarlama işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="69450-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="69450-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, ve <xref:System.Linq.Enumerable.Union%2A> veri satırları kümelerinin değer tabanlı karşılaştırma işlemleri gerçekleştirmek için işleçleri.[ Verileri içine bir DataSet yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) bkz [DataRow karşılaştırma](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) hakkında daha fazla bilgi için <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="69450-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="69450-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="69450-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="69450-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="69450-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="69450-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="69450-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="69450-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="69450-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="69450-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="69450-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="69450-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="69450-109">Example</span></span>  
 <span data-ttu-id="69450-110">Bu örnekte <xref:System.Linq.Enumerable.Distinct%2A> yöntemi bir dizideki yinelenen öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="69450-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="69450-111">Dışlama</span><span class="sxs-lookup"><span data-stu-id="69450-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="69450-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="69450-112">Example</span></span>  
 <span data-ttu-id="69450-113">Bu örnekte <xref:System.Linq.Enumerable.Except%2A> görünen kişileri ilk tablonun ancak ikinci döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="69450-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="69450-114">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="69450-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="69450-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="69450-115">Example</span></span>  
 <span data-ttu-id="69450-116">Bu örnekte <xref:System.Linq.Enumerable.Intersect%2A> her iki tabloda görünen kişileri döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="69450-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="69450-117">UNION</span><span class="sxs-lookup"><span data-stu-id="69450-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="69450-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="69450-118">Example</span></span>  
 <span data-ttu-id="69450-119">Bu örnekte <xref:System.Linq.Enumerable.Union%2A> benzersiz kişiler iki tablo birini döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="69450-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="69450-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69450-120">See also</span></span>

- [<span data-ttu-id="69450-121">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="69450-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="69450-122">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="69450-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="69450-123">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="69450-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="69450-124">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69450-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
