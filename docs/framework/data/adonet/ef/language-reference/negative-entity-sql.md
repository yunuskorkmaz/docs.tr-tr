---
title: '- (Negatif) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 5d1726be6a4a59891646d05b344f59962d548c75
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="--negative-entity-sql"></a>-(Olumsuz) (varlık SQL)
Sayısal bir ifadenin değerini negatif döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Sayısal veri türleri herhangi birinin geçerli bir ifade.  
  
## <a name="result-types"></a>Sonuç türleri  
 Veri türü `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `expression` imzasız bir tür sonuç türü türüne en yakından ilişkili imzalı türü olacaktır `expression`. Örneğin, varsa `expression` bayt, Int16 döndürülecek türünde bir değer türüdür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır sayısal bir ifadenin değerini negatif döndürülecek aritmetik işleç. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
