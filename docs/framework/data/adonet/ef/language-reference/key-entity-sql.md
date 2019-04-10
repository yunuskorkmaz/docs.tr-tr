---
title: ANAHTAR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 9cd3276583741f2b0261cb8a0e55f4185d20100e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319345"
---
# <a name="key-entity-sql"></a>ANAHTAR (varlık SQL)
Bir başvuru veya varlık ifade anahtarını ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varlık anahtarı anahtar değerlerinin doğru sırayla belirtilen varlık veya varlık başvurusu içerir. Birden çok varlık kümeleri aynı türüne göre çünkü aynı anahtarı her varlık kümesinde görünebilir. Benzersiz bir başvuru almak için kullanın `REF`. ANAHTAR işlecinin dönüş türü varlığın her anahtar için bir alan aynı sırada içeren bir satır türüdür.  
  
 Aşağıdaki örnekte, anahtar işleci BadOrder varlığına yönelik bir başvuru geçirilir ve bu başvuru anahtar bölümünü döndürür. Bu durumda, bir kayıt türü tam olarak bir alan için karşılık gelen ile `Id` özelliği.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu anahtar işleci bir ifade tür başvurusu ile anahtar bölümünü ayıklamak için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
