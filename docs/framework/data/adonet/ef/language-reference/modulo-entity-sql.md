---
description: 'Daha fazla bilgi edinin: (modül) (Entity SQL)'
title: Modül (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 8ac9bf2fa9dbee843215dcfeed13fefc7bd54796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696639"
---
# <a name="modulo-entity-sql"></a>Modül (Entity SQL)

Bir ifadenin kalan kısmını başka bir ifade döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `dividend`  
 Bölünecek sayısal ifade. `dividend` , herhangi bir sayısal veri türü için geçerli bir ifadedir.  
  
 `divisor`  
 Bölüneni bölmek için sayısal ifade. `divisor` , herhangi bir sayısal veri türü için geçerli bir ifadedir.  
  
## <a name="result-types"></a>Sonuç türleri  

 Edm.Int32  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir ifadenin kalan kısmını başka bir ifade döndürmek için% aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
