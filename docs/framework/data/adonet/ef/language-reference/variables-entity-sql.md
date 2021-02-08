---
description: 'Hakkında daha fazla bilgi edinin: değişkenler (Entity SQL)'
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 134fee8f61c8e87a18520e6622f6a6a5cceb0076
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795046"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="75f87-103">Değişkenler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="75f87-103">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="75f87-104">Değişken</span><span class="sxs-lookup"><span data-stu-id="75f87-104">Variable</span></span>  

 <span data-ttu-id="75f87-105">Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="75f87-105">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="75f87-106">Bir değişken başvurusu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , [tanımlayıcılarında](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir tanımlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f87-106">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="75f87-107">Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75f87-107">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="75f87-108">`c`From yan tümcesinde değişkenin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="75f87-108">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="75f87-109">`c`Select yan tümcesinde kullanımı, değişken başvurusunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="75f87-109">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="75f87-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f87-110">See also</span></span>

- [<span data-ttu-id="75f87-111">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="75f87-111">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="75f87-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75f87-112">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="75f87-113">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="75f87-113">Entity SQL Overview</span></span>](entity-sql-overview.md)
