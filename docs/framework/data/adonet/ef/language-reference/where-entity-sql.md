---
title: Burada (varlık SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 0b9cf9bdb211a74acd8fc229c53f3565b48e5ddd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670582"
---
# <a name="where-entity-sql"></a><span data-ttu-id="e17c8-102">Burada (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e17c8-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="e17c8-103">WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e17c8-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e17c8-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e17c8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e17c8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e17c8-106">Bir Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="e17c8-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e17c8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e17c8-107">Remarks</span></span>  
 <span data-ttu-id="e17c8-108">WHERE yan tümcesi için açıklandığı gibi aynı semantiğe sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e17c8-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e17c8-109">Bu koşul başarılı olanlar kaynak koleksiyonları öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="e17c8-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="e17c8-110">İfade `e` Boolean türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e17c8-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="e17c8-111">WHERE yan tümcesi doğrudan FROM yan tümcesinden sonra ve önce tüm gruplandırma, sıralama veya yansıtma uygulanan yerini alır.</span><span class="sxs-lookup"><span data-stu-id="e17c8-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="e17c8-112">FROM yan tümcesinde tanımlı tüm öğe adları, WHERE yan tümcesinin ifadesi için görülebilir.</span><span class="sxs-lookup"><span data-stu-id="e17c8-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17c8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e17c8-113">See also</span></span>
- [<span data-ttu-id="e17c8-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e17c8-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e17c8-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e17c8-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
