---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319426"
---
# <a name="parameters-entity-sql"></a>Parametreler (Entity SQL)
Parametreler, genellikle bir ana bilgisayar dili tarafından kullanılan bağlama API 'SI aracılığıyla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dışında tanımlanan değişkenlerdir. Her parametrenin bir adı ve türü vardır. Parametre adları, (@) simgesi olan sorgu ifadelerinde ön ek olarak tanımlanır. Bu, bunları, sorgu adlarından veya sorguda tanımlanan diğer adlarla ayırt ediyor.  
  
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
