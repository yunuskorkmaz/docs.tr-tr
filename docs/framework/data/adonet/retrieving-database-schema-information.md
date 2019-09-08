---
title: Veritabanı Şema Bilgilerini Alma
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782731"
---
# <a name="retrieving-database-schema-information"></a>Veritabanı Şema Bilgilerini Alma
Şema bulma işlemi ile bir veritabanından şema bilgileri alma işlemi gerçekleştirilir. Şema bulma, uygulamaların belirli bir veritabanının *meta verileri*olarak da bilinen veritabanı şeması hakkındaki bilgileri bulmasını ve döndürmesini ister. Tablolar, sütunlar ve saklı yordamlar gibi farklı veritabanı şeması öğeleri, şema koleksiyonları aracılığıyla sunulur. Her şema koleksiyonu, kullanılmakta olan sağlayıcıya özgü çeşitli şema bilgilerini içerir.  
  
 .NET Framework yönetilen sağlayıcıların her biri, **bağlantı** sınıfında **GetSchema** yöntemini uygular ve **GetSchema** yönteminden döndürülen şema bilgileri bir <xref:System.Data.DataTable>biçiminde gelir. **GetSchema** yöntemi, döndürülecek şema koleksiyonunu belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş bir yöntemdir.  
  
 OLE DB, ODBC, Oracle ve SqlClient .NET Framework veri sağlayıcıları, **DataReader**'ın sütun meta verilerini açıklayan bir DataTable döndüren **GetSchemaTable** yöntemi sağlar.  
  
 OLE DB için .NET Framework veri sağlayıcısı, <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> <xref:System.Data.OleDb.OleDbConnection> nesne yöntemini kullanarak şema bilgilerini de kullanıma sunar. Bağımsız değişkenler olarak, **GetOleDbSchemaTable** , <xref:System.Data.OleDb.OleDbSchemaGuid> Döndürülecek şema bilgilerini ve döndürülen sütunlara yönelik bir dizi kısıtlamayı belirleyen bir kullanır. **GetOleDbSchemaTable** , istenen <xref:System.Data.DataTable> şema bilgileriyle doldurulmuş bir değer döndürüyor.  
  
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
 <xref:System.Data.Common.DbConnection> Sınıfının **GetSchema** metodunu açıklar.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <xref:System.Data.Odbc.OdbcConnection> Sınıfının **GetSchema** metodunu açıklar.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <xref:System.Data.OleDb.OleDbConnection> Sınıfının **GetSchema** metodunu açıklar.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <xref:System.Data.OracleClient.OracleConnection> Sınıfının **GetSchema** metodunu açıklar.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <xref:System.Data.SqlClient.SqlConnection> Sınıfının **GetSchema** metodunu açıklar.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <xref:System.Data.Common.DbDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <xref:System.Data.Odbc.OdbcDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <xref:System.Data.OleDb.OleDbDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <xref:System.Data.OracleClient.OracleDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <xref:System.Data.SqlClient.SqlDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
