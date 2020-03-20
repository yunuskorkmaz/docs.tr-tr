---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150020"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="fa7e8-102">Parametreler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fa7e8-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="fa7e8-103">Parametreler, genellikle ana bilgisayar [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dili tarafından kullanılan bağlayıcı bir API aracılığıyla, dışarıdan tanımlanan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="fa7e8-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="fa7e8-104">Her parametrenin bir adı ve türü vardır.</span><span class="sxs-lookup"><span data-stu-id="fa7e8-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="fa7e8-105">Parametre adları, sorgu ifadelerinde önek olarak at (@) simgesi olan tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fa7e8-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="fa7e8-106">Bu, bunları sorguda tanımlanan özelliklerin veya diğer adların adlarından ayrıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="fa7e8-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="fa7e8-107">Ana bilgisayar dili bağlama API'si, bağlama parametreleri için API sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa7e8-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa7e8-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa7e8-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa7e8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa7e8-109">See also</span></span>

- [<span data-ttu-id="fa7e8-110">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fa7e8-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fa7e8-111">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa7e8-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
