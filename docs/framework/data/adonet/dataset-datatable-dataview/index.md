---
title: DataSets, DataTables ve DataViews
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 9c57f75dd94f3fbda74c13a5d5773825051fe416
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105735"
---
# <a name="datasets-datatables-and-dataviews"></a>DataSets, DataTables ve DataViews
ADO.NET <xref:System.Data.DataSet> içerdiği veri kaynağını bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan veri bellekte gösterimidir. A <xref:System.Data.DataSet> sipariş ve tablolar arasındaki ilişkileri yanı sıra, verileri sınırlamak içeren tablolar da dahil olmak üzere veri eksiksiz bir kümesini temsil eder.  
  
 İle çalışmaya ilişkin birkaç şekilde bir <xref:System.Data.DataSet>, hangi uygulanabilir bağımsız olarak veya birlikte. Şunları yapabilirsiniz:  
  
-   Program aracılığıyla oluşturma bir <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, ve <xref:System.Data.Constraint> içinde bir <xref:System.Data.DataSet> ve tabloları verilerle doldurun.  
  
-   Doldurma <xref:System.Data.DataSet> var olan bir ilişkisel veri kaynağı kullanarak veri tabloları içeren bir `DataAdapter`.  
  
-   Yük ve kalıcı <xref:System.Data.DataSet> kullanarak XML içeriği. Daha fazla bilgi için [kullanarak bir veri kümesi XML'de](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Türü kesin belirlenmiş <xref:System.Data.DataSet> kullanarak bir XML Web Hizmeti ayrıca taşınabilen. Tasarımını <xref:System.Data.DataSet> XML Web Hizmetleri ile veri taşıma için ideal hale getirir. XML Web Hizmetleri genel bakış için bkz. [XML Web Hizmetleri genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). Kullanan bir örnek için bir <xref:System.Data.DataSet> bir XML Web hizmetinden bkz [bir XML Web hizmetinden DataSet kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 Örneği oluşturmak için söz dizimini açıklar bir <xref:System.Data.DataSet>.  
  
 [DataSet’e DataTable Ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 Oluşturma ve tablolar ve sütunlar ekleme açıklar bir <xref:System.Data.DataSet>.  
  
 [DataRelations Ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 Tablolar arasındaki ilişkileri oluşturmayı açıklar bir <xref:System.Data.DataSet>.  
  
 [DataRelations İçinde Gezinme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Tablolar arasındaki ilişkileri açıklar bir <xref:System.Data.DataSet> bir üst-alt ilişkinin alt veya üst satırları döndürür.  
  
 [DataSet İçeriklerini Birleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 İçeriği bir birleştirme işlemini açıklamaktadır <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> başka bir diziye <xref:System.Data.DataSet>.  
  
 [DataSet İçeriklerini Kopyalama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 Bir kopyasını oluşturmayı açıklar bir <xref:System.Data.DataSet> belirtilen verilerin yanı sıra şema içerebilir.  
  
 [DataSet Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 Olayları açıklayan bir <xref:System.Data.DataSet> ve bunların nasıl kullanıldığı.  
  
 [Türü Belirtilmiş DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 Hangi yazılmış anlatılmaktadır <xref:System.Data.DataSet> olduğu ve nasıl oluşturup kullanabilirsiniz.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable>şema tanımlayabilir ve verilerini işleme.  
  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Nasıl oluşturup kullanacağınızı açıklayan bir <xref:System.Data.DataTableReader>.  
  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Oluşturma ve bunlarla çalışmak açıklar `DataViews` ve çalışmak <xref:System.Data.DataView> olayları.  
  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Açıklayan nasıl <xref:System.Data.DataSet> yükleniyor ve içeriğini kalıcı dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir <xref:System.Data.DataSet> XML verileri olarak.  
  
 [XML Web Hizmetinden DataSet Kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 Kullanan bir XML Web hizmeti oluşturmayı açıklar bir <xref:System.Data.DataSet> aktarım veri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET’teki Yenilikler](../../../../../docs/framework/data/adonet/whats-new.md)  
 ADO.NET yeni özellikleri tanıtır.  
  
 [ADO.NET’e Genel Bakış](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Tasarım ve ADO.NET bileşenlerini tanıtır.  
  
 [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Nasıl yükleneceğini açıklayan bir **veri kümesi** bir veri kaynağı ile.  
  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Veriler üzerinde değişiklikler çözümlemeyi açıklar bir **veri kümesi** veri kaynağına geri dönün.  
  
 [DataSet’e Var Olan Kısıtlamaları Ekleme](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Nasıl doldurulacağını açıklar bir **veri kümesi** birincil anahtar bilgilerini bir veri kaynağından.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
