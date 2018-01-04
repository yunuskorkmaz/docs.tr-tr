---
title: "CREATEREF (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ad5329e50a5bea933e8fdfdfd473b2d4b9e0b211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="createref-entity-sql"></a>CREATEREF (varlık SQL)
Bir entityset varlık başvuruları fabricates.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Entityset tanımlayıcısı, olmayan bir değişmez dize değeri.  
  
 `row_typed_expression`  
 Varlık türünün temel özelliklerine karşılık gelen bir satır yazılan bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `row_typed_expression`varlık için anahtar türü yapısal olarak eşdeğer olmalıdır. Diğer bir deyişle, aynı sayısı ve türleri alanları varlık anahtarları aynı sırada olmalıdır.  
  
 Aşağıdaki örnekte, siparişler ve BadOrders her iki entityset'i sipariş türünde olan ve kimliği sipariş tek anahtar özelliği olarak kabul edilir. Örnek nasıl biz BadOrders içinde bir varlığa bir başvuru üretebilir gösterir. Başvuru sarkan unutmayın.  Diğer bir deyişle, başvuru gerçekte belirli bir varlık tanımlayabilir değil. Bu durumlarda, bir `DEREF` bu başvuruyu işlemi null döndürür.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu CREATEREF işlecindeki bir varlık kümesinin varlık başvuruları imal için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
