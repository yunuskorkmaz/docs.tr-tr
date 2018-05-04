---
title: Toplama işlevleri (SqlClient Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 558e9f8480dd69e2277603e9bb1013acfbc29467
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Toplama işlevleri (SqlClient Entity Framework)
SQL Server (SqlClient) için .NET Framework veri sağlayıcısı toplama işlevleri sağlar. Toplama işlevleri giriş değerleri kümesine göre hesaplamalar ve bir değer döndürür. Bu SqlServer ad alanında SqlClient kullandığınızda kullanılabilir olduğu işlevlerdir. Bir sağlayıcının ad özelliği, hangi önekin türler ve işlevler gibi belirli yapıları için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.  
  
 Aşağıdaki tabloda SqlClient toplama işlevleri gösterir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`AVG(` `expression` `)`|Bir koleksiyondaki değerlerin ortalamasını döndürür.<br /><br /> Null değerler göz ardı edilir.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir `Int32`, `Int64`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(` `collection` `)`|Bir koleksiyonda bulunan değerlerin toplamını döndürür.<br /><br /> Null değerler göz ardı edilir.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (`Int32`).<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(` `expression` `)`|Bir koleksiyon olarak öğe sayısını döndürür bir `Int32`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (T aşağıdaki türlerden biri olduğu T):<br /><br /> `Guid` (SQL Server 2000'de döndürülen değil),<br /><br /> `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, veya `Binary`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(` `expression` `)`|Bir koleksiyon olarak öğe sayısını döndürür bir `bigint`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (T aşağıdaki türlerden biri olduğu T):<br /><br /> `Guid` (SQL Server 2000'de döndürülen değil), `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, veya `Binary`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int64`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(` `expression` `)`|En büyük değer koleksiyonunu döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (T olduğu aşağıdaki türlerden biri T): `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time` , `String`, `Binary`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(` `expression` `)`|Bir koleksiyondaki en küçük değeri döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (T olduğu aşağıdaki türlerden biri T): `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time` , `String`,<br /><br /> `Binary`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(` `expression` `)`|Belirtilen ifade istatistiksel tüm değerlerin standart sapmasını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (`Double`).<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(` `expression` `)`|Belirtilen ifadedeki tüm değerlerin popülasyon için istatistiksel standart sapma döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (`Double`).<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(` `expression` `)`|Koleksiyondaki tüm değerlerin toplamını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (T olduğu aşağıdaki türlerden biri T): `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(` `expression` `)`|Belirtilen ifade istatistiksel tüm değerlerin varyansını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (`Double`).<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(` `expression` `)`|Belirtilen ifade istatistiksel tüm değerlerin popülasyon varyansını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir koleksiyon (`Double`).<br /><br /> **Dönüş değeri**<br /><br /> A `Double`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 SqlClient destekleyen toplama işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcısı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Toplama işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[Toplama işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[Toplama işlevleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Toplu Kurallı İşlevler](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
