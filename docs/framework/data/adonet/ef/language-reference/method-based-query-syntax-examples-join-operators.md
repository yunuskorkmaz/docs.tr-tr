---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 2f26f937901debd27cb936d1f642e0a5149b167a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250129"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="decc3-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="decc3-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="decc3-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="decc3-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="decc3-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="decc3-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="decc3-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="decc3-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="decc3-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="decc3-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="decc3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="decc3-107">Example</span></span>  
 <span data-ttu-id="decc3-108">Aşağıdaki örnek, müşteri başına <xref:System.Linq.Enumerable.GroupJoin%2A> sipariş sayısını bulmak için SalesOrderHeader ve SalesOrderDetail tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="decc3-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="decc3-109">Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="decc3-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="decc3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="decc3-110">Example</span></span>  
 <span data-ttu-id="decc3-111">Aşağıdaki örnek, iletişim başına <xref:System.Linq.Enumerable.GroupJoin%2A> düşen sipariş sayısını bulmak için Contact ve SalesOrderHeader tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="decc3-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="decc3-112">Her bir kişinin sıra sayısı ve kimlikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="decc3-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="decc3-113">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="decc3-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="decc3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="decc3-114">Example</span></span>  
 <span data-ttu-id="decc3-115">Aşağıdaki örnek, Contact ve SalesOrderHeader tabloları üzerinde bir JOIN uygular.</span><span class="sxs-lookup"><span data-stu-id="decc3-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="decc3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="decc3-116">Example</span></span>  
 <span data-ttu-id="decc3-117">Aşağıdaki örnek, Contact ve SalesOrderHeader tabloları üzerinde bir JOIN gerçekleştirerek sonuçları ilgili kişi KIMLIĞINE göre gruplandırıyor.</span><span class="sxs-lookup"><span data-stu-id="decc3-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="decc3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="decc3-118">See also</span></span>

- [<span data-ttu-id="decc3-119">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="decc3-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
