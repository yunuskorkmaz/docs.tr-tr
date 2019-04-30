---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 700c29222d10177774e118e53fb51f177b723679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760538"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="d4ccd-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d4ccd-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="d4ccd-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="d4ccd-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d4ccd-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="d4ccd-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="d4ccd-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="d4ccd-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="d4ccd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4ccd-107">Example</span></span>  
 <span data-ttu-id="d4ccd-108">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> her müşteri siparişleri sayısını bulmak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="d4ccd-109">Grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili hiçbir öğe olsa bile, döndüren bir sol dış birleşim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="d4ccd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4ccd-110">Example</span></span>  
 <span data-ttu-id="d4ccd-111">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> kişi başına siparişlerin sayısını bulmak için iletişim ve SalesOrderHeader tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="d4ccd-112">Her kişi için kimlikleri ve sipariş sayısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="d4ccd-113">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="d4ccd-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="d4ccd-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4ccd-114">Example</span></span>  
 <span data-ttu-id="d4ccd-115">Aşağıdaki örnek, kişi ve SalesOrderHeader tablolar üzerindeki bir birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="d4ccd-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4ccd-116">Example</span></span>  
 <span data-ttu-id="d4ccd-117">Aşağıdaki örnek, ilgili bir birleştirme gerçekleştirir ve kimliği sonuçlarına göre gruplandırma SalesOrderHeader tablolar başvurun</span><span class="sxs-lookup"><span data-stu-id="d4ccd-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d4ccd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ccd-118">See also</span></span>

- [<span data-ttu-id="d4ccd-119">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="d4ccd-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
