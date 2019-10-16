---
title: ÖRTÜŞMELER (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: bdee9281fd406a3d029d3a10536cbdd48d2f7a58
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319422"
---
# <a name="overlaps-entity-sql"></a>ÖRTÜŞMELER (Entity SQL)
İki koleksiyonun ortak öğelere sahip olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi. Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `expression` olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İki koleksiyonun ortak öğeleri varsa `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 ÖRTÜŞMELER, aşağıdaki gibi işlevsel bir eşdeğer sağlar:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 ÖRTÜŞÜYOR [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. @No__t-0 kümesi işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, iki koleksiyonun ortak bir değere sahip olup olmadığını belirleyen ÖRTÜŞMELER işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bunu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
