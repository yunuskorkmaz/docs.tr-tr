---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150020"
---
# <a name="parameters-entity-sql"></a>Parametreler (Entity SQL)
Parametreler, genellikle ana bilgisayar [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dili tarafından kullanılan bağlayıcı bir API aracılığıyla, dışarıdan tanımlanan değişkenlerdir. Her parametrenin bir adı ve türü vardır. Parametre adları, sorgu ifadelerinde önek olarak at (@) simgesi olan tanımlanır. Bu, bunları sorguda tanımlanan özelliklerin veya diğer adların adlarından ayrıştırıyor.  
  
 Ana bilgisayar dili bağlama API'si, bağlama parametreleri için API sağlar.  
  
## <a name="example"></a>Örnek  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
