---
title: BIRLEŞIM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 34eac0dfd28d39ec68f084ea10dd46693f44eea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248794"
---
# <a name="union-entity-sql"></a>BIRLEŞIM (Entity SQL)
İki veya daha fazla sorgunun sonuçlarını tek bir koleksiyonda birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Koleksiyon ile birleştirmek için bir koleksiyon döndüren geçerli bir sorgu ifadesi tüm ifadeler aynı türde veya ortak temel veya türetilmiş türde `expression`olmalıdır.  
  
 UNION  
 Birden çok koleksiyonun birleştirildiğini ve tek bir koleksiyon olarak döndürüleceğini belirtir.  
  
 BÜTÜN  
 Birden çok koleksiyonun birleştirildiğini ve yinelemeler dahil olmak üzere tek bir koleksiyon olarak döndürüleceğini belirtir. Belirtilmemişse, yinelemeler sonuç koleksiyonundan kaldırılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı türde veya ortak bir temel ya da türetilmiş türden `expression`bir koleksiyon.  
  
## <a name="remarks"></a>Açıklamalar  
 Birleşim, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Set işleçleri için öncelik bilgileri için bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, iki sorgunun sonuçlarını tek bir koleksiyonda birleştirmek için UNıON ALL işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
