---
title: DataView’da DataRowView Koleksiyonunu Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 8b6b6c5b9d7157b1279f23770b1d223635252685
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092961"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>DataView’da DataRowView Koleksiyonunu Sorgulama
<xref:System.Data.DataView> Numaralandırılabilir bir topluluğu gösterir <xref:System.Data.DataRowView> nesneleri. <xref:System.Data.DataRowView> özelleştirilmiş bir görünümünü temsil eden bir <xref:System.Data.DataRow> ve, belirli bir sürümünü görüntüler <xref:System.Data.DataRow> denetiminde. Yalnızca bir sürümü bir <xref:System.Data.DataRow> gibi bir denetim aracılığıyla görüntülenebilir bir <xref:System.Windows.Forms.DataGridView>. Erişebildiğiniz <xref:System.Data.DataRow> tarafından sunulan <xref:System.Data.DataRowView> aracılığıyla <xref:System.Data.DataRowView.Row%2A> özelliği <xref:System.Data.DataRowView>. Görüntülediğinizde değerleri kullanarak bir <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> özelliği temel alınan hangi satır sürümünü belirler <xref:System.Data.DataRow> sunulur. Farklı satır sürümlerini kullanarak erişme hakkında bilgi için bir <xref:System.Data.DataRow>, bkz: [satır durumları ve satır sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Çünkü koleksiyonunu <xref:System.Data.DataRowView> nesneler tarafından kullanıma sunulan <xref:System.Data.DataView> olan numaralandırılabilir, kullanabilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ele sorgulanamıyor.  
  
 Aşağıdaki örnek sorgularda `Product` kırmızı renkli ürünleri için tablo ve bu sorgudan bir tablo oluşturur. A <xref:System.Data.DataView> tablodan oluşturulur ve <xref:System.Data.DataView.RowStateFilter%2A> özelliği, silinen ve değiştirilen satırlar üzerinde filtrelemek için ayarlanır. <xref:System.Data.DataView> Bir LINQ Sorgu kaynağı olarak kullanılır ve <xref:System.Data.DataRowView> değiştirilen ve Silinen nesneler için ilişkili bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Aşağıdaki örnek, bir görünümden bağlı Ürünler tablosu oluşturur. bir <xref:System.Windows.Forms.DataGridView> denetimi. <xref:System.Data.DataView> Kırmızı renkli ürün ve sipariş edilen için sorgulanır sonuçları için ilişkili bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
