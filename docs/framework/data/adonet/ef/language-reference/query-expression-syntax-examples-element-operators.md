---
title: 'Sorgu ifade sözdizimi örnekleri: Öğesi işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: ac10bbcb76e7e4e1feebaffbc85551993626933e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762240"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="7ef03-102">Sorgu ifade sözdizimi örnekleri: Öğesi işleçleri</span><span class="sxs-lookup"><span data-stu-id="7ef03-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="7ef03-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> sorgu yönteme [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7ef03-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using the query expression syntax.</span></span> <span data-ttu-id="7ef03-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7ef03-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7ef03-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="7ef03-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="7ef03-106">ilk</span><span class="sxs-lookup"><span data-stu-id="7ef03-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ef03-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ef03-107">Example</span></span>  
 <span data-ttu-id="7ef03-108">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.First%2A> ilk kişinin ilk adını döndürmek için yöntemdir "Brooke".</span><span class="sxs-lookup"><span data-stu-id="7ef03-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="7ef03-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef03-109">See Also</span></span>  
 [<span data-ttu-id="7ef03-110">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="7ef03-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
