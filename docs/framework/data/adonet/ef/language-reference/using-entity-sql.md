---
title: (Varlık SQL) kullanma
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 6a5b374bc253cb2deb7a9e1de942c32d8e8bbfcf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168031"
---
# <a name="using-entity-sql"></a>(Varlık SQL) kullanma
Bir sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Bir ad alanı ile nitelemek için daha kısa bir diğer ad belirtir.  
  
 `namespace`  
 Geçerli bir ad alanı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu kullanarak işleci bir sorgu ifadesinde kullanılan ad alanları belirtmek için kullanır. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad Alanları](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
