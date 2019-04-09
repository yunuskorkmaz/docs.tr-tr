---
title: CREATEREF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 7003805429df36fec82e5d57811ed38af6323379
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095613"
---
# <a name="createref-entity-sql"></a>CREATEREF (varlık SQL)
Bir entityset varlık başvuruları fabricates.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Entityset tanımlayıcısı olmayan bir dize sabit değeri olabilir.  
  
 `row_typed_expression`  
 Varlık türünün temel özelliklerine karşılık gelen bir satır yazılmış bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `row_typed_expression` varlık için anahtar türü yapısal olarak eşdeğer olması gerekir. Diğer bir deyişle, aynı sayısını ve türlerini alanların varlık anahtarları aynı sırada olmalıdır.  
  
 Aşağıdaki örnekte, siparişler ve BadOrders sipariş türünde iki entityset'i olan ve kimliği siparişinin tek anahtar özellik olarak kabul edilir. Örnek bir varlıkta BadOrders başvuru hazırladığımız nasıl gösterir. Başvuru sarkan unutmayın.  Diğer bir deyişle, başvuru, belirli bir varlığa gerçekten tanımlayamayabilir. Bu durumlarda, bir `DEREF` bu başvuru üzerinde işlem, bir null döndürür.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu CREATEREF işlecindeki bir varlık kümesinin varlık başvuruları imal için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
