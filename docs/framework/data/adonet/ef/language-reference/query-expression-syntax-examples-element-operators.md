---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: ddd352fe3bf731c2d436937616d21c0a7257acdc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398479"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="65bd6-102">Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="65bd6-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="65bd6-103">Bu konudaki örneklerde, sorgu ifadesi sözdizimini kullanarak <xref:System.Linq.Enumerable.First%2A> [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="65bd6-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="65bd6-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="65bd6-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="65bd6-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="65bd6-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="65bd6-106">Adı</span><span class="sxs-lookup"><span data-stu-id="65bd6-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="65bd6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="65bd6-107">Example</span></span>  
 <span data-ttu-id="65bd6-108">Aşağıdaki örnek, ilk adı <xref:System.Linq.Enumerable.First%2A> "Brooke" olan ilk kişiyi döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="65bd6-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="65bd6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65bd6-109">See also</span></span>

- [<span data-ttu-id="65bd6-110">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="65bd6-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
