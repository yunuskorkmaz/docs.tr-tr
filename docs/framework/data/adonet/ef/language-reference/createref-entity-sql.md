---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251110"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
Bir EntitySet 'teki bir varlığa başvurular başvurusu yapar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Bir dize sabit değeri değil EntitySet tanımlayıcısı.  
  
 `row_typed_expression`  
 Varlık türünün temel özelliklerine karşılık gelen satır türü bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `row_typed_expression`varlık için anahtar türüne yapısal olarak eşdeğer olmalıdır. Yani, varlık anahtarlarıyla aynı sırada aynı sayıda ve türde alanlara sahip olması gerekir.  
  
 Aşağıdaki örnekte, Orders ve BadOrders öğelerinin her ikisi de sıralamayla ve kimliğin tek bir anahtar özelliği olarak kabul edilir. Örnek, Rozetteki bir varlığa nasıl başvuru üretebiliriz gösterir. Başvurunun tehlike altında olabileceğini unutmayın.  Diğer bir deyişle, başvuru gerçekten belirli bir varlığı tanımlamayabilir. Bu durumlarda, bu başvuru `DEREF` üzerindeki bir işlem null değeri döndürür.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir varlık kümesindeki bir varlığa başvuruları almak için CREATEREF işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
