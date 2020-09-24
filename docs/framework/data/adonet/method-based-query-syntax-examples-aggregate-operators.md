---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: toplu Işleçler (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: f702506e648c73dc179cf1755a467b13afce4bc6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164668"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="8e653-102">Yöntem tabanlı sorgu söz dizimi örnekleri: toplu Işleçler (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8e653-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="8e653-103">Bu konudaki örneklerde,,,,,, <xref:System.Linq.Enumerable.Aggregate%2A> <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> ve <xref:System.Linq.Enumerable.Sum%2A> işleçlerini <xref:System.Data.DataSet> Yöntem sorgu sözdizimini kullanarak bir ve verileri sorgulamak için nasıl kullanacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8e653-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="8e653-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8e653-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8e653-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e653-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8e653-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="8e653-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="8e653-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8e653-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="8e653-108">Toplama</span><span class="sxs-lookup"><span data-stu-id="8e653-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-109">Example</span></span>  

 <span data-ttu-id="8e653-110">Bu örnek, <xref:System.Linq.Enumerable.Aggregate%2A> tablosundan ilk 5 kişiyi almak `Contact` ve son adların virgülle ayrılmış bir listesini oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="8e653-111">Ortalama</span><span class="sxs-lookup"><span data-stu-id="8e653-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-112">Example</span></span>  

 <span data-ttu-id="8e653-113">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-114">Example</span></span>  

 <span data-ttu-id="8e653-115">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her stilin ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-116">Example</span></span>  

 <span data-ttu-id="8e653-117">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> süresi dolan ortalama toplamı bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-118">Example</span></span>  

 <span data-ttu-id="8e653-119">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her bir kışı kimliği için Ortalama toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-120">Example</span></span>  

 <span data-ttu-id="8e653-121">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her bir kişi için Ortalama olan siparişleri almak için yöntemini kullanır `TotalDue` .</span><span class="sxs-lookup"><span data-stu-id="8e653-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="8e653-122">Count</span><span class="sxs-lookup"><span data-stu-id="8e653-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-123">Example</span></span>  

 <span data-ttu-id="8e653-124">Bu örnek, <xref:System.Linq.Enumerable.Count%2A> tablodaki ürünlerin sayısını döndürmek için yöntemini kullanır `Product` .</span><span class="sxs-lookup"><span data-stu-id="8e653-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="8e653-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-125">Example</span></span>  

 <span data-ttu-id="8e653-126">Bu örnek, <xref:System.Linq.Enumerable.Count%2A> Iletişim kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="8e653-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-127">Example</span></span>  

 <span data-ttu-id="8e653-128">Bu örnek, ürünleri renge göre gruplandırır ve <xref:System.Linq.Enumerable.Count%2A> her renk grubundaki ürün sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="8e653-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="8e653-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-130">Example</span></span>  

 <span data-ttu-id="8e653-131">Bu örnek, iletişim sayısını uzun bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="8e653-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="8e653-132">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="8e653-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-133">Example</span></span>  

 <span data-ttu-id="8e653-134">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> en büyük toplam tarihi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-135">Example</span></span>  

 <span data-ttu-id="8e653-136">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> her bir kışı kimliği için en fazla toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-137">Example</span></span>  

 <span data-ttu-id="8e653-138">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> `TotalDue` her BIR kişi kimliği için en büyük olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="8e653-139">Min</span><span class="sxs-lookup"><span data-stu-id="8e653-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-140">Example</span></span>  

 <span data-ttu-id="8e653-141">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> süresi dolan en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-142">Example</span></span>  

 <span data-ttu-id="8e653-143">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> her bir kışı kimliği için en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-144">Example</span></span>  

 <span data-ttu-id="8e653-145">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> her kişi için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="8e653-146">Toplam</span><span class="sxs-lookup"><span data-stu-id="8e653-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e653-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-147">Example</span></span>  

 <span data-ttu-id="8e653-148">Bu örnek, <xref:System.Linq.Enumerable.Sum%2A> tablodaki toplam sipariş miktarı sayısını almak için yöntemini kullanır `SalesOrderDetail` .</span><span class="sxs-lookup"><span data-stu-id="8e653-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="8e653-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e653-149">Example</span></span>  

 <span data-ttu-id="8e653-150">Bu örnek, <xref:System.Linq.Enumerable.Sum%2A> her bir ILETIŞIM kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e653-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8e653-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e653-151">See also</span></span>

- [<span data-ttu-id="8e653-152">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="8e653-152">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="8e653-153">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="8e653-153">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="8e653-154">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="8e653-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8e653-155">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e653-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
