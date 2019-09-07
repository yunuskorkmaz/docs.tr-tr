---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: c9876c72a03f7827ec4b28d78f06ed372460caff
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398460"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="2e623-102">Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="2e623-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="2e623-103">Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak `GroupBy` [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e623-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="2e623-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="2e623-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2e623-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="2e623-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="2e623-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e623-106">Example</span></span>  
 <span data-ttu-id="2e623-107">Aşağıdaki örnek, posta `Address` koduna göre gruplanmış nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e623-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="2e623-108">Sonuçlar anonim bir türe yansıtılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2e623-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="2e623-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e623-109">Example</span></span>  
 <span data-ttu-id="2e623-110">Aşağıdaki örnek, kişinin `Contact` son adının ilk harfine göre gruplanmış nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e623-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="2e623-111">Sonuçlar Ayrıca, son adın ilk harfine göre sıralanır ve bir anonim türe yansıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e623-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="2e623-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e623-112">Example</span></span>  
 <span data-ttu-id="2e623-113">Aşağıdaki örnek, müşteri `SalesOrderHeader` kimliğine göre gruplanmış nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e623-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="2e623-114">Her müşteri için satış sayısı da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2e623-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="2e623-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e623-115">See also</span></span>

- [<span data-ttu-id="2e623-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="2e623-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
