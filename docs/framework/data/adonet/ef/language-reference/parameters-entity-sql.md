---
description: 'Hakkında daha fazla bilgi edinin: parametreler (Entity SQL)'
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 77b1e6ee95b5d367fec8d99345bbb416c2b9787d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724537"
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
