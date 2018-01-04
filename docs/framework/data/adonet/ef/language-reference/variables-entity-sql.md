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
# <a name="variables-entity-sql"></a>Değişkenleri (varlık SQL)
## <a name="variable"></a>Değişken  
 Bir başvuru geçerli kapsamda tanımlı adlandırılmış bir ifade bir değişken ifadesidir. Bir değişken başvurusu geçerli bir olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Aşağıdaki örnek ifade bir değişken kullanımını göstermektedir. `c` FROM yan tümcesi değişkeni tanımıdır. Kullanımını `c` SELECT yan tümcesi değişken başvuru temsil eder.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanımlayıcılar](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [Parametreler](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
