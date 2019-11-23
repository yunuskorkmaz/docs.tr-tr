---
title: BIRLEŞIM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: a5a20beb0ab55dcbaf2dbbb75801b50ab9ef6722
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319226"
---
# <a name="union-entity-sql"></a>BIRLEŞIM (Entity SQL)
İki veya daha fazla sorgunun sonuçlarını tek bir koleksiyonda birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Koleksiyon ile birleştirmek için bir koleksiyon döndüren geçerli bir sorgu ifadesi tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression`.  
  
 UNION  
 Birden çok koleksiyonun birleştirildiğini ve tek bir koleksiyon olarak döndürüleceğini belirtir.  
  
 Bütün  
 Birden çok koleksiyonun birleştirildiğini ve yinelemeler dahil olmak üzere tek bir koleksiyon olarak döndürüleceğini belirtir. Belirtilmemişse, yinelemeler sonuç koleksiyonundan kaldırılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 UNION [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, iki sorgunun sonuçlarını tek bir koleksiyonda birleştirmek için UNıON ALL işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
