---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Öğe İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 9a057cd80b3dc110626d1a9a850ee7c9704b33b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250254"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="7b80c-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Öğe İşleçleri</span><span class="sxs-lookup"><span data-stu-id="7b80c-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="7b80c-103">Bu konudaki örneklerde, Yöntem tabanlı sorgu söz dizimini kullanarak <xref:System.Linq.Enumerable.First%2A> [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b80c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="7b80c-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7b80c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7b80c-105">Bu konudaki örnek aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="7b80c-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="7b80c-106">Adı</span><span class="sxs-lookup"><span data-stu-id="7b80c-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="7b80c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b80c-107">Example</span></span>  
 <span data-ttu-id="7b80c-108">Aşağıdaki örnek, ' Caroline ' ile başlayan ilk e-posta adresini bulmak için <xref:System.Linq.Enumerable.First%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b80c-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7b80c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b80c-109">See also</span></span>

- [<span data-ttu-id="7b80c-110">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="7b80c-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
