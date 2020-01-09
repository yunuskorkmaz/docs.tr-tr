---
title: Veri Bağlama ve LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 2b49e2a3ff0d95dcbceff8099f51993c0f08d64e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634878"
---
# <a name="data-binding-and-linq-to-dataset"></a>Veri Bağlama ve LINQ to DataSet
*Veri bağlama* , uygulama kullanıcı arabirimi ve iş mantığı arasında bağlantı kuran işlemdir. Bağlamanın doğru ayarları varsa ve veriler doğru bildirimleri sağlıyorsa, veriler değerini değiştirdiğinde veriye bağlanan öğeler otomatik olarak değişiklikleri yansıtır. <xref:System.Data.DataSet>, içerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellek içi bir gösterimidir. ADO.NET 2,0 <xref:System.Data.DataView>, bir <xref:System.Data.DataTable>depolanan verileri sıralamanıza ve filtrelemenize olanak sağlar. Bu işlevsellik genellikle veri bağlama uygulamalarında kullanılır. <xref:System.Data.DataView>kullanarak verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz. <xref:System.Data.DataView> nesnesi hakkında daha fazla bilgi için bkz. [DataView](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet, geliştiricilerin dil ile tümleşik sorgu (LINQ) kullanarak bir <xref:System.Data.DataSet> üzerinde karmaşık ve güçlü sorgular oluşturmalarına olanak tanır. Ancak, bir LINQ to DataSet sorgusu, bir bağlama senaryosunda kolayca kullanılmayan <xref:System.Data.DataRow> nesnelerinin bir listesini döndürür. Bağlamayı kolaylaştırmak için bir LINQ to DataSet sorgusundan <xref:System.Data.DataView> oluşturabilirsiniz. Bu <xref:System.Data.DataView> sorguda belirtilen filtreleme ve sıralamayı kullanır, ancak veri bağlama için daha uygundur. LINQ to DataSet, LINQ ifade tabanlı filtreleme ve sıralama sağlayarak <xref:System.Data.DataView> işlevselliğini genişleterek, dize tabanlı filtreleme ve sıralamaya kıyasla çok daha karmaşık ve güçlü filtreleme ve sıralama işlemlerine olanak tanır.  
  
 <xref:System.Data.DataView> sorgunun kendisini temsil ettiğini ve sorgunun üzerine bir görünüm olamayacağını unutmayın. <xref:System.Data.DataView>, bir <xref:System.Windows.Forms.DataGrid> veya <xref:System.Windows.Forms.DataGridView>gibi bir kullanıcı arabirimi denetimine (basit veri bağlama modeli sağlar) bağlanır. Bir <xref:System.Data.DataView> Ayrıca, bu tablo için varsayılan bir görünüm sağlayarak bir <xref:System.Data.DataTable>oluşturulabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataView Nesnesi Oluşturma](creating-a-dataview-object-linq-to-dataset.md)  
 <xref:System.Data.DataView>oluşturma hakkında bilgi sağlar.  
  
 [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView>nasıl filtreleneceğini açıklar.  
  
 [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView>ile nasıl sıralanacağını açıklar.  
  
 [DataView’da DataRowView Koleksiyonunu Sorgulama](querying-the-datarowview-collection-in-a-dataview.md)  
 <xref:System.Data.DataView>tarafından sunulan <xref:System.Data.DataRowView> koleksiyonunu sorgulama hakkında bilgi sağlar.  
  
 [DataView Performansı](dataview-performance.md)  
 <xref:System.Data.DataView> ve performans hakkında bilgi sağlar.  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Bir <xref:System.Data.DataView> nesnesinin bir <xref:System.Windows.Forms.DataGridView>nasıl bağlanacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
