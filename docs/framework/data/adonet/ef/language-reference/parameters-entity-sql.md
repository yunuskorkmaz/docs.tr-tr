---
title: Parametreler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187684"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="acdab-102">Parametreler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="acdab-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="acdab-103">Parametrelerdir dışında tanımlanan değişkenler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], genellikle bir konak dil tarafından kullanılan bir bağlama API aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="acdab-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="acdab-104">Her bir parametreye bir ad ve bir türü vardır.</span><span class="sxs-lookup"><span data-stu-id="acdab-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="acdab-105">Parametre adları ile sorgu ifadelerinde tanımlanır, (@) öneki olarak sembol.</span><span class="sxs-lookup"><span data-stu-id="acdab-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="acdab-106">Bu bunları özelliklerin adları veya sorguda tanımlanan diğer adlar belirgin hale getirir.</span><span class="sxs-lookup"><span data-stu-id="acdab-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="acdab-107">Konak dili bağlama API parametre bağlama için API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="acdab-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acdab-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="acdab-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="acdab-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acdab-109">See also</span></span>

- [<span data-ttu-id="acdab-110">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="acdab-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="acdab-111">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="acdab-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
