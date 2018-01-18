---
title: DataAdapters ve DataReader
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3a7ce8787dec2f80ba04bef08c5ac355a907feaf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters ve DataReader
ADO.NET kullanabilirsiniz **DataReader** bir veritabanından veri salt okunur, yalnızca ileri akışı alınamadı. Sonuçları sorgu yürütür ve bunları isteyen kadar istemci üzerinde ağ arabelleği depolanan gibi döndürülür kullanarak **okuma** yöntemi **DataReader**. Kullanarak **DataReader** hem kullanılabilir olduğunda hemen verileri alarak ve (varsayılan) uygulama performansını artırabilirsiniz sistem yükünü azaltma bellekte bir anda yalnızca bir satır depolama.  
  
 A <xref:System.Data.Common.DataAdapter> bir veri kaynağından veri almak ve tablolarına doldurmak için kullanılan bir <xref:System.Data.DataSet>. `DataAdapter` Yapılan değişiklikleri de çözümler `DataSet` veri kaynağına geri. `DataAdapter` Kullanan `Connection` nesne bir veri kaynağı ve onu bağlanmak için .NET Framework Veri Sağlayıcısı'nın kullandığı `Command` verilerin alınacağı ve veri kaynağına değişiklikler çözümlemek için nesneleri.  
  
 .NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbDataReader> ve <xref:System.Data.Common.DbDataAdapter> nesnesi: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbDataReader> ve bir <xref:System.Data.OleDb.OleDbDataAdapter> nesnesi, SQL için .NET Framework veri sağlayıcısı Sunucuyu içeren bir <xref:System.Data.SqlClient.SqlDataReader> ve <xref:System.Data.SqlClient.SqlDataAdapter> nesne ODBC için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.Odbc.OdbcDataReader> ve bir <xref:System.Data.Odbc.OdbcDataAdapter> nesne ve Oracle için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OracleClient.OracleDataReader> ve bir <xref:System.Data.OracleClient.OracleDataAdapter> nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataReader Kullanarak Veri Alma](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 ADO.NET açıklar **DataReader** nesne ve nasıl sonuçlarının bir akış veri kaynağından döndürmek için kullanılır.  
  
 [DataAdapter’dan bir DataSet Doldurma](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Doldurmak nasıl açıklar bir `DataSet` tabloları, sütunları ve satırları kullanarak bir `DataAdapter`.  
  
 [DataAdapter Parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Parametreler ile komut özelliklerini kullanmayı açıklar bir `DataAdapter` bir sütunun içeriğine eşleme de dahil olmak üzere bir `DataSet` için bir komut parametresi.  
  
 [DataSet’e Var Olan Kısıtlamaları Ekleme](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Varolan kısıtlamalara eklemeyi açıklar bir `DataSet`.  
  
 [DataAdapter DataTable ve DataColumn Eşlemeleri](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Nasıl ayarlanacağını açıklar `DataTableMappings` ve `ColumnMappings` için bir `DataAdapter`.  
  
 [Sorgu Sonucunu Sayfalama](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Bir sorgunun sonuçlarını veri sayfaları olarak görüntüleme ilişkin bir örnek verilmektedir.  
  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Nasıl kullanılacağını açıklar bir `DataAdapter` değişiklikleri çözümlemek için bir `DataSet` veritabanına.  
  
 [DataAdapter Olaylarını İşleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Açıklar `DataAdapter` olaylar ve bunları nasıl kullanacağınızı.  
  
 [DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Güncelleştirmeleri uygularken SQL Server'a gidiş dönüş sayısını azaltarak geliştirerek uygulama performansı açıklar `DataSet`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
