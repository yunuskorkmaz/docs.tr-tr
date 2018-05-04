---
title: (Varlık SQL) kullanma
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 89306c8b4c317ebaba0d964869c4fe9e1028631a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="using-entity-sql"></a>(Varlık SQL) kullanma
Ad alanları sorgu ifadesinde kullanılan belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Bir ad alanıyla nitelemek için daha kısa bir diğer ad belirtir.  
  
 `namespace`  
 Tüm geçerli ad alanı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu kullanarak işleci sorgu ifadesinde kullanılan ad alanları belirtmek için kullanır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ad Alanları](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
