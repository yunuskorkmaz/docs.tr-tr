---
title: (Varlık arasında SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: cface8ab50e53f21293ad54ea6961c7e308080b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690702"
---
# <a name="between-entity-sql"></a>(Varlık arasında SQL)
Bir ifadenin belirtilen bir aralıktaki bir değer sonuçlanıp sonuçlanmayacağını belirler. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ifadesi arasında Transact-SQL deyimi ile aynı işlevlere sahiptir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tarafından tanımlanan aralıkta test etmek için herhangi bir geçerli ifade `begin_expression` ve `end_expression`. `expression` her ikisi de aynı türde olmalıdır `begin_expression` ve `end_expression`.  
  
 `begin_expression`  
 Herhangi bir geçerli ifade. `begin_expression` her ikisi de aynı türde olmalıdır `expression` ve `end_expression`. `begin_expression` olmalıdır küçüktür `end_expression`, dönüş değerine değilleme Aksi takdirde.  
  
 `end_expression`  
 Herhangi bir geçerli ifade. `end_expression` her ikisi de aynı türde olmalıdır `expression` ve `begin_expression`.  
  
 DEĞİL  
 BETWEEN sonucunu negatif olduğunu belirtir.  
  
 AND  
 Gösteren bir yer tutucu olarak görev yapar `expression` tarafından belirtilen aralığı içinde olmalıdır `begin_expression` ve `end_expression`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` varsa `expression` tarafından belirtilen aralık arasında `begin_expression` ve `end_expression`; Aksi takdirde `false`. `null` ise döndürülecek `expression` olduğu `null` veya `begin_expression` veya `end_expression` olduğu `null`.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir aralık belirtmek için BETWEEN yerine büyüktür (>) ve küçüktür (<) işleçlerini kullanın.  
  
## <a name="example"></a>Örnek  
 ARASINDA işleci bir ifade değeri belirtilen bir aralıktaki sonuçlanıp sonuçlanmayacağını belirlemek için aşağıdaki varlık SQL sorgusu kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
