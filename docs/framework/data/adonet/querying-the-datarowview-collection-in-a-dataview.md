---
title: DataView’da DataRowView Koleksiyonunu Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 5757079bbc0ef8c498ea1db1a88f6b356ab0409e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172755"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>DataView’da DataRowView Koleksiyonunu Sorgulama

, <xref:System.Data.DataView> Nesnelerin sıralanabilir koleksiyonunu ortaya koyar <xref:System.Data.DataRowView> . <xref:System.Data.DataRowView> , öğesinin özelleştirilmiş bir görünümünü temsil eder <xref:System.Data.DataRow> ve bir denetimdeki belirli bir sürümünü <xref:System.Data.DataRow> görüntüler. Yalnızca bir sürümü bir <xref:System.Data.DataRow> Denetim aracılığıyla görüntülenebilir (örneğin,) <xref:System.Windows.Forms.DataGridView> . <xref:System.Data.DataRow>Öğesinin özelliği aracılığıyla tarafından açığa çıkarılan öğesine erişebilirsiniz <xref:System.Data.DataRowView> <xref:System.Data.DataRowView.Row%2A> <xref:System.Data.DataRowView> . Kullanarak değerleri görüntülediğinizde <xref:System.Data.DataRowView> , <xref:System.Data.DataView.RowStateFilter%2A> özelliği temel alınan satır sürümünün sunulma durumunu belirler <xref:System.Data.DataRow> . Kullanarak farklı satır sürümlerine erişme hakkında daha fazla bilgi için <xref:System.Data.DataRow> bkz. [Satır durumları ve satır sürümleri](./dataset-datatable-dataview/row-states-and-row-versions.md). <xref:System.Data.DataRowView>Tarafından kullanıma sunulan nesne koleksiyonu <xref:System.Data.DataView> numaralandırılacağından, üzerinde sorgulama yapmak için LINQ to DataSet kullanabilirsiniz.  
  
 Aşağıdaki örnek, `Product` tabloyu kırmızı renkli ürünler için sorgular ve bu sorgudan bir tablo oluşturur. , <xref:System.Data.DataView> Tablosundan oluşturulur ve <xref:System.Data.DataView.RowStateFilter%2A> özellik silinen ve değiştirilen satırları filtrele olarak ayarlanır. <xref:System.Data.DataView>Daha sonra BIR LINQ sorgusunda kaynak olarak kullanılır ve <xref:System.Data.DataRowView> değiştirilmiş ve silinmiş nesneler bir <xref:System.Windows.Forms.DataGridView> denetime bağlanır.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Aşağıdaki örnek, bir denetime bağlanan bir görünümden bir ürün tablosu oluşturur <xref:System.Windows.Forms.DataGridView> . , <xref:System.Data.DataView> Kırmızı renkli ürünler için sorgulanır ve sıralı sonuçlar bir <xref:System.Windows.Forms.DataGridView> denetime bağlanır.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
