---
title: Parametreler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249585"
---
# <a name="parameters-entity-sql"></a>Parametreler (Entity SQL)
Parametreler, genellikle bir ana bilgisayar dili [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tarafından kullanılan bir bağlama API 'si aracılığıyla dışında tanımlanan değişkenlerdir. Her parametrenin bir adı ve türü vardır. Parametre adları, (@) simgesi olan sorgu ifadelerinde ön ek olarak tanımlanır. Bu, bunları, sorgu adlarından veya sorguda tanımlanan diğer adlarla ayırt ediyor.  
  
 Konak dili bağlama API 'SI bağlama parametreleri için API 'Ler sağlar.  
  
## <a name="example"></a>Örnek  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
