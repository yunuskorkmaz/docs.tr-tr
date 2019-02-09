---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Toplama işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 88f7e71c3008818a657bc54ae6459e75359ab3f3
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903587"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="4ed2b-102">Metot tabanlı sorgu söz dizimi örnekleri: Toplama işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4ed2b-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="4ed2b-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Sum%2A> sorgu işleçleri bir <xref:System.Data.DataSet> yöntemi sorgusu kullanarak veri toplama söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="4ed2b-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="4ed2b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="4ed2b-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4ed2b-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="4ed2b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="4ed2b-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4ed2b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="4ed2b-108">Toplama</span><span class="sxs-lookup"><span data-stu-id="4ed2b-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-109">Example</span></span>  
 <span data-ttu-id="4ed2b-110">Bu örnekte <xref:System.Linq.Enumerable.Aggregate%2A> ilk 5 ilgili kişileri almak için yöntemi `Contact` tablo ve son adlarının virgülle ayrılmış bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="4ed2b-111">Ortalama</span><span class="sxs-lookup"><span data-stu-id="4ed2b-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-112">Example</span></span>  
 <span data-ttu-id="4ed2b-113">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama liste fiyatı ürünleri bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-114">Example</span></span>  
 <span data-ttu-id="4ed2b-115">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama liste fiyatı her stilin ürünleri bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-116">Example</span></span>  
 <span data-ttu-id="4ed2b-117">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama toplam son bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-118">Example</span></span>  
 <span data-ttu-id="4ed2b-119">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> kimliği her kişi için ortalama toplam son almak için yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ed2b-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-120">Example</span></span>  
 <span data-ttu-id="4ed2b-121">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> siparişleri ortalamasını almak için yöntemi `TotalDue` her kişi için.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="4ed2b-122">Sayı</span><span class="sxs-lookup"><span data-stu-id="4ed2b-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-123">Example</span></span>  
 <span data-ttu-id="4ed2b-124">Bu örnekte <xref:System.Linq.Enumerable.Count%2A> ürünlerin sayısını döndürmek için yöntemin `Product` tablo.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-125">Example</span></span>  
 <span data-ttu-id="4ed2b-126">Bu örnekte <xref:System.Linq.Enumerable.Count%2A> kişi kimlikleri listesini ve kaç her siparişleri döndürmek için yöntemin vardır.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-127">Example</span></span>  
 <span data-ttu-id="4ed2b-128">Bu örnekte, ürünleri rengine göre gruplandırır ve kullandığı <xref:System.Linq.Enumerable.Count%2A> ürün sayısı, her bir renk grubu geri dönmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="4ed2b-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="4ed2b-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-130">Example</span></span>  
 <span data-ttu-id="4ed2b-131">Bu örnek, kişi sayısı uzun bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="4ed2b-132">Maks.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-133">Example</span></span>  
 <span data-ttu-id="4ed2b-134">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süre almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-135">Example</span></span>  
 <span data-ttu-id="4ed2b-136">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-137">Example</span></span>  
 <span data-ttu-id="4ed2b-138">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> siparişleri en büyük almak için yöntemi `TotalDue` her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="4ed2b-139">Min.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-140">Example</span></span>  
 <span data-ttu-id="4ed2b-141">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam süre almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-142">Example</span></span>  
 <span data-ttu-id="4ed2b-143">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-144">Example</span></span>  
 <span data-ttu-id="4ed2b-145">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam siparişleri almak için yöntemi her kişi için son.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="4ed2b-146">Toplam</span><span class="sxs-lookup"><span data-stu-id="4ed2b-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="4ed2b-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-147">Example</span></span>  
 <span data-ttu-id="4ed2b-148">Bu örnekte <xref:System.Linq.Enumerable.Sum%2A> sipariş miktarlar toplam sayısını almak için yöntemi `SalesOrderDetail` tablo.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4ed2b-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed2b-149">Example</span></span>  
 <span data-ttu-id="4ed2b-150">Bu örnekte <xref:System.Linq.Enumerable.Sum%2A> toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4ed2b-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ed2b-151">See also</span></span>
- [<span data-ttu-id="4ed2b-152">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="4ed2b-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="4ed2b-153">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4ed2b-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="4ed2b-154">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="4ed2b-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4ed2b-155">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ed2b-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
