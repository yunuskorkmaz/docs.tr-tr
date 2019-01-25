---
title: 'Sorgu ifadesi söz dizimi örnekleri: Öğe işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 19a68903783edfc190f0b32bd67fcc74e47937ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681332"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="e0fd1-102">Sorgu ifadesi söz dizimi örnekleri: Öğe işleçleri</span><span class="sxs-lookup"><span data-stu-id="e0fd1-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="e0fd1-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> sorgu yöntemine [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="e0fd1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using the query expression syntax.</span></span> <span data-ttu-id="e0fd1-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0fd1-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e0fd1-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="e0fd1-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="e0fd1-106">ilk</span><span class="sxs-lookup"><span data-stu-id="e0fd1-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="e0fd1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0fd1-107">Example</span></span>  
 <span data-ttu-id="e0fd1-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.First%2A> yöntemi ilk kişinin ilk adı döndürülecek olan "Brooke".</span><span class="sxs-lookup"><span data-stu-id="e0fd1-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="e0fd1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0fd1-109">See also</span></span>
- [<span data-ttu-id="e0fd1-110">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="e0fd1-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
