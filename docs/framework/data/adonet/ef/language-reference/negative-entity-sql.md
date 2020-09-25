---
title: '- Negatif (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 71749dab073fade854c2a494841e3f6b408ebd1d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204417"
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
