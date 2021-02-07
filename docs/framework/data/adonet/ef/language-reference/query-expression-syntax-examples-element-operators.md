---
description: 'Hakkında daha fazla bilgi edinin: sorgu Ifadesi sözdizimi örnekleri: öğe Işleçleri'
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 0dc6d49959abba712cef572eaa549138af646bd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696249"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="5f9f0-103">Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5f9f0-103">Query Expression Syntax Examples: Element Operators</span></span>

<span data-ttu-id="5f9f0-104">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.First%2A> sorgu ifadesi sözdizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f9f0-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="5f9f0-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5f9f0-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5f9f0-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="5f9f0-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="5f9f0-107">Birinci</span><span class="sxs-lookup"><span data-stu-id="5f9f0-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="5f9f0-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f9f0-108">Example</span></span>  

 <span data-ttu-id="5f9f0-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.First%2A> ilk adı "Brooke" olan ilk kişiyi döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f9f0-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="5f9f0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f9f0-110">See also</span></span>

- [<span data-ttu-id="5f9f0-111">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="5f9f0-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
