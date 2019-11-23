---
title: Toplama Işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700053"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Toplama Işlevleri (Entity Framework için SqlClient)
SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı toplama işlevleri sağlar. Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar gerçekleştirir ve bir değer döndürür. Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır. Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.  
  
 Aşağıdaki, SqlClient toplama işlevleridir.  

## <a name="avgexpression"></a>Ort (ifade)

Bir koleksiyondaki değerlerin ortalamasını döndürür. Null değerler yok sayılır.

**Bağımsız Değişkenler**

`Int32`, `Int64`, `Double`ve `Decimal`.

**Dönüş değeri**

`expression` öğesinin türü.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG (koleksiyon)
 
 Bir koleksiyondaki değerlerin sağlama toplamını döndürür. Null değerler yok sayılır.
 
 **Bağımsız Değişkenler**
 
 Bir koleksiyon (`Int32`).
 
 **Dönüş değeri**
 
 Bir `Int32`.
 
 **Örnek**
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>COUNT (ifade)

Bir koleksiyondaki öğelerin sayısını `Int32`olarak döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon\<T >, burada T aşağıdaki türlerden biridir:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (SQL Server 2000 ' de döndürülmez)|

**Dönüş değeri**

Bir `Int32`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a>COUNT_BIG (ifade)
 
Bir koleksiyondaki öğelerin sayısını `bigint`olarak döndürür.
 
 **Bağımsız Değişkenler**
 
 Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (SQL Server 2000 ' de döndürülmez)|

**Dönüş değeri**

Bir `Int64`.

**Örnek**

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

`expression` öğesinin türü.

**Örnek**

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

`expression` öğesinin türü.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV (ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapmasını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDSAPMAS (ifade)

Belirtilen ifadedeki tüm değerler için popülasyonun istatistiksel standart sapmasını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM (ifade)

Koleksiyondaki tüm değerlerin toplamını döndürür.

**Bağımsız Değişkenler**

T 'nin şu türlerden biri olduğu bir koleksiyon (T): `Int32`, `Int64`, `Double``Decimal`.

**Dönüş değeri**

`expression` öğesinin türü.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel varyansını döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (ifade)

Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı döndürür.

**Bağımsız Değişkenler**

Bir koleksiyon (`Double`).

**Dönüş değeri**

A `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplama Işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Toplu Kurallı İşlevler](./language-reference/aggregate-canonical-functions.md)
