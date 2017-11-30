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
ms.openlocfilehash: 551b6d6feab6829c9a2f6f2e89e1918acf463411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variables-entity-sql"></a>Değişkenleri (varlık SQL)
## <a name="variable"></a>Değişken  
 Bir başvuru geçerli kapsamda tanımlı adlandırılmış bir ifade bir değişken ifadesidir. Bir değişken başvurusu geçerli bir olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Aşağıdaki örnek ifade bir değişken kullanımını göstermektedir. `c` FROM yan tümcesi değişkeni tanımıdır. Kullanımını `c` SELECT yan tümcesi değişken başvuru temsil eder.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [Parametreleri](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
