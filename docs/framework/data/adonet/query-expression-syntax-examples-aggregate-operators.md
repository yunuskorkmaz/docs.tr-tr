---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Toplama Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 44e38a53823cb52040a612d4762e33283f90e1d1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794519"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="83626-102">Sorgu İfadesi Söz Dizimi Örnekleri: Toplama Işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="83626-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="83626-103"><xref:System.Linq.Enumerable.Average%2A>Bu konudaki örneklerde <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Min%2A> ,sorgu<xref:System.Linq.Enumerable.Sum%2A> ifadesi söz dizimini kullanarak bir <xref:System.Data.DataSet> ve verileri sorgulamak için, ,,veyöntemlerininnasılkullanılacağıgösterilmektedir.<xref:System.Linq.Enumerable.Max%2A></span><span class="sxs-lookup"><span data-stu-id="83626-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="83626-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="83626-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="83626-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83626-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="83626-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="83626-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="83626-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="83626-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="83626-108">Ortalama</span><span class="sxs-lookup"><span data-stu-id="83626-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="83626-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-109">Example</span></span>  
 <span data-ttu-id="83626-110">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her stilin ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="83626-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-111">Example</span></span>  
 <span data-ttu-id="83626-112">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her bir kişi kimliği için Ortalama toplamı almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="83626-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-113">Example</span></span>  
 <span data-ttu-id="83626-114">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her bir kişi için Ortalama `TotalDue` olan siparişleri almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="83626-115">Count</span><span class="sxs-lookup"><span data-stu-id="83626-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="83626-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-116">Example</span></span>  
 <span data-ttu-id="83626-117">Bu örnek, <xref:System.Linq.Enumerable.Count%2A> iletişim kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="83626-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-118">Example</span></span>  
 <span data-ttu-id="83626-119">Bu örnek, ürünleri renge göre gruplandırır ve <xref:System.Linq.Enumerable.Count%2A> her renk grubundaki ürünlerin sayısını döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="83626-120">Maks.</span><span class="sxs-lookup"><span data-stu-id="83626-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="83626-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-121">Example</span></span>  
 <span data-ttu-id="83626-122">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> her bir kişi kimliği için en fazla toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="83626-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-123">Example</span></span>  
 <span data-ttu-id="83626-124">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> her bir kişi kimliği için en büyük `TotalDue` olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="83626-125">Min.</span><span class="sxs-lookup"><span data-stu-id="83626-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="83626-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-126">Example</span></span>  
 <span data-ttu-id="83626-127">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> her bir kişi kimliği için en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="83626-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-128">Example</span></span>  
 <span data-ttu-id="83626-129">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> her kişi için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="83626-130">Toplam</span><span class="sxs-lookup"><span data-stu-id="83626-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="83626-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="83626-131">Example</span></span>  
 <span data-ttu-id="83626-132">Bu örnek, <xref:System.Linq.Enumerable.Sum%2A> her bir iletişim kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="83626-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="83626-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83626-133">See also</span></span>

- [<span data-ttu-id="83626-134">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="83626-134">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="83626-135">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="83626-135">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="83626-136">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="83626-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="83626-137">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83626-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
