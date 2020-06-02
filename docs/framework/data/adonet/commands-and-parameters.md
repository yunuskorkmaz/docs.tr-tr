---
title: Komutlar ve Parametreler
description: Komutları çalıştırmak ve bir veri kaynağından sonuçları döndürmek için her bir .NET Framework veri sağlayıcısı için komut nesnelerini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: c0baec4d6c3984cb50178c3aa7f9ed3878055bb6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287148"
---
# <a name="commands-and-parameters"></a>Komutlar ve Parametreler
Bir veri kaynağına bağlantı kurulduktan sonra, komutları yürütebilir ve sonuçları bir nesne kullanarak veri kaynağından döndürebilirsiniz <xref:System.Data.Common.DbCommand> . Üzerinde çalıştığınız .NET Framework veri sağlayıcısı için komut oluşturucularından birini kullanarak bir komut oluşturabilirsiniz. Oluşturucular, veri kaynağı, nesne veya nesne üzerinde yürütülecek bir SQL deyimsi gibi isteğe bağlı bağımsız değişkenler alabilir <xref:System.Data.Common.DbConnection> <xref:System.Data.Common.DbTransaction> . Bu nesneleri komutun özellikleri olarak da yapılandırabilirsiniz. Ayrıca, bir nesnenin yöntemini kullanarak belirli bir bağlantı için bir komut oluşturabilirsiniz <xref:System.Data.Common.DbConnection.CreateCommand%2A> `DbConnection` . Komutu tarafından yürütülen SQL deyimleri özelliği kullanılarak yapılandırılabilir <xref:System.Data.Common.DbCommand.CommandText%2A> .  
  
 .NET Framework eklenen her .NET Framework veri sağlayıcısının bir `Command` nesnesi vardır. OLE DB için .NET Framework Veri Sağlayıcısı bir nesne içerir, Veri Sağlayıcısı .NET Framework SQL Server bir nesne içerir, ODBC için .NET Framework veri sağlayıcısı bir nesne içerir <xref:System.Data.OleDb.OleDbCommand> <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.Odbc.OdbcCommand> ve Oracle için .NET Framework veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleCommand> nesnesi içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Komut Yürütme](executing-a-command.md)  
 ADO.NET `Command` nesnesini ve bir veri kaynağına karşı sorguları ve komutları yürütmek için nasıl kullanılacağını açıklar.  
  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](configuring-parameters-and-parameter-data-types.md)  
 `Command`Yön, veri türleri ve parametre sözdizimi dahil olmak üzere parametrelerle çalışmayı açıklar.  
  
 [CommandBuilders ile Komut Oluşturma](generating-commands-with-commandbuilders.md)  
 Tek tablo seçme komutu olan bir için otomatik olarak INSERT, UPDATE ve DELETE komutlarını oluşturmak üzere komut oluşturucuların nasıl kullanılacağını açıklar `DataAdapter` .  
  
 [Veritabanından Tek Değer Alma](obtaining-a-single-value-from-a-database.md)  
 Bir `ExecuteScalar` `Command` veritabanı sorgusundan tek bir değer döndürmek için nesnesinin yönteminin nasıl kullanılacağını açıklar.  
  
 [Verileri Değiştirmek için Komutları Kullanma](using-commands-to-modify-data.md)  
 Saklı yordamları veya veri tanımlama dili (DDL) deyimlerini yürütmek için bir veri sağlayıcısının nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [Bir veri kaynağına bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
