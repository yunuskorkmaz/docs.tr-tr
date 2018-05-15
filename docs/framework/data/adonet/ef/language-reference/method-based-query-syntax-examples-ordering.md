---
title: 'Yöntem temelli sorgu sözdizimi örnekleri: sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 3a0b70e112e2ba3ce19324dc1389c9fedea5d710
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="843c9-102">Yöntem temelli sorgu sözdizimi örnekleri: sıralama</span><span class="sxs-lookup"><span data-stu-id="843c9-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="843c9-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ThenBy%2A> sorgu yönteme [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="843c9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="843c9-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="843c9-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="843c9-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="843c9-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="843c9-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="843c9-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="843c9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="843c9-107">Example</span></span>  
 <span data-ttu-id="843c9-108">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte kullanır <xref:System.Linq.Queryable.OrderBy%2A> ve <xref:System.Linq.Queryable.ThenBy%2A> kişiler soyadı ve ardından ad göre sıralanan listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="843c9-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="843c9-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="843c9-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="843c9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="843c9-110">Example</span></span>  
 <span data-ttu-id="843c9-111">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.OrderBy%2A> ve <xref:System.Linq.Queryable.ThenByDescending%2A> ilk yöntemlere sıralama fiyat listesi ve azalan sırada sıralar, ürün adları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="843c9-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="843c9-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="843c9-112">See Also</span></span>  
 [<span data-ttu-id="843c9-113">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="843c9-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
