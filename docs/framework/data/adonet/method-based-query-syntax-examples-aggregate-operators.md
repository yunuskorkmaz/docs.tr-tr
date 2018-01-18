---
title: "Yöntem temelli sorgu sözdizimi örnekler: Toplama işleçleri (LINQ-DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56188c42fabc678c2f5689f0ca09136c5556f189
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="31aa2-102">Yöntem temelli sorgu sözdizimi örnekler: Toplama işleçleri (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="31aa2-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="31aa2-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Sum%2A> sorgu işleçleri bir <xref:System.Data.DataSet> yöntemi sorgu kullanarak verileri toplama söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="31aa2-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="31aa2-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="31aa2-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="31aa2-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="31aa2-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="31aa2-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="31aa2-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="31aa2-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="31aa2-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="31aa2-108">Toplama</span><span class="sxs-lookup"><span data-stu-id="31aa2-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-109">Example</span></span>  
 <span data-ttu-id="31aa2-110">Bu örnekte <xref:System.Linq.Enumerable.Aggregate%2A> ilk 5 kişilerden almak için yöntemi `Contact` tablo ve son adlarının virgülle ayrılmış bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="31aa2-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="31aa2-111">Ortalama</span><span class="sxs-lookup"><span data-stu-id="31aa2-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-112">Example</span></span>  
 <span data-ttu-id="31aa2-113">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ürünleri ortalama fiyat listesi bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="31aa2-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-114">Example</span></span>  
 <span data-ttu-id="31aa2-115">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> her stil ürünleri ortalama fiyat listesi bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="31aa2-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-116">Example</span></span>  
 <span data-ttu-id="31aa2-117">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama toplam son bulma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31aa2-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-118">Example</span></span>  
 <span data-ttu-id="31aa2-119">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> her kişi için ortalama toplam son almak için yöntemi kimliği</span><span class="sxs-lookup"><span data-stu-id="31aa2-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-120">Example</span></span>  
 <span data-ttu-id="31aa2-121">Bu örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama siparişleri almak için yöntemi `TotalDue` her kişi için.</span><span class="sxs-lookup"><span data-stu-id="31aa2-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="31aa2-122">Sayısı</span><span class="sxs-lookup"><span data-stu-id="31aa2-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-123">Example</span></span>  
 <span data-ttu-id="31aa2-124">Bu örnekte <xref:System.Linq.Enumerable.Count%2A> ürünlerinde sayısını döndürmek için yöntemin `Product` tablo.</span><span class="sxs-lookup"><span data-stu-id="31aa2-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-125">Example</span></span>  
 <span data-ttu-id="31aa2-126">Bu örnekte <xref:System.Linq.Enumerable.Count%2A> kişi kimlikleri listesini ve kaç tane her siparişleri döndürülecek yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="31aa2-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-127">Example</span></span>  
 <span data-ttu-id="31aa2-128">Bu örnek ürünleri rengine göre gruplandırır ve kullandığı <xref:System.Linq.Enumerable.Count%2A> yöntemi her renk grubundaki ürünlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="31aa2-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="31aa2-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="31aa2-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-130">Example</span></span>  
 <span data-ttu-id="31aa2-131">Bu örnek kişi sayısını uzun tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="31aa2-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="31aa2-132">Maks.</span><span class="sxs-lookup"><span data-stu-id="31aa2-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-133">Example</span></span>  
 <span data-ttu-id="31aa2-134">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süresi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31aa2-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-135">Example</span></span>  
 <span data-ttu-id="31aa2-136">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süresi almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="31aa2-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-137">Example</span></span>  
 <span data-ttu-id="31aa2-138">Bu örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük siparişleri almak için yöntemi `TotalDue` her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="31aa2-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="31aa2-139">Min.</span><span class="sxs-lookup"><span data-stu-id="31aa2-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-140">Example</span></span>  
 <span data-ttu-id="31aa2-141">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> en küçük toplam süresi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31aa2-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-142">Example</span></span>  
 <span data-ttu-id="31aa2-143">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> en küçük toplam süresi almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="31aa2-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-144">Example</span></span>  
 <span data-ttu-id="31aa2-145">Bu örnekte <xref:System.Linq.Enumerable.Min%2A> en küçük toplam siparişleri almak için yöntemi her kişi için son.</span><span class="sxs-lookup"><span data-stu-id="31aa2-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="31aa2-146">TOPLA</span><span class="sxs-lookup"><span data-stu-id="31aa2-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="31aa2-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-147">Example</span></span>  
 <span data-ttu-id="31aa2-148">Bu örnekte <xref:System.Linq.Enumerable.Sum%2A> siparişi miktarlarında toplam sayısını almak üzere yöntemi `SalesOrderDetail` tablo.</span><span class="sxs-lookup"><span data-stu-id="31aa2-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31aa2-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="31aa2-149">Example</span></span>  
 <span data-ttu-id="31aa2-150">Bu örnekte <xref:System.Linq.Enumerable.Sum%2A> toplam süresi almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="31aa2-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="31aa2-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31aa2-151">See Also</span></span>  
 [<span data-ttu-id="31aa2-152">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="31aa2-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="31aa2-153">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="31aa2-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="31aa2-154">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31aa2-154">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
