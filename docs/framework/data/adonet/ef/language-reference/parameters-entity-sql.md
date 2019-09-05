---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249585"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="34a6a-102">Parametreler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="34a6a-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="34a6a-103">Parametreler, genellikle bir ana bilgisayar dili [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tarafından kullanılan bir bağlama API 'si aracılığıyla dışında tanımlanan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="34a6a-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="34a6a-104">Her parametrenin bir adı ve türü vardır.</span><span class="sxs-lookup"><span data-stu-id="34a6a-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="34a6a-105">Parametre adları, (@) simgesi olan sorgu ifadelerinde ön ek olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="34a6a-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="34a6a-106">Bu, bunları, sorgu adlarından veya sorguda tanımlanan diğer adlarla ayırt ediyor.</span><span class="sxs-lookup"><span data-stu-id="34a6a-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="34a6a-107">Konak dili bağlama API 'SI bağlama parametreleri için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="34a6a-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34a6a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="34a6a-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="34a6a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34a6a-109">See also</span></span>

- [<span data-ttu-id="34a6a-110">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="34a6a-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="34a6a-111">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34a6a-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
