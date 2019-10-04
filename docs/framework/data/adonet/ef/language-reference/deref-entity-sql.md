---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833899"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Başvuru değerine başvurur ve başvurunun sonucunu üretir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş değeri  
 Başvurulan varlığın değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 DEREF işleci bir başvuru değerine başvurur ve başvurunun sonucunu üretir. Örneğin, `r`, ref @ no__t-1T > türünde bir başvuru ise, `Deref(r)` `r` tarafından başvurulan varlığı veren `T` türünde bir ifadedir. Başvuru değeri null ise veya tehlike varsa (yani, başvurunun hedefi yoksa), DEREF işlecinin sonucu null olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, başvuru değeri başvurusu yapmak ve bu başvurunun sonucunu üretmek için DEREF işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu Executeprimitivettypeınfo sorgu yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [ANAHTAR](key-entity-sql.md)
- [Null yapılabilir yapılandırılmış türler](nullable-structured-types-entity-sql.md)
