---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149823"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="30e1a-102">Değişkenler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="30e1a-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="30e1a-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="30e1a-103">Variable</span></span>  
 <span data-ttu-id="30e1a-104">Değişken ifade, geçerli kapsamda tanımlanan adlandırılmış bir ifadeye yapılan bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="30e1a-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="30e1a-105">Değişken başvuru, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] [Tanımlayıcılar'da](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir tanımlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30e1a-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="30e1a-106">Aşağıdaki örnek, ifadede bir değişkenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30e1a-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="30e1a-107">FROM `c` yan tümcesi değişkenin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="30e1a-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="30e1a-108">SELECT yan `c` tümcesinin kullanımı değişken başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="30e1a-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="30e1a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30e1a-109">See also</span></span>

- [<span data-ttu-id="30e1a-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="30e1a-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="30e1a-111">Parametre</span><span class="sxs-lookup"><span data-stu-id="30e1a-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="30e1a-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30e1a-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
