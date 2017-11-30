---
title: "SONRA (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99fd941c963ff87203d7b315beb606d40001224d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="then-entity-sql"></a>SONRA (varlık SQL)
Sonuç olarak değerlendirildiğinde WHEN yan tümcesinin `true`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `when_expression`  
 Geçerli bir Boole ifadesi.  
  
 `then_expression`  
 Bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `when_expression` değeri değerlendiren `true`, karşılık gelen sonucudur `then-expression`. Yoksa ne zaman, koşul karşılanır, `else-expression` değerlendirilir. Ancak, yoksa hiçbir `else-expression`, sonuç NULL'dur.  
  
 Bir örnek için bkz: [durumda](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Bir dizi değerlendirmek için büyük/küçük HARFE ifade aşağıdaki varlık SQL sorgusunu kullanır `Boolean` ifadeler. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DURUMU](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
