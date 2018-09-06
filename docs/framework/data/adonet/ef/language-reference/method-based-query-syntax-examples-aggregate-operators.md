---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Toplu işleçler'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 1f4090cbffc4177c4b9edd08381e8dd294ae0c41
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740906"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="04f1b-102">Metot tabanlı sorgu söz dizimi örnekleri: Toplu işleçler</span><span class="sxs-lookup"><span data-stu-id="04f1b-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="04f1b-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Sum%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="04f1b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="04f1b-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="04f1b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="04f1b-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="04f1b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="04f1b-106">Ortalama</span><span class="sxs-lookup"><span data-stu-id="04f1b-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="04f1b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-107">Example</span></span>  
 <span data-ttu-id="04f1b-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama liste fiyatı ürünleri bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-109">Example</span></span>  
 <span data-ttu-id="04f1b-110">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama liste fiyatı her stilin ürünleri bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-111">Example</span></span>  
 <span data-ttu-id="04f1b-112">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Average%2A> ortalama toplam son bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-113">Example</span></span>  
 <span data-ttu-id="04f1b-114">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Average%2A> kimliği her kişi için ortalama toplam son almak için yöntemi</span><span class="sxs-lookup"><span data-stu-id="04f1b-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-115">Example</span></span>  
 <span data-ttu-id="04f1b-116">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Average%2A> her kişi için son toplam siparişleri ortalamasını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="04f1b-117">Sayısı</span><span class="sxs-lookup"><span data-stu-id="04f1b-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="04f1b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-118">Example</span></span>  
 <span data-ttu-id="04f1b-119">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Count%2A> Product tablosuna ürünleri sayısını döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-120">Example</span></span>  
 <span data-ttu-id="04f1b-121">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Count%2A> kişi kimlikleri listesini ve kaç her siparişleri döndürmek için yöntemin vardır.</span><span class="sxs-lookup"><span data-stu-id="04f1b-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-122">Example</span></span>  
 <span data-ttu-id="04f1b-123">Aşağıdaki örnek ürünleri rengine göre gruplandırır ve kullandığı <xref:System.Linq.Enumerable.Count%2A> ürün sayısı, her bir renk grubu geri dönmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="04f1b-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="04f1b-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="04f1b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-125">Example</span></span>  
 <span data-ttu-id="04f1b-126">Aşağıdaki örnek, kişi sayısı uzun bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="04f1b-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="04f1b-127">Maks.</span><span class="sxs-lookup"><span data-stu-id="04f1b-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="04f1b-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-128">Example</span></span>  
 <span data-ttu-id="04f1b-129">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süre almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-130">Example</span></span>  
 <span data-ttu-id="04f1b-131">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="04f1b-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-132">Example</span></span>  
 <span data-ttu-id="04f1b-133">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Max%2A> siparişleri en büyük toplam son almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="04f1b-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="04f1b-134">Min.</span><span class="sxs-lookup"><span data-stu-id="04f1b-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="04f1b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-135">Example</span></span>  
 <span data-ttu-id="04f1b-136">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam süre almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-137">Example</span></span>  
 <span data-ttu-id="04f1b-138">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="04f1b-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-139">Example</span></span>  
 <span data-ttu-id="04f1b-140">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Min%2A> küçük toplam siparişleri almak için yöntemi her kişi için son.</span><span class="sxs-lookup"><span data-stu-id="04f1b-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="04f1b-141">TOPLA</span><span class="sxs-lookup"><span data-stu-id="04f1b-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="04f1b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-142">Example</span></span>  
 <span data-ttu-id="04f1b-143">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Sum%2A> sipariş miktarlarının toplam sayısı satış siparişi ayrıntısını tabloda almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04f1b-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="04f1b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f1b-144">Example</span></span>  
 <span data-ttu-id="04f1b-145">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Sum%2A> toplam süre almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="04f1b-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="04f1b-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04f1b-146">See Also</span></span>  
 [<span data-ttu-id="04f1b-147">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="04f1b-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
