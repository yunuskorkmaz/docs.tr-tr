---
title: 'Yöntem temelli sorgu sözdizimi örnekleri: gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 1bc2ab6f7dbfb3b2babcc5a9565a7bfd9fd962c4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="43d25-102">Yöntem temelli sorgu sözdizimi örnekleri: gruplandırma</span><span class="sxs-lookup"><span data-stu-id="43d25-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="43d25-103">Bu konudaki örnekler nasıl kullanılacağını gösterir `GroupBy` sorgu yönteme [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="43d25-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="43d25-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="43d25-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="43d25-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="43d25-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="43d25-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="43d25-106">Example</span></span>  
 <span data-ttu-id="43d25-107">Aşağıdaki örnek kullanır `GroupBy` döndürülecek yöntemi `Address` posta koduna göre gruplandırılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="43d25-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="43d25-108">Sonuçları anonim bir tür öngörülen.</span><span class="sxs-lookup"><span data-stu-id="43d25-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="43d25-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="43d25-109">Example</span></span>  
 <span data-ttu-id="43d25-110">Aşağıdaki örnek kullanır `GroupBy` döndürülecek yöntemi `Contact` kişinin soyadını ilk harfe göre gruplandırılmış nesneleri.</span><span class="sxs-lookup"><span data-stu-id="43d25-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="43d25-111">Sonuçlar Ayrıca son adının ilk harfi göre sıralanır ve anonim bir tür öngörülen.</span><span class="sxs-lookup"><span data-stu-id="43d25-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="43d25-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="43d25-112">Example</span></span>  
 <span data-ttu-id="43d25-113">Aşağıdaki örnek kullanır `GroupBy` döndürülecek yöntemi `SalesOrderHeader` müşteri kimliğine göre gruplandırılmış nesneleri</span><span class="sxs-lookup"><span data-stu-id="43d25-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="43d25-114">Her müşteri için satış sayısını da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43d25-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="43d25-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43d25-115">See Also</span></span>  
 [<span data-ttu-id="43d25-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="43d25-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
