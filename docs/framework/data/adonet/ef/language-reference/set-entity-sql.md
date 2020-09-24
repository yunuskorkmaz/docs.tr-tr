---
title: AYARLA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 2ac7db5b22ad21eb152788b6c6d6a8e65c1f6a7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169641"
---
# <a name="set-entity-sql"></a>AYARLA (Entity SQL)

KÜME ifadesi, tüm yinelenen öğelerle kaldırılan yeni bir koleksiyon sunarak bir nesne koleksiyonunu bir kümesine dönüştürmek için kullanılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  

 Küme ifadesi `SET(c)` aşağıdaki SELECT deyimine mantıksal olarak eşdeğerdir:  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` , [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Bkz. set işleçleri için öncelik bilgileri [hariç](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgu bir nesne koleksiyonunu bir kümesine dönüştürmek için SET ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
