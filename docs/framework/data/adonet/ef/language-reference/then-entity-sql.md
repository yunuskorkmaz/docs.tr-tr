---
description: 'Daha fazla bilgi edinin: (Entity SQL)'
title: SONRA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: e1f0657cfef3786832f489434fd8fc0342e8687b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673472"
---
# <a name="then-entity-sql"></a>SONRA (Entity SQL)

Olarak değerlendirildiğinde bir where yan tümcesinin sonucu `true` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `when_expression`  
 Herhangi bir geçerli Boole ifadesi.  
  
 `then_expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  

 `when_expression`Değer değerlendirilirse `true` , sonuç karşılık gelir `then-expression` . NE zaman koşullarından hiçbiri karşılanmıyorsa, olarak `else-expression` değerlendirilir. Ancak, hayır ise `else-expression` sonuç null olur.  
  
 Bir örnek için bkz. [Case](case-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir ifade kümesini değerlendirmek için CASE ifadesini kullanır `Boolean` . Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HARFLERINI](case-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
