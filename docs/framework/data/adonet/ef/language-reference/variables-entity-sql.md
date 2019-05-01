---
title: Değişkenleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879781"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="913bc-102">Değişkenleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="913bc-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="913bc-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="913bc-103">Variable</span></span>  
 <span data-ttu-id="913bc-104">Değişken ifade geçerli kapsamda tanımlı adlandırılmış bir ifade bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="913bc-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="913bc-105">Bir değişken başvurusu geçerli olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcısı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="913bc-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="913bc-106">Aşağıdaki örnek ifade bir değişken kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="913bc-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="913bc-107">`c` İçinde FROM yan tümcesi değişkeni tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="913bc-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="913bc-108">Kullanımını `c` SELECT yan tümcesi, değişken başvurusu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="913bc-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="913bc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="913bc-109">See also</span></span>

- [<span data-ttu-id="913bc-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="913bc-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [<span data-ttu-id="913bc-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="913bc-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [<span data-ttu-id="913bc-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="913bc-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
