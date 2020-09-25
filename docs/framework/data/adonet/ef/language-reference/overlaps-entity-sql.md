---
title: ÖRTÜŞMELER (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 6902a44af343c37ccb26412738d9f96b28551814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204430"
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
