---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319197"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="3833a-102">Değişkenler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3833a-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="3833a-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="3833a-103">Variable</span></span>  
 <span data-ttu-id="3833a-104">Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="3833a-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="3833a-105">Değişken başvurusu, [tanımlayıcıda](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3833a-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3833a-106">Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3833a-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="3833a-107">FROM yan tümcesindeki `c` değişkenin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="3833a-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="3833a-108">SELECT yan tümcesinde `c` kullanımı, değişken başvurusunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3833a-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="3833a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3833a-109">See also</span></span>

- [<span data-ttu-id="3833a-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="3833a-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="3833a-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3833a-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="3833a-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3833a-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
