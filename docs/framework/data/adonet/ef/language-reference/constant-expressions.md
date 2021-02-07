---
description: 'Daha fazla bilgi edinin: sabit Ifadeler'
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 3c040918df4af6a0302d2435e3564e395044108e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724836"
---
# <a name="constant-expressions"></a><span data-ttu-id="3667c-103">Sabit İfadeler</span><span class="sxs-lookup"><span data-stu-id="3667c-103">Constant Expressions</span></span>

<span data-ttu-id="3667c-104">Sabit bir ifade sabit bir değerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3667c-104">A constant expression consists of a constant value.</span></span> <span data-ttu-id="3667c-105">Sabit değerler, istemci üzerinde herhangi bir çeviri olmadan doğrudan sabit komut ağacı ifadelerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="3667c-105">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="3667c-106">Bu, sabit bir değere neden olan ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3667c-106">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="3667c-107">Bu nedenle, sabitleri içeren tüm ifadeler için veri kaynağı davranışının beklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="3667c-107">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="3667c-108">Bu, CLR davranışından farklı davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3667c-108">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="3667c-109">Aşağıdaki örnek, sunucuda değerlendirilen sabit bir ifadeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3667c-109">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="3667c-110">LINQ to Entities, bir Kullanıcı sınıfının sabit olarak kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3667c-110">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="3667c-111">Ancak, bir Kullanıcı sınıfındaki özellik başvurusu bir sabit kabul edilir ve bir komut ağacı sabit ifadesine dönüştürülür ve veri kaynağında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3667c-111">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3667c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3667c-112">See also</span></span>

- [<span data-ttu-id="3667c-113">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3667c-113">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
