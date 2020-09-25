---
title: Veritabanı Şema Bilgilerini Alma
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: c0aaadc82771d1c2a36d797bc157d88b8d3cacdc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177364"
---
# <a name="retrieving-database-schema-information"></a>Veritabanı Şema Bilgilerini Alma

Şema bulma işlemi ile bir veritabanından şema bilgileri alma işlemi gerçekleştirilir. Şema bulma, uygulamaların belirli bir veritabanının *meta verileri*olarak da bilinen veritabanı şeması hakkındaki bilgileri bulmasını ve döndürmesini ister. Tablolar, sütunlar ve saklı yordamlar gibi farklı veritabanı şeması öğeleri, şema koleksiyonları aracılığıyla sunulur. Her şema koleksiyonu, kullanılmakta olan sağlayıcıya özgü çeşitli şema bilgilerini içerir.  
  
 .NET Framework yönetilen sağlayıcıların her biri, **bağlantı** sınıfında **GetSchema** yöntemini uygular ve **GetSchema** yönteminden döndürülen şema bilgileri bir biçiminde gelir <xref:System.Data.DataTable> . **GetSchema** yöntemi, döndürülecek şema koleksiyonunu belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş bir yöntemdir.  
  
 OLE DB, ODBC, Oracle ve SqlClient .NET Framework veri sağlayıcıları, **DataReader**'ın sütun meta verilerini açıklayan bir DataTable döndüren **GetSchemaTable** yöntemi sağlar.  
  
 OLE DB için .NET Framework Veri Sağlayıcısı, nesne yöntemini kullanarak şema bilgilerini de kullanıma sunar <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> <xref:System.Data.OleDb.OleDbConnection> . Bağımsız değişkenler olarak, **GetOleDbSchemaTable** , <xref:System.Data.OleDb.OleDbSchemaGuid> Döndürülecek şema bilgilerini ve döndürülen sütunlara yönelik bir dizi kısıtlamayı belirleyen bir kullanır. **GetOleDbSchemaTable** <xref:System.Data.DataTable> , istenen şema bilgileriyle doldurulmuş bir değer döndürüyor.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [GetSchema ve Şema Koleksiyonları](getschema-and-schema-collections.md)  
 **GetSchema** yöntemini ve bir veritabanından şema bilgilerini almak ve kısıtlamak için nasıl kullanılabileceğini açıklar.  
  
 Şema Kısıtlamaları  
 **GetSchema**ile kullanılabilen şema kısıtlamalarını açıklar.  
  
 [Ortak Şema Koleksiyonları](common-schema-collections.md)  
 Tüm .NET Framework yönetilen sağlayıcılar tarafından desteklenen tüm ortak şema koleksiyonlarını açıklar.  
  
 [SQL Server Şema Koleksiyonları](sql-server-schema-collections.md)  
 SQL Server için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonunu açıklar.  
  
 [Oracle Şema Koleksiyonları](oracle-schema-collections.md)  
 Oracle için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonunu açıklar.  
  
 [ODBC Şema Koleksiyonları](odbc-schema-collections.md)  
 ODBC sürücüleri için şema koleksiyonlarını açıklar.  
  
 [OLE DB Şema Koleksiyonları](ole-db-schema-collections.md)  
 OLE DB sağlayıcıları için şema koleksiyonlarını açıklar.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.Common.DbConnection> .  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.Odbc.OdbcConnection> .  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.OleDb.OleDbConnection> .  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.OracleClient.OracleConnection> .  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.SqlClient.SqlConnection> .  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.Common.DbDataReader> .  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.Odbc.OdbcDataReader> .  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.OleDb.OleDbDataReader> .  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.OracleClient.OracleDataReader> .  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.SqlClient.SqlDataReader> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
