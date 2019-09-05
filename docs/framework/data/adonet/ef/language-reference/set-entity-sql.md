---
title: AYARLA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249234"
---
# <a name="set-entity-sql"></a>AYARLA (Entity SQL)
KÜME ifadesi, tüm yinelenen öğelerle kaldırılan yeni bir koleksiyon sunarak bir nesne koleksiyonunu bir kümesine dönüştürmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Küme ifadesi `SET(c)` aşağıdaki SELECT deyimine mantıksal olarak eşdeğerdir:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET`, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Bkz [](except-entity-sql.md) . [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçleri için öncelik bilgileri hariç.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgu bir nesne koleksiyonunu bir kümesine dönüştürmek için SET ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
