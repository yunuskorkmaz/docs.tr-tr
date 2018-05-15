---
title: Parametreler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: c8bdb54e52b4c0d189f3bff72bdb24785c1a9c27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="3c794-102">Parametreler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="3c794-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="3c794-103">Parametreleridir dışında tanımlanan değişkenler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], genellikle bir ana bilgisayar dil tarafından kullanılan bir bağlama API'si aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="3c794-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="3c794-104">Her bir parametreyi bir ad ve bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="3c794-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="3c794-105">Parametre adları sorgu ifadeleri ile tanımlanmış adresindeki (@) öneki olarak simge.</span><span class="sxs-lookup"><span data-stu-id="3c794-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="3c794-106">Bu onları özellik adlarını veya sorguda tanımlanan diğer adları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c794-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="3c794-107">Ana bilgisayar dil bağlama API parametre bağlama için API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c794-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c794-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c794-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c794-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c794-109">See Also</span></span>  
 [<span data-ttu-id="3c794-110">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3c794-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="3c794-111">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c794-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
