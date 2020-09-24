---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: c0c975ab5cf2761496db6efa1f88f409aa1b1abd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148223"
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
