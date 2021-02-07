---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: sorgu Ifadesi sözdizimi örnekleri: sıralama'
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: 931225344311e8dde6318564ddeba6eae0e2411d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696106"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="92755-103">Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama</span><span class="sxs-lookup"><span data-stu-id="92755-103">Query Expression Syntax Examples: Ordering</span></span>

<span data-ttu-id="92755-104">Bu konudaki örneklerde, `OrderBy` `OrderByDescending` sorgu ifadesi sözdizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="92755-104">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="92755-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="92755-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="92755-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="92755-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="92755-107">OrderBy</span><span class="sxs-lookup"><span data-stu-id="92755-107">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="92755-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="92755-108">Example</span></span>  

 <span data-ttu-id="92755-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.OrderBy%2A> son ada göre sıralanan kişilerin listesini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="92755-109">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="92755-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="92755-110">Example</span></span>  

 <span data-ttu-id="92755-111">Aşağıdaki örnek, <xref:System.Linq.Enumerable.OrderBy%2A> bir kişi listesini son ad uzunluğuna göre sıralamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="92755-111">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="92755-112">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="92755-112">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="92755-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="92755-113">Example</span></span>  

 <span data-ttu-id="92755-114">Aşağıdaki örnek, `orderby… descending` `Order By … Descending` <xref:System.Linq.Enumerable.OrderByDescending%2A> Fiyat listesini en yüksekten en düşüğe sıralamak için yöntemine eşdeğer olan (Visual Basic olarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="92755-114">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="92755-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="92755-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="92755-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="92755-116">Example</span></span>  

 <span data-ttu-id="92755-117">Aşağıdaki örnek, <xref:System.Linq.Queryable.OrderBy%2A> <xref:System.Linq.Queryable.ThenBy%2A> en son ada göre sıralanmış kişilerin listesini ve sonra adı ve sonra adını döndürmek için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="92755-117">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="92755-118">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="92755-118">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="92755-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="92755-119">Example</span></span>  

 <span data-ttu-id="92755-120">Aşağıdaki örnek `OrderBy… Descending` , <xref:System.Linq.Enumerable.ThenByDescending%2A> bir ürün listesini öncelikle ada göre ve ardından en yüksekten en düşüğe kadar olan bir ürün listesini sıralamak için yöntemine denk gelen ' ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="92755-120">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="92755-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92755-121">See also</span></span>

- [<span data-ttu-id="92755-122">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="92755-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
