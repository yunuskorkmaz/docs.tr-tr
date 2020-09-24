---
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c2d34ae708f79d9f920679b3714a100fe8943c38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164421"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="55dcd-102">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="55dcd-102">Convert a Type to a Generic IEnumerable</span></span>

<span data-ttu-id="55dcd-103"><xref:System.Linq.Enumerable.AsEnumerable%2A>Genel olarak yazılmış bağımsız değişkeni döndürmek için kullanın `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="55dcd-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55dcd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="55dcd-104">Example</span></span>  

 <span data-ttu-id="55dcd-105">Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (varsayılan genel kullanılarak `Query` ) sorguyu SQL 'e dönüştürmeye ve sunucuda yürütmeye çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="55dcd-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="55dcd-106">Ancak `where` yan tümce, SQL 'e dönüştürülemeyen Kullanıcı tanımlı bir istemci tarafı yöntemine ( `isValidProduct` ) başvurur.</span><span class="sxs-lookup"><span data-stu-id="55dcd-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="55dcd-107">Çözüm, genel ' i değiştirmek için istemci tarafı genel <xref:System.Collections.Generic.IEnumerable%601> uygulamasını belirtmektir `where` <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="55dcd-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="55dcd-108">Bunu, işlecini çağırarak yapabilirsiniz <xref:System.Linq.Enumerable.AsEnumerable%2A> .</span><span class="sxs-lookup"><span data-stu-id="55dcd-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="55dcd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55dcd-109">See also</span></span>

- [<span data-ttu-id="55dcd-110">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="55dcd-110">Query Examples</span></span>](query-examples.md)
