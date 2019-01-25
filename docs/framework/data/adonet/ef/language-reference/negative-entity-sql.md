---
title: '- (Negatif) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f33b672ecd635234b8a8859651d117aabdaf14d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745863"
---
# <a name="--negative-entity-sql"></a>-(Negatif) (varlık SQL)
Negatif bir sayısal ifadenin değeri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade herhangi birinin sayısal veri türleri.  
  
## <a name="result-types"></a>Sonuç türleri  
 Veri türü `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `expression` işaretsiz bir türü olan sonuç türünü türüne en yakından ilişkili işaretli bir türe olacaktır `expression`. Örneğin, varsa `expression` Byte, Int16 döndürülecek türünde bir değer türüdür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır aritmetik işleç değerin sayısal ifadenin negatif döndürülecek. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
