---
title: "Yöntem temelli sorgu sözdizimi örnekler: Toplama işleçleri"
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
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3a86b508531f0db216f5d6bda04dc091a98ab0e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="63339-102">Yöntem temelli sorgu sözdizimi örnekler: Toplama işleçleri</span><span class="sxs-lookup"><span data-stu-id="63339-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="63339-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Sum%2A> sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="63339-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="63339-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63339-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="63339-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="63339-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="63339-106">Ortalama</span><span class="sxs-lookup"><span data-stu-id="63339-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="63339-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-107">Example</span></span>  
 <span data-ttu-id="63339-108">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Average%2A> ürünleri ortalama fiyat listesi bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="63339-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-109">Example</span></span>  
 <span data-ttu-id="63339-110">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Average%2A> her stil ürünleri ortalama fiyat listesi bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="63339-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-111">Example</span></span>  
 <span data-ttu-id="63339-112">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Average%2A> ortalama toplam son bulma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63339-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-113">Example</span></span>  
 <span data-ttu-id="63339-114">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Average%2A> her kişi için ortalama toplam son almak için yöntemi kimliği</span><span class="sxs-lookup"><span data-stu-id="63339-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-115">Example</span></span>  
 <span data-ttu-id="63339-116">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Average%2A> ortalama siparişleri her kişi için son toplam almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63339-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="63339-117">Sayısı</span><span class="sxs-lookup"><span data-stu-id="63339-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="63339-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-118">Example</span></span>  
 <span data-ttu-id="63339-119">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Count%2A> yöntemi ürün tabloda ürünleri sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="63339-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="63339-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-120">Example</span></span>  
 <span data-ttu-id="63339-121">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Count%2A> kişi kimlikleri listesini ve kaç tane her siparişleri döndürülecek yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="63339-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="63339-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-122">Example</span></span>  
 <span data-ttu-id="63339-123">Aşağıdaki örnek ürünleri rengine göre gruplandırır ve kullandığı <xref:System.Linq.Enumerable.Count%2A> yöntemi her renk grubundaki ürünlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="63339-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="63339-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="63339-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="63339-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-125">Example</span></span>  
 <span data-ttu-id="63339-126">Aşağıdaki örnek kişi sayısını uzun tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="63339-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="63339-127">Maks.</span><span class="sxs-lookup"><span data-stu-id="63339-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="63339-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-128">Example</span></span>  
 <span data-ttu-id="63339-129">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süresi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63339-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-130">Example</span></span>  
 <span data-ttu-id="63339-131">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süresi almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="63339-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-132">Example</span></span>  
 <span data-ttu-id="63339-133">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Max%2A> en büyük toplam süre sonu olan siparişleri almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="63339-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="63339-134">Min.</span><span class="sxs-lookup"><span data-stu-id="63339-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="63339-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-135">Example</span></span>  
 <span data-ttu-id="63339-136">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Min%2A> en küçük toplam süresi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63339-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-137">Example</span></span>  
 <span data-ttu-id="63339-138">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Min%2A> en küçük toplam süresi almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="63339-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-139">Example</span></span>  
 <span data-ttu-id="63339-140">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Min%2A> en küçük toplam siparişleri almak için yöntemi her kişi için son.</span><span class="sxs-lookup"><span data-stu-id="63339-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="63339-141">TOPLA</span><span class="sxs-lookup"><span data-stu-id="63339-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="63339-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-142">Example</span></span>  
 <span data-ttu-id="63339-143">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Sum%2A> sipariş miktarları toplam sayısı satış siparişi ayrıntısını tabloda almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="63339-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="63339-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="63339-144">Example</span></span>  
 <span data-ttu-id="63339-145">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Sum%2A> toplam süresi almak için yöntemi her biri için bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="63339-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="63339-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63339-146">See Also</span></span>  
 [<span data-ttu-id="63339-147">LINQ to Entities sorguları</span><span class="sxs-lookup"><span data-stu-id="63339-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
