---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: dc7338d176302b8683d541ab0dc715dd8d149c6f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319762"
---
# <a name="intersect-entity-sql"></a>INTERSECT (Entity SQL)
INTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürür. Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `expression` olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` olarak.  
  
## <a name="remarks"></a>Açıklamalar  
 INTERSECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. @No__t-0 kümesi işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, ıNTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürmek için ıNTERSECT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
