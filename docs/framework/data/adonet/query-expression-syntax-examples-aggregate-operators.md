---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Toplama işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: e7151fd85c7e3988051ed87a60acc2b53a8af646
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122778"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="b8b8a-102">Sorgu İfadesi Söz Dizimi Örnekleri: Toplama işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="b8b8a-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="b8b8a-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Sum%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve sorgu ifadesi söz dizimi kullanarak verileri.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="b8b8a-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b8b8a-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="b8b8a-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b8b8a-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="b8b8a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="b8b8a-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b8b8a-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="b8b8a-108">Ortalama</span><span class="sxs-lookup"><span data-stu-id="b8b8a-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="b8b8a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-109">Example</span></span>  
 <span data-ttu-id="b8b8a-110">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama liste fiyatı her stilin ürünleri bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="b8b8a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-111">Example</span></span>  
 <span data-ttu-id="b8b8a-112">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama toplam son her biri için almak için kimliği başvurun</span><span class="sxs-lookup"><span data-stu-id="b8b8a-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="b8b8a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-113">Example</span></span>  
 <span data-ttu-id="b8b8a-114">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> siparişleri ortalaması alınacak `TotalDue` her kişi için.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="b8b8a-115">Sayı</span><span class="sxs-lookup"><span data-stu-id="b8b8a-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="b8b8a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-116">Example</span></span>  
 <span data-ttu-id="b8b8a-117">Bu örnekte <xref:System.Linq.Enumerable.Count%2A> kişi kimlikleri listesini ve kaç her siparişleri döndürmek için vardır.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="b8b8a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-118">Example</span></span>  
 <span data-ttu-id="b8b8a-119">Bu örnekte, ürünleri rengine göre gruplandırır ve kullandığı <xref:System.Linq.Enumerable.Count%2A> ürün sayısı, her bir renk grubu döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="b8b8a-120">Maks.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="b8b8a-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-121">Example</span></span>  
 <span data-ttu-id="b8b8a-122">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="b8b8a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-123">Example</span></span>  
 <span data-ttu-id="b8b8a-124">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> siparişleri en büyük almak için yöntemi `TotalDue` her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="b8b8a-125">Min.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="b8b8a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-126">Example</span></span>  
 <span data-ttu-id="b8b8a-127">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="b8b8a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-128">Example</span></span>  
 <span data-ttu-id="b8b8a-129">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam siparişleri almak için yöntemi her kişi için son.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="b8b8a-130">Toplam</span><span class="sxs-lookup"><span data-stu-id="b8b8a-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="b8b8a-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b8a-131">Example</span></span>  
 <span data-ttu-id="b8b8a-132">Bu örnekte <xref:System.Linq.Enumerable.Sum%2A> toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="b8b8a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b8a-133">See also</span></span>

- [<span data-ttu-id="b8b8a-134">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="b8b8a-134">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="b8b8a-135">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="b8b8a-135">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="b8b8a-136">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="b8b8a-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b8b8a-137">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b8a-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
