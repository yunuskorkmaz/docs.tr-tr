---
title: "SEÇİN (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 26d62b4ccab71d1d21a8f65f7feacb8cec727a94
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
 Çoğaltmaları sonuç kümesinde görünebilir belirtir. Tüm varsayılan değerdir.  
  
 DISTINCT  
 Yalnızca benzersiz sonuçları sonuç kümesinde görünebilir belirtir.  
  
 DEĞER  
 Yalnızca bir öğesinin belirtilmesine izin verir ve bir satır sarmalayıcı eklemez.  
  
 `topSubclause`  
 Formun sorgudan döndürülecek ilk sonuç sayısını gösterir. geçerli bir ifade `top (``expr``)`.  
  
 SINIR parametresinin [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) işleci de olanak tanır, sonuç kümesinde ilk n öğeleri seçin.  
  
 `aliasedExpr`  
 Bir ifade formun:  
  
 `expr`olarak `identifier` &#124;`expr`  
  
 `expr`  
 Bir sabit değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 SELECT yan tümcesi sonra değerlendirilir [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), ve [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) yan tümceleri değerlendirilir. SELECT yan tümcesi, yalnızca (FROM yan tümcesi, veya dış kapsamları) şu anda kapsam öğelerine başvurabilir. GROUP BY yan tümcesinde belirtilen SELECT yan tümcesi yalnızca GROUP BY anahtarları için diğer adlar başvurmak için izin verilir. FROM yan tümcesi öğelerine başvuran yalnızca toplama işlevleri içinde izin verilir.  
  
 SELECT anahtar sözcüğü aşağıdaki bir veya daha fazla sorgu ifadeleri listesi seçim listesi olarak veya projeksiyon olarak daha resmi olarak bilinir. En genel projeksiyon tek sorgu ifadesi biçimidir. Üye seçerseniz `member1` bir koleksiyondan `collection1`, tüm yeni bir koleksiyon oluşturacak `member1` her nesnenin değerleri `collection1`aşağıdaki örnekte gösterildiği gibi.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Örneğin, varsa `customers` türü koleksiyonudur `Customer` bir özellik olan `Name` türü olan `string`, seçme `Name` gelen `customers` dizeleri koleksiyonu aşağıdaki örnekte gösterildiği gibi sunacak .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 JOIN söz dizimi (tam, iç, sol, dış, ON ve sağa) kullanmak da mümkündür. ON İç birleşimler için gereklidir ve nhizmetin birleştirmeler izin verilir.  
  
## <a name="row-and-value-select-clauses"></a>Satır ve değer Select yan tümceleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]SELECT yan tümcesi iki çeşidini destekler. Satır seçin, ilk değişken SELECT anahtar sözcüğe göre tanımlanır ve çıkışı öngörülen bir veya daha fazla değerleri belirtmek için kullanılır. Bir satır sarmalayıcı döndürdüğü değer örtük olarak eklendiğinden, sorgu ifadesi her zaman bir çoklu küme satır sonucudur.  
  
 Her bir satır select sorgu ifadesinde bir diğer ad belirtmeniz gerekir. Diğer ad belirtilmezse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer adı oluşturma kuralları kullanarak bir diğer ad oluşturmak çalışır.  
  
 Bir değer seçin, SELECT yan tümcesi türevi SELECT VALUE anahtar sözcüğü tarafından tanımlanır. Belirtilmesi tek bir değer verir ve bir satır sarmalayıcı eklemez.  
  
 Bir satır seçin her zaman aşağıdaki örnekte gösterildiği gibi değeri seçin bakımından ifade.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Tüm ve ayrı değiştiricileri  
 Her iki SELECT çeşitlemelerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BÜTÜN belirtimi izin ver veya ayrı değiştiricisi. AYRI değiştiricisi belirtilirse, yinelenen sorgu ifadesi (kadar ve SELECT yan tümcesi de dahil olmak üzere) tarafından üretilen koleksiyonundan ortadan kalkar. Tüm değiştiricisi ise, belirtilen, Hayır yinelenen eleme gerçekleştirilir; Tüm varsayılan değerdir.  
  
## <a name="differences-from-transact-sql"></a>Transact-SQL farkları  
 Transact-SQL, aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanımını desteklemez * SELECT yan tümcesinde bağımsız değişkeni.  Bunun yerine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm kayıtları FROM yan tümcesinden koleksiyonu diğer adlar başvurarak aşağıdaki örnekte gösterildiği gibi projeye sorguları sağlar.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Önceki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] sorgu ifadesi olarak ifade edilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu şekilde.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu sorgu tarafından döndürülen öğeler belirtmek için SELECT işlecini kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
