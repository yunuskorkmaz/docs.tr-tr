---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181004"
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
