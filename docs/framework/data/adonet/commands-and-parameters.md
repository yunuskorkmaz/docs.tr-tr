---
title: Komutlar ve Parametreler
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 1d0c3adb56e5ff44b5c5e065ac040f25584a1946
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784960"
---
# <a name="commands-and-parameters"></a>Komutlar ve Parametreler
Bir veri kaynağına bağlantı kurulduktan sonra, komutları yürütebilir ve sonuçları bir <xref:System.Data.Common.DbCommand> nesne kullanarak veri kaynağından döndürebilirsiniz. Üzerinde çalıştığınız .NET Framework veri sağlayıcısı için komut oluşturucularından birini kullanarak bir komut oluşturabilirsiniz. Oluşturucular, veri kaynağı, <xref:System.Data.Common.DbConnection> nesne <xref:System.Data.Common.DbTransaction> veya nesne üzerinde yürütülecek bir SQL deyimsi gibi isteğe bağlı bağımsız değişkenler alabilir. Bu nesneleri komutun özellikleri olarak da yapılandırabilirsiniz. Ayrıca, <xref:System.Data.Common.DbConnection.CreateCommand%2A> bir `DbConnection` nesnenin yöntemini kullanarak belirli bir bağlantı için bir komut oluşturabilirsiniz. Komutu tarafından yürütülen SQL deyimleri <xref:System.Data.Common.DbCommand.CommandText%2A> özelliği kullanılarak yapılandırılabilir.  
  
 .NET Framework eklenen her .NET Framework veri sağlayıcısının bir `Command` nesnesi vardır. OLE DB için .NET Framework veri sağlayıcısı bir <xref:System.Data.OleDb.OleDbCommand> nesne içerir, veri sağlayıcısı için .NET Framework SQL Server bir <xref:System.Data.SqlClient.SqlCommand> nesnesi içerir, ODBC için .NET Framework veri sağlayıcısı bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleCommand> nesne içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Komut Yürütme](executing-a-command.md)  
 ADO.net `Command` nesnesini ve bir veri kaynağına karşı sorguları ve komutları yürütmek için nasıl kullanılacağını açıklar.  
  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](configuring-parameters-and-parameter-data-types.md)  
 Yön, veri `Command` türleri ve parametre sözdizimi dahil olmak üzere parametrelerle çalışmayı açıklar.  
  
 [CommandBuilders ile Komut Oluşturma](generating-commands-with-commandbuilders.md)  
 Tek tablo seçme komutu olan bir `DataAdapter` için otomatik olarak INSERT, Update ve DELETE komutlarını oluşturmak üzere komut oluşturucuların nasıl kullanılacağını açıklar.  
  
 [Veritabanından Tek Değer Alma](obtaining-a-single-value-from-a-database.md)  
 Bir veritabanı sorgusundan tek bir `ExecuteScalar` değer döndürmek için `Command` nesnesinin yönteminin nasıl kullanılacağını açıklar.  
  
 [Verileri Değiştirmek için Komutları Kullanma](using-commands-to-modify-data.md)  
 Saklı yordamları veya veri tanımlama dili (DDL) deyimlerini yürütmek için bir veri sağlayıcısının nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
