---
title: Veri Bağlama ve LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 563d57249daa3aa720da1d9654866727f770afb3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786695"
---
# <a name="data-binding-and-linq-to-dataset"></a>Veri Bağlama ve LINQ to DataSet
*Veri bağlama* , uygulama kullanıcı arabirimi ve iş mantığı arasında bağlantı kuran işlemdir. Bağlamanın doğru ayarları varsa ve veriler doğru bildirimleri sağlıyorsa, veriler değerini değiştirdiğinde veriye bağlanan öğeler otomatik olarak değişiklikleri yansıtır. , <xref:System.Data.DataSet> İçerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellek içi gösterimidir. ADO.NET 2,0 <xref:System.Data.DataView> , <xref:System.Data.DataTable>içinde depolanan verileri sıralamanıza ve filtrelemenize olanak sağlar. Bu işlevsellik genellikle veri bağlama uygulamalarında kullanılır. Bir <xref:System.Data.DataView>kullanarak, verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz. <xref:System.Data.DataView> Nesnesi hakkında daha fazla bilgi için bkz. [DataView](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet, geliştiricilerin kullanarak <xref:System.Data.DataSet> [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]üzerinde karmaşık ve güçlü sorgular oluşturmalarına olanak tanır. Ancak, bir LINQ to DataSet sorgusu, bir bağlama senaryosunda <xref:System.Data.DataRow> kolayca kullanılmayan nesnelerin bir listesini döndürür. Bağlama daha kolay hale getirmek için bir LINQ to DataSet sorgusundan <xref:System.Data.DataView> bir oluşturabilirsiniz. Bu <xref:System.Data.DataView> , sorguda belirtilen filtreleme ve sıralamayı kullanır, ancak veri bağlama için daha uygundur. LINQ to DataSet, <xref:System.Data.DataView> dize tabanlı filtrelemeye ve sıralamaya [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] kıyasla çok daha karmaşık ve güçlü filtreleme ve sıralama işlemlerine izin veren ifade tabanlı filtreleme ve sıralama sağlayarak işlevselliğini genişletir.  
  
 Öğesinin sorgunun kendisini temsil ettiğini ve sorgunun üstünde bir görünüm olduğunu unutmayın. <xref:System.Data.DataView> , Bir <xref:System.Windows.Forms.DataGrid> veya<xref:System.Windows.Forms.DataGridView>gibi bir UI denetimine bağlanır ve basit veri bağlama modeli sağlar. <xref:System.Data.DataView> Ayrıca, bu tablo <xref:System.Data.DataTable> içinvarsayılanbirgörünümsağlayanbir'dandaoluşturulabilir.<xref:System.Data.DataView>  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataView Nesnesi Oluşturma](creating-a-dataview-object-linq-to-dataset.md)  
 Oluşturma hakkında bilgi sağlar <xref:System.Data.DataView>.  
  
 [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)  
 İle nasıl filtreleneceğini açıklar <xref:System.Data.DataView>.  
  
 [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)  
 İle nasıl sıralanacağını açıklar <xref:System.Data.DataView>.  
  
 [DataView’da DataRowView Koleksiyonunu Sorgulama](querying-the-datarowview-collection-in-a-dataview.md)  
 <xref:System.Data.DataRowView> Tarafından<xref:System.Data.DataView>sunulan koleksiyonu sorgulama hakkında bilgi sağlar.  
  
 [DataView Performansı](dataview-performance.md)  
 Ve performansı hakkında <xref:System.Data.DataView> bilgi sağlar.  
  
 [Nasıl yapılır: Bir DataView nesnesini Windows Forms DataGridView denetimine bağlama](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Bir <xref:System.Data.DataView> nesnesinin bir <xref:System.Windows.Forms.DataGridView>öğesine nasıl bağlanacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
