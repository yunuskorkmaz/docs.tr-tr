---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: toplama Işleçleri'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 26398af95398905f2e28c603ef90a04a4a2c56bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673623"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="ac58a-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler</span><span class="sxs-lookup"><span data-stu-id="ac58a-103">Method-Based Query Syntax Examples: Aggregate Operators</span></span>

<span data-ttu-id="ac58a-104">Bu konudaki örneklerde,,,,, <xref:System.Linq.Enumerable.Aggregate%2A> <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> ve <xref:System.Linq.Enumerable.Sum%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ac58a-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="ac58a-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ac58a-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ac58a-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="ac58a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="ac58a-107">Ortalama</span><span class="sxs-lookup"><span data-stu-id="ac58a-107">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac58a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-108">Example</span></span>  

 <span data-ttu-id="ac58a-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Average%2A> ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-109">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-110">Example</span></span>  

 <span data-ttu-id="ac58a-111">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> stilin ürünlerinin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-111">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-112">Example</span></span>  

 <span data-ttu-id="ac58a-113">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Average%2A> süresi dolan ortalama toplamı bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-113">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-114">Example</span></span>  

 <span data-ttu-id="ac58a-115">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kışı kimliği için Ortalama toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-115">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-116">Example</span></span>  

 <span data-ttu-id="ac58a-117">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kişi için ödenecek ortalama toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-117">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="ac58a-118">Count</span><span class="sxs-lookup"><span data-stu-id="ac58a-118">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac58a-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-119">Example</span></span>  

 <span data-ttu-id="ac58a-120">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> ürün tablosundaki ürünlerin sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-120">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-121">Example</span></span>  

 <span data-ttu-id="ac58a-122">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> Iletişim kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-122">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-123">Example</span></span>  

 <span data-ttu-id="ac58a-124">Aşağıdaki örnek, ürünleri renge göre gruplandırır ve <xref:System.Linq.Enumerable.Count%2A> her renk grubundaki ürün sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-124">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="ac58a-125">LongCount</span><span class="sxs-lookup"><span data-stu-id="ac58a-125">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac58a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-126">Example</span></span>  

 <span data-ttu-id="ac58a-127">Aşağıdaki örnek, iletişim sayısını uzun bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-127">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="ac58a-128">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="ac58a-128">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac58a-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-129">Example</span></span>  

 <span data-ttu-id="ac58a-130">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A> süresi dolan en büyük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-130">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-131">Example</span></span>  

 <span data-ttu-id="ac58a-132">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> ILETIŞIM kimliği için en fazla toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-132">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-133">Example</span></span>  

 <span data-ttu-id="ac58a-134">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> kışı kimliği için en büyük toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-134">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="ac58a-135">Min</span><span class="sxs-lookup"><span data-stu-id="ac58a-135">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac58a-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-136">Example</span></span>  

 <span data-ttu-id="ac58a-137">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Min%2A> süresi dolan en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-137">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-138">Example</span></span>  

 <span data-ttu-id="ac58a-139">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Min%2A> kışı kimliği için en küçük toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-139">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-140">Example</span></span>  

 <span data-ttu-id="ac58a-141">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Min%2A> her kişi için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-141">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="ac58a-142">Sum</span><span class="sxs-lookup"><span data-stu-id="ac58a-142">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac58a-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-143">Example</span></span>  

 <span data-ttu-id="ac58a-144">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Sum%2A> SalesOrderDetail tablosundaki toplam sipariş miktarı sayısını almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-144">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="ac58a-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac58a-145">Example</span></span>  

 <span data-ttu-id="ac58a-146">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Sum%2A> ILETIŞIM kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac58a-146">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ac58a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac58a-147">See also</span></span>

- [<span data-ttu-id="ac58a-148">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="ac58a-148">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
