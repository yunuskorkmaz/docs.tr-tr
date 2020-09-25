---
title: BIRLEŞIM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 9c4106d26fb73219d7b5f0c6763736aaf9163d4b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200985"
---
# <a name="union-entity-sql"></a>BIRLEŞIM (Entity SQL)

İki veya daha fazla sorgunun sonuçlarını tek bir koleksiyonda birleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Koleksiyon ile birleştirmek için bir koleksiyon döndüren geçerli bir sorgu ifadesi tüm ifadeler aynı türde veya ortak temel veya türetilmiş türde olmalıdır `expression` .  
  
 UNION  
 Birden çok koleksiyonun birleştirildiğini ve tek bir koleksiyon olarak döndürüleceğini belirtir.  
  
 ALL  
 Birden çok koleksiyonun birleştirildiğini ve yinelemeler dahil olmak üzere tek bir koleksiyon olarak döndürüleceğini belirtir. Belirtilmemişse, yinelemeler sonuç koleksiyonundan kaldırılır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .  
  
## <a name="remarks"></a>Açıklamalar  

 BIRLEŞIM, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, iki sorgunun sonuçlarını tek bir koleksiyonda birleştirmek için UNıON ALL işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
