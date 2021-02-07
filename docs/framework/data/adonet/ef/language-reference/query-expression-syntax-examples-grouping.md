---
description: 'Daha fazla bilgi: sorgu Ifadesi söz dizimi örnekleri: gruplandırma'
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: 1d8bd51a783cbd53716daebfa9b547f5e4fffc1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696223"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="609ae-103">Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="609ae-103">Query Expression Syntax Examples: Grouping</span></span>

<span data-ttu-id="609ae-104">Bu konudaki örneklerde, `GroupBy` sorgu ifadesi söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="609ae-104">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="609ae-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="609ae-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="609ae-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="609ae-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="609ae-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="609ae-107">Example</span></span>  

 <span data-ttu-id="609ae-108">Aşağıdaki örnek, `Address` posta koduna göre gruplanmış nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="609ae-108">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="609ae-109">Sonuçlar anonim bir türe yansıtılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="609ae-109">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="609ae-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="609ae-110">Example</span></span>  

 <span data-ttu-id="609ae-111">Aşağıdaki örnek, `Contact` kişinin son adının ilk harfine göre gruplanmış nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="609ae-111">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="609ae-112">Sonuçlar Ayrıca, son adın ilk harfine göre sıralanır ve bir anonim türe yansıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="609ae-112">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="609ae-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="609ae-113">Example</span></span>  

 <span data-ttu-id="609ae-114">Aşağıdaki örnek, `SalesOrderHeader` MÜŞTERI kimliğine göre gruplanmış nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="609ae-114">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="609ae-115">Her müşteri için satış sayısı da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="609ae-115">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="609ae-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609ae-116">See also</span></span>

- [<span data-ttu-id="609ae-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="609ae-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
