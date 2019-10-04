---
title: VAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 44f128a292b013fd3a3a80efdd2d10a63e3cfb07
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833831"
---
# <a name="exists-entity-sql"></a>VAR (Entity SQL)
Bir koleksiyonun boş olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Bir koleksiyon döndüren geçerli bir ifade.  
  
 BAŞLATıLMADı  
 Sonucunun var olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş değeri  
 koleksiyon boş değilse, `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 VAR [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. @No__t-0 kümesi işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, koleksiyonun boş olup olmadığını anlamak için EXISTS işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
