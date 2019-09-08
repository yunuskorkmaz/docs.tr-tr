---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Işleç ayarlama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783582"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="23d6d-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Işleç ayarlama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="23d6d-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="23d6d-103">Bu konudaki örneklerde, veri satırı kümelerinde değer tabanlı karşılaştırma <xref:System.Linq.Enumerable.Distinct%2A>işlemleri <xref:System.Linq.Enumerable.Except%2A>gerçekleştirmek <xref:System.Linq.Enumerable.Intersect%2A>için, <xref:System.Linq.Enumerable.Union%2A> , ve işleçlerinin nasıl kullanılacağı gösterilmektedir.[ Veri kümesine veri yükleme](loading-data-into-a-dataset.md) hakkında <xref:System.Data.DataRowComparer>daha fazla bilgi Için bkz. [DataRow karşılaştırması](comparing-datarows-linq-to-dataset.md) .</span><span class="sxs-lookup"><span data-stu-id="23d6d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="23d6d-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23d6d-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="23d6d-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="23d6d-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="23d6d-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="23d6d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="23d6d-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="23d6d-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="23d6d-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="23d6d-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="23d6d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d6d-109">Example</span></span>  
 <span data-ttu-id="23d6d-110">Bu örnek, <xref:System.Linq.Enumerable.Distinct%2A> bir dizideki yinelenen öğeleri kaldırmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23d6d-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="23d6d-111">Dışlama</span><span class="sxs-lookup"><span data-stu-id="23d6d-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="23d6d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d6d-112">Example</span></span>  
 <span data-ttu-id="23d6d-113">Bu örnek, ilk <xref:System.Linq.Enumerable.Except%2A> tabloda görünen ancak ikincide olmayan kişileri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23d6d-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="23d6d-114">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="23d6d-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="23d6d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d6d-115">Example</span></span>  
 <span data-ttu-id="23d6d-116">Bu örnek, <xref:System.Linq.Enumerable.Intersect%2A> her iki tabloda görünen kişileri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23d6d-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="23d6d-117">UNION</span><span class="sxs-lookup"><span data-stu-id="23d6d-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="23d6d-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d6d-118">Example</span></span>  
 <span data-ttu-id="23d6d-119">Bu örnek, <xref:System.Linq.Enumerable.Union%2A> iki tablodan birindeki benzersiz kişileri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23d6d-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="23d6d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23d6d-120">See also</span></span>

- [<span data-ttu-id="23d6d-121">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="23d6d-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="23d6d-122">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="23d6d-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="23d6d-123">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="23d6d-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="23d6d-124">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23d6d-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
