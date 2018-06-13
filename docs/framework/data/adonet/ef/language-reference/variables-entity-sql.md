---
title: Değişkenleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: f271ffc31875e7d94a27f4752b71bfe508fcb620
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765522"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="87ee1-102">Değişkenleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="87ee1-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="87ee1-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="87ee1-103">Variable</span></span>  
 <span data-ttu-id="87ee1-104">Bir başvuru geçerli kapsamda tanımlı adlandırılmış bir ifade bir değişken ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="87ee1-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="87ee1-105">Bir değişken başvurusu geçerli bir olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="87ee1-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="87ee1-106">Aşağıdaki örnek ifade bir değişken kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="87ee1-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="87ee1-107">`c` FROM yan tümcesi değişkeni tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="87ee1-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="87ee1-108">Kullanımını `c` SELECT yan tümcesi değişken başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="87ee1-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="87ee1-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87ee1-109">See Also</span></span>  
 [<span data-ttu-id="87ee1-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="87ee1-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="87ee1-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87ee1-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="87ee1-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="87ee1-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
