---
title: SET (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: b6adce314e5d4fb1e4077b0efef758d07444e496
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744446"
---
# <a name="set-entity-sql"></a>SET (varlık SQL)
Küme ifadesinin, kaldırılan tüm yinelenen öğeleri ile yeni bir koleksiyon sonuçlanmıyor tarafından bir küme içine nesneler koleksiyonunu dönüştürmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir koleksiyon döndürür herhangi bir geçerli ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Küme ifadesinin `SET(c)` aşağıdaki select deyimine mantıksal olarak eşdeğerdir:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir. Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu, nesnelerin bir koleksiyonunu bir kümeyi dönüştürmek küme ifadesi kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
