---
title: DataAdapters ve DataReaders
description: Bir veritabanından veri alan ve veri kaynağından veri alan ve bir veri kümesini dolduran ADO.NET DataReader hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 17463d65266baa53521bed9603c8abd96923277b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286979"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters ve DataReaders
Bir veritabanından salt okunurdur ve salt ileri bir veri akışı almak için ADO.NET **DataReader** 'ı kullanabilirsiniz. Sonuçlar sorgu yürütüldüğü için döndürülür ve **DataReader**'ın **Read** yöntemini kullanarak isteene kadar istemcideki ağ arabelleğine depolanır. **DataReader** 'ın kullanılması, hem verileri kullanılabilir duruma getirerek hem de (varsayılan olarak), bellekteki bir seferde yalnızca bir satır depolayarak sistem yükünü azaltarak uygulama performansını artırabilir.  
  
 Bir <xref:System.Data.Common.DataAdapter> veri kaynağından veri almak ve içindeki tabloları doldurmak için kullanılır <xref:System.Data.DataSet> . `DataAdapter`Ayrıca veri kaynağına geri yapılan değişiklikleri de çözer `DataSet` . , `DataAdapter` `Connection` Bir veri kaynağına bağlanmak için .NET Framework veri sağlayıcısının nesnesini kullanır ve veri `Command` kaynağındaki değişiklikleri almak ve verileri çözümlemek için nesneleri kullanır.  
  
 .NET Framework eklenen her .NET Framework veri sağlayıcısının bir ve bir nesnesi vardır <xref:System.Data.Common.DbDataReader> <xref:System.Data.Common.DbDataAdapter> : OLE DB için .NET Framework veri sağlayıcısı bir ve nesnesi içeriyorsa, .NET Framework için veri sağlayıcısı SQL Server bir ve nesnesi Içerir ve <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.OleDb.OleDbDataAdapter> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.Odbc.OdbcDataReader> <xref:System.Data.Odbc.OdbcDataAdapter> Oracle için <xref:System.Data.OracleClient.OracleDataReader> <xref:System.Data.OracleClient.OracleDataAdapter> .NET Framework veri sağlayıcısı, ve bir nesnesi içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataReader Kullanarak Veri Alma](retrieving-data-using-a-datareader.md)  
 ADO.NET **DataReader** nesnesini ve bir veri kaynağından sonuçların akışını döndürmek için nasıl kullanılacağını açıklar.  
  
 [DataAdapter’dan bir DataSet Doldurma](populating-a-dataset-from-a-dataadapter.md)  
 ' `DataSet` I kullanarak bir tablo, sütun ve satır ile nasıl doldurulacağını açıklar `DataAdapter` .  
  
 [DataAdapter Parametreleri](dataadapter-parameters.md)  
 `DataAdapter`İçindeki bir sütunun içeriklerinin bir komut parametresine nasıl eşlenme dahil olmak üzere öğesinin komut özellikleriyle parametrelerin nasıl kullanılacağını açıklar `DataSet` .  
  
 [DataSet’e Var Olan Kısıtlamaları Ekleme](adding-existing-constraints-to-a-dataset.md)  
 ' A varolan kısıtlamaların nasıl ekleneceğini açıklar `DataSet` .  
  
 [DataAdapter DataTable ve DataColumn Eşlemeleri](dataadapter-datatable-and-datacolumn-mappings.md)  
 ' Nin nasıl ayarlanacağını açıklar `DataTableMappings` `ColumnMappings` `DataAdapter` .  
  
 [Sorgu Sonucunu Sayfalama](paging-through-a-query-result.md)  
 Sorgunun sonuçlarını veri sayfaları olarak görüntülemenin bir örneğini sağlar.  
  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)  
 `DataAdapter`Veritabanına geri yapılan değişiklikleri çözümlemek için ' nin nasıl kullanılacağını açıklar `DataSet` .  
  
 [DataAdapter Olaylarını İşleme](handling-dataadapter-events.md)  
 `DataAdapter`Olayları ve bunların nasıl kullanılacağını açıklar.  
  
 [DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme](performing-batch-operations-using-dataadapters.md)  
 ' Den Güncelleştirme uygulanırken SQL Server gidiş dönüş sayısını azaltarak uygulama performansının nasıl geliştirileneceğini açıklar `DataSet` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir veri kaynağına bağlanma](connecting-to-a-data-source.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
