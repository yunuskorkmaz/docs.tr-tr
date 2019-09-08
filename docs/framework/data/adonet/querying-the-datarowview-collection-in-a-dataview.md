---
title: DataView’da DataRowView Koleksiyonunu Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 17fab6e4c178eee6b5135045fb953267db810898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794461"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>DataView’da DataRowView Koleksiyonunu Sorgulama
, <xref:System.Data.DataView> <xref:System.Data.DataRowView> Nesnelerin sıralanabilir koleksiyonunu ortaya koyar. <xref:System.Data.DataRowView>, öğesinin özelleştirilmiş bir <xref:System.Data.DataRow> görünümünü temsil eder ve bir denetimdeki belirli bir sürümünü <xref:System.Data.DataRow> görüntüler. Yalnızca bir sürümü bir denetim <xref:System.Data.DataRow> aracılığıyla görüntülenebilir (örneğin, <xref:System.Windows.Forms.DataGridView>). <xref:System.Data.DataRow> <xref:System.Data.DataRowView> Öğesinin özelliğiaracılığıyla<xref:System.Data.DataRowView.Row%2A>tarafından açığa çıkarılan öğesine erişebilirsiniz <xref:System.Data.DataRowView>. Kullanarak <xref:System.Data.DataRowView>değerleri görüntülediğinizde <xref:System.Data.DataView.RowStateFilter%2A> , özelliği temel alınan <xref:System.Data.DataRow> satır sürümünün sunulma durumunu belirler. Kullanarak <xref:System.Data.DataRow>farklı satır sürümlerine erişme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](./dataset-datatable-dataview/row-states-and-row-versions.md). Tarafından kullanıma sunulan <xref:System.Data.DataRowView>nesnekoleksiyonu numaralandırılacağından,üzerindesorgulamayapmakiçinLINQtoDataSetkullanabilirsiniz.<xref:System.Data.DataView>  
  
 Aşağıdaki örnek, `Product` tabloyu kırmızı renkli ürünler için sorgular ve bu sorgudan bir tablo oluşturur. , Tablosundan oluşturulur <xref:System.Data.DataView.RowStateFilter%2A> ve özellik silinen ve değiştirilen satırları filtrele olarak ayarlanır. <xref:System.Data.DataView> Daha sonra bir LINQ sorgusunda kaynak olarak kullanılır <xref:System.Data.DataRowView> ve değiştirilmiş ve silinmiş nesneler bir <xref:System.Windows.Forms.DataGridView> denetime bağlanır. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> denetime bağlanan bir görünümden bir ürün tablosu oluşturur. , <xref:System.Data.DataView> Kırmızı renkli ürünler için sorgulanır ve sıralı sonuçlar bir <xref:System.Windows.Forms.DataGridView> denetime bağlanır.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
