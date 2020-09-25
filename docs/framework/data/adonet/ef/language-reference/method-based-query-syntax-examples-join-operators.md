---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri'
description: LINQ to Entities içindeki Yöntem tabanlı sorgu söz dizimini kullanarak bir modeli sorgulamak için JOIN ve Groupjoın yöntemlerini nasıl kullanacağınızı öğrenmek için bu örnekleri kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 7f02379f4ececb75981ab262f22ebdeb510739ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191968"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="8947b-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8947b-103">Method-Based Query Syntax Examples: Join Operators</span></span>

<span data-ttu-id="8947b-104">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8947b-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="8947b-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8947b-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8947b-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="8947b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="8947b-107">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="8947b-107">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="8947b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8947b-108">Example</span></span>  

 <span data-ttu-id="8947b-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.GroupJoin%2A> müşteri başına sipariş sayısını bulmak Için SalesOrderHeader ve SalesOrderDetail tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="8947b-109">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="8947b-110">Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="8947b-110">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="8947b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8947b-111">Example</span></span>  

 <span data-ttu-id="8947b-112">Aşağıdaki örnek, iletişim <xref:System.Linq.Enumerable.GroupJoin%2A> başına düşen sipariş sayısını bulmak Için Contact ve SalesOrderHeader tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="8947b-112">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="8947b-113">Her bir kişinin sıra sayısı ve kimlikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8947b-113">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="8947b-114">Birleştir</span><span class="sxs-lookup"><span data-stu-id="8947b-114">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="8947b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8947b-115">Example</span></span>  

 <span data-ttu-id="8947b-116">Aşağıdaki örnek, Contact ve SalesOrderHeader tabloları üzerinde bir JOIN uygular.</span><span class="sxs-lookup"><span data-stu-id="8947b-116">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="8947b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="8947b-117">Example</span></span>  

 <span data-ttu-id="8947b-118">Aşağıdaki örnek, Contact ve SalesOrderHeader tabloları üzerinde bir JOIN gerçekleştirerek sonuçları ilgili kişi KIMLIĞINE göre gruplandırıyor.</span><span class="sxs-lookup"><span data-stu-id="8947b-118">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8947b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8947b-119">See also</span></span>

- [<span data-ttu-id="8947b-120">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="8947b-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
