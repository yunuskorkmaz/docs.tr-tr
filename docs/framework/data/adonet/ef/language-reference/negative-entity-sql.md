---
title: '- Negatif (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319531"
---
# <a name="--negative-entity-sql"></a>-(Negatif) (Entity SQL)
Sayısal bir ifadenin değerinin negatifini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.  
  
## <a name="result-types"></a>Sonuç türleri  
 @No__t-0 ' ın veri türü.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 işaretsiz bir tür ise, sonuç türü, `expression` türü ile en yakından ilişkili olan imzalı tür olur. Örneğin, `expression` bayt türünde ise, Int16 türünde bir değer döndürülür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir sayısal ifadenin değerinin negatifini döndürmek için-aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
