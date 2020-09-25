---
title: Toplama Işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1c32ccfe18c67c9baeb7df0f981c9129b3bbc8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204521"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Toplama Işlevleri (Entity Framework için SqlClient)

SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı toplama işlevleri sağlar. Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar gerçekleştirir ve bir değer döndürür. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.  
  
 Aşağıdaki, SqlClient toplama işlevleridir.  

## <a name="avgexpression"></a>Ort (ifade)

Bir koleksiyondaki değerlerin ortalamasını döndürür. Null değerler yok sayılır.

**Arguments**

`Int32`,, `Int64` `Double` Ve `Decimal` .

**Dönüş Değeri**

Türü `expression` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG (koleksiyon)

 Bir koleksiyondaki değerlerin sağlama toplamını döndürür. Null değerler yok sayılır.

 **Arguments**

 Bir koleksiyon ( `Int32` ).

 **Dönüş Değeri**

 Bir `Int32` .

 **Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a>COUNT (ifade)

Bir koleksiyondaki öğelerin sayısını bir olarak döndürür `Int32` .

**Arguments**

Bir koleksiyon \<T> , T aşağıdaki türlerden biridir:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (SQL Server 2000 ' de döndürülmez)|

**Dönüş Değeri**

Bir `Int32` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a>COUNT_BIG (ifade)

Bir koleksiyondaki öğelerin sayısını bir olarak döndürür `bigint` .

 **Arguments**

 Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (SQL Server 2000 ' de döndürülmez)|

**Dönüş Değeri**

Bir `Int64` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX (ifade)

Koleksiyonun en büyük değerini döndürür.

**Arguments**

Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş Değeri**

Türü `expression` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN (ifade)

Bir koleksiyondaki en küçük değeri döndürür.

**Arguments**

Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş Değeri**

Türü `expression` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV (ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapmasını döndürür.

**Arguments**

Bir koleksiyon ( `Double` ).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDSAPMAS (ifade)

Belirtilen ifadedeki tüm değerler için popülasyonun istatistiksel standart sapmasını döndürür.

**Arguments**

Bir koleksiyon ( `Double` ).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM (ifade)

Koleksiyondaki tüm değerlerin toplamını döndürür.

**Arguments**

T (T): `Int32` , `Int64` ,, `Double` `Decimal` .

**Dönüş Değeri**

Türü `expression` .

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel varyansını döndürür.

**Arguments**

Bir koleksiyon ( `Double` ).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (ifade)

Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı döndürür.

**Arguments**

Bir koleksiyon ( `Double` ).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplama Işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Toplu Kurallı İşlevler](./language-reference/aggregate-canonical-functions.md)
