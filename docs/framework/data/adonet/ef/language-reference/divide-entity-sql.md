---
title: '- Sayısına (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 79fdbebc648daac4f695387d52d2a915383f99ca
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833883"
---
# <a name="-divide-entity-sql"></a>/(Böl) (Entity SQL)
Bir sayıyı başka bir sayıya böler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `dividend`  
 Bölünecek sayısal ifade. `dividend`, herhangi bir sayısal veri türü için geçerli bir ifadedir.  
  
 `divisor`  
 Bölüneni bölmek için sayısal ifade. `divisor`, herhangi bir sayısal veri türü için geçerli bir ifadedir.  
  
## <a name="result-types"></a>Sonuç türleri  
 İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir sayıyı başka bir sayıya bölmek için/aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
