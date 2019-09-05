---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplama İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: d9007e4d650c79a636f908a638bb382457f6b29b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250274"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="50adf-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="50adf-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="50adf-103">Bu konudaki örneklerde,,,,,, ve <xref:System.Linq.Enumerable.Aggregate%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Count%2A> yöntemlerini<xref:System.Linq.Enumerable.Sum%2A> kullanarak [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için nasıl kullanılacağı gösterilmektedir. Yöntem tabanlı sorgu söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="50adf-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="50adf-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="50adf-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="50adf-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="50adf-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="50adf-106">Ortalama</span><span class="sxs-lookup"><span data-stu-id="50adf-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="50adf-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-107">Example</span></span>  
 <span data-ttu-id="50adf-108">Aşağıdaki örnek, ürünlerin ortalama <xref:System.Linq.Enumerable.Average%2A> liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-109">Example</span></span>  
 <span data-ttu-id="50adf-110">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> stilin ürünlerinin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-111">Example</span></span>  
 <span data-ttu-id="50adf-112">Aşağıdaki örnek, süresi dolan <xref:System.Linq.Enumerable.Average%2A> ortalama toplamı bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-113">Example</span></span>  
 <span data-ttu-id="50adf-114">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kişi kimliği için Ortalama toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-115">Example</span></span>  
 <span data-ttu-id="50adf-116">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kişi için ödenecek ortalama toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="50adf-117">Count</span><span class="sxs-lookup"><span data-stu-id="50adf-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="50adf-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-118">Example</span></span>  
 <span data-ttu-id="50adf-119">Aşağıdaki örnek, ürün tablosundaki <xref:System.Linq.Enumerable.Count%2A> ürünlerin sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="50adf-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-120">Example</span></span>  
 <span data-ttu-id="50adf-121">Aşağıdaki örnek, iletişim kimliklerinin <xref:System.Linq.Enumerable.Count%2A> bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="50adf-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-122">Example</span></span>  
 <span data-ttu-id="50adf-123">Aşağıdaki örnek, ürünleri renge göre gruplandırır ve her renk <xref:System.Linq.Enumerable.Count%2A> grubundaki ürün sayısını döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="50adf-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="50adf-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="50adf-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-125">Example</span></span>  
 <span data-ttu-id="50adf-126">Aşağıdaki örnek, iletişim sayısını uzun bir tamsayı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="50adf-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="50adf-127">Maks.</span><span class="sxs-lookup"><span data-stu-id="50adf-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="50adf-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-128">Example</span></span>  
 <span data-ttu-id="50adf-129">Aşağıdaki örnek, süresi dolan <xref:System.Linq.Enumerable.Max%2A> en büyük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-130">Example</span></span>  
 <span data-ttu-id="50adf-131">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> iletişim kimliği için en fazla toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-132">Example</span></span>  
 <span data-ttu-id="50adf-133">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> kişi kimliği için en büyük toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="50adf-134">Min.</span><span class="sxs-lookup"><span data-stu-id="50adf-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="50adf-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-135">Example</span></span>  
 <span data-ttu-id="50adf-136">Aşağıdaki örnek, süresi dolan <xref:System.Linq.Enumerable.Min%2A> en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-137">Example</span></span>  
 <span data-ttu-id="50adf-138">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Min%2A> kişi kimliği için en küçük toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-139">Example</span></span>  
 <span data-ttu-id="50adf-140">Aşağıdaki örnek, her kişi <xref:System.Linq.Enumerable.Min%2A> için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="50adf-141">Toplam</span><span class="sxs-lookup"><span data-stu-id="50adf-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="50adf-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-142">Example</span></span>  
 <span data-ttu-id="50adf-143">Aşağıdaki örnek, SalesOrderDetail <xref:System.Linq.Enumerable.Sum%2A> tablosundaki toplam sipariş miktarı sayısını almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="50adf-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="50adf-144">Example</span></span>  
 <span data-ttu-id="50adf-145">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Sum%2A> iletişim kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="50adf-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="50adf-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50adf-146">See also</span></span>

- [<span data-ttu-id="50adf-147">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="50adf-147">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
