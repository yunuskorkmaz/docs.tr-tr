---
title: Seç (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 860e2a9a3e484e8d09cad282be8c0126c8235b46
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202220"
---
# <a name="select-entity-sql"></a>Seç (Entity SQL)

Bir sorgu tarafından döndürülen öğeleri belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 ALL  
 Tekrarların sonuç kümesinde görünebilen belirtir. TÜMÜ varsayılandır.  
  
 DISTINCT  
 Sonuç kümesinde yalnızca benzersiz sonuçların görüneabileceğini belirtir.  
  
 DEĞER  
 Yalnızca bir öğenin belirtilmesini sağlar ve satır sarmalayıcısı eklemez.  
  
 `topSubclause`  
 Formun sorgusundan döndürülecek ilk sonuçların sayısını gösteren geçerli bir ifade `top(expr)` .  
  
 [Order by](order-by-entity-sql.md) işlecinin LIMIT parametresi, sonuç kümesindeki ilk n öğeyi seçmenizi de sağlar.  
  
 `aliasedExpr`  
 Formun bir ifadesi:  
  
 `expr``identifier`&#124; olarak`expr`  
  
 `expr`  
 Bir sabit değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 SELECT yan tümcesi from, [Group By](group-by-entity-sql.md)ve [HAVING](having-entity-sql.md) yan [tümcelerinden](from-entity-sql.md)sonra değerlendirilir. SELECT yan tümcesi yalnızca şu anda kapsamda olan öğelere (FROM yan tümcesinden veya dış kapsamlardan) başvurabilir. GROUP BY yan tümcesi belirtilmişse, SELECT yan tümcesinin yalnızca GROUP BY anahtarlarına yönelik diğer adlara başvuruda bulunmasına izin verilir. FROM yan tümcesi öğelerine başvurmak için yalnızca toplama işlevlerinde izin verilir.  
  
 SELECT anahtar sözcüğünü izleyen bir veya daha fazla sorgu ifadesinin listesi, seçim listesi veya yansıtma olarak daha resmi olarak bilinir. En genel projeksiyon formu tek bir sorgu deyimidir. `member1`Bir koleksiyondan üye seçerseniz `collection1` , `member1` `collection1` Aşağıdaki örnekte gösterildiği gibi, içindeki her bir nesne için tüm değerlerin yeni bir koleksiyonunu oluşturacaksınız.  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 Örneğin, `customers` `Customer` türünde bir özelliğine sahip olan bir tür koleksiyonudur `Name` `string` , `Name` öğesinden seçim `customers` Aşağıdaki örnekte gösterildiği gibi bir dize koleksiyonu olur.  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 BIRLEŞIM söz dizimini (tam, Iç, sol, dış, açık ve sağ) kullanmak da mümkündür. ON, İç birleştirmeler için gereklidir ve buna Çapraz birleştirmeler için izin verilir.  
  
## <a name="row-and-value-select-clauses"></a>Satır ve değer seçim yan tümceleri  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SELECT yan tümcesinin iki çeşidini destekler. İlk varyant, Row Select, SELECT anahtar sözcüğü tarafından tanımlanır ve, yansıtılmalıdır bir veya daha fazla değer belirtmek için kullanılabilir. Satır sarmalayıcı döndürülen değerlerin çevresine örtük olarak eklendiğinden, sorgu ifadesinin sonucu her zaman bir satır kümesi olur.  
  
 Satırdaki her sorgu ifadesi Select bir diğer ad belirtmelidir. Diğer ad belirtilmemişse, diğer ad [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturma kurallarını kullanarak bir diğer ad oluşturmaya çalışır.  
  
 SELECT yan tümcesinin diğer varyantı, değer Select, SELECT VALUE anahtar sözcüğü tarafından tanımlanır. Yalnızca bir değerin belirtilmesini sağlar ve bir satır sarmalayıcı eklemez.  
  
 Aşağıdaki örnekte gösterildiği gibi, bir satır seçimi her zaman değer SEÇIM bakımından ifade edilir.  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a>Tüm ve farklı değiştiriciler  

 ' In her iki varyantı de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm veya ayrı bir değiştirici belirtimine izin verir. AYRı değiştirici belirtilirse, yinelemeler sorgu ifadesi tarafından üretilen koleksiyondan kaldırılır (SELECT yan tümcesi ile ve dahil). Tüm değiştirici belirtilirse, yinelenen bir eleme gerçekleştirilmez; TÜMÜ varsayılandır.  
  
## <a name="differences-from-transact-sql"></a>Transact-SQL arasındaki farklılıklar  

 Transact-SQL ' den farklı olarak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Select yan tümcesinde * bağımsız değişkeninin kullanımını desteklemez.  Bunun yerine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki örnekte gösterildiği gibi,, from yan tümcesindeki koleksiyon diğer adlarına başvurarak tüm kayıtları proje için sorgular sağlar.  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 Önceki Transact-SQL sorgu ifadesi aşağıdaki şekilde ifade edilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir sorgu tarafından döndürülecek öğeleri belirtmek için SELECT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Sayfanın Üstü](top-entity-sql.md)
