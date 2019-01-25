---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Öğe işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 302530b38e4feb7c34e672fbaa4473044515faf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542866"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="82e32-102">Metot tabanlı sorgu söz dizimi örnekleri: Öğe işleçleri</span><span class="sxs-lookup"><span data-stu-id="82e32-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="82e32-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> sorgu yöntemine [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="82e32-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="82e32-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82e32-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="82e32-105">Aşağıdaki örnekte bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="82e32-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="82e32-106">ilk</span><span class="sxs-lookup"><span data-stu-id="82e32-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="82e32-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="82e32-107">Example</span></span>  
 <span data-ttu-id="82e32-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.First%2A> 'caroline' ile başlayan ilk e-posta adresini bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="82e32-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="82e32-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e32-109">See also</span></span>
- [<span data-ttu-id="82e32-110">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="82e32-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
