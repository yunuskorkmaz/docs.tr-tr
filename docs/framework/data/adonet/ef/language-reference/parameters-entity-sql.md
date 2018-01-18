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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bb631a752bfe0e741b654ec6774a14c82c89157c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="11cc8-102">Parametreler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="11cc8-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="11cc8-103">Parametreleridir dışında tanımlanan değişkenler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], genellikle bir ana bilgisayar dil tarafından kullanılan bir bağlama API'si aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="11cc8-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="11cc8-104">Her bir parametreyi bir ad ve bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="11cc8-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="11cc8-105">Parametre adları sorgu ifadeleri ile tanımlanmış adresindeki (@) öneki olarak simge.</span><span class="sxs-lookup"><span data-stu-id="11cc8-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="11cc8-106">Bu onları özellik adlarını veya sorguda tanımlanan diğer adları açıklar.</span><span class="sxs-lookup"><span data-stu-id="11cc8-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="11cc8-107">Ana bilgisayar dil bağlama API parametre bağlama için API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="11cc8-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11cc8-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="11cc8-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="11cc8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11cc8-109">See Also</span></span>  
 [<span data-ttu-id="11cc8-110">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="11cc8-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="11cc8-111">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11cc8-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
