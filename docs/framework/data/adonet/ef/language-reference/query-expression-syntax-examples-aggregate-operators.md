---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Toplama İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 54b5ab6fc5eac6ba522a58afa3aa3c0218e86bcf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397190"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="11c48-102">Sorgu İfadesi Söz Dizimi Örnekleri: Toplama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="11c48-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="11c48-103">Bu konudaki örneklerde,,, ve <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Min%2A> yöntemlerininsorguifadesisözdiziminikullanarakAdventureWorksSalesmodelinisorgulamakiçin<xref:System.Linq.Enumerable.Sum%2A> nasıl kullanılacağı [](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11c48-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="11c48-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="11c48-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="11c48-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="11c48-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="11c48-106">Ortalama</span><span class="sxs-lookup"><span data-stu-id="11c48-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="11c48-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-107">Example</span></span>  
 <span data-ttu-id="11c48-108">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> stilin ürünlerinin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="11c48-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-109">Example</span></span>  
 <span data-ttu-id="11c48-110">Aşağıdaki örnek, her <xref:System.Linq.Enumerable.Average%2A> bir kişi kimliği için Ortalama toplamı almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="11c48-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-111">Example</span></span>  
 <span data-ttu-id="11c48-112">Aşağıdaki örnek, her <xref:System.Linq.Enumerable.Average%2A> bir kişi için ödenecek ortalama toplam olan siparişleri almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="11c48-113">Count</span><span class="sxs-lookup"><span data-stu-id="11c48-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="11c48-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-114">Example</span></span>  
 <span data-ttu-id="11c48-115">Aşağıdaki örnek, iletişim <xref:System.Linq.Enumerable.Count%2A> kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="11c48-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-116">Example</span></span>  
 <span data-ttu-id="11c48-117">Aşağıdaki örnek, ürünleri renge göre gruplandırır ve her <xref:System.Linq.Enumerable.Count%2A> renk grubundaki ürünlerin sayısını döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="11c48-118">Maks.</span><span class="sxs-lookup"><span data-stu-id="11c48-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="11c48-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-119">Example</span></span>  
 <span data-ttu-id="11c48-120">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> iletişim kimliği için en fazla toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="11c48-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-121">Example</span></span>  
 <span data-ttu-id="11c48-122">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> kişi kimliği için en büyük toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="11c48-123">Min.</span><span class="sxs-lookup"><span data-stu-id="11c48-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="11c48-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-124">Example</span></span>  
 <span data-ttu-id="11c48-125">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Min%2A> kişi kimliği için en küçük toplamı almak üzere yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="11c48-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-126">Example</span></span>  
 <span data-ttu-id="11c48-127">Aşağıdaki örnek, her kişi <xref:System.Linq.Enumerable.Min%2A> için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="11c48-128">Toplam</span><span class="sxs-lookup"><span data-stu-id="11c48-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="11c48-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="11c48-129">Example</span></span>  
 <span data-ttu-id="11c48-130">Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Sum%2A> iletişim kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="11c48-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="11c48-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11c48-131">See also</span></span>

- [<span data-ttu-id="11c48-132">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="11c48-132">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
