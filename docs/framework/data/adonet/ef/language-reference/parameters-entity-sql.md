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
ms.workload: dotnet
ms.openlocfilehash: 4cbc13433b742cea1063cbd284690ce8cabbbfc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="parameters-entity-sql"></a>Parametreler (varlık SQL)
Parametreleridir dışında tanımlanan değişkenler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], genellikle bir ana bilgisayar dil tarafından kullanılan bir bağlama API'si aracılığıyla. Her bir parametreyi bir ad ve bir türe sahip. Parametre adları sorgu ifadeleri ile tanımlanmış adresindeki (@) öneki olarak simge. Bu onları özellik adlarını veya sorguda tanımlanan diğer adları açıklar.  
  
 Ana bilgisayar dil bağlama API parametre bağlama için API'ler sağlar.  
  
## <a name="example"></a>Örnek  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
