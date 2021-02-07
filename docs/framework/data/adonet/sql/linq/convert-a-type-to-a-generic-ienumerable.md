---
description: "Hakkında daha fazla bilgi edinin: bir türü genel IEnumerable 'a dönüştürme"
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: 9be9022bce84808e18514937116ea962065dc1a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712525"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="159dd-103">Türü Genel IEnumerable Öğesine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="159dd-103">Convert a Type to a Generic IEnumerable</span></span>

<span data-ttu-id="159dd-104"><xref:System.Linq.Enumerable.AsEnumerable%2A>Genel olarak yazılmış bağımsız değişkeni döndürmek için kullanın `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="159dd-104">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="159dd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="159dd-105">Example</span></span>  

 <span data-ttu-id="159dd-106">Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (varsayılan genel kullanılarak `Query` ) sorguyu SQL 'e dönüştürmeye ve sunucuda yürütmeye çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="159dd-106">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="159dd-107">Ancak `where` yan tümce, SQL 'e dönüştürülemeyen Kullanıcı tanımlı bir istemci tarafı yöntemine ( `isValidProduct` ) başvurur.</span><span class="sxs-lookup"><span data-stu-id="159dd-107">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="159dd-108">Çözüm, genel ' i değiştirmek için istemci tarafı genel <xref:System.Collections.Generic.IEnumerable%601> uygulamasını belirtmektir `where` <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="159dd-108">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="159dd-109">Bunu, işlecini çağırarak yapabilirsiniz <xref:System.Linq.Enumerable.AsEnumerable%2A> .</span><span class="sxs-lookup"><span data-stu-id="159dd-109">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="159dd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="159dd-110">See also</span></span>

- [<span data-ttu-id="159dd-111">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="159dd-111">Query Examples</span></span>](query-examples.md)
