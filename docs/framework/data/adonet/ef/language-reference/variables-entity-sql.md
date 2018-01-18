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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d035f8d5616f2eb4c5a4db31857da2be0cd3d930
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
