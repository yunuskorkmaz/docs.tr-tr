---
title: Burada (varlık SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 43c038e9ff0acfdeff88492aa2ca34fbf4ada94a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="where-entity-sql"></a>Burada (varlık SQL)
WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir Boolean türü.  
  
## <a name="remarks"></a>Açıklamalar  
 WHERE yan tümcesi için açıklandığı gibi aynı semantiğine sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Bu koşul geçirmek için kaynak koleksiyonlarını öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.  
  
```  
select c from cs as c where e  
```  
  
 İfade `e` Boolean türünde olmalıdır.  
  
 WHERE yan tümcesi FROM yan tümcesi hemen sonra ve hiçbir gruplandırma, sıralama veya yansıtma önce uygulandığı yerini alır. FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesi ifade için görünür durumdadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
