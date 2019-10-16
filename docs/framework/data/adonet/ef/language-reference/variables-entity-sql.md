---
title: Değişkenler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319197"
---
# <a name="variables-entity-sql"></a>Değişkenler (Entity SQL)
## <a name="variable"></a>Değişken  
 Değişken ifadesi, geçerli kapsamda tanımlanan bir adlandırılmış ifadeye başvurudur. Değişken başvurusu, [tanımlayıcıda](identifiers-entity-sql.md)tanımlandığı gibi geçerli bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcısı olmalıdır.  
  
 Aşağıdaki örnek, ifadesindeki bir değişkenin kullanımını gösterir. FROM yan tümcesindeki `c` değişkenin tanımıdır. SELECT yan tümcesinde `c` kullanımı, değişken başvurusunu temsil eder.  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcılar](identifiers-entity-sql.md)
- [Parametreler](parameters-entity-sql.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
