---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu sözdizimi örnekleri: Işleç ayarlama (LINQ to DataSet)'
title: 'Method-Based sorgu söz dizimi örnekleri: set Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 3a50c9793e3af6fdab08227b4789c4042dd64931
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723757"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="0ec50-103">Method-Based sorgu söz dizimi örnekleri: set Işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0ec50-103">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="0ec50-104">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Except%2A> <xref:System.Linq.Enumerable.Intersect%2A> <xref:System.Linq.Enumerable.Union%2A> veri satırı kümelerinde değer tabanlı karşılaştırma işlemleri gerçekleştirmek için,, ve işleçlerinin[ nasıl kullanılacağı gösterilmektedir. Veri kümesine veri yükleme](loading-data-into-a-dataset.md) hakkında daha fazla bilgi için bkz. [DataRow karşılaştırması](comparing-datarows-linq-to-dataset.md) <xref:System.Data.DataRowComparer> .</span><span class="sxs-lookup"><span data-stu-id="0ec50-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="0ec50-105">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ec50-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0ec50-106">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ec50-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0ec50-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="0ec50-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0ec50-108">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0ec50-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="0ec50-109">Distinct</span><span class="sxs-lookup"><span data-stu-id="0ec50-109">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ec50-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ec50-110">Example</span></span>  

 <span data-ttu-id="0ec50-111">Bu örnek, <xref:System.Linq.Enumerable.Distinct%2A> bir dizideki yinelenen öğeleri kaldırmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ec50-111">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="0ec50-112">Dışlama</span><span class="sxs-lookup"><span data-stu-id="0ec50-112">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ec50-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ec50-113">Example</span></span>  

 <span data-ttu-id="0ec50-114">Bu örnek, <xref:System.Linq.Enumerable.Except%2A> ilk tabloda görünen ancak ikincide olmayan kişileri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ec50-114">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="0ec50-115">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="0ec50-115">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ec50-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ec50-116">Example</span></span>  

 <span data-ttu-id="0ec50-117">Bu örnek, <xref:System.Linq.Enumerable.Intersect%2A> her iki tabloda görünen kişileri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ec50-117">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="0ec50-118">Birleşim</span><span class="sxs-lookup"><span data-stu-id="0ec50-118">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ec50-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ec50-119">Example</span></span>  

 <span data-ttu-id="0ec50-120">Bu örnek, <xref:System.Linq.Enumerable.Union%2A> iki tablodan birindeki benzersiz kişileri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ec50-120">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="0ec50-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ec50-121">See also</span></span>

- [<span data-ttu-id="0ec50-122">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="0ec50-122">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0ec50-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0ec50-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0ec50-124">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="0ec50-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0ec50-125">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ec50-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
