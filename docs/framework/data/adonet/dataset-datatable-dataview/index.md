---
title: DataSets, DataTables ve DataViews
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4b5e81f415685d6ee3529c7e4f9d389e8017427e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203641"
---
# <a name="datasets-datatables-and-dataviews"></a>DataSets, DataTables ve DataViews
ADO.net <xref:System.Data.DataSet> , içerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. Bir <xref:System.Data.DataSet> , verileri içeren tablolar ve tablolar arasındaki ilişkiler dahil olmak üzere tüm veri kümesini temsil eder.  
  
 Bağımsız olarak veya birleşimine uygulanabilecek bir <xref:System.Data.DataSet>ile çalışmanın birkaç yolu vardır. Şunları yapabilirsiniz:  
  
- Programlı olarak <xref:System.Data.DataRelation>bir <xref:System.Data.DataTable> <xref:System.Data.Constraint> , veiçindevetablolarıverilerledoldurma.<xref:System.Data.DataSet>  
  
- ' İ kullanarak var olan bir `DataAdapter`ilişkisel veri kaynağından veri tabloları iledoldurun.<xref:System.Data.DataSet>  
  
- XML kullanarak <xref:System.Data.DataSet> içerikleri yükleyin ve kalıcı hale getirin. Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).  
  
 Türü kesin belirlenmiş <xref:System.Data.DataSet> bir XML Web hizmeti kullanılarak da taşıyabilirsiniz. Tasarımı, XML Web <xref:System.Data.DataSet> Hizmetleri kullanarak verileri aktarmak için ideal hale getirir. XML Web hizmetlerine genel bakış için bkz. [XML Web Hizmetleri 'Ne genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). XML Web hizmetinden alınan bir <xref:System.Data.DataSet> örnek için bkz. [XML Web hizmetinden veri kümesi](consuming-a-dataset-from-an-xml-web-service.md)kullanma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet Oluşturma](creating-a-dataset.md)  
 Bir <xref:System.Data.DataSet>örneğini oluşturmak için söz dizimini açıklar.  
  
 [DataSet’e DataTable Ekleme](adding-a-datatable-to-a-dataset.md)  
 ' A <xref:System.Data.DataSet>tablo ve sütun oluşturmayı ve eklemeyi açıklar.  
  
 [DataRelations Ekleme](adding-datarelations.md)  
 İçindeki tablolar arasında ilişki oluşturmayı açıklar <xref:System.Data.DataSet>.  
  
 [DataRelations İçinde Gezinme](navigating-datarelations.md)  
 Bir <xref:System.Data.DataSet> üst-alt ilişkisinin alt veya üst satırlarını döndürmek için içindeki tablolar arasındaki ilişkilerin nasıl kullanılacağını açıklar.  
  
 [DataSet İçeriklerini Birleştirme](merging-dataset-contents.md)  
 Bir <xref:System.Data.DataSet>, veya dizisinin içeriğinin başka bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>veya <xref:System.Data.DataRow> dizisinin içeriğini nasıl birleştirebileceğinizi açıklar.  
  
 [DataSet İçeriklerini Kopyalama](copying-dataset-contents.md)  
 Bir <xref:System.Data.DataSet> öğesinin, belirtilen verilerin yanı sıra şema içerebilen bir kopyasının nasıl oluşturulduğunu açıklar.  
  
 [DataSet Olaylarını İşleme](handling-dataset-events.md)  
 ' A <xref:System.Data.DataSet> ait olayları ve bunların nasıl kullanılacağını açıklar.  
  
 [Türü Belirtilmiş DataSets](typed-datasets.md)  
 Türü <xref:System.Data.DataSet> nelerin olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.  
  
 [DataTables](datatables.md)  
 Oluşturma <xref:System.Data.DataTable>, şema tanımlama ve verileri işleme işlemlerinin nasıl yapılacağını açıklar.  
  
 [DataTableReaders](datatablereaders.md)  
 Oluşturmayı ve kullanmayı <xref:System.Data.DataTableReader>açıklar.  
  
 [DataViews](dataviews.md)  
 Oluşturma ve `DataViews` bunlarla çalışmayı ve <xref:System.Data.DataView> olayları nasıl kullanacağınızı açıklar.  
  
 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 Bir veri kaynağı <xref:System.Data.DataSet> olarak XML ile nasıl etkileşime gireceğini açıklar ve bir <xref:System.Data.DataSet> XML verisi olarak içeriğini yükleme ve kalıcı hale getirme de dahildir.  
  
 [XML Web Hizmetinden DataSet Kullanma](consuming-a-dataset-from-an-xml-web-service.md)  
 Verileri aktarmak için kullanan bir <xref:System.Data.DataSet> XML Web hizmeti oluşturmayı açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET’teki Yenilikler](../whats-new.md)  
 ADO.NET ' de yeni olan özellikleri tanıtır.  
  
 [ADO.NET’e Genel Bakış](../ado-net-overview.md)  
 ADO.NET 'in tasarımına ve bileşenlerine bir giriş sağlar.  
  
 [DataAdapter’dan bir DataSet Doldurma](../populating-a-dataset-from-a-dataadapter.md)  
 Veri kaynağından veri içeren bir veri **kümesinin** nasıl yükleneceğini açıklar.  
  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../updating-data-sources-with-dataadapters.md)  
 Veri **kümesindeki** verilerde yapılan değişikliklerin veri kaynağına geri nasıl çözümleneceğini açıklar.  
  
 [DataSet’e Var Olan Kısıtlamaları Ekleme](../adding-existing-constraints-to-a-dataset.md)  
 Bir veri **kümesinin** birincil anahtar bilgileri ile bir veri kaynağından nasıl doldurulacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
