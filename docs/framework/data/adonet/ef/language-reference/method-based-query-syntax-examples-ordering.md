---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 8da335bc2b45153aa00cd28f1a6baf58d11020ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250103"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="e63e8-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama</span><span class="sxs-lookup"><span data-stu-id="e63e8-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="e63e8-103">Bu konudaki örneklerde, Yöntem tabanlı sorgu söz dizimini kullanarak <xref:System.Linq.Enumerable.ThenBy%2A> [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e63e8-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="e63e8-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="e63e8-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e63e8-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="e63e8-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="e63e8-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="e63e8-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="e63e8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e63e8-107">Example</span></span>  
 <span data-ttu-id="e63e8-108">Yöntem tabanlı sorgu söz diziminde aşağıdaki örnek, son <xref:System.Linq.Queryable.OrderBy%2A> ada <xref:System.Linq.Queryable.ThenBy%2A> göre sıralanmış kişilerin listesini ve sonra adı ve sonra adını döndürmek için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="e63e8-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="e63e8-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="e63e8-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="e63e8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e63e8-110">Example</span></span>  
 <span data-ttu-id="e63e8-111">Aşağıdaki örnek, ilk olarak <xref:System.Linq.Queryable.OrderBy%2A> liste <xref:System.Linq.Queryable.ThenByDescending%2A> fiyatına göre sıralama yapmak için ve yöntemlerini kullanır ve ardından ürün adlarının azalan sıralamasını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e63e8-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="e63e8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e63e8-112">See also</span></span>

- [<span data-ttu-id="e63e8-113">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="e63e8-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
