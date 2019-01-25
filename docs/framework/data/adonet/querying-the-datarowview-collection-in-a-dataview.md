---
title: Dataview'da DataRowView koleksiyonunu sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 1890ab2fcc7e1427d9c74f6c981e232802b0eb1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643747"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Dataview'da DataRowView koleksiyonunu sorgulama
<xref:System.Data.DataView> Numaralandırılabilir bir topluluğu gösterir <xref:System.Data.DataRowView> nesneleri. <xref:System.Data.DataRowView> özelleştirilmiş bir görünümünü temsil eden bir <xref:System.Data.DataRow> ve, belirli bir sürümünü görüntüler <xref:System.Data.DataRow> denetiminde. Yalnızca bir sürümü bir <xref:System.Data.DataRow> gibi bir denetim aracılığıyla görüntülenebilir bir <xref:System.Windows.Forms.DataGridView>. Erişebildiğiniz <xref:System.Data.DataRow> tarafından sunulan <xref:System.Data.DataRowView> aracılığıyla <xref:System.Data.DataRowView.Row%2A> özelliği <xref:System.Data.DataRowView>. Görüntülediğinizde değerleri kullanarak bir <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> özelliği temel alınan hangi satır sürümünü belirler <xref:System.Data.DataRow> sunulur. Farklı satır sürümlerini kullanarak erişme hakkında bilgi için bir <xref:System.Data.DataRow>, bkz: [satır durumları ve satır sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Çünkü koleksiyonunu <xref:System.Data.DataRowView> nesneler tarafından kullanıma sunulan <xref:System.Data.DataView> olan numaralandırılabilir, kullanabilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ele sorgulanamıyor.  
  
 Aşağıdaki örnek sorgularda `Product` kırmızı renkli ürünleri için tablo ve bu sorgudan bir tablo oluşturur. A <xref:System.Data.DataView> tablodan oluşturulur ve <xref:System.Data.DataView.RowStateFilter%2A> özelliği, silinen ve değiştirilen satırlar üzerinde filtrelemek için ayarlanır. <xref:System.Data.DataView> Bir LINQ Sorgu kaynağı olarak kullanılır ve <xref:System.Data.DataRowView> değiştirilen ve Silinen nesneler için ilişkili bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Aşağıdaki örnek, bir görünümden bağlı Ürünler tablosu oluşturur. bir <xref:System.Windows.Forms.DataGridView> denetimi. <xref:System.Data.DataView> Kırmızı renkli ürün ve sipariş edilen için sorgulanır sonuçları için ilişkili bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
