---
title: DataSets, DataTables ve DataViews
description: Tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimi olan ADO.NET veri kümesiyle çalışmanın birkaç yolunu öğrenin.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286901"
---
# <a name="datasets-datatables-and-dataviews"></a>DataSets, DataTables ve DataViews
ADO.NET, <xref:System.Data.DataSet> içerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. Bir, <xref:System.Data.DataSet> verileri içeren tablolar ve tablolar arasındaki ilişkiler dahil olmak üzere tüm veri kümesini temsil eder.  
  
 Bağımsız olarak veya birleşimine uygulanabilecek bir ile çalışmanın birkaç yolu vardır <xref:System.Data.DataSet> . Seçenekleriniz şunlardır:  
  
- Programlı olarak <xref:System.Data.DataTable> bir, <xref:System.Data.DataRelation> ve <xref:System.Data.Constraint> içinde ve <xref:System.Data.DataSet> tabloları verilerle doldurma.  
  
- ' İ <xref:System.Data.DataSet> kullanarak var olan bir ilişkisel veri kaynağından veri tabloları ile doldurun `DataAdapter` .  
  
- XML kullanarak içerikleri yükleyin ve kalıcı hale getirin <xref:System.Data.DataSet> . Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).  
  
 Türü kesin belirlenmiş bir <xref:System.Data.DataSet> XML Web hizmeti kullanılarak da taşıyabilirsiniz. Tasarımı, <xref:System.Data.DataSet> XML Web Hizmetleri kullanarak verileri aktarmak için ideal hale getirir. XML Web hizmetlerine genel bakış için bkz. [XML Web Hizmetleri 'Ne genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). <xref:System.Data.DataSet>XML Web hizmetinden alınan bir örnek için bkz. [XML Web hizmetinden veri kümesi](consuming-a-dataset-from-an-xml-web-service.md)kullanma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet Oluşturma](creating-a-dataset.md)  
 Bir örneğini oluşturmak için söz dizimini açıklar <xref:System.Data.DataSet> .  
  
 [DataSet’e DataTable Ekleme](adding-a-datatable-to-a-dataset.md)  
 ' A tablo ve sütun oluşturmayı ve eklemeyi açıklar <xref:System.Data.DataSet> .  
  
 [DataRelations Ekleme](adding-datarelations.md)  
 İçindeki tablolar arasında ilişki oluşturmayı açıklar <xref:System.Data.DataSet> .  
  
 [DataRelations İçinde Gezinme](navigating-datarelations.md)  
 Bir <xref:System.Data.DataSet> üst-alt ilişkisinin alt veya üst satırlarını döndürmek için içindeki tablolar arasındaki ilişkilerin nasıl kullanılacağını açıklar.  
  
 [DataSet İçeriklerini Birleştirme](merging-dataset-contents.md)  
 Bir <xref:System.Data.DataSet> , <xref:System.Data.DataTable> veya dizisinin içeriğinin başka bir, veya dizisinin içeriğini <xref:System.Data.DataRow> nasıl birleştirebileceğinizi açıklar <xref:System.Data.DataSet> .  
  
 [DataSet İçeriklerini Kopyalama](copying-dataset-contents.md)  
 Bir öğesinin, <xref:System.Data.DataSet> belirtilen verilerin yanı sıra şema içerebilen bir kopyasının nasıl oluşturulduğunu açıklar.  
  
 [DataSet Olaylarını İşleme](handling-dataset-events.md)  
 ' A ait olayları <xref:System.Data.DataSet> ve bunların nasıl kullanılacağını açıklar.  
  
 [Türü Belirtilmiş DataSets](typed-datasets.md)  
 Türü nelerin <xref:System.Data.DataSet> olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.  
  
 [DataTables](datatables.md)  
 Oluşturma <xref:System.Data.DataTable> , şema tanımlama ve verileri işleme işlemlerinin nasıl yapılacağını açıklar.  
  
 [DataTableReaders](datatablereaders.md)  
 Oluşturmayı ve kullanmayı açıklar <xref:System.Data.DataTableReader> .  
  
 [DataViews](dataviews.md)  
 Oluşturma ve bunlarla çalışmayı ve olayları nasıl kullanacağınızı açıklar `DataViews` <xref:System.Data.DataView> .  
  
 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 <xref:System.Data.DataSet>Bir veri kaynağı olarak XML ile nasıl etkileşime gireceğini açıklar ve BIR XML verisi olarak içeriğini yükleme ve kalıcı hale getirme de dahildir <xref:System.Data.DataSet> .  
  
 [XML Web Hizmetinden DataSet Kullanma](consuming-a-dataset-from-an-xml-web-service.md)  
 Verileri aktarmak için kullanan bir XML Web hizmeti oluşturmayı açıklar <xref:System.Data.DataSet> .  
  
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
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
