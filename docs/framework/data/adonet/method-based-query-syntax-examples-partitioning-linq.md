---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: bölümleme (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 0ef7176ccffb7037a7d4496cc7d4da7991741d38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147937"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="38b27-102">Yöntem tabanlı sorgu söz dizimi örnekleri: bölümleme (LINQ</span><span class="sxs-lookup"><span data-stu-id="38b27-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>

<span data-ttu-id="38b27-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.SkipWhile%2A> <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.TakeWhile%2A> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak bir sorgusu sorgulamak için,, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38b27-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="38b27-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38b27-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="38b27-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38b27-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="38b27-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="38b27-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="38b27-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="38b27-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="38b27-108">Atla</span><span class="sxs-lookup"><span data-stu-id="38b27-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="38b27-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b27-109">Example</span></span>  

 <span data-ttu-id="38b27-110">Bu örnek, <xref:System.Linq.Enumerable.Skip%2A> tablonun ilk beş kişisiyle tümünü almak için yöntemini kullanır `Contact` .</span><span class="sxs-lookup"><span data-stu-id="38b27-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="38b27-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b27-111">Example</span></span>  

 <span data-ttu-id="38b27-112">Bu örnek, <xref:System.Linq.Enumerable.Skip%2A> Seattle 'daki ilk iki adres hariç tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="38b27-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="38b27-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="38b27-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="38b27-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b27-114">Example</span></span>  

 <span data-ttu-id="38b27-115">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> ve, <xref:System.Linq.Enumerable.SkipWhile%2A> `Product` 300,00 ' den büyük bir liste fiyatına sahip olan tablodaki ürünleri döndürmek için ve yöntemleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38b27-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="38b27-116">Take</span><span class="sxs-lookup"><span data-stu-id="38b27-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="38b27-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b27-117">Example</span></span>  

 <span data-ttu-id="38b27-118">Bu örnek, <xref:System.Linq.Enumerable.Take%2A> tablosundan yalnızca ilk beş kişiyi almak için yöntemini kullanır `Contact` .</span><span class="sxs-lookup"><span data-stu-id="38b27-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="38b27-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b27-119">Example</span></span>  

 <span data-ttu-id="38b27-120">Bu örnek, <xref:System.Linq.Enumerable.Take%2A> Seattle 'daki ilk üç adresi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="38b27-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="38b27-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="38b27-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="38b27-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b27-122">Example</span></span>  

 <span data-ttu-id="38b27-123">Bu örnek <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.TakeWhile%2A> , `Product` tablosundan 300,00 'den küçük bir liste fiyatına sahip ürünleri geri döndürmek için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="38b27-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="38b27-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38b27-124">See also</span></span>

- [<span data-ttu-id="38b27-125">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="38b27-125">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="38b27-126">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="38b27-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="38b27-127">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="38b27-127">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="38b27-128">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38b27-128">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
