---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248685"
---
# <a name="variables-entity-sql"></a>Değişkenler (Entity SQL)
## <a name="variable"></a>Değişken  
 Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur. Bir değişken başvurusu, [tanımlayıcılarında](identifiers-entity-sql.md)tanımlandığı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gibi geçerli bir tanımlayıcı olmalıdır.  
  
 Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir. `c` From yan tümcesinde değişkenin tanımıdır. Select yan tümcesinde `c` kullanımı, değişken başvurusunu temsil eder.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcılar](identifiers-entity-sql.md)
- [Parametreler](parameters-entity-sql.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
