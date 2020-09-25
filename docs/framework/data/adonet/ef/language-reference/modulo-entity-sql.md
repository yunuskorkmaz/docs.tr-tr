---
title: Modül (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175713"
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
