---
description: 'Hakkında daha fazla bilgi edinin: parametreler (Entity SQL)'
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 77b1e6ee95b5d367fec8d99345bbb416c2b9787d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724537"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="541db-103">Parametreler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="541db-103">Parameters (Entity SQL)</span></span>

<span data-ttu-id="541db-104">Parametreler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , genellikle bir ana bilgisayar dili tarafından kullanılan bir bağlama API 'si aracılığıyla dışında tanımlanan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="541db-104">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="541db-105">Her parametrenin bir adı ve türü vardır.</span><span class="sxs-lookup"><span data-stu-id="541db-105">Each parameter has a name and a type.</span></span> <span data-ttu-id="541db-106">Parametre adları, (@) simgesi olan sorgu ifadelerinde ön ek olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="541db-106">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="541db-107">Bu, bunları, sorgu adlarından veya sorguda tanımlanan diğer adlarla ayırt ediyor.</span><span class="sxs-lookup"><span data-stu-id="541db-107">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="541db-108">Konak dili bağlama API 'SI bağlama parametreleri için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="541db-108">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="541db-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="541db-109">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="541db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="541db-110">See also</span></span>

- [<span data-ttu-id="541db-111">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="541db-111">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="541db-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="541db-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
