---
title: SONRA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319291"
---
# <a name="then-entity-sql"></a>SONRA (Entity SQL)
@No__t-0 olarak değerlendirildiğinde bir where yan tümcesinin sonucu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Herhangi bir geçerli Boole ifadesi.  
  
 `then_expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 `true` değerini verirse, sonuç karşılık gelen `then-expression` ' dir. NE zaman koşullarından hiçbiri karşılanmıyorsa `else-expression` değerlendirilir. Ancak, `else-expression` yoksa sonuç null olur.  
  
 Bir örnek için bkz. [Case](case-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadesi kümesini değerlendirmek için CASE ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CASE](case-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
