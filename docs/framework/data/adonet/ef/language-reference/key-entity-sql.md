---
title: ANAHTAR (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150175"
---
# <a name="key-entity-sql"></a>ANAHTAR (Varlık SQL)
Başvurunun veya varlık ifadesinin anahtarını ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varlık anahtarı, belirtilen varlık veya varlık başvurusu doğru sırada anahtar değerlerini içerir. Birden çok varlık kümesi aynı türü temel alabilecek olduğundan, her varlık kümesinde aynı anahtar görünebilir. Benzersiz bir başvuru almak `REF`için. KEY işlecinin dönüş türü, varlığın her anahtarı için aynı sırada bir alan içeren bir satır türüdür.  
  
 Aşağıdaki örnekte, anahtar işleci BadOrder varlığına bir başvuru geçirilir ve bu başvurunun anahtar kısmını döndürür. Bu durumda, `Id` özelliğe karşılık gelen tam bir alana sahip bir kayıt türü.  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, tür başvurusu olan bir ifadenin anahtar bölümünü ayıklamak için KEY işleci kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
