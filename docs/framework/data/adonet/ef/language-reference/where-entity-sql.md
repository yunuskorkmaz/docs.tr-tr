---
title: Burada (varlık SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489853"
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
 WHERE yan tümcesi, Transact-SQL için açıklandığı gibi aynı semantiğe sahip. Bu koşul başarılı olanlar kaynak koleksiyonları öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.  
  
```  
select c from cs as c where e  
```  
  
 İfade `e` Boolean türüne sahip olmalıdır.  
  
 WHERE yan tümcesi doğrudan FROM yan tümcesinden sonra ve önce tüm gruplandırma, sıralama veya yansıtma uygulanan yerini alır. FROM yan tümcesinde tanımlı tüm öğe adları, WHERE yan tümcesinin ifadesi için görülebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
