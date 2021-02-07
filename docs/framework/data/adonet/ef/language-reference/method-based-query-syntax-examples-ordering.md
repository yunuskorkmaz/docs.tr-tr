---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: sıralama'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 7b1c67ba66f549e82a57b5b34c645d36d1255a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696704"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="972cb-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama</span><span class="sxs-lookup"><span data-stu-id="972cb-103">Method-Based Query Syntax Examples: Ordering</span></span>

<span data-ttu-id="972cb-104">Bu konudaki örneklerde, yöntem <xref:System.Linq.Enumerable.ThenBy%2A> tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="972cb-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="972cb-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="972cb-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="972cb-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="972cb-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="972cb-107">ThenBy</span><span class="sxs-lookup"><span data-stu-id="972cb-107">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="972cb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="972cb-108">Example</span></span>  

 <span data-ttu-id="972cb-109">Yöntem tabanlı sorgu söz diziminde aşağıdaki örnek, <xref:System.Linq.Queryable.OrderBy%2A> <xref:System.Linq.Queryable.ThenBy%2A> son ada göre sıralanmış kişilerin listesini ve sonra adı ve sonra adını döndürmek için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="972cb-109">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="972cb-110">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="972cb-110">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="972cb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="972cb-111">Example</span></span>  

 <span data-ttu-id="972cb-112">Aşağıdaki örnek, ilk olarak <xref:System.Linq.Queryable.OrderBy%2A> <xref:System.Linq.Queryable.ThenByDescending%2A> liste fiyatına göre sıralama yapmak için ve yöntemlerini kullanır ve ardından ürün adlarının azalan sıralamasını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="972cb-112">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="972cb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="972cb-113">See also</span></span>

- [<span data-ttu-id="972cb-114">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="972cb-114">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
