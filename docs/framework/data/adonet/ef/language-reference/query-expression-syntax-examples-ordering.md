---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: fbcb6ffe27234beb120e71ebc71c782abd4be24a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249462"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="5abd2-102">Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama</span><span class="sxs-lookup"><span data-stu-id="5abd2-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="5abd2-103">Bu konudaki örneklerde, sorgu ifadesi sözdizimini kullanarak `OrderBy` [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için ve `OrderByDescending` yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5abd2-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="5abd2-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5abd2-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5abd2-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="5abd2-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="5abd2-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="5abd2-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="5abd2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5abd2-107">Example</span></span>  
 <span data-ttu-id="5abd2-108">Aşağıdaki örnek, son <xref:System.Linq.Enumerable.OrderBy%2A> ada göre sıralanan kişilerin listesini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5abd2-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="5abd2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5abd2-109">Example</span></span>  
 <span data-ttu-id="5abd2-110">Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.OrderBy%2A> kişi listesini son ad uzunluğuna göre sıralamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5abd2-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="5abd2-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="5abd2-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="5abd2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5abd2-112">Example</span></span>  
 <span data-ttu-id="5abd2-113">Aşağıdaki örnek, Fiyat `orderby… descending` listesini`Order By … Descending` en yüksekten en düşüğe sıralamak için <xref:System.Linq.Enumerable.OrderByDescending%2A> yöntemine eşdeğer olan (Visual Basic olarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5abd2-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="5abd2-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="5abd2-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="5abd2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5abd2-115">Example</span></span>  
 <span data-ttu-id="5abd2-116">Aşağıdaki örnek, en <xref:System.Linq.Queryable.OrderBy%2A> son <xref:System.Linq.Queryable.ThenBy%2A> ada göre sıralanmış kişilerin listesini ve sonra adı ve sonra adını döndürmek için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="5abd2-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="5abd2-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="5abd2-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="5abd2-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="5abd2-118">Example</span></span>  
 <span data-ttu-id="5abd2-119">Aşağıdaki örnek, bir `OrderBy… Descending`ürün listesini öncelikle ada göre ve <xref:System.Linq.Enumerable.ThenByDescending%2A> ardından en yüksekten en düşüğe kadar olan bir ürün listesini sıralamak için yöntemine denk gelen ' ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5abd2-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="5abd2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5abd2-120">See also</span></span>

- [<span data-ttu-id="5abd2-121">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="5abd2-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
