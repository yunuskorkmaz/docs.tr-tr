---
title: Veri Bağlama ve LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 3203310029f463e55d7517e79f5a1f0424a0a80c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166878"
---
# <a name="data-binding-and-linq-to-dataset"></a>Veri Bağlama ve LINQ to DataSet

*Veri bağlama* , uygulama kullanıcı arabirimi ve iş mantığı arasında bağlantı kuran işlemdir. Bağlamanın doğru ayarları varsa ve veriler doğru bildirimleri sağlıyorsa, veriler değerini değiştirdiğinde veriye bağlanan öğeler otomatik olarak değişiklikleri yansıtır. , <xref:System.Data.DataSet> İçerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellek içi gösterimidir. ADO.NET 2,0, <xref:System.Data.DataView> içinde depolanan verileri sıralamanıza ve filtrelemenize olanak sağlar <xref:System.Data.DataTable> . Bu işlevsellik genellikle veri bağlama uygulamalarında kullanılır. Bir kullanarak <xref:System.Data.DataView> , verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz. Nesnesi hakkında daha fazla bilgi için <xref:System.Data.DataView> bkz. [DataView](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet, geliştiricilerin <xref:System.Data.DataSet> dil Ile tümleşik sorgu (LINQ) kullanarak bir üzerinde karmaşık ve güçlü sorgular oluşturmalarına olanak tanır. Ancak, bir LINQ to DataSet sorgusu, <xref:System.Data.DataRow> bir bağlama senaryosunda kolayca kullanılmayan nesnelerin bir listesini döndürür. Bağlama daha kolay hale getirmek için bir <xref:System.Data.DataView> LINQ to DataSet sorgusundan bir oluşturabilirsiniz. Bu, <xref:System.Data.DataView> sorguda belirtilen filtreleme ve sıralamayı kullanır, ancak veri bağlama için daha uygundur. LINQ to DataSet, <xref:System.Data.DataView> LINQ ifade tabanlı filtreleme ve sıralama sağlayarak, dize tabanlı filtrelemeye ve sıralamaya kıyasla çok daha karmaşık ve güçlü filtreleme ve sıralama işlemlerine olanak tanıyan ' nin işlevselliğini genişletir.  
  
 <xref:System.Data.DataView>Öğesinin sorgunun kendisini temsil ettiğini ve sorgunun üstünde bir görünüm olduğunu unutmayın. , <xref:System.Data.DataView> Bir veya gibi BIR UI denetimine bağlanır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> basit veri bağlama modeli sağlar. <xref:System.Data.DataView>Ayrıca <xref:System.Data.DataTable> , bu tablo için varsayılan bir görünüm sağlayan bir ' dan da oluşturulabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [DataView Nesnesi Oluşturma](creating-a-dataview-object-linq-to-dataset.md)  
 Oluşturma hakkında bilgi sağlar <xref:System.Data.DataView> .  
  
 [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)  
 İle nasıl filtreleneceğini açıklar <xref:System.Data.DataView> .  
  
 [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)  
 İle nasıl sıralanacağını açıklar <xref:System.Data.DataView> .  
  
 [DataView’da DataRowView Koleksiyonunu Sorgulama](querying-the-datarowview-collection-in-a-dataview.md)  
 Tarafından sunulan koleksiyonu sorgulama hakkında bilgi sağlar <xref:System.Data.DataRowView> <xref:System.Data.DataView> .  
  
 [DataView Performansı](dataview-performance.md)  
 Ve performansı hakkında bilgi sağlar <xref:System.Data.DataView> .  
  
 [Nasıl yapılır: Windows Forms DataGridView Denetimine DataView Nesnesi Bağlama](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 <xref:System.Data.DataView>Bir nesnesinin bir öğesine nasıl bağlanacağını açıklar <xref:System.Windows.Forms.DataGridView> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
