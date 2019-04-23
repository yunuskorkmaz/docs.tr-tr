---
title: Parametreler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187684"
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
