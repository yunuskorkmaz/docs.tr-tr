---
description: 'Daha fazla bilgi edinin: CREATEREF (Entity SQL)'
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c4e96f97bd3587e50b34f6cbd63c5ae9ed8d94ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724784"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)

Bir EntitySet 'teki bir varlığa başvurular başvurusu yapar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `entityset_identifier`  
 Bir dize sabit değeri değil EntitySet tanımlayıcısı.  
  
 `row_typed_expression`  
 Varlık türünün temel özelliklerine karşılık gelen satır türü bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 `row_typed_expression` varlık için anahtar türüne yapısal olarak eşdeğer olmalıdır. Yani, varlık anahtarlarıyla aynı sırada aynı sayıda ve türde alanlara sahip olması gerekir.  
  
 Aşağıdaki örnekte, Orders ve BadOrders öğelerinin her ikisi de sıralamayla ve kimliğin tek bir anahtar özelliği olarak kabul edilir. Örnek, Rozetteki bir varlığa nasıl başvuru üretebiliriz gösterir. Başvurunun tehlike altında olabileceğini unutmayın.  Diğer bir deyişle, başvuru gerçekten belirli bir varlığı tanımlamayabilir. Bu durumlarda, `DEREF` Bu başvuru üzerindeki bir işlem null değeri döndürür.  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir varlık kümesindeki bir varlığa başvuruları almak için CREATEREF işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [ANAHTAR](key-entity-sql.md)
- [REF](ref-entity-sql.md)
