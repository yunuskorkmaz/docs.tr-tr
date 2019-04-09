---
title: SONRA (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: d5f9f2b8c9d7397cbcd91fa52a95544fc66e4dce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184604"
---
# <a name="then-entity-sql"></a>SONRA (varlık SQL)
Sonuç olarak değerlendirildiğinde WHEN yan tümcesinin `true`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Geçerli bir Boolean ifadesi.  
  
 `then_expression`  
 Bir koleksiyon döndürür herhangi bir geçerli ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `when_expression` değere Değerlenen `true`, karşılık gelen sonucudur `then-expression`. Yoksa ne zaman koşullar sağlanırsa, `else-expression` değerlendirilir. Ancak, yoksa hiçbir `else-expression`, sonuç NULL'dur.  
  
 Bir örnek için bkz. [çalışması](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu, bir dizi değerlendirmek için CASE ifadesi kullanır. `Boolean` ifadeler. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
