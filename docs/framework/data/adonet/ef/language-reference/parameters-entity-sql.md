---
title: Parametreler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 5fa050e43e4590f61c3011a1b9bb0937da7032a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632393"
---
# <a name="parameters-entity-sql"></a>Parametreler (varlık SQL)
Parametrelerdir dışında tanımlanan değişkenler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], genellikle bir konak dil tarafından kullanılan bir bağlama API aracılığıyla. Her bir parametreye bir ad ve bir türü vardır. Parametre adları ile sorgu ifadelerinde tanımlanır, (@) öneki olarak sembol. Bu bunları özelliklerin adları veya sorguda tanımlanan diğer adlar belirgin hale getirir.  
  
 Konak dili bağlama API parametre bağlama için API'ler sağlar.  
  
## <a name="example"></a>Örnek  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
