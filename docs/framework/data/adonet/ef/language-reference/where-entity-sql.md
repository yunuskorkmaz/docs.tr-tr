---
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319177"
---
# <a name="where-entity-sql"></a><span data-ttu-id="6e156-102">Burada (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6e156-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="6e156-103">WHERE yan tümcesi [from](from-entity-sql.md) yan tümcesinden sonra doğrudan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6e156-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e156-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e156-104">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e156-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e156-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6e156-106">Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="6e156-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e156-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e156-107">Remarks</span></span>  
 <span data-ttu-id="6e156-108">WHERE yan tümcesi Transact-SQL için açıklananla aynı semantiğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6e156-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="6e156-109">Kaynak koleksiyonlarının öğelerini koşulu geçecek olanlarla sınırlayarak sorgu ifadesi tarafından üretilen nesneleri kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="6e156-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="6e156-110">@No__t-0 ifadesi Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e156-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="6e156-111">WHERE yan tümcesi FROM yan tümcesinden sonra ve herhangi bir gruplandırma, sıralama veya projeksiyon gerçekleşmeden önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6e156-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="6e156-112">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesinin ifadesi tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="6e156-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e156-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e156-113">See also</span></span>

- [<span data-ttu-id="6e156-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6e156-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6e156-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6e156-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
