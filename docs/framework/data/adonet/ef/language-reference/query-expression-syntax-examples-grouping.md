---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: 0a4aa57ba709852c30223598b9d1af146eaf6013
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212004"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="2e4af-102">Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="2e4af-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="2e4af-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `GroupBy` sorgu yöntemine [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2e4af-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="2e4af-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2e4af-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2e4af-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="2e4af-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="2e4af-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e4af-106">Example</span></span>  
 <span data-ttu-id="2e4af-107">Aşağıdaki örnek döndürür `Address` posta koduna göre gruplandırılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2e4af-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="2e4af-108">Anonim bir tür yansıtılan sonuçları.</span><span class="sxs-lookup"><span data-stu-id="2e4af-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="2e4af-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e4af-109">Example</span></span>  
 <span data-ttu-id="2e4af-110">Aşağıdaki örnek döndürür `Contact` kişinin soyadı ilk harfe göre gruplanan nesneler.</span><span class="sxs-lookup"><span data-stu-id="2e4af-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="2e4af-111">Sonuçları da son adının ilk harfi sıralanır ve anonim bir tür yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="2e4af-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="2e4af-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e4af-112">Example</span></span>  
 <span data-ttu-id="2e4af-113">Aşağıdaki örnek döndürür `SalesOrderHeader` müşteri kimliğine göre gruplandırılmış nesneleri</span><span class="sxs-lookup"><span data-stu-id="2e4af-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="2e4af-114">Ayrıca, her müşteri için satış sayısı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2e4af-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="2e4af-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e4af-115">See also</span></span>

- [<span data-ttu-id="2e4af-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="2e4af-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
