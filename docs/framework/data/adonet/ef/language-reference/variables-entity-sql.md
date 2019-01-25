---
title: Değişkenleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: a16c450401eee1021aeef885fba129c943a87fd7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742282"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="c1be5-102">Değişkenleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="c1be5-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="c1be5-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="c1be5-103">Variable</span></span>  
 <span data-ttu-id="c1be5-104">Değişken ifade geçerli kapsamda tanımlı adlandırılmış bir ifade bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="c1be5-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="c1be5-105">Bir değişken başvurusu geçerli olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcısı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c1be5-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c1be5-106">Aşağıdaki örnek ifade bir değişken kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1be5-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="c1be5-107">`c` İçinde FROM yan tümcesi değişkeni tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="c1be5-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="c1be5-108">Kullanımını `c` SELECT yan tümcesi, değişken başvurusu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1be5-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1be5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1be5-109">See also</span></span>
- [<span data-ttu-id="c1be5-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="c1be5-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [<span data-ttu-id="c1be5-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1be5-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [<span data-ttu-id="c1be5-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1be5-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
