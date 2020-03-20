---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149823"
---
# <a name="variables-entity-sql"></a>Değişkenler (Entity SQL)
## <a name="variable"></a>Değişken  
 Değişken ifade, geçerli kapsamda tanımlanan adlandırılmış bir ifadeye yapılan bir başvurudur. Değişken başvuru, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] [Tanımlayıcılar'da](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir tanımlayıcı olmalıdır.  
  
 Aşağıdaki örnek, ifadede bir değişkenin kullanımını gösterir. FROM `c` yan tümcesi değişkenin tanımıdır. SELECT yan `c` tümcesinin kullanımı değişken başvuruyu temsil eder.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcılar](identifiers-entity-sql.md)
- [Parametre](parameters-entity-sql.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
