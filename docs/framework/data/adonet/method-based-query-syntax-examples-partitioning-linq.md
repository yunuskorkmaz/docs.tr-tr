---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümlendirme (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 7e01bd9702ae267f80ecf24de0c0cc90d638a84c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783589"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="bbcd1-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümlendirme (LINQ</span><span class="sxs-lookup"><span data-stu-id="bbcd1-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="bbcd1-103">Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak bir <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Data.DataSet> sorgusu <xref:System.Linq.Enumerable.SkipWhile%2A>sorgulamak <xref:System.Linq.Enumerable.Take%2A>için, <xref:System.Linq.Enumerable.TakeWhile%2A> , ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="bbcd1-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="bbcd1-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bbcd1-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="bbcd1-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="bbcd1-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="bbcd1-108">Atla</span><span class="sxs-lookup"><span data-stu-id="bbcd1-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="bbcd1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcd1-109">Example</span></span>  
 <span data-ttu-id="bbcd1-110">Bu örnek, `Contact` tablonun <xref:System.Linq.Enumerable.Skip%2A> ilk beş kişisiyle tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="bbcd1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcd1-111">Example</span></span>  
 <span data-ttu-id="bbcd1-112">Bu örnek, <xref:System.Linq.Enumerable.Skip%2A> Seattle 'daki ilk iki adres hariç tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="bbcd1-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="bbcd1-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="bbcd1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcd1-114">Example</span></span>  
 <span data-ttu-id="bbcd1-115">Bu örnekte ve <xref:System.Linq.Enumerable.OrderBy%2A> , <xref:System.Linq.Enumerable.SkipWhile%2A> 300,00 ' den büyük bir liste `Product` fiyatına sahip olan tablodaki ürünleri döndürmek için ve yöntemleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="bbcd1-116">Take</span><span class="sxs-lookup"><span data-stu-id="bbcd1-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="bbcd1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcd1-117">Example</span></span>  
 <span data-ttu-id="bbcd1-118">Bu örnek, `Contact` tablosundan <xref:System.Linq.Enumerable.Take%2A> yalnızca ilk beş kişiyi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="bbcd1-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcd1-119">Example</span></span>  
 <span data-ttu-id="bbcd1-120">Bu örnek, <xref:System.Linq.Enumerable.Take%2A> Seattle 'daki ilk üç adresi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="bbcd1-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="bbcd1-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="bbcd1-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcd1-122">Example</span></span>  
 <span data-ttu-id="bbcd1-123">Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.TakeWhile%2A> tablosundan300,00'denküçükbirlistefiyatınasahipürünlerigeridöndürmek`Product` için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="bbcd1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbcd1-124">See also</span></span>

- [<span data-ttu-id="bbcd1-125">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="bbcd1-125">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="bbcd1-126">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="bbcd1-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="bbcd1-127">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="bbcd1-127">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="bbcd1-128">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbcd1-128">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
