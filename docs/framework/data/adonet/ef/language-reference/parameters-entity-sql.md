---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319426"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="d7274-102">Parametreler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7274-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="d7274-103">Parametreler, genellikle bir ana bilgisayar dili tarafından kullanılan bağlama API 'SI aracılığıyla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dışında tanımlanan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="d7274-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="d7274-104">Her parametrenin bir adı ve türü vardır.</span><span class="sxs-lookup"><span data-stu-id="d7274-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="d7274-105">Parametre adları, (@) simgesi olan sorgu ifadelerinde ön ek olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d7274-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="d7274-106">Bu, bunları, sorgu adlarından veya sorguda tanımlanan diğer adlarla ayırt ediyor.</span><span class="sxs-lookup"><span data-stu-id="d7274-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="d7274-107">Konak dili bağlama API 'SI bağlama parametreleri için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7274-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7274-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7274-108">Example</span></span>  
  
```sql  
SELECT c   
      FROM LOB.Customers AS c   
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7274-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7274-109">See also</span></span>

- [<span data-ttu-id="d7274-110">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d7274-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="d7274-111">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d7274-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
