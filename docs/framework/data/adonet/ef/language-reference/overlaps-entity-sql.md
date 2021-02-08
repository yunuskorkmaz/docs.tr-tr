---
description: 'Hakkında daha fazla bilgi edinin: ÖRTÜŞMELER (Entity SQL)'
title: ÖRTÜŞMELER (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: dd2f4a0925c57edcc3dd2d1264d00921b092525a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791913"
---
# <a name="overlaps-entity-sql"></a>ÖRTÜŞMELER (Entity SQL)

İki koleksiyonun ortak öğelere sahip olup olmadığını belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` İki koleksiyonun ortak öğeleri varsa; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 ÖRTÜŞMELER, aşağıdaki gibi işlevsel bir eşdeğer sağlar:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 ÖRTÜŞÜYOR, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, iki koleksiyonun ortak bir değere sahip olup olmadığını belirleyen ÖRTÜŞMELER işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bunu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
