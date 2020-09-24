---
title: 'Sorgu Ifadesi söz dizimi örnekleri: toplu Işleçler (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 2277058c4dad4632f4f47a39e32463eaf77dcd5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164577"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="4f47f-102">Sorgu Ifadesi söz dizimi örnekleri: toplu Işleçler (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4f47f-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="4f47f-103">Bu konudaki örneklerde <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Sum%2A> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak bir ve verileri sorgulamak için,,, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f47f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="4f47f-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f47f-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="4f47f-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4f47f-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="4f47f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="4f47f-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4f47f-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="4f47f-108">Ortalama</span><span class="sxs-lookup"><span data-stu-id="4f47f-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="4f47f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-109">Example</span></span>  

 <span data-ttu-id="4f47f-110">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her stilin ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="4f47f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-111">Example</span></span>  

 <span data-ttu-id="4f47f-112">Bu örnek <xref:System.Linq.Enumerable.Average%2A> , her bir kışı kimliği için Ortalama toplamı almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4f47f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-113">Example</span></span>  

 <span data-ttu-id="4f47f-114">Bu örnek, <xref:System.Linq.Enumerable.Average%2A> her bir kişi için Ortalama olan siparişleri almak için kullanır `TotalDue` .</span><span class="sxs-lookup"><span data-stu-id="4f47f-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="4f47f-115">Count</span><span class="sxs-lookup"><span data-stu-id="4f47f-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="4f47f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-116">Example</span></span>  

 <span data-ttu-id="4f47f-117">Bu örnek <xref:System.Linq.Enumerable.Count%2A> , Iletişim kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="4f47f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-118">Example</span></span>  

 <span data-ttu-id="4f47f-119">Bu örnek, ürünleri renge göre gruplandırır ve <xref:System.Linq.Enumerable.Count%2A> her renk grubundaki ürünlerin sayısını döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="4f47f-120">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="4f47f-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="4f47f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-121">Example</span></span>  

 <span data-ttu-id="4f47f-122">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> her bir kışı kimliği için en fazla toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4f47f-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-123">Example</span></span>  

 <span data-ttu-id="4f47f-124">Bu örnek, <xref:System.Linq.Enumerable.Max%2A> `TotalDue` her BIR kişi kimliği için en büyük olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="4f47f-125">Min</span><span class="sxs-lookup"><span data-stu-id="4f47f-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="4f47f-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-126">Example</span></span>  

 <span data-ttu-id="4f47f-127">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> her bir kışı kimliği için en küçük toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4f47f-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-128">Example</span></span>  

 <span data-ttu-id="4f47f-129">Bu örnek, <xref:System.Linq.Enumerable.Min%2A> her kişi için en küçük Toplam olan siparişleri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="4f47f-130">Toplam</span><span class="sxs-lookup"><span data-stu-id="4f47f-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="4f47f-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f47f-131">Example</span></span>  

 <span data-ttu-id="4f47f-132">Bu örnek, <xref:System.Linq.Enumerable.Sum%2A> her bir ILETIŞIM kimliği için bir süre için bu yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f47f-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4f47f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f47f-133">See also</span></span>

- [<span data-ttu-id="4f47f-134">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="4f47f-134">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="4f47f-135">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4f47f-135">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="4f47f-136">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="4f47f-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4f47f-137">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f47f-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
