---
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 1907b8786622d3c8019c75916f997c830cc07cfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180965"
---
# <a name="where-entity-sql"></a><span data-ttu-id="c04a2-102">Burada (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c04a2-102">WHERE (Entity SQL)</span></span>

<span data-ttu-id="c04a2-103">WHERE yan tümcesi [from](from-entity-sql.md) yan tümcesinden sonra doğrudan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c04a2-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04a2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c04a2-104">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c04a2-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c04a2-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="c04a2-106">Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="c04a2-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c04a2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c04a2-107">Remarks</span></span>  

 <span data-ttu-id="c04a2-108">WHERE yan tümcesi Transact-SQL için açıklananla aynı semantiğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c04a2-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="c04a2-109">Kaynak koleksiyonlarının öğelerini koşulu geçecek olanlarla sınırlayarak sorgu ifadesi tarafından üretilen nesneleri kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="c04a2-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="c04a2-110">İfade, `e` Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c04a2-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="c04a2-111">WHERE yan tümcesi FROM yan tümcesinden sonra ve herhangi bir gruplandırma, sıralama veya projeksiyon gerçekleşmeden önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c04a2-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="c04a2-112">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesinin ifadesi tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c04a2-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04a2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04a2-113">See also</span></span>

- [<span data-ttu-id="c04a2-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c04a2-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c04a2-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c04a2-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
