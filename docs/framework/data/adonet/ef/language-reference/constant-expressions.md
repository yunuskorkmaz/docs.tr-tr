---
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: cc3a214a2faa06c79ee0794b0158381bff0c4b0b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539894"
---
# <a name="constant-expressions"></a><span data-ttu-id="1a3b6-102">Sabit İfadeler</span><span class="sxs-lookup"><span data-stu-id="1a3b6-102">Constant Expressions</span></span>
<span data-ttu-id="1a3b6-103">Sabit bir ifade bir sabit değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="1a3b6-104">Sabit değerleri, sabit komut ağaç ifadeleri, istemcideki herhangi bir çeviri olmadan doğrudan dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="1a3b6-105">Bu, bir sabit değer ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="1a3b6-106">Bu nedenle, veri kaynağı davranışı sabitleri içeren tüm ifadeler için beklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="1a3b6-107">Bu CLR davranışından farklıdır davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="1a3b6-108">Aşağıdaki örnek, sunucu üzerinde değerlendirilen sabit bir ifade gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="1a3b6-109">LINQ to Entities kullanıcı sınıfı bir sabit olarak kullanma desteği olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="1a3b6-110">Ancak, bir kullanıcı sınıfta bir özellik başvurusu bir sabit olarak kabul edilir ve bir komut ağacı sabit ifade dönüştürülür ve veri kaynağında yürütülen.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3b6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a3b6-111">See also</span></span>

- [<span data-ttu-id="1a3b6-112">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1a3b6-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
