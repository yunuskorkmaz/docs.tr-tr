---
title: Toplama işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 8ed9a58da9914724fe312876d6594cb526f2e0e9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856523"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Toplama işlevleri (Entity Framework için SqlClient)
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı toplama işlevleri sağlar. Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar ve bir değer döndürür. Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır. Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.  
  
 SqlClient toplama işlevleri aşağıda verilmiştir.  

## <a name="avgexpression"></a>AVG(Expression)

Bir koleksiyondaki değerlerin ortalamasını döndürür. Null değerler yoksayılır.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, ve `Decimal`.

**Dönüş değeri**

Türünü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a>CHECKSUM_AGG(Collection)
 
 Sağlama toplamı değerleri, bir koleksiyon döndürür. Null değerler yoksayılır.
 
 **Bağımsız Değişkenler**
 
 Bir koleksiyon (`Int32`).
 
 **Dönüş değeri**
 
 Bir `Int32`.
 
 **Örnek**
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>Count (deyim)

Bir koleksiyondaki öğe sayısını döndürür. bir `Int32`.

**Bağımsız Değişkenler**

Bir koleksiyon\<T >, burada T aşağıdaki türlerden biridir:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (SQL Server 2000'de döndürülmez)|

**Dönüş değeri**

Bir `Int32`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
[! kod sql[#SQLSERVER_COUNT DP EntityServices kavramları](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)
 
## <a name="countbigexpression"></a>COUNT_BIG(Expression)
 
 Bir koleksiyondaki öğe sayısını döndürür. bir `bigint`.
 
 **Bağımsız Değişkenler**
 
 Burada T aşağıdaki türlerden biri, bir Collection(T):
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (SQL Server 2000'de döndürülmez)|

**Dönüş değeri**

Bir `Int64`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX(Expression)

En yüksek değer koleksiyonunu döndürür.

**Bağımsız Değişkenler**

Burada T aşağıdaki türlerden biri, bir Collection(T): 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş değeri**

Türünü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN(Expression)

En düşük değer, bir koleksiyon döndürür.

**Bağımsız Değişkenler**

Burada T aşağıdaki türlerden biri, bir Collection(T): 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş değeri**

Türünü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV(Expression)

Belirtilen ifadedeki istatistiksel tüm değerlerin standart sapmasını verir.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>StDevP(Expression)

Belirtilen ifadedeki tüm değerlerin popülasyon için istatistiksel standart sapma döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM(Expression)

Koleksiyondaki tüm değerlerin toplamını döndürür.

**Bağımsız Değişkenler**

Burada T, şu türlerden birinde bir Collection(T): `Int32`, `Int64`, `Double`, `Decimal`.

**Dönüş değeri**

Türünü `expression`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR(Expression)

Belirtilen ifadedeki istatistiksel tüm değerlerin varyansını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VarP(Expression)

Belirtilen ifadedeki istatistiksel tüm değerlerin popülasyon varyansını verir.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Ayrıca bkz.

SqlClient destekleyen toplama işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
**SQL Server 2005'te**: [toplama işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))  
**SQL Server 2008 ve üzeri**: [toplama işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)  
[Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
[Toplu Kurallı İşlevler](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
