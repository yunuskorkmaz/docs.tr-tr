---
title: "Sorgu ifade sözdizimi örnekleri: sıralama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 70f3cc72eb5b77dd5480164e53535214100a6816
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="397da-102">Sorgu ifade sözdizimi örnekleri: sıralama</span><span class="sxs-lookup"><span data-stu-id="397da-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="397da-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `OrderBy` ve `OrderByDescending` sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="397da-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="397da-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="397da-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="397da-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="397da-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="397da-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="397da-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="397da-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="397da-107">Example</span></span>  
 <span data-ttu-id="397da-108">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.OrderBy%2A> kişiler son ada göre sıralanan listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="397da-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="397da-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="397da-109">Example</span></span>  
 <span data-ttu-id="397da-110">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.OrderBy%2A> kişilerin listesini Soyadı uzunluğa göre sıralamak için.</span><span class="sxs-lookup"><span data-stu-id="397da-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="397da-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="397da-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="397da-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="397da-112">Example</span></span>  
 <span data-ttu-id="397da-113">Aşağıdaki örnek kullanır `orderby… descending` (`Order By … Descending` Visual Basic'te), eşdeğer olduğu <xref:System.Linq.Enumerable.OrderByDescending%2A> fiyat yüksekten en düşük sıralamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="397da-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="397da-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="397da-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="397da-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="397da-115">Example</span></span>  
 <span data-ttu-id="397da-116">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.OrderBy%2A> ve <xref:System.Linq.Queryable.ThenBy%2A> kişiler soyadı ve ardından ad göre sıralanan listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="397da-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="397da-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="397da-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="397da-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="397da-118">Example</span></span>  
 <span data-ttu-id="397da-119">Aşağıdaki örnek kullanır `OrderBy… Descending`, eşdeğer olduğu <xref:System.Linq.Enumerable.ThenByDescending%2A> bir ürün ilk adı ve ardından göre fiyat listesi yüksekten en düşük sıralamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="397da-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="397da-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="397da-120">See Also</span></span>  
 [<span data-ttu-id="397da-121">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="397da-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
