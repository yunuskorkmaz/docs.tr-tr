---
title: 'Yöntem temelli sorgu sözdizimi örnekler: (LINQ bölümlendirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: d517b09ac921001ab16216e4950df66dfabda13d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="fa256-102">Yöntem temelli sorgu sözdizimi örnekler: (LINQ bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="fa256-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="fa256-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, ve <xref:System.Linq.Enumerable.TakeWhile%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fa256-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="fa256-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="fa256-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="fa256-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa256-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fa256-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="fa256-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="fa256-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fa256-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="fa256-108">Atla</span><span class="sxs-lookup"><span data-stu-id="fa256-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="fa256-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa256-109">Example</span></span>  
 <span data-ttu-id="fa256-110">Bu örnekte <xref:System.Linq.Enumerable.Skip%2A> tüm almak için yöntemi ancak ilk beş kişiler `Contact` tablo.</span><span class="sxs-lookup"><span data-stu-id="fa256-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="fa256-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa256-111">Example</span></span>  
 <span data-ttu-id="fa256-112">Bu örnekte <xref:System.Linq.Enumerable.Skip%2A> tüm almak için yöntemi ancak ilk iki adres Seattle'da.</span><span class="sxs-lookup"><span data-stu-id="fa256-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="fa256-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="fa256-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="fa256-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa256-114">Example</span></span>  
 <span data-ttu-id="fa256-115">Bu örnek kullanır <xref:System.Linq.Enumerable.OrderBy%2A> ve <xref:System.Linq.Enumerable.SkipWhile%2A> ürünlerinden döndürülecek yöntemleri `Product` bir fiyat listesi 300.00 büyük içeren tablo.</span><span class="sxs-lookup"><span data-stu-id="fa256-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="fa256-116">Take</span><span class="sxs-lookup"><span data-stu-id="fa256-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="fa256-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa256-117">Example</span></span>  
 <span data-ttu-id="fa256-118">Bu örnekte <xref:System.Linq.Enumerable.Take%2A> yalnızca ilk beş almak için yöntemi kişiler `Contact` tablo.</span><span class="sxs-lookup"><span data-stu-id="fa256-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="fa256-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa256-119">Example</span></span>  
 <span data-ttu-id="fa256-120">Bu örnekte <xref:System.Linq.Enumerable.Take%2A> ilk üç adres Seattle almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa256-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="fa256-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="fa256-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="fa256-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa256-122">Example</span></span>  
 <span data-ttu-id="fa256-123">Bu örnek kullanır <xref:System.Linq.Enumerable.OrderBy%2A> ve <xref:System.Linq.Enumerable.TakeWhile%2A> ürünlerinden döndürülecek `Product` bir fiyat listesi 300.00 değerinden içeren tablo.</span><span class="sxs-lookup"><span data-stu-id="fa256-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="fa256-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa256-124">See Also</span></span>  
 [<span data-ttu-id="fa256-125">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="fa256-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="fa256-126">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="fa256-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="fa256-127">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa256-127">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
