---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 611e90f362bbc0eac521e1e1998fb85200169c19
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039942"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler. İfade ARASıNDAKI [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL BETWEEN ifadesiyle aynı işlevselliğe sahiptir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 `begin_expression` ve `end_expression`tarafından tanımlanan aralıkta test edilecek geçerli bir ifade. `expression`, `begin_expression` ve `end_expression`aynı türde olmalıdır.  
  
 `begin_expression`  
 Herhangi bir geçerli ifade. `begin_expression`, `expression` ve `end_expression`aynı türde olmalıdır. `begin_expression` `end_expression`küçük olmalıdır, aksi takdirde dönüş değeri de kullanılacaktır.  
  
 `end_expression`  
 Herhangi bir geçerli ifade. `end_expression`, `expression` ve `begin_expression`aynı türde olmalıdır.  
  
 BAŞLATıLMADı  
 ARASıNDAKI sonucun nelenmiş olduğunu belirtir.  
  
 AND  
 `expression`, `begin_expression` ve `end_expression`belirtilen aralık dahilinde olması gerektiğini belirten bir yer tutucu görevi görür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `expression`, `begin_expression` ve `end_expression`tarafından belirtilen Aralık arasında ise `true`; Aksi takdirde, `false`. `null`, `expression` `null` ya da `begin_expression` veya `end_expression` `null`ise döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir Aralık belirtmek için BETWEEN (>) ve küçüktür (<) işleçlerini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını anlamak için BETWEEN işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
