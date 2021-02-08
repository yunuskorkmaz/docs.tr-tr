---
description: 'Hakkında daha fazla bilgi edinin: USING (Entity SQL)'
title: KULLANMA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 084ab56f25041377dd6a0a35dd743122f482eeba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795059"
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
