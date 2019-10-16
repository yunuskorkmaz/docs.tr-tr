---
title: KULLANMA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319212"
---
# <a name="using-entity-sql"></a>KULLANMA (Entity SQL)
Sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Bir ad alanını nitelemek için daha kısa bir diğer ad belirtir.  
  
 `namespace`  
 Geçerli herhangi bir ad alanı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir sorgu ifadesinde kullanılan ad alanlarını belirtmek için USING işlecini kullanır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanları](namespaces-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
