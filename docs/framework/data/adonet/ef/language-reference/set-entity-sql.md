---
title: AYARLA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 9d4cdeac317509fd61741a19276a6764a1c2bfce
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319348"
---
# <a name="set-entity-sql"></a>AYARLA (Entity SQL)
KÜME ifadesi, tüm yinelenen öğelerle kaldırılan yeni bir koleksiyon sunarak bir nesne koleksiyonunu bir kümesine dönüştürmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 kümesi ifadesi aşağıdaki SELECT deyimine mantıksal olarak eşdeğerdir:  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET`, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. @No__t-1 kümesi işleçleri için öncelik bilgisi [hariç](except-entity-sql.md) bölümüne bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgu bir nesne koleksiyonunu bir kümesine dönüştürmek için SET ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
