---
title: Burada (varlık SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 02eeaeb8cfa335e5545b26d3d52b91c4e1614629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879443"
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
 WHERE yan tümcesi için açıklandığı gibi aynı semantiğe sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Bu koşul başarılı olanlar kaynak koleksiyonları öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.  
  
```  
select c from cs as c where e  
```  
  
 İfade `e` Boolean türüne sahip olmalıdır.  
  
 WHERE yan tümcesi doğrudan FROM yan tümcesinden sonra ve önce tüm gruplandırma, sıralama veya yansıtma uygulanan yerini alır. FROM yan tümcesinde tanımlı tüm öğe adları, WHERE yan tümcesinin ifadesi için görülebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
