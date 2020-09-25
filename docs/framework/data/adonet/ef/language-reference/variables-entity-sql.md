---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181004"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="38aab-102">Değişkenler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="38aab-102">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="38aab-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="38aab-103">Variable</span></span>  

 <span data-ttu-id="38aab-104">Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="38aab-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="38aab-105">Bir değişken başvurusu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , [tanımlayıcılarında](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir tanımlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38aab-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="38aab-106">Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38aab-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="38aab-107">`c`From yan tümcesinde değişkenin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="38aab-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="38aab-108">`c`Select yan tümcesinde kullanımı, değişken başvurusunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="38aab-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="38aab-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38aab-109">See also</span></span>

- [<span data-ttu-id="38aab-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="38aab-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="38aab-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38aab-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="38aab-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38aab-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
