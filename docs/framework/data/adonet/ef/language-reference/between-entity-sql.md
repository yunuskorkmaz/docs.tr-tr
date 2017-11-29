---
title: "(Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ab5c08dad5f11d968eec4efa51ff225d3cfd0fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="between-entity-sql"></a>(Varlık SQL)
Belirtilen aralıktaki bir değere bir ifade sonucu olup olmadığını belirler. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Arasındaki deyim arasında Transact-SQL ifadesi aynı işlevleri vardır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tarafından tanımlanan aralıktaki sınamak için herhangi bir geçerli ifadeler `begin_expression` ve `end_expression`. `expression`her ikisi de aynı türde olmalıdır `begin_expression` ve `end_expression`.  
  
 `begin_expression`  
 Herhangi bir geçerli ifade. `begin_expression`her ikisi de aynı türde olmalıdır `expression` ve `end_expression`. `begin_expression`olmalıdır değerinden `end_expression`, dönüş değeri tasarruflarını Aksi takdirde.  
  
 `end_expression`  
 Herhangi bir geçerli ifade. `end_expression`her ikisi de aynı türde olmalıdır `expression` ve `begin_expression`.  
  
 DEĞİL  
 BETWEEN sonucunu tasarruflarını gerektiğini belirtir.  
  
 AND  
 Gösteren yer tutucu olarak davranan `expression` tarafından belirtilen aralıkta olmalıdır `begin_expression` ve `end_expression`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`varsa `expression` tarafından belirtilen aralık arasında `begin_expression` ve `end_expression`; Aksi halde, `false`. `null`olursa döndürülür `expression` olan `null` veya `begin_expression` veya `end_expression` olan `null`.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir aralık belirtmek için yerine BETWEEN büyüktür (>) ve küçük (<) işleçleri kullanın.  
  
## <a name="example"></a>Örnek  
 ARASINDA bir değer belirli bir aralık içinde bir ifade sonuçlanıp sonuçlanmayacağını belirlemek için işleci aşağıdaki varlık SQL sorgusu kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
