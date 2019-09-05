---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248685"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="228f8-102">Değişkenler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="228f8-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="228f8-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="228f8-103">Variable</span></span>  
 <span data-ttu-id="228f8-104">Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="228f8-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="228f8-105">Bir değişken başvurusu, [tanımlayıcılarında](identifiers-entity-sql.md)tanımlandığı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gibi geçerli bir tanımlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="228f8-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="228f8-106">Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="228f8-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="228f8-107">`c` From yan tümcesinde değişkenin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="228f8-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="228f8-108">Select yan tümcesinde `c` kullanımı, değişken başvurusunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="228f8-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="228f8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="228f8-109">See also</span></span>

- [<span data-ttu-id="228f8-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="228f8-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="228f8-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="228f8-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="228f8-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="228f8-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
