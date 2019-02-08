---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Öğe işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 89cbda4d049b30ee50accf94d5b7ec172bc25ae2
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826505"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="1bf6f-102">Metot tabanlı sorgu söz dizimi örnekleri: Öğe işleçleri</span><span class="sxs-lookup"><span data-stu-id="1bf6f-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="1bf6f-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> sorgu yöntemine [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="1bf6f-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1bf6f-105">Aşağıdaki örnekte bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="1bf6f-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="1bf6f-106">ilk</span><span class="sxs-lookup"><span data-stu-id="1bf6f-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="1bf6f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bf6f-107">Example</span></span>  
 <span data-ttu-id="1bf6f-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.First%2A> 'caroline' ile başlayan ilk e-posta adresini bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf6f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-109">See also</span></span>
- [<span data-ttu-id="1bf6f-110">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="1bf6f-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
