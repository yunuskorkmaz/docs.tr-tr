---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251293"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between ifadesi, Transact-SQL between ifadesiyle aynı işlevselliğe sahiptir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 `begin_expression` Ve`end_expression`tarafından tanımlanan aralıkta test edilecek geçerli bir ifade. `expression`hem `begin_expression` hem de ile `end_expression`aynı türde olmalıdır.  
  
 `begin_expression`  
 Herhangi bir geçerli ifade. `begin_expression`hem `expression` hem de ile `end_expression`aynı türde olmalıdır. `begin_expression`Şundan `end_expression`küçük olmalıdır, aksi takdirde dönüş değeri de kullanılır.  
  
 `end_expression`  
 Herhangi bir geçerli ifade. `end_expression`hem `expression` hem de ile `begin_expression`aynı türde olmalıdır.  
  
 DEĞİL  
 ARASıNDAKI sonucun nelenmiş olduğunu belirtir.  
  
 AND  
 , Ve `expression` tarafından`end_expression`belirtilen aralık dahilinde olması gerektiğini belirten bir yer tutucu görevi görür. `begin_expression`  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`, ve `begin_expression`ilebelirtilen Aralık arasındaysa; Aksi takdirde, `false`. `expression` `end_expression` `null``expression` , veya`null` ise,`null`döndürülür. `begin_expression` `end_expression`  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir Aralık belirtmek için BETWEEN (>) ve küçüktür (<) işleçlerini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını anlamak için BETWEEN işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
