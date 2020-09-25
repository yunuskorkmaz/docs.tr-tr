---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 17e3fe97942b34232640b0326eca2c5729e86989
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201180"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)

Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Between ifadesi, Transact-SQL between ifadesiyle aynı işlevselliğe sahiptir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Ve tarafından tanımlanan aralıkta test edilecek geçerli bir ifade `begin_expression` `end_expression` . `expression` hem hem de ile aynı türde olmalıdır `begin_expression` `end_expression` .  
  
 `begin_expression`  
 Herhangi bir geçerli ifade. `begin_expression` hem hem de ile aynı türde olmalıdır `expression` `end_expression` . `begin_expression` Şundan küçük olmalıdır `end_expression` , aksi takdirde dönüş değeri de kullanılır.  
  
 `end_expression`  
 Herhangi bir geçerli ifade. `end_expression` hem hem de ile aynı türde olmalıdır `expression` `begin_expression` .  
  
 NOT  
 ARASıNDAKI sonucun nelenmiş olduğunu belirtir.  
  
 AND  
 , `expression` Ve tarafından belirtilen aralık dahilinde olması gerektiğini belirten bir yer tutucu görevi `begin_expression` görür `end_expression` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` , `expression` ve ile belirtilen Aralık arasındaysa `begin_expression` `end_expression` ; Aksi takdirde, `false` . `null` , veya ise, `expression` döndürülür `null` `begin_expression` `end_expression` `null` .  
  
## <a name="remarks"></a>Açıklamalar  

 Özel bir Aralık belirtmek için BETWEEN (>) ve küçüktür (<) işleçlerini kullanın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını anlamak için BETWEEN işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
