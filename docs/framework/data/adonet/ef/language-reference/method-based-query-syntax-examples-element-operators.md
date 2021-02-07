---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: öğe Işleçleri'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Öğe İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 8a83602c4d374ae02b4f39ee75821718f8b53f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673589"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="394cd-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="394cd-103">Method-Based Query Syntax Examples: Element Operators</span></span>

<span data-ttu-id="394cd-104">Bu konudaki örneklerde, yöntem <xref:System.Linq.Enumerable.First%2A> tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="394cd-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="394cd-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="394cd-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="394cd-106">Bu konudaki örnek aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="394cd-106">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="394cd-107">Birinci</span><span class="sxs-lookup"><span data-stu-id="394cd-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="394cd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="394cd-108">Example</span></span>  

 <span data-ttu-id="394cd-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.First%2A> ' Caroline ' ile başlayan ilk e-posta adresini bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="394cd-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="394cd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="394cd-110">See also</span></span>

- [<span data-ttu-id="394cd-111">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="394cd-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
