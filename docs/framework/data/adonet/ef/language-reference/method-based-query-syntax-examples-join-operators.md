---
title: 'Yöntem temelli sorgu sözdizimi örnekler: Birleştirme işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: a77a58d28c667e5dabf0dda4c8d2f4782ea83572
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="94c17-102">Yöntem temelli sorgu sözdizimi örnekler: Birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="94c17-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="94c17-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="94c17-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="94c17-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="94c17-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="94c17-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="94c17-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="94c17-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="94c17-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="94c17-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="94c17-107">Example</span></span>  
 <span data-ttu-id="94c17-108">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> müşteri başına sipariş sayısını bulmak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinde.</span><span class="sxs-lookup"><span data-stu-id="94c17-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="94c17-109">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="94c17-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="94c17-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="94c17-110">Example</span></span>  
 <span data-ttu-id="94c17-111">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> kişi başına siparişleri sayısını bulmak için iletişim ve SalesOrderHeader tablolar üzerinde.</span><span class="sxs-lookup"><span data-stu-id="94c17-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="94c17-112">Sıra sayısı ve her kişi için kimlikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="94c17-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="94c17-113">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="94c17-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="94c17-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="94c17-114">Example</span></span>  
 <span data-ttu-id="94c17-115">Aşağıdaki örnek, ilgili kişi ve SalesOrderHeader tablolar üzerindeki bir birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="94c17-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="94c17-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="94c17-116">Example</span></span>  
 <span data-ttu-id="94c17-117">Aşağıdaki örnek, ilgili bir birleştirme gerçekleştirir ve sonuçları göre gruplandırma SalesOrderHeader tabloları kimliği başvurun</span><span class="sxs-lookup"><span data-stu-id="94c17-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="94c17-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94c17-118">See Also</span></span>  
 [<span data-ttu-id="94c17-119">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="94c17-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
