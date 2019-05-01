---
title: Değişkenleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bf6fa95e38d1eb5817fd67165b6993cbb0755fd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879781"
---
# <a name="variables-entity-sql"></a>Değişkenleri (varlık SQL)
## <a name="variable"></a>Değişken  
 Değişken ifade geçerli kapsamda tanımlı adlandırılmış bir ifade bir başvurudur. Bir değişken başvurusu geçerli olmalıdır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlandığı gibi tanımlayıcısı [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 Aşağıdaki örnek ifade bir değişken kullanımını gösterir. `c` İçinde FROM yan tümcesi değişkeni tanımıdır. Kullanımını `c` SELECT yan tümcesi, değişken başvurusu temsil eder.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcılar](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [Parametreler](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
