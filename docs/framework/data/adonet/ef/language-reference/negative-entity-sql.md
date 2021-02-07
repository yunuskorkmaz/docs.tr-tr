---
description: Hakkında daha fazla bilgi edinin:-(negatif) (Entity SQL)
title: '- Negatif (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f3d30ce36b95e44755d148dc06279f67f15b0664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712889"
---
# <a name="--negative-entity-sql"></a>-(Negatif) (Entity SQL)

Sayısal bir ifadenin değerinin negatifini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.  
  
## <a name="result-types"></a>Sonuç türleri  

 Veri türü `expression` .  
  
## <a name="remarks"></a>Açıklamalar  

 `expression`İmzasız bir tür ise, sonuç türü, türü ile en yakından ilişkili olan imzalı tür olur `expression` . Örneğin, `expression` byte türünde ise, Int16 türünde bir değer döndürülür.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir sayısal ifadenin değerinin negatifini döndürmek için-aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
