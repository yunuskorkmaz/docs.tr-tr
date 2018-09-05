---
title: DataAdapters ve DataReaders
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 6e711b11ef9a3eca53806b825f1e721169ab662d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516783"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters ve DataReaders
ADO.NET kullanarak **DataReader** bir veritabanından veri salt okunur, salt iletme akışını almak için. Sonuçları döndüren sorguyu yürütür ve bunları isteyen kadar istemci üzerinde ağ arabellekteki depolanır kullanarak **okuma** yöntemi **DataReader**. Kullanarak **DataReader** hem kullanılabilir duruma geldiği veri alarak ve (varsayılan) uygulama performansını artırabilir sistem yükünü azaltarak bellekte bir anda yalnızca bir satır depolama.  
  
 A <xref:System.Data.Common.DataAdapter> bir veri kaynağından veri alabilir ve tablolarına doldurmak için kullanılan bir <xref:System.Data.DataSet>. `DataAdapter` Yapılan değişiklikleri de çözümler `DataSet` veri kaynağına geri dönün. `DataAdapter` Kullanan `Connection` nesne veri kaynağı ve bu bağlantı için .NET Framework Veri Sağlayıcısı'nın kullandığı `Command` verileri almak ve değişiklikleri veri kaynağına çözmek için nesneleri.  
  
 .NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbDataReader> ve <xref:System.Data.Common.DbDataAdapter> nesne: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbDataReader> ve bir <xref:System.Data.OleDb.OleDbDataAdapter> nesne, SQL için .NET Framework veri sağlayıcısı Server içeren bir <xref:System.Data.SqlClient.SqlDataReader> ve <xref:System.Data.SqlClient.SqlDataAdapter> nesnesi, ODBC için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.Odbc.OdbcDataReader> ve <xref:System.Data.Odbc.OdbcDataAdapter> nesne ve Oracle için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OracleClient.OracleDataReader> ve bir <xref:System.Data.OracleClient.OracleDataAdapter> nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataReader Kullanarak Veri Alma](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 ADO.NET açıklar **DataReader** nesnesi ve bir veri kaynağından bir akışa sonuçlarının döndürmek için kullanma.  
  
 [DataAdapter’dan bir DataSet Doldurma](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Nasıl doldurulacağını açıklar bir `DataSet` tabloları, sütunları ve satırları kullanarak ile bir `DataAdapter`.  
  
 [DataAdapter Parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Parametreler ile komut özelliklerini kullanmayı açıklar bir `DataAdapter` bir sütunda içeriğini eşlemeyle ilgili bilgi de dahil olmak üzere bir `DataSet` için komut parametresi.  
  
 [DataSet’e Var Olan Kısıtlamaları Ekleme](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Mevcut kısıtlamalar eklemeyi açıklar bir `DataSet`.  
  
 [DataAdapter DataTable ve DataColumn Eşlemeleri](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Nasıl ayarlanacağını açıklar `DataTableMappings` ve `ColumnMappings` için bir `DataAdapter`.  
  
 [Sorgu Sonucunu Sayfalama](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Bir sorgunun sonuçlarını veri sayfasını görüntüleme bir örnek sağlar.  
  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Nasıl kullanılacağını açıklayan bir `DataAdapter` değişiklikleri çözmek için bir `DataSet` veritabanına.  
  
 [DataAdapter Olaylarını İşleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Açıklar `DataAdapter` olayları ve bunların nasıl kullanıldığı.  
  
 [DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Güncelleştirmeleri uygularken SQL Server gidiş dönüş sayısını azaltarak geliştirerek uygulama performansını açıklar `DataSet`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
