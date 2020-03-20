---
title: SELECT (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149915"
---
# <a name="select-entity-sql"></a>SELECT (Varlık SQL)
Sorgu tarafından döndürülen öğeleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 TÜMÜ  
 Sonuç kümesinde yinelemelerin görünebileceğini belirtir. ALL varsayılandır.  
  
 DISTINCT  
 Sonuç kümesinde yalnızca benzersiz sonuçların görünebileceğini belirtir.  
  
 DEĞER  
 Yalnızca bir öğenin belirtilmesine izin verir ve satır sarıcıya eklemez.  
  
 `topSubclause`  
 Formun `top(expr)`sorgudan döndürülecek ilk sonuç sayısını gösteren geçerli bir ifade .  
  
 [ORDER BY](order-by-entity-sql.md) işlecinin LIMIT parametresi, sonuç kümesindeki ilk n maddelerini seçmenize de olanak tanır.  
  
 `aliasedExpr`  
 Formun bir ifadesi:  
  
 `expr`olarak `identifier` &#124;`expr`  
  
 `expr`  
 Gerçek bir ifade ya da ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 SELECT yan tümcesi [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)ve [HAVING](having-entity-sql.md) yan tümceleri değerlendirildikten sonra değerlendirilir. SELECT yan tümcesi yalnızca şu anda kapsam içinde olan (FROM yan tümcesinden veya dış kapsamlardan) maddelere başvurabilir. GROUP BY yan tümcesi belirtilmişse, SELECT yan tümcesinin yalnızca GROUP BY tuşlarına başvurmasına izin verilir. FROM yan tümcesi öğelerine atıfta bulunulması yalnızca toplu işlevlerde izin verilir.  
  
 SELECT anahtar sözcükten sonra bir veya daha fazla sorgu ifadesinin listesi seçlistesi veya daha resmi olarak projeksiyon olarak bilinir. Projeksiyonun en genel biçimi tek bir sorgu ifadesidir. `member1` Bir koleksiyondan `collection1`bir üye seçerseniz, aşağıdaki örnekte `member1` gösterildiği `collection1`gibi, her nesne için tüm değerlerin yeni bir koleksiyon üretecektir.  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 Örneğin, türünde `customers` `Customer` `Name` `string`bir özelliğe sahip bir tür koleksiyonu ise, aşağıdaki örnekte gösterildiği gibi, seçerek `Name` dizeleri bir koleksiyon `customers` verecektir.  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 JOIN sözdizimini (TAM, İç, SOL, DıŞ, AVEVek) ve SAĞ olarak da kullanmak mümkündür. ON iç birleştirmeler için gereklidir ve çapraz birleştirmeler için nto izin verilir.  
  
## <a name="row-and-value-select-clauses"></a>Satır ve Değer Seç Yan Tümceleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]SELECT yan tümcesinin iki türevlerini destekler. İlk varyant, satır seç, SELECT anahtar sözcüğü tarafından tanımlanır ve öngörenebilmek gereken bir veya daha fazla değer belirtmek için kullanılabilir. Satır sarıcı döndürülen değerlerin etrafına örtülü olarak eklenmiştir, sorgu ifadesinin sonucu her zaman bir satır çok kümesidir.  
  
 Bir satırdaki her sorgu ifadesi nin bir takma ad belirtmesi gerekir. Takma ad belirtilmemişse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarını kullanarak bir takma ad oluşturmaya çalışır.  
  
 SELECT yan tümcesinin diğer varyantı, değer seçin, SELECT VALUE anahtar kelimesi tarafından tanımlanır. Yalnızca bir değerin belirtilmesine izin verir ve satır sarıcı eklemez.  
  
 Aşağıdaki örnekte gösterildiği gibi, bir satır seçimi, VALUE SELECT açısından her zaman ifade edilebilir.  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a>Tüm ve Farklı Değiştiriciler  
 SELECT'in her [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki varyantı da BIR ALL veya DISTINCT değiştiricinin belirtimine izin verir. DISTINCT değiştirici belirtilirse, yinelenenler sorgu ifadesi tarafından üretilen koleksiyondan (SELECT yan tümcesi dahil) ortadan kalkar. TÜM değiştirici belirtilirse, yinelenen eleme yapılmaz; ALL varsayılandır.  
  
## <a name="differences-from-transact-sql"></a>Transact-SQL'den Farklar  
 Transact-SQL'in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aksine, SELECT yan tümcesindeki * bağımsız değişkeninin kullanımını desteklemez.  Bunun [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yerine, aşağıdaki örnekte gösterildiği gibi, FROM yan tümcesinden toplama takma adlarına başvurarak sorguların tüm kayıtları yansıtmasına olanak tanır.  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 Önceki Transact-SQL sorgu ifadesi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki şekilde ifade edilir.  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, sorgu tarafından döndürülecek öğeleri belirtmek için SELECT işleci kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Sayfanın Üstü](top-entity-sql.md)
