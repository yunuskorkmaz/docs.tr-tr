---
title: Veritabanı şema bilgilerini alma
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 8a076ca792ee1b4b2194b778c51fefbd0bb19bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494034"
---
# <a name="retrieving-database-schema-information"></a>Veritabanı şema bilgilerini alma
Veritabanı şema bilgilerini alma şema bulma işlemi ile gerçekleştirilir. Şema bulma sağlayan yönetilen sağlayıcıları bulun ve veritabanı şeması hakkında bilgi döndürür olarak da bilinen istemek uygulamaları *meta verileri*, belirli bir veritabanı. Tablolar, sütunlar ve saklı yordamlar gibi farklı veritabanı şeması öğeleri şema koleksiyonları sunulur. Şema bilgileri kullanılan sağlayıcıya özgü çeşitli her şema koleksiyonu içerir.  
  
 Her .NET Framework yönetilen sağlayıcıları uygulama **GetSchema** yönteminde **bağlantı** sınıfı ve öğesinden döndürülen şema bilgileri **GetSchema**yöntemi gelen biçiminde bir <xref:System.Data.DataTable>. **GetSchema** döndürmek için şema koleksiyonu belirtme ve döndürülen bilgi tutarını sınırlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş yöntem yöntemidir.  
  
 .NET Framework veri sağlayıcıları için OLE DB, ODBC, Oracle ve SqlClient sağlayan bir **GetSchemaTable** sütun meta verileri tanımlayan bir DataTable döndüren yöntem **DataReader**.  
  
 Ayrıca OLE DB için .NET Framework veri sağlayıcısı kullanarak şema bilgileri sunan <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> yöntemi <xref:System.Data.OleDb.OleDbConnection> nesne. Bağımsız değişken **GetOleDbSchemaTable** götüren bir <xref:System.Data.OleDb.OleDbSchemaGuid> döndürmek için şema bilgileri tanımlayan ve bu kısıtlamaları bir dizi sütun döndürdü. **GetOleDbSchemaTable** döndürür bir <xref:System.Data.DataTable> istenen şemanın bilgilerle doldurulur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [GetSchema ve Şema Koleksiyonları](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 Açıklar **GetSchema** yöntemi ve nasıl, almak ve şema bilgilerini veritabanından kısıtlamak için kullanılabilir.  
  
 Şema kısıtlamaları  
 İle kullanılan şema kısıtlamaları açıklamaktadır **GetSchema**.  
  
 [Ortak Şema Koleksiyonları](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 Tüm tüm .NET Framework yönetilen sağlayıcı tarafından desteklenen ortak şema koleksiyonları açıklar.  
  
 [SQL Server Şema Koleksiyonları](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 SQL Server için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonu açıklar.  
  
 [Oracle Şema Koleksiyonları](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 Oracle için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonu açıklar.  
  
 [ODBC Şema Koleksiyonları](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 ODBC sürücüleri için şema koleksiyonları açıklar.  
  
 [OLE DB Şema Koleksiyonları](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 OLE DB sağlayıcısı için şema koleksiyonları açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Açıklar **GetSchema** yöntemi <xref:System.Data.Common.DbConnection> sınıfı.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Açıklar **GetSchema** yöntemi <xref:System.Data.Odbc.OdbcConnection> sınıfı.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Açıklar **GetSchema** yöntemi <xref:System.Data.OleDb.OleDbConnection> sınıfı.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Açıklar **GetSchema** yöntemi <xref:System.Data.OracleClient.OracleConnection> sınıfı.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Açıklar **GetSchema** yöntemi <xref:System.Data.SqlClient.SqlConnection> sınıfı.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Açıklar **GetSchemaTable** yöntemi <xref:System.Data.Common.DbDataReader> sınıfı.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Açıklar **GetSchemaTable** yöntemi <xref:System.Data.Odbc.OdbcDataReader> sınıfı.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Açıklar **GetSchemaTable** yöntemi <xref:System.Data.OleDb.OleDbDataReader> sınıfı.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Açıklar **GetSchemaTable** yöntemi <xref:System.Data.OracleClient.OracleDataReader> sınıfı.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Açıklar **GetSchemaTable** yöntemi <xref:System.Data.SqlClient.SqlDataReader> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
