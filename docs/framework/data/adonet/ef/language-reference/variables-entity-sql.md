---
title: "Değişkenleri (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fff24c4572fab483c701a93167c0f229d5111d61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="variables-entity-sql"></a><span data-ttu-id="7d5dd-102">Değişkenleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="7d5dd-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="7d5dd-103">Değişken</span><span class="sxs-lookup"><span data-stu-id="7d5dd-103">Variable</span></span>  
 <span data-ttu-id="7d5dd-104">Bir başvuru geçerli kapsamda tanımlı adlandırılmış bir ifade bir değişken ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="7d5dd-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="7d5dd-105">Bir değişken başvurusu geçerli bir olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7d5dd-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="7d5dd-106">Aşağıdaki örnek ifade bir değişken kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7d5dd-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="7d5dd-107">`c` FROM yan tümcesi değişkeni tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="7d5dd-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="7d5dd-108">Kullanımını `c` SELECT yan tümcesi değişken başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d5dd-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d5dd-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d5dd-109">See Also</span></span>  
 [<span data-ttu-id="7d5dd-110">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="7d5dd-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="7d5dd-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d5dd-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="7d5dd-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d5dd-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
