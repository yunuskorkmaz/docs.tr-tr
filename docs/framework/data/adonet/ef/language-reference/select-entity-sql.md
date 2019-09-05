---
title: Seç (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249210"
---
# <a name="select-entity-sql"></a>Seç (Entity SQL)
Bir sorgu tarafından döndürülen öğeleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Arguments  
 BÜTÜN  
 Tekrarların sonuç kümesinde görünebilen belirtir. TÜMÜ varsayılandır.  
  
 AYRI  
 Sonuç kümesinde yalnızca benzersiz sonuçların görüneabileceğini belirtir.  
  
 DEERI  
 Yalnızca bir öğenin belirtilmesini sağlar ve satır sarmalayıcısı eklemez.  
  
 `topSubclause`  
 Formun `top(expr)`sorgusundan döndürülecek ilk sonuçların sayısını gösteren geçerli bir ifade.  
  
 [Order by](order-by-entity-sql.md) işlecinin LIMIT parametresi, sonuç kümesindeki ilk n öğeyi seçmenizi de sağlar.  
  
 `aliasedExpr`  
 Formun bir ifadesi:  
  
 `expr`as `identifier` &#124;`expr`  
  
 `expr`  
 Bir sabit değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 SELECT yan tümcesi from, [Group By](group-by-entity-sql.md)ve [HAVING](having-entity-sql.md) yan [tümcelerinden](from-entity-sql.md)sonra değerlendirilir. SELECT yan tümcesi yalnızca şu anda kapsamda olan öğelere (FROM yan tümcesinden veya dış kapsamlardan) başvurabilir. GROUP BY yan tümcesi belirtilmişse, SELECT yan tümcesinin yalnızca GROUP BY anahtarlarına yönelik diğer adlara başvuruda bulunmasına izin verilir. FROM yan tümcesi öğelerine başvurmak için yalnızca toplama işlevlerinde izin verilir.  
  
 SELECT anahtar sözcüğünü izleyen bir veya daha fazla sorgu ifadesinin listesi, seçim listesi veya yansıtma olarak daha resmi olarak bilinir. En genel projeksiyon formu tek bir sorgu deyimidir. `member1` Bir koleksiyondan `collection1`üye seçerseniz, aşağıdaki örnekte gösterildiği gibi, içindeki `collection1`her bir nesne için tüm `member1` değerlerin yeni bir koleksiyonunu oluşturacaksınız.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Örneğin, `customers` türünde `Name` `Customer` `Name` bir özelliğine sahip olan bir tür koleksiyonudur, öğesinden `customers` seçim aşağıdaki örnekte gösterildiği gibi bir dize koleksiyonu olur. `string` .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 BIRLEŞIM söz dizimini (tam, Iç, sol, dış, açık ve sağ) kullanmak da mümkündür. ON, İç birleştirmeler için gereklidir ve buna Çapraz birleştirmeler için izin verilir.  
  
## <a name="row-and-value-select-clauses"></a>Satır ve değer seçim yan tümceleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]SELECT yan tümcesinin iki çeşidini destekler. İlk varyant, Row Select, SELECT anahtar sözcüğü tarafından tanımlanır ve, yansıtılmalıdır bir veya daha fazla değer belirtmek için kullanılabilir. Satır sarmalayıcı döndürülen değerlerin çevresine örtük olarak eklendiğinden, sorgu ifadesinin sonucu her zaman bir satır kümesi olur.  
  
 Satırdaki her sorgu ifadesi Select bir diğer ad belirtmelidir. Diğer ad belirtilmemişse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarını kullanarak bir diğer ad oluşturmaya çalışır.  
  
 SELECT yan tümcesinin diğer varyantı, değer Select, SELECT VALUE anahtar sözcüğü tarafından tanımlanır. Yalnızca bir değerin belirtilmesini sağlar ve bir satır sarmalayıcı eklemez.  
  
 Aşağıdaki örnekte gösterildiği gibi, bir satır seçimi her zaman değer SEÇIM bakımından ifade edilir.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Tüm ve farklı değiştiriciler  
 ' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] In her iki varyantı de tüm veya ayrı bir değiştirici belirtimine izin verir. AYRı değiştirici belirtilirse, yinelemeler sorgu ifadesi tarafından üretilen koleksiyondan kaldırılır (SELECT yan tümcesi ile ve dahil). Tüm değiştirici belirtilirse, yinelenen bir eleme gerçekleştirilmez; TÜMÜ varsayılandır.  
  
## <a name="differences-from-transact-sql"></a>Transact-SQL arasındaki farklılıklar  
 Transact-SQL ' den [!INCLUDE[esql](../../../../../../includes/esql-md.md)] farklı olarak, select yan tümcesinde * bağımsız değişkeninin kullanımını desteklemez.  Bunun yerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aşağıdaki örnekte gösterildiği gibi,, from yan tümcesindeki koleksiyon diğer adlarına başvurarak tüm kayıtları proje için sorgular sağlar.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Önceki Transact-SQL sorgu ifadesi aşağıdaki şekilde ifade [!INCLUDE[esql](../../../../../../includes/esql-md.md)] edilir.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir sorgu tarafından döndürülecek öğeleri belirtmek için SELECT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [TOP](top-entity-sql.md)
