---
description: 'Daha fazla bilgi edinin: DEREF (Entity SQL)'
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 9d0f29123c1459c6eab21ea9cd860b5c9e77f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724732"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)

Başvuru değerine başvurur ve başvurunun sonucunu üretir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Başvurulan varlığın değeri.  
  
## <a name="remarks"></a>Açıklamalar  

 DEREF işleci bir başvuru değerine başvurur ve başvurunun sonucunu üretir. Örneğin, `r` başvuru türü başvurusu ise \<T> , `Deref(r)` tarafından başvurulan varlığı veren türünde bir ifadedir `T` `r` . Başvuru değeri null ise veya tehlike varsa (yani, başvurunun hedefi yoksa), DEREF işlecinin sonucu null olur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, başvuru değeri başvurusu yapmak ve bu başvurunun sonucunu üretmek IÇIN DEREF işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu Executeprimitivettypeınfo sorgu yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [ANAHTAR](key-entity-sql.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
