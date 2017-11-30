---
title: "Veri kümeleri, DataTable ve DataView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 642a81b926262fb8ea95234d90e4c1a0c49ea96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datasets-datatables-and-dataviews"></a>Veri kümeleri, DataTable ve DataView
ADO.NET <xref:System.Data.DataSet> içerdiği veri kaynağını bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlar veri bellekte gösterimidir. A <xref:System.Data.DataSet> sipariş ve tablolar arasındaki ilişkileri yanı sıra, verileri sınırlamak içeren tablolar dahil olmak üzere verileri eksiksiz bir kümesini temsil eder.  
  
 İle çalışmaya ilişkin birkaç yolu vardır bir <xref:System.Data.DataSet>, hangi uygulanabilir bağımsız olarak veya birlikte. Şunları yapabilirsiniz:  
  
-   Program aracılığıyla oluşturma bir <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, ve <xref:System.Data.Constraint> içinde bir <xref:System.Data.DataSet> ve veri tablolarıyla doldurabilirsiniz.  
  
-   Doldurmak <xref:System.Data.DataSet> var olan bir ilişkisel veri kaynağı kullanılarak verileri tablolar ile bir `DataAdapter`.  
  
-   Yük ve kalıcı <xref:System.Data.DataSet> XML kullanarak içeriği. Daha fazla bilgi için bkz: [XML kullanarak bir veri kümesinde](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Kesin türü belirtilmiş <xref:System.Data.DataSet> bir XML Web hizmetini kullanarak da taşınabilen. Tasarımını <xref:System.Data.DataSet> XML Web Hizmetleri kullanarak veri taşıma için ideal hale getirir. XML Web Hizmetleri genel bakış için bkz: [XML Web Hizmetleri genel bakış](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d). Kullanma örneği için bir <xref:System.Data.DataSet> bir XML Web hizmetinden bkz [bir XML Web hizmetinden veri kümesi kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir veri kümesi oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 Örneği oluşturmak için söz dizimi açıklanmıştır bir <xref:System.Data.DataSet>.  
  
 [DataTable bir veri kümesine ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 Oluşturma ve tablolar ve sütunlar ekleme açıklar bir <xref:System.Data.DataSet>.  
  
 [DataRelation ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 Tablolar arasındaki ilişkileri oluşturmayı açıklar bir <xref:System.Data.DataSet>.  
  
 [DataRelation gezinme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Tablolar arasındaki ilişkileri kullanmayı açıklar bir <xref:System.Data.DataSet> üst-alt ilişkinin bir alt veya üst satır döndürülecek.  
  
 [Veri kümesi içeriği birleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 İçeriği bir birleştirme açıklar <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> başka diziye <xref:System.Data.DataSet>.  
  
 [Veri kümesi içeriği kopyalama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 Bir kopyasını oluşturmayı açıklar bir <xref:System.Data.DataSet> belirtilen veri yanı sıra şema içerebilir.  
  
 [Veri kümesi olayları işleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 Olayları açıklayan bir <xref:System.Data.DataSet> ve bunları nasıl kullanacağınızı.  
  
 [Yazılan veri kümeleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 Hangi yazılmış anlatılmaktadır <xref:System.Data.DataSet> olduğu ve nasıl oluşturulacağı ve bunu kullanın.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable>Şeması Tanımlama ve verileri işlemek.  
  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Oluşturma ve kullanma açıklar bir <xref:System.Data.DataTableReader>.  
  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Oluşturma ve bunlarla çalışmak açıklar `DataViews` ve bunlarla çalışmak <xref:System.Data.DataView> olaylar.  
  
 [Bir veri kümesini XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Açıklar nasıl <xref:System.Data.DataSet> yükleme ve içeriği kalıcı yapma dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir <xref:System.Data.DataSet> XML verileri olarak.  
  
 [XML Web hizmetinden veri kümesi kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 Kullanan XML Web hizmeti oluşturmayı açıklar bir <xref:System.Data.DataSet> Aktarım verileri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET yenilikler nelerdir?](../../../../../docs/framework/data/adonet/whats-new.md)  
 ADO.NET yeni özellikler sunar.  
  
 [ADO.NET genel bakış](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Tasarım ve ADO.NET bileşenlerinin bir giriş sağlar.  
  
 [DataAdapter kümesinden doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Nasıl yükleneceğini açıklayan bir **DataSet** bir veri kaynağı ile.  
  
 [Veri kaynakları ile DataAdapters güncelleştiriliyor](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Verilerde değişiklik çözümlemeyi açıklar bir **DataSet** veri kaynağına geri.  
  
 [Varolan kısıtlamaları bir veri kümesine ekleme](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Doldurmak nasıl açıklar bir **DataSet** bir veri kaynağından birincil anahtar bilgileri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
