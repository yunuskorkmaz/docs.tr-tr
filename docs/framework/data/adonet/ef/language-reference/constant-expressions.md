---
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: b31cd881f1307ec734c026d3c873d7a650e19a20
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251128"
---
# <a name="constant-expressions"></a><span data-ttu-id="88587-102">Sabit İfadeler</span><span class="sxs-lookup"><span data-stu-id="88587-102">Constant Expressions</span></span>
<span data-ttu-id="88587-103">Sabit bir ifade sabit bir değerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="88587-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="88587-104">Sabit değerler, istemci üzerinde herhangi bir çeviri olmadan doğrudan sabit komut ağacı ifadelerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="88587-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="88587-105">Bu, sabit bir değere neden olan ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="88587-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="88587-106">Bu nedenle, sabitleri içeren tüm ifadeler için veri kaynağı davranışının beklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="88587-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="88587-107">Bu, CLR davranışından farklı davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="88587-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="88587-108">Aşağıdaki örnek, sunucuda değerlendirilen sabit bir ifadeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="88587-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="88587-109">LINQ to Entities, bir Kullanıcı sınıfının sabit olarak kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="88587-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="88587-110">Ancak, bir Kullanıcı sınıfındaki özellik başvurusu bir sabit kabul edilir ve bir komut ağacı sabit ifadesine dönüştürülür ve veri kaynağında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="88587-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88587-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88587-111">See also</span></span>

- [<span data-ttu-id="88587-112">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="88587-112">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
