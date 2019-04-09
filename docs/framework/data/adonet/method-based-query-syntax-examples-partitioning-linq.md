---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Partitioning (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: bfc26835258606ff20dd066ecb6e4c874d0be2f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116720"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="da1f4-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Partitioning (LINQ</span><span class="sxs-lookup"><span data-stu-id="da1f4-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="da1f4-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, ve <xref:System.Linq.Enumerable.TakeWhile%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="da1f4-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="da1f4-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="da1f4-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="da1f4-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="da1f4-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="da1f4-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="da1f4-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="da1f4-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="da1f4-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="da1f4-108">Atla</span><span class="sxs-lookup"><span data-stu-id="da1f4-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="da1f4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="da1f4-109">Example</span></span>  
 <span data-ttu-id="da1f4-110">Bu örnekte <xref:System.Linq.Enumerable.Skip%2A> tüm almak için yöntemi ancak ilk beş kişiler `Contact` tablo.</span><span class="sxs-lookup"><span data-stu-id="da1f4-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="da1f4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="da1f4-111">Example</span></span>  
 <span data-ttu-id="da1f4-112">Bu örnekte <xref:System.Linq.Enumerable.Skip%2A> , ancak ilk iki adres Seattle tüm almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="da1f4-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="da1f4-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="da1f4-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="da1f4-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="da1f4-114">Example</span></span>  
 <span data-ttu-id="da1f4-115">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> ve <xref:System.Linq.Enumerable.SkipWhile%2A> ürünleri döndürmek için yöntemleri `Product` 300.00 büyük bir liste fiyatı içeren tablo.</span><span class="sxs-lookup"><span data-stu-id="da1f4-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="da1f4-116">Take</span><span class="sxs-lookup"><span data-stu-id="da1f4-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="da1f4-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="da1f4-117">Example</span></span>  
 <span data-ttu-id="da1f4-118">Bu örnekte <xref:System.Linq.Enumerable.Take%2A> yalnızca ilk beş almak için yöntemi ile iletişim kurar `Contact` tablo.</span><span class="sxs-lookup"><span data-stu-id="da1f4-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="da1f4-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="da1f4-119">Example</span></span>  
 <span data-ttu-id="da1f4-120">Bu örnekte <xref:System.Linq.Enumerable.Take%2A> Seattle ilk üç adresini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="da1f4-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="da1f4-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="da1f4-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="da1f4-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="da1f4-122">Example</span></span>  
 <span data-ttu-id="da1f4-123">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> ve <xref:System.Linq.Enumerable.TakeWhile%2A> ürünleri döndürmek için `Product` 300.00 değerinden bir liste fiyatı içeren tablo.</span><span class="sxs-lookup"><span data-stu-id="da1f4-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="da1f4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da1f4-124">See also</span></span>

- [<span data-ttu-id="da1f4-125">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="da1f4-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="da1f4-126">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="da1f4-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="da1f4-127">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="da1f4-127">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="da1f4-128">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da1f4-128">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
