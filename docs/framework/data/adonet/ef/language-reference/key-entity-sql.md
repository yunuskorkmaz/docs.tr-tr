---
title: ANAHTAR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: c35cac018392aa9688866e280ff64fdf6a1453f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
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
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
