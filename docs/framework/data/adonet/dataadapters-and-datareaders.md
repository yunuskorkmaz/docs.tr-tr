---
title: DataAdapters ve DataReaders
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786643"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters ve DataReaders
Bir veritabanından salt okunurdur ve salt ileri bir veri akışı almak için ADO.NET **DataReader** 'ı kullanabilirsiniz. Sonuçlar sorgu yürütüldüğü için döndürülür ve **DataReader**'ın **Read** yöntemini kullanarak isteene kadar istemcideki ağ arabelleğine depolanır. **DataReader** 'ın kullanılması, hem verileri kullanılabilir duruma getirerek hem de (varsayılan olarak), bellekteki bir seferde yalnızca bir satır depolayarak sistem yükünü azaltarak uygulama performansını artırabilir.  
  
 Bir <xref:System.Data.Common.DataAdapter> veri kaynağından veri almak ve <xref:System.Data.DataSet>içindeki tabloları doldurmak için kullanılır. Ayrıca veri kaynağına `DataSet` geri yapılan değişiklikleri de çözer. `DataAdapter` , `DataAdapter` Bir veri `Connection` kaynağına bağlanmak için .NET Framework veri sağlayıcısının nesnesini kullanır ve veri kaynağındaki değişiklikleri almak ve verileri çözümlemek `Command` için nesneleri kullanır.  
  
 .NET Framework eklenen her .NET Framework <xref:System.Data.Common.DbDataReader> veri sağlayıcısının bir ve bir <xref:System.Data.Common.DbDataAdapter> nesnesi vardır: <xref:System.Data.OleDb.OleDbDataAdapter> OLE DB <xref:System.Data.OleDb.OleDbDataReader> için .NET Framework veri sağlayıcısı, SQL için .NET Framework veri sağlayıcısı. <xref:System.Data.SqlClient.SqlDataReader> Sunucu bir <xref:System.Data.Odbc.OdbcDataReader> <xref:System.Data.Odbc.OdbcDataAdapter> <xref:System.Data.OracleClient.OracleDataReader> ve bir nesnesiiçerir,ODBCiçin.NETFrameworkverisağlayıcısıbirvenesnesiiçerirveOracleiçin.NETFrameworkverisağlayıcısıbirveiçerir<xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.OracleClient.OracleDataAdapter> nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataReader Kullanarak Veri Alma](retrieving-data-using-a-datareader.md)  
 ADO.NET **DataReader** nesnesini ve bir veri kaynağından sonuçların akışını döndürmek için nasıl kullanılacağını açıklar.  
  
 [DataAdapter’dan bir DataSet Doldurma](populating-a-dataset-from-a-dataadapter.md)  
 ' I `DataSet` `DataAdapter`kullanarak bir tablo, sütun ve satır ile nasıl doldurulacağını açıklar.  
  
 [DataAdapter Parametreleri](dataadapter-parameters.md)  
 İçindeki bir sütunun içeriklerinin bir komut parametresine nasıl eşlenme `DataAdapter` dahil olmak üzere öğesinin komut özellikleriyle parametrelerin nasıl kullanılacağını açıklar. `DataSet`  
  
 [DataSet’e Var Olan Kısıtlamaları Ekleme](adding-existing-constraints-to-a-dataset.md)  
 ' A `DataSet`varolan kısıtlamaların nasıl ekleneceğini açıklar.  
  
 [DataAdapter DataTable ve DataColumn Eşlemeleri](dataadapter-datatable-and-datacolumn-mappings.md)  
 `DataTableMappings` '`ColumnMappings`Ninnasıl ayarlanacağını açıklar. `DataAdapter`  
  
 [Sorgu Sonucunu Sayfalama](paging-through-a-query-result.md)  
 Sorgunun sonuçlarını veri sayfaları olarak görüntülemenin bir örneğini sağlar.  
  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)  
 Veritabanına `DataSet` geri yapılan değişiklikleri çözümlemek `DataAdapter` için ' nin nasıl kullanılacağını açıklar.  
  
 [DataAdapter Olaylarını İşleme](handling-dataadapter-events.md)  
 Olayları `DataAdapter` ve bunların nasıl kullanılacağını açıklar.  
  
 [DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme](performing-batch-operations-using-dataadapters.md)  
 ' Den `DataSet`Güncelleştirme uygulanırken SQL Server gidiş dönüş sayısını azaltarak uygulama performansının nasıl geliştirileneceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
