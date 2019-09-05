---
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248481"
---
# <a name="where-entity-sql"></a><span data-ttu-id="6ed43-102">Burada (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6ed43-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="6ed43-103">WHERE yan tümcesi [from](from-entity-sql.md) yan tümcesinden sonra doğrudan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6ed43-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ed43-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ed43-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6ed43-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6ed43-106">Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="6ed43-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed43-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ed43-107">Remarks</span></span>  
 <span data-ttu-id="6ed43-108">WHERE yan tümcesi Transact-SQL için açıklananla aynı semantiğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6ed43-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="6ed43-109">Kaynak koleksiyonlarının öğelerini koşulu geçecek olanlarla sınırlayarak sorgu ifadesi tarafından üretilen nesneleri kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="6ed43-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="6ed43-110">İfade `e` , Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ed43-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="6ed43-111">WHERE yan tümcesi FROM yan tümcesinden sonra ve herhangi bir gruplandırma, sıralama veya projeksiyon gerçekleşmeden önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6ed43-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="6ed43-112">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesinin ifadesi tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="6ed43-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed43-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ed43-113">See also</span></span>

- [<span data-ttu-id="6ed43-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6ed43-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6ed43-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6ed43-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
