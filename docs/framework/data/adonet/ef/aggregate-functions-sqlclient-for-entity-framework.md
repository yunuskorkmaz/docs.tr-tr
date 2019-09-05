---
title: Toplama Işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251701"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Toplama Işlevleri (Entity Framework için SqlClient)
SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı toplama işlevleri sağlar. Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar gerçekleştirir ve bir değer döndürür. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.  
  
 Aşağıdaki, SqlClient toplama işlevleridir.  

## <a name="avgexpression"></a>Ort (ifade)

Bir koleksiyondaki değerlerin ortalamasını döndürür. Null değerler yok sayılır.

**Bağımsız Değişkenler**

`Int32` ,`Int64`, Ve .`Decimal` `Double`

**Dönüş değeri**

Türü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG (koleksiyon)
 
 Bir koleksiyondaki değerlerin sağlama toplamını döndürür. Null değerler yok sayılır.
 
 **Bağımsız Değişkenler**
 
 Bir koleksiyon (`Int32`).
 
 **Dönüş değeri**
 
 Bir `Int32`.
 
 **Örnek**
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>COUNT (ifade)

Bir koleksiyondaki öğelerin sayısını bir `Int32`olarak döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon\<t >, burada T aşağıdaki türlerden biridir:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(SQL Server 2000 ' de döndürülmez)|

**Dönüş değeri**

Bir `Int32`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
[! Code-SQL[DP EntityServices kavramları # SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)
 
## <a name="count_bigexpression"></a>COUNT_BıG (ifade)
 
 Bir koleksiyondaki öğelerin sayısını bir `bigint`olarak döndürür.
 
 **Bağımsız Değişkenler**
 
 Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(SQL Server 2000 ' de döndürülmez)|

**Dönüş değeri**

Bir `Int64`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX (ifade)

Koleksiyonun en büyük değerini döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (T), burada T aşağıdaki türlerden biridir: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş değeri**

Türü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN (ifade)

Bir koleksiyondaki en küçük değeri döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (T), burada T aşağıdaki türlerden biridir: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş değeri**

Türü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV (ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapmasını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDSAPMAS (ifade)

Belirtilen ifadedeki tüm değerler için popülasyonun istatistiksel standart sapmasını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM (ifade)

Koleksiyondaki tüm değerlerin toplamını döndürür.

**Bağımsız Değişkenler**

T (T) `Int32`:, `Int64`, `Double` `Decimal`,.

**Dönüş değeri**

Türü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel varyansını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (ifade)

Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Ayrıca bkz.

SqlClient tarafından desteklenen toplama işlevleri hakkında daha fazla bilgi için, SqlClient sağlayıcısı bildiriminde belirttiğiniz SQL Server sürümü için belgelere bakın:

- **SQL Server 2005:** [Toplama Işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))
- **SQL Server 2008 ve üzeri:** [Toplama Işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)

- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Toplu Kurallı İşlevler](./language-reference/aggregate-canonical-functions.md)
