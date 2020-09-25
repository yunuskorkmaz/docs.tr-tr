---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: f8754101e7ec55fe5f9836300de1d077e1db2478
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192132"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="c4a97-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler</span><span class="sxs-lookup"><span data-stu-id="c4a97-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>

<span data-ttu-id="c4a97-103">Bu konudaki örneklerde,,,,, <xref:System.Linq.Enumerable.Aggregate%2A> <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> ve <xref:System.Linq.Enumerable.Sum%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c4a97-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="c4a97-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c4a97-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c4a97-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="c4a97-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="c4a97-106">Ortalama</span><span class="sxs-lookup"><span data-stu-id="c4a97-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="c4a97-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-107">Example</span></span>  

 <span data-ttu-id="c4a97-108">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Average%2A> ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-109">Example</span></span>  

 <span data-ttu-id="c4a97-110">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> stilin ürünlerinin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-111">Example</span></span>  

 <span data-ttu-id="c4a97-112">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Average%2A> süresi dolan ortalama toplamı bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-113">Example</span></span>  

 <span data-ttu-id="c4a97-114">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kışı kimliği için Ortalama toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-115">Example</span></span>  

 <span data-ttu-id="c4a97-116">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kişi için ödenecek ortalama toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="c4a97-117">Count</span><span class="sxs-lookup"><span data-stu-id="c4a97-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="c4a97-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-118">Example</span></span>  

 <span data-ttu-id="c4a97-119">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> ürün tablosundaki ürünlerin sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-120">Example</span></span>  

 <span data-ttu-id="c4a97-121">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> Iletişim kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-122">Example</span></span>  

 <span data-ttu-id="c4a97-123">Aşağıdaki örnek, ürünleri renge göre gruplandırır ve <xref:System.Linq.Enumerable.Count%2A> her renk grubundaki ürün sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="c4a97-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="c4a97-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="c4a97-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-125">Example</span></span>  

 <span data-ttu-id="c4a97-126">Aşağıdaki örnek, iletişim sayısını uzun bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="c4a97-127">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="c4a97-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="c4a97-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-128">Example</span></span>  

 <span data-ttu-id="c4a97-129">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A> süresi dolan en büyük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-130">Example</span></span>  

 <span data-ttu-id="c4a97-131">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> ILETIŞIM kimliği için en fazla toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-132">Example</span></span>  

 <span data-ttu-id="c4a97-133">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> kışı kimliği için en büyük toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="c4a97-134">Min</span><span class="sxs-lookup"><span data-stu-id="c4a97-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="c4a97-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-135">Example</span></span>  

 <span data-ttu-id="c4a97-136">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Min%2A> süresi dolan en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-137">Example</span></span>  

 <span data-ttu-id="c4a97-138">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Min%2A> kışı kimliği için en küçük toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-139">Example</span></span>  

 <span data-ttu-id="c4a97-140">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Min%2A> her kişi için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="c4a97-141">Toplam</span><span class="sxs-lookup"><span data-stu-id="c4a97-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="c4a97-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-142">Example</span></span>  

 <span data-ttu-id="c4a97-143">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Sum%2A> SalesOrderDetail tablosundaki toplam sipariş miktarı sayısını almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="c4a97-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4a97-144">Example</span></span>  

 <span data-ttu-id="c4a97-145">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Sum%2A> ILETIŞIM kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a97-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c4a97-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4a97-146">See also</span></span>

- [<span data-ttu-id="c4a97-147">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="c4a97-147">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
