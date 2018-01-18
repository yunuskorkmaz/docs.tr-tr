---
title: "Veritabanı şema bilgileri alınıyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09a0ec444801d1fe2caccf9e25a68e3c6ae8f5c2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-database-schema-information"></a>Veritabanı şema bilgileri alınıyor
Şema bilgileri veritabanından alma şema bulma işlemi ile gerçekleştirilir. Şema bulma sağlar yönetilen sağlayıcıları bulmak ve veritabanı şeması hakkında bilgi döndürür olarak da bilinen istemek uygulamalar *meta veri*, belirli bir veritabanı. Farklı veritabanı şema öğeleri tablolar, sütunlar ve saklı yordamlar gibi şema koleksiyonlarına sunulur. Her bir şema koleksiyonu şema bilgileri kullanılan sağlayıcıya özgü çeşitli içerir.  
  
 .NET Framework yönetilen sağlayıcıları uygulayan her **GetSchema** yönteminde **bağlantı** sınıfı ve sunucudan döndürülen şema bilgileri **GetSchema**yöntemi gelen biçiminde bir <xref:System.Data.DataTable>. **GetSchema** dönmek için şema koleksiyonu belirtme ve döndürülen bilgi tutarını sınırlamak için isteğe bağlı parametreler sağlayan bir aşırı yüklenmiş yöntemin bir yöntemdir.  
  
 OLE DB, ODBC, Oracle ve SqlClient için .NET Framework veri sağlayıcıları sağlayan bir **GetSchemaTable** sütun meta verileri tanımlayan bir DataTable verir yöntemi **DataReader**.  
  
 Ayrıca OLE DB için .NET Framework veri sağlayıcısı kullanarak şema bilgileri sunan <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> yöntemi <xref:System.Data.OleDb.OleDbConnection> nesnesi. Bağımsız değişken **GetOleDbSchemaTable** geçen bir <xref:System.Data.OleDb.OleDbSchemaGuid> döndürmek için şema bilgileri tanımlar ve sütunları bu kısıtlamalar bir dizi döndürdü. **GetOleDbSchemaTable** döndüren bir <xref:System.Data.DataTable> istenen şema bilgileri ile doldurulur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [GetSchema ve Şema Koleksiyonları](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 Açıklar **GetSchema** yöntemi ve nasıl bu almak ve şema bilgilerini veritabanından kısıtlamak için kullanılabilir.  
  
 Şema kısıtlamaları  
 İle kullanılan şema kısıtlamaları açıklar **GetSchema**.  
  
 [Ortak Şema Koleksiyonları](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 Tüm .NET çerçevesi ile yönetilen sağlayıcılar tarafından desteklenen ortak şeması koleksiyonları tümünün açıklar.  
  
 [SQL Server Şema Koleksiyonları](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 SQL Server için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonu açıklar.  
  
 [Oracle Şema Koleksiyonları](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 Oracle için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonu açıklar.  
  
 [ODBC Şema Koleksiyonları](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 ODBC sürücüleri için şema koleksiyonları açıklar.  
  
 [OLE DB Şema Koleksiyonları](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 OLE DB sağlayıcıları için şema koleksiyonları açıklar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
