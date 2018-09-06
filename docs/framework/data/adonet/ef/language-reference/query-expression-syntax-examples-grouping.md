---
title: 'Sorgu ifadesi söz dizimi örnekleri: gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: 519f9073954e8f7710c9e73b61f40b4fcfefd25b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873856"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="9b51b-102">Sorgu ifadesi söz dizimi örnekleri: gruplandırma</span><span class="sxs-lookup"><span data-stu-id="9b51b-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="9b51b-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `GroupBy` sorgu yöntemine [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="9b51b-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="9b51b-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9b51b-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9b51b-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="9b51b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="9b51b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b51b-106">Example</span></span>  
 <span data-ttu-id="9b51b-107">Aşağıdaki örnek döndürür `Address` posta koduna göre gruplandırılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9b51b-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="9b51b-108">Anonim bir tür yansıtılan sonuçları.</span><span class="sxs-lookup"><span data-stu-id="9b51b-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="9b51b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b51b-109">Example</span></span>  
 <span data-ttu-id="9b51b-110">Aşağıdaki örnek döndürür `Contact` kişinin soyadı ilk harfe göre gruplanan nesneler.</span><span class="sxs-lookup"><span data-stu-id="9b51b-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="9b51b-111">Sonuçları da son adının ilk harfi sıralanır ve anonim bir tür yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="9b51b-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="9b51b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b51b-112">Example</span></span>  
 <span data-ttu-id="9b51b-113">Aşağıdaki örnek döndürür `SalesOrderHeader` müşteri kimliğine göre gruplandırılmış nesneleri</span><span class="sxs-lookup"><span data-stu-id="9b51b-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="9b51b-114">Ayrıca, her müşteri için satış sayısı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9b51b-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="9b51b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b51b-115">See Also</span></span>  
 [<span data-ttu-id="9b51b-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="9b51b-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
