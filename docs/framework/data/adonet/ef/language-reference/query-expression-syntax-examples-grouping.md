---
title: 'Sorgu ifade sözdizimi örnekleri: gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: a5222110bc5ac41ecaaa8e5003262360fd4d9ff5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="908d5-102">Sorgu ifade sözdizimi örnekleri: gruplandırma</span><span class="sxs-lookup"><span data-stu-id="908d5-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="908d5-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `GroupBy` sorgu yönteme [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="908d5-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="908d5-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="908d5-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="908d5-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="908d5-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="908d5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="908d5-106">Example</span></span>  
 <span data-ttu-id="908d5-107">Aşağıdaki örnek verir `Address` posta koduna göre gruplandırılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="908d5-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="908d5-108">Sonuçları anonim bir tür öngörülen.</span><span class="sxs-lookup"><span data-stu-id="908d5-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="908d5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="908d5-109">Example</span></span>  
 <span data-ttu-id="908d5-110">Aşağıdaki örnek verir `Contact` kişinin soyadını ilk harfe göre gruplandırılmış nesneleri.</span><span class="sxs-lookup"><span data-stu-id="908d5-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="908d5-111">Sonuçlar Ayrıca son adının ilk harfi göre sıralanır ve anonim bir tür öngörülen.</span><span class="sxs-lookup"><span data-stu-id="908d5-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="908d5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="908d5-112">Example</span></span>  
 <span data-ttu-id="908d5-113">Aşağıdaki örnek verir `SalesOrderHeader` müşteri kimliğine göre gruplandırılmış nesneleri</span><span class="sxs-lookup"><span data-stu-id="908d5-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="908d5-114">Her müşteri için satış sayısını da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="908d5-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="908d5-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="908d5-115">See Also</span></span>  
 [<span data-ttu-id="908d5-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="908d5-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
