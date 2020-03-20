---
title: BETWEEN (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150499"
---
# <a name="between-entity-sql"></a>BETWEEN (Varlık SQL)
İfadenin belirli bir aralıktaki bir değerle sonuçlanıp sonuçlaşmadığını belirler. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ifadesi, Transact-SQL BETWEEN ifadesi ile aynı işlevsellik tesahiptir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Tarafından tanımlanan aralıkta test etmek `begin_expression` için `end_expression`geçerli bir ifade ve . `expression`her ikisi `begin_expression` yle aynı `end_expression`türde olmalıdır ve .  
  
 `begin_expression`  
 Herhangi bir geçerli ifade. `begin_expression`her ikisi `expression` yle aynı `end_expression`türde olmalıdır ve . `begin_expression`daha `end_expression`az olmalıdır, aksi takdirde iade değeri inkar edilecektir.  
  
 `end_expression`  
 Herhangi bir geçerli ifade. `end_expression`her ikisi `expression` yle aynı `begin_expression`türde olmalıdır ve .  
  
 NOT  
 BETWEEN sonucunun inkâr edilmesi gerektiğini belirtir.  
  
 AND  
 Tarafından belirtilen aralıkta `expression` olması gerektiğini belirten bir `begin_expression` `end_expression`yer tutucu görevi görür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`tarafından `expression` `begin_expression` belirtilen aralık arasında `end_expression`ise ve ; aksi `false`takdirde, . `null`ise `expression` `null` veya ise `begin_expression` iade `end_expression` edilecektir. `null`  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir aralık belirtmek için, (>) ve (<) işleçlerden daha büyük olan işleçleri ARA ILE'den daha az kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir ifadenin belirli bir aralıktaki bir değerle sonuçlanıp sonuçlanmadığını belirlemek için ARA Işleci'ni kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
