---
title: SEÇİN (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: af704d00800a72b4ab670781c5bb3adec93683cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489884"
---
# <a name="select-entity-sql"></a>SEÇİN (varlık SQL)
Bir sorgu tarafından döndürülen öğeleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Arguments  
 TÜM  
 Yinelenen sonuç kümesinde göründüğünü belirtir. Tüm varsayılan değerdir.  
  
 DISTINCT  
 Yalnızca benzersiz sonuçları sonuç kümesinde görünebileceğini belirtir.  
  
 DEĞER  
 Yalnızca bir öğe belirtilmesine olanak sağlar ve bir satır sarmalayıcı üzerinde eklemez.  
  
 `topSubclause`  
 Form sorgudan döndürülecek ilk sonuç sayısını gösteren herhangi bir geçerli ifade `top(expr)`.  
  
 SINIRI parametresi [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) işleci de olanak tanır, sonuç kümesindeki ilk n öğe seçin.  
  
 `aliasedExpr`  
 Bir ifade formun:  
  
 `expr` as `identifier` &#124; `expr`  
  
 `expr`  
 Değişmez değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 SELECT yan tümcesi sonra değerlendirilir [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), ve [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) yan tümceleri değerlendirilir. SELECT yan tümcesi yalnızca (FROM yan tümcesi, veya dış kapsamları) şu anda kapsam öğelerine başvurabilir. GROUP BY yan tümcesi belirtilmiş ise SELECT yan tümcesi yalnızca GROUP BY anahtarları için diğer adlar başvurmak için izin verilir. FROM yan tümcesi öğelerine başvuran yalnızca toplama işlevlerinde izin verilir.  
  
 SELECT anahtar sözcüğünü izleyen bir veya daha fazla sorgu ifadeleri listesini seçim listesi olarak veya daha eski adıyla projeksiyon olarak bilinir. En genel projeksiyon tek sorgu ifadesi biçimindedir. Bir üye seçtiğinizde `member1` bir koleksiyondan `collection1`, tüm yeni bir koleksiyon oluşturacak `member1` her nesne için değerler `collection1`aşağıdaki örnekte gösterildiği gibi.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Örneğin, varsa `customers` türü koleksiyonudur `Customer` bir özelliği olan `Name` türü olan `string`u seçerek `Name` gelen `customers` dizelerden oluşan bir koleksiyonu, aşağıdaki örnekte gösterildiği gibi verecek olan .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 JOIN söz dizimini (tam, iç, sol, dış, ON ve SAĞDA) kullanmak mümkündür. Şirket iç birleştirmeler için gereklidir ve nBaşka birleştirmeler izin verilir.  
  
## <a name="row-and-value-select-clauses"></a>Yan tümceleri satır ve değer seçin  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SELECT yan tümcesi birinin iki çeşidi destekler. İlk satırı seçin, değişken, SELECT anahtar sözcüğü tarafından tanımlanır ve çıkış öngörülen bir veya daha fazla değerleri belirtmek için kullanılabilir. Bir satır sarmalayıcı döndürülen değerlerden örtük olarak eklendiğinden, sorgu ifadesi her zaman bir çoklu küme satır sonucudur.  
  
 Her sorgu ifadesi içinde bir satırı seçin, bir diğer ad belirtmeniz gerekir. Diğer ad yok belirtilirse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarını kullanarak bir diğer ad oluşturmaya çalışır.  
  
 Bir değişken değeri select, SELECT yan tümcesi, SELECT VALUE anahtar sözcüğü tarafından tanımlanır. Yalnızca bir değer belirtilmesine olanak tanır ve satır sarmalayıcı eklemez.  
  
 Bir satır seçin her zaman aşağıdaki örnekte gösterildiği gibi değeri seçin açısından ifade.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Tüm ve ayrı değiştiriciler  
 Her iki SELECT türevleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BÜTÜN belirtilmesine izin ver veya ayrı değiştiricisi. FARKLI değiştiricisi belirtilirse, çoğaltmaları (en fazla ve SELECT yan tümcesi dahil olmak üzere) sorgu ifadesi tarafından üretilen koleksiyondan ortadan kalkar. Belirtilen, Hayır yinelenen tüm değiştiricisi, eleme gerçekleştirilir; Tüm varsayılan değerdir.  
  
## <a name="differences-from-transact-sql"></a>Transact-SQL arasındaki farklar  
 Transact-SQL, aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanımını desteklemiyor * SELECT yan tümcesinde bağımsız değişken.  Bunun yerine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm kayıtları süzer koleksiyonu diğer adlar FROM yan tümcesinden başvurarak aşağıdaki örnekte gösterildiği gibi projeye sorguları sağlar.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Önceki Transact-SQL sorgu ifadesi olarak ifade edilen [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu şekilde.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu seçme işleci bir sorgu tarafından döndürülen öğeleri belirtmek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
