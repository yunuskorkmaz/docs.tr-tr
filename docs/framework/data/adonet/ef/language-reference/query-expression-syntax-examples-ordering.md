---
title: 'Sorgu ifadesi söz dizimi örnekleri: sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: bc8bfaabb9e90e66e4ec81e551fd66319a78ca7e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871874"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="6cb89-102">Sorgu ifadesi söz dizimi örnekleri: sıralama</span><span class="sxs-lookup"><span data-stu-id="6cb89-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="6cb89-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `OrderBy` ve `OrderByDescending` sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6cb89-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="6cb89-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6cb89-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6cb89-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="6cb89-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="6cb89-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="6cb89-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="6cb89-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb89-107">Example</span></span>  
 <span data-ttu-id="6cb89-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.OrderBy%2A> kişileri soyadına göre sıralanmış bir listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="6cb89-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="6cb89-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb89-109">Example</span></span>  
 <span data-ttu-id="6cb89-110">Aşağıdaki örnekte <xref:System.Linq.Enumerable.OrderBy%2A> Soyadı uzunluğuna kişilerin listesini sıralamak için.</span><span class="sxs-lookup"><span data-stu-id="6cb89-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="6cb89-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="6cb89-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="6cb89-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb89-112">Example</span></span>  
 <span data-ttu-id="6cb89-113">Aşağıdaki örnekte `orderby… descending` (`Order By … Descending` Visual Basic'te), eşdeğer olan <xref:System.Linq.Enumerable.OrderByDescending%2A> fiyat listesinin en yüksekten en düşük sıralamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cb89-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="6cb89-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="6cb89-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="6cb89-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb89-115">Example</span></span>  
 <span data-ttu-id="6cb89-116">Aşağıdaki örnekte <xref:System.Linq.Queryable.OrderBy%2A> ve <xref:System.Linq.Queryable.ThenBy%2A> kişileri soyadına göre ve ardından ilk adına göre sıralanmış bir listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="6cb89-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="6cb89-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="6cb89-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="6cb89-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb89-118">Example</span></span>  
 <span data-ttu-id="6cb89-119">Aşağıdaki örnekte `OrderBy… Descending`, eşdeğer olan <xref:System.Linq.Enumerable.ThenByDescending%2A> en düşük ilk adına ve ardından göre en yüksekten liste fiyatı, ürünlerin listesini sıralamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cb89-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb89-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cb89-120">See Also</span></span>  
 [<span data-ttu-id="6cb89-121">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="6cb89-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
