---
description: 'Hakkında daha fazla bilgi edinin: (Entity SQL)'
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: e094a93927f6ac77aef772654f1d8d4fcf999cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712876"
---
# <a name="where-entity-sql"></a><span data-ttu-id="84653-103">Burada (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="84653-103">WHERE (Entity SQL)</span></span>

<span data-ttu-id="84653-104">WHERE yan tümcesi [from](from-entity-sql.md) yan tümcesinden sonra doğrudan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="84653-104">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84653-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="84653-105">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="84653-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="84653-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="84653-107">Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="84653-107">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84653-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84653-108">Remarks</span></span>  

 <span data-ttu-id="84653-109">WHERE yan tümcesi Transact-SQL için açıklananla aynı semantiğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="84653-109">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="84653-110">Kaynak koleksiyonlarının öğelerini koşulu geçecek olanlarla sınırlayarak sorgu ifadesi tarafından üretilen nesneleri kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="84653-110">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="84653-111">İfade, `e` Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84653-111">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="84653-112">WHERE yan tümcesi FROM yan tümcesinden sonra ve herhangi bir gruplandırma, sıralama veya projeksiyon gerçekleşmeden önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="84653-112">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="84653-113">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesinin ifadesi tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="84653-113">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84653-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84653-114">See also</span></span>

- [<span data-ttu-id="84653-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="84653-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="84653-116">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="84653-116">Query Expressions</span></span>](query-expressions-entity-sql.md)
