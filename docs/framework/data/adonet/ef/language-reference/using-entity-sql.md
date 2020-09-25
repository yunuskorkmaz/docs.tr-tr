---
title: KULLANMA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203598"
---
# <a name="using-entity-sql"></a>KULLANMA (Entity SQL)

Sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `alias`  
 Bir ad alanını nitelemek için daha kısa bir diğer ad belirtir.  
  
 `namespace`  
 Geçerli herhangi bir ad alanı.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir sorgu ifadesinde kullanılan ad alanlarını belirtmek için USING işlecini kullanır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanları](namespaces-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
