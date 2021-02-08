---
description: 'Hakkında daha fazla bilgi edinin: değişkenler (Entity SQL)'
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 134fee8f61c8e87a18520e6622f6a6a5cceb0076
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795046"
---
# <a name="variables-entity-sql"></a>Değişkenler (Entity SQL)

## <a name="variable"></a>Değişken  

 Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur. Bir değişken başvurusu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , [tanımlayıcılarında](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir tanımlayıcı olmalıdır.  
  
 Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir. `c`From yan tümcesinde değişkenin tanımıdır. `c`Select yan tümcesinde kullanımı, değişken başvurusunu temsil eder.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcılar](identifiers-entity-sql.md)
- [Parametreler](parameters-entity-sql.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
