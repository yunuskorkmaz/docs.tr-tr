---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: c059bd771667c23bb9aeb78b548e7036e4b8a73a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647797"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="0de2c-102">Metot tabanlı sorgu söz dizimi örnekleri: sıralama</span><span class="sxs-lookup"><span data-stu-id="0de2c-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="0de2c-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ThenBy%2A> sorgu yöntemine [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0de2c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="0de2c-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0de2c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0de2c-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="0de2c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="0de2c-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="0de2c-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="0de2c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0de2c-107">Example</span></span>  
 <span data-ttu-id="0de2c-108">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte kullanan <xref:System.Linq.Queryable.OrderBy%2A> ve <xref:System.Linq.Queryable.ThenBy%2A> kişileri soyadına göre ve ardından ilk adına göre sıralanmış bir listesini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="0de2c-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="0de2c-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="0de2c-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="0de2c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0de2c-110">Example</span></span>  
 <span data-ttu-id="0de2c-111">Aşağıdaki örnekte <xref:System.Linq.Queryable.OrderBy%2A> ve <xref:System.Linq.Queryable.ThenByDescending%2A> ilk yöntemlerine göre fiyat listesi sıralama ve azalan düzende sıralar, ürün adları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0de2c-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0de2c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0de2c-112">See Also</span></span>  
 [<span data-ttu-id="0de2c-113">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="0de2c-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
