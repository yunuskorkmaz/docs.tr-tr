---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 759452902461e1a460b69774bb33f92bbd532ed0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177527"
---
# <a name="parameters-entity-sql"></a>Parametreler (Entity SQL)

Parametreler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , genellikle bir ana bilgisayar dili tarafından kullanılan bir bağlama API 'si aracılığıyla dışında tanımlanan değişkenlerdir. Her parametrenin bir adı ve türü vardır. Parametre adları, (@) simgesi olan sorgu ifadelerinde ön ek olarak tanımlanır. Bu, bunları, sorgu adlarından veya sorguda tanımlanan diğer adlarla ayırt ediyor.  
  
 Konak dili bağlama API 'SI bağlama parametreleri için API 'Ler sağlar.  
  
## <a name="example"></a>Örnek  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
