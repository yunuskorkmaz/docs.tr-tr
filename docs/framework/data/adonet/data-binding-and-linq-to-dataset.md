---
title: Veri Bağlama ve LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: b081a648023aa21eea3a20ec409600d3bcbe9878
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607407"
---
# <a name="data-binding-and-linq-to-dataset"></a>Veri Bağlama ve LINQ to DataSet
*Veri bağlama* iş mantığı ve UI uygulama arasında bağlantı kuran işlemidir. Verilere bağlı öğeleri doğru ayarların bağlama varsa ve veri değeri değiştiğinde verileri uygun bildirimleri sağlar, değişiklikleri otomatik olarak yansıtır. <xref:System.Data.DataSet> Bir bellek içi tutarlı bir ilişkisel programlama modeli, içerdiği veri kaynağı ne olursa olsun sağlayan veri gösterimidir. ADO.NET 2.0 <xref:System.Data.DataView> depolanan verilerini sıralama ve filtreleme sayesinde bir <xref:System.Data.DataTable>. Bu işlevsellik, çoğunlukla veri bağlama uygulamalarda kullanılır. Kullanarak bir <xref:System.Data.DataView>sıralamalar farklı olan bir tabloda verilerini açığa çıkarabilir ve verileri satır durum ya da bir filtre ifadesi temelinde göre filtre uygulayabilirsiniz. Hakkında daha fazla bilgi için <xref:System.Data.DataView> nesne, bkz: [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] üzerinde karmaşık ve güçlü sorgular oluşturmak geliştiricilerinin sağlayan bir <xref:System.Data.DataSet> kullanarak [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]. Ancak, bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgunun döndürdüğü numaralandırması <xref:System.Data.DataRow> kolayca bir bağlama senaryosunda kullanılmayan nesneler. Bağlama kolaylaştırmak için oluşturabileceğiniz bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Bu <xref:System.Data.DataView> filtreleme ve sıralama sorguda belirtilen kullanır, ancak daha iyi veri bağlama için uygundur. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] işlevselliğini genişletir <xref:System.Data.DataView> sağlayarak [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ifade tabanlı filtreleme ve sıralama, çok daha karmaşık ve güçlü filtreleme ve sıralama dize tabanlı filtreleme ve sıralama işlemleri sağlar.  
  
 Unutmayın <xref:System.Data.DataView> sorgu temsil eder ve sorgu üzerinde bir görünüm değil. <xref:System.Data.DataView> Gibi bir UI denetimine bağlı bir <xref:System.Windows.Forms.DataGrid> veya <xref:System.Windows.Forms.DataGridView>, basit veri bağlama modelini sağlar. A <xref:System.Data.DataView> da oluşturulabilir bir <xref:System.Data.DataTable>, bu tablonun varsayılan bir görünüm.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataView Nesnesi Oluşturma](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 Oluşturma hakkında bilgi sağlayan bir <xref:System.Data.DataView>.  
  
 [DataView ile Filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 Filtrele açıklar <xref:System.Data.DataView>.  
  
 [DataView ile Sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 İle sıralama açıklar <xref:System.Data.DataView>.  
  
 [DataView’da DataRowView Koleksiyonunu Sorgulama](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 Sorgulama hakkında bilgi sağlar <xref:System.Data.DataRowView> koleksiyon tarafından açığa çıkarılan <xref:System.Data.DataView>.  
  
 [DataView Performansı](../../../../docs/framework/data/adonet/dataview-performance.md)  
 Hakkında bilgi sağlar <xref:System.Data.DataView> ve performans.  
  
 [Nasıl yapılır: Windows Forms DataGridView denetimine DataView nesnesi bağlama](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Nasıl bağlanacağını açıklayan bir <xref:System.Data.DataView> nesnesini bir <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
