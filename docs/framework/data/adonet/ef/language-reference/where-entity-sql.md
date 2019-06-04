---
title: Burada (varlık SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489853"
---
# <a name="where-entity-sql"></a><span data-ttu-id="0a340-102">Burada (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="0a340-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="0a340-103">WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="0a340-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a340-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a340-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a340-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0a340-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0a340-106">Bir Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="0a340-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a340-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a340-107">Remarks</span></span>  
 <span data-ttu-id="0a340-108">WHERE yan tümcesi, Transact-SQL için açıklandığı gibi aynı semantiğe sahip.</span><span class="sxs-lookup"><span data-stu-id="0a340-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="0a340-109">Bu koşul başarılı olanlar kaynak koleksiyonları öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="0a340-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="0a340-110">İfade `e` Boolean türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a340-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="0a340-111">WHERE yan tümcesi doğrudan FROM yan tümcesinden sonra ve önce tüm gruplandırma, sıralama veya yansıtma uygulanan yerini alır.</span><span class="sxs-lookup"><span data-stu-id="0a340-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="0a340-112">FROM yan tümcesinde tanımlı tüm öğe adları, WHERE yan tümcesinin ifadesi için görülebilir.</span><span class="sxs-lookup"><span data-stu-id="0a340-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a340-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a340-113">See also</span></span>

- [<span data-ttu-id="0a340-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0a340-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="0a340-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="0a340-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
