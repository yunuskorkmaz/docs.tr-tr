---
title: "Parametreler (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2a3700b5f9bdc996b147609d86bcaed0ec0bb116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="e77ba-102">Parametreler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e77ba-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="e77ba-103">Parametreleridir dışında tanımlanan değişkenler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], genellikle bir ana bilgisayar dil tarafından kullanılan bir bağlama API'si aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="e77ba-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="e77ba-104">Her bir parametreyi bir ad ve bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="e77ba-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="e77ba-105">Parametre adları sorgu ifadeleri ile tanımlanmış adresindeki (@) öneki olarak simge.</span><span class="sxs-lookup"><span data-stu-id="e77ba-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="e77ba-106">Bu onları özellik adlarını veya sorguda tanımlanan diğer adları açıklar.</span><span class="sxs-lookup"><span data-stu-id="e77ba-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="e77ba-107">Ana bilgisayar dil bağlama API parametre bağlama için API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e77ba-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77ba-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e77ba-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="e77ba-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e77ba-109">See Also</span></span>  
 [<span data-ttu-id="e77ba-110">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e77ba-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e77ba-111">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="e77ba-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
