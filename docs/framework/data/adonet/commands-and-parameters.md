---
title: Komutlar ve parametreler
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 8e476d68b60272d944eecfe585fd77d8a7a8f08c
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46527996"
---
# <a name="commands-and-parameters"></a>Komutlar ve parametreler
Bir veri kaynağı ile bağlantı kurulduktan sonra komutları yürütmek ve sonuçları döndürür kullanarak veri kaynağına bir <xref:System.Data.Common.DbCommand> nesne. Bir komut oluşturucular çalışıyorsanız ve .NET Framework veri sağlayıcısı kullanarak bir komut oluşturabilirsiniz. Oluşturucular, veri kaynağında yürütmek için bir SQL deyimi gibi isteğe bağlı bağımsız değişkenlere gerçekleştirebileceğiniz bir <xref:System.Data.Common.DbConnection> nesnesi veya bir <xref:System.Data.Common.DbTransaction> nesne. Bu gibi durumlarda, bu nesneleri ayrıca komut özellikleri olarak yapılandırabilirsiniz. Ayrıca belirli bir bağlantı kullanarak bir komut oluşturun <xref:System.Data.Common.DbConnection.CreateCommand%2A> yöntemi bir `DbConnection` nesne. Komutu tarafından yürütülen SQL deyimini kullanarak yapılandırılabilir <xref:System.Data.Common.DbCommand.CommandText%2A> özelliği.  
  
 .NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir `Command` nesne. OLE DB için .NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.OleDb.OleDbCommand> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlCommand> nesnesi, ODBC için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcısı'nı içeren bir <xref:System.Data.OracleClient.OracleCommand> nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Komut Yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)  
 ADO.NET açıklar `Command` nesne ve nasıl sorgular ve veri kaynaklarında komutları yürütmek için kullanılır.  
  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 İle çalışmayı açıklar `Command` yönü, veri türleri ve parametre söz dizimi de dahil olmak üzere parametreleri.  
  
 [CommandBuilders ile Komut Oluşturma](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 Komut oluşturucular için INSERT, UPDATE ve DELETE komutlarını otomatik olarak oluşturmak için kullanmayı açıklar bir `DataAdapter` olan tek tablolu bir SELECT komutu.  
  
 [Veritabanından Tek Değer Alma](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 Nasıl kullanılacağını açıklar `ExecuteScalar` yöntemi bir `Command` tek bir değer bir veritabanı sorgusundan döndürülecek nesne.  
  
 [Verileri Değiştirmek için Komutları Kullanma](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 Saklı yordamları ya da veri tanımlama dili (DDL) deyimleri yürütmek için veri sağlayıcısı kullanmayı açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
