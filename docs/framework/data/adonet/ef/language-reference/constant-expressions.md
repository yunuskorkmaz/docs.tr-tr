---
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 10c74ede8d490bf96a9d0855889669bdc2628b01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785365"
---
# <a name="constant-expressions"></a><span data-ttu-id="08176-102">Sabit İfadeler</span><span class="sxs-lookup"><span data-stu-id="08176-102">Constant Expressions</span></span>
<span data-ttu-id="08176-103">Sabit bir ifade bir sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="08176-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="08176-104">Sabit değerleri, sabit komut ağaç ifadeleri, istemcideki herhangi bir çeviri olmadan doğrudan dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="08176-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="08176-105">Bu, bir sabit değer ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="08176-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="08176-106">Bu nedenle, veri kaynağı davranışı sabitleri içeren tüm ifadeler için beklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="08176-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="08176-107">Bu CLR davranışından farklıdır davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="08176-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="08176-108">Aşağıdaki örnek, sunucu üzerinde değerlendirilen sabit bir ifade gösterir.</span><span class="sxs-lookup"><span data-stu-id="08176-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] <span data-ttu-id="08176-109">Kullanıcı sınıfı bir sabit olarak kullanma desteği olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="08176-109">does not support using a user class as a constant.</span></span> <span data-ttu-id="08176-110">Ancak, bir kullanıcı sınıfta bir özellik başvurusu bir sabit olarak kabul edilir ve bir komut ağacı sabit ifade dönüştürülür ve veri kaynağında yürütülen.</span><span class="sxs-lookup"><span data-stu-id="08176-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08176-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08176-111">See also</span></span>

- [<span data-ttu-id="08176-112">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="08176-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
