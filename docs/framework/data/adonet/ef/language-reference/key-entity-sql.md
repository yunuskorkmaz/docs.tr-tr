---
title: "ANAHTAR (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ccc13599889eb91755c775600f2386d1812880b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="key-entity-sql"></a>ANAHTAR (varlık SQL)
Bir başvuru veya varlık ifade anahtarını ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir varlık anahtarı doğru sırada belirtilen varlık veya varlık başvurusu anahtar değerlerini içerir. Birden çok varlık kümesine aynı türüne dayalı olabilir çünkü, aynı anahtar her varlık kümesinde görünebilir. Benzersiz bir başvuru almak için `REF`. ANAHTAR işleci dönüş türü varlığın her anahtar için bir alan aynı sırada içeren bir satır türüdür.  
  
 Aşağıdaki örnekte, anahtar işleci BadOrder varlığa bir başvuru geçirilir ve bu başvuruyu anahtar bölümünü döndürür. Bu durumda, bir kayıt türü tam olarak bir alan karşılık gelen ile `Id` özelliği.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu anahtar işlecini kullanan bir ifade türü başvuru içeren anahtar bölümünü ayıklamak için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
