---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: c3a9bcef1944d0d018134383d3e556fe6ac24822
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250214"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="da7b0-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="da7b0-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="da7b0-103">Bu konudaki örneklerde, Yöntem tabanlı sorgu söz dizimini kullanarak `GroupBy` [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da7b0-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="da7b0-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="da7b0-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="da7b0-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="da7b0-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="da7b0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7b0-106">Example</span></span>  
 <span data-ttu-id="da7b0-107">Aşağıdaki örnek, posta koduna `GroupBy` göre gruplandırılan nesneleri `Address` döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da7b0-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="da7b0-108">Sonuçlar anonim bir türe yansıtılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="da7b0-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="da7b0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7b0-109">Example</span></span>  
 <span data-ttu-id="da7b0-110">Aşağıdaki örnek, kişinin son `GroupBy` adının ilk harfine `Contact` göre gruplanmış nesneleri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da7b0-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="da7b0-111">Sonuçlar Ayrıca son adın ilk harfine göre sıralanır ve bir anonim türe yansıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da7b0-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="da7b0-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7b0-112">Example</span></span>  
 <span data-ttu-id="da7b0-113">Aşağıdaki örnek, müşteri kimliğine `GroupBy` göre gruplanmış nesneleri `SalesOrderHeader` döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da7b0-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="da7b0-114">Her müşteri için satış sayısı da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="da7b0-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="da7b0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da7b0-115">See also</span></span>

- [<span data-ttu-id="da7b0-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="da7b0-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
