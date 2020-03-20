---
title: Toplam Fonksiyonlar (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150655"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Toplam Fonksiyonlar (Entity Framework için SqlClient)
SQL Server için .NET Framework Data Provider (SqlClient) toplu işlevler sağlar. Toplam işlevler, giriş değerleri kümesi üzerinde hesaplamalar yapar ve bir değer döndürür. Bu işlevler, SqlClient'ı kullandığınızda kullanılabilen SqlServer ad alanındadır. Sağlayıcının ad alanı özelliği, Varlık Çerçevesi'nin bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için hangi önek kullanıldığını keşfetmesine olanak tanır.  
  
 Aşağıdaki sqlclient toplu işlevleri vardır.  

## <a name="avgexpression"></a>AVG(ifade)

Koleksiyondaki değerlerin ortalamasını verir. Null değerleri yoksayılır.

**Bağımsız Değişkenler**

Bir `Int32` `Int64`, `Double`, `Decimal`ve .

**Dönüş Değeri**

Türü `expression`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG(toplama)

 Koleksiyondaki değerlerin denetimini verir. Null değerleri yoksayılır.

 **Bağımsız Değişkenler**

 Bir Koleksiyon(`Int32`).

 **Dönüş Değeri**

 Bir `Int32`.

 **Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a>COUNT(ifade)

Koleksiyondaki öğe sayısını ' `Int32`olarak verir.

**Bağımsız Değişkenler**

T'nin aşağıdaki türlerden biri olduğu Bir Koleksiyon\<T>:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(SQL Server 2000'de döndürülmez)|

**Dönüş Değeri**

Bir `Int32`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a>COUNT_BIG(ifade)

Koleksiyondaki madde sayısını ' `bigint`olarak verir.

 **Bağımsız Değişkenler**

 T'nin aşağıdaki türlerden biri olduğu Koleksiyon(T)

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(SQL Server 2000'de döndürülmez)|

**Dönüş Değeri**

Bir `Int64`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX(ifade)

Koleksiyonun en büyük değerini verir.

**Bağımsız Değişkenler**

T'nin aşağıdaki türlerden biri olduğu Koleksiyon(T)

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş Değeri**

Türü `expression`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN(ifade)

Koleksiyondaki minimum değeri verir.

**Bağımsız Değişkenler**

T'nin aşağıdaki türlerden biri olduğu Koleksiyon(T)

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Dönüş Değeri**

Türü `expression`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDSAPMA(ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapını verir.

**Bağımsız Değişkenler**

Bir Koleksiyon(`Double`).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDSAPMAS(ifade)

Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel standart sapması verir.

**Bağımsız Değişkenler**

Bir Koleksiyon(`Double`).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM(ifade)

Koleksiyondaki tüm değerlerin toplamını verir.

**Bağımsız Değişkenler**

T'nin aşağıdaki türlerden biri olduğu Bir `Int32` `Int64`Koleksiyon(T) : , , `Double`, `Decimal`.

**Dönüş Değeri**

Türü `expression`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR(ifade)

Belirtilen ifadedeki tüm değerlerin istatistiksel değişkenini verir.

**Bağımsız Değişkenler**

Bir Koleksiyon(`Double`).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP(ifade)

Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı verir.

**Bağımsız Değişkenler**

Bir Koleksiyon(`Double`).

**Dönüş Değeri**

Bir `Double`.

**Örnek**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplam Fonksiyonlar (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Toplu Kurallı İşlevler](./language-reference/aggregate-canonical-functions.md)
