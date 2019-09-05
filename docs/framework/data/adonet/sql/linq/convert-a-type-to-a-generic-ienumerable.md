---
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247728"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="487e7-102">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="487e7-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="487e7-103"><xref:System.Linq.Enumerable.AsEnumerable%2A> Genel`IEnumerable`olarak yazılmış bağımsız değişkeni döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="487e7-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="487e7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="487e7-104">Example</span></span>  
 <span data-ttu-id="487e7-105">Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (varsayılan genel `Query`kullanılarak) sorguyu SQL 'e dönüştürmeye ve sunucuda yürütmeye çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="487e7-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="487e7-106">Ancak yan tümce, SQL 'e dönüştürülemeyen Kullanıcı tanımlı bir istemci tarafı yöntemine`isValidProduct`() başvurur. `where`</span><span class="sxs-lookup"><span data-stu-id="487e7-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="487e7-107">Çözüm, genel <xref:System.Collections.Generic.IEnumerable%601> `where` 'ideğiştirmekiçinistemcitarafıgenel<xref:System.Linq.IQueryable%601>uygulamasını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="487e7-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="487e7-108">Bunu, <xref:System.Linq.Enumerable.AsEnumerable%2A> işlecini çağırarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="487e7-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="487e7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="487e7-109">See also</span></span>

- [<span data-ttu-id="487e7-110">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="487e7-110">Query Examples</span></span>](query-examples.md)
