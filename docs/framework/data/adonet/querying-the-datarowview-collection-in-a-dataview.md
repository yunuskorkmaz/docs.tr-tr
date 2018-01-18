---
title: DataView DataRowView koleksiyonunda sorgulama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1912526d98dc7872470953e1bf61b72db191de5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>DataView DataRowView koleksiyonunda sorgulama
<xref:System.Data.DataView> Numaralandırılabilir bir topluluğu gösterir <xref:System.Data.DataRowView> nesneleri. <xref:System.Data.DataRowView>özelleştirilmiş bir görünümünü temsil eden bir <xref:System.Data.DataRow> ve, belirli bir sürümünü görüntüler <xref:System.Data.DataRow> denetiminde. Yalnızca bir sürümü bir <xref:System.Data.DataRow> bir denetim aracılığıyla gibi görüntülenebilen bir <xref:System.Windows.Forms.DataGridView>. Erişebileceğiniz <xref:System.Data.DataRow> tarafından sunulan <xref:System.Data.DataRowView> aracılığıyla <xref:System.Data.DataRowView.Row%2A> özelliği <xref:System.Data.DataRowView>. Kullanarak değerleri görüntülerken bir <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> özelliği, arka plandaki hangi satır sürümü belirler <xref:System.Data.DataRow> sunulur. Kullanarak farklı satır sürümler erişme hakkında bilgi için bir <xref:System.Data.DataRow>, bkz: [satır durumları ve satır sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Çünkü koleksiyonunu <xref:System.Data.DataRowView> tarafından sunulan nesneleri <xref:System.Data.DataView> olan numaralandırılabilir, kullanabilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ele sorgulanamıyor.  
  
 Aşağıdaki örnek sorgularda `Product` tablo için kırmızı renkli ürünler ve bu sorgudan bir tablo oluşturur. A <xref:System.Data.DataView> tablosundan oluşturulur ve <xref:System.Data.DataView.RowStateFilter%2A> özelliği, silinen ve değiştirilen satırlarda filtrelemek için ayarlanır. <xref:System.Data.DataView> Daha sonra bir LINQ Sorgu kaynağı olarak kullanılır ve <xref:System.Data.DataRowView> , değiştirilen ve silinen nesneleri bağlı bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Aşağıdaki örnek, bağlı bir görünümden ürünlerin bir tablo oluşturur. bir <xref:System.Windows.Forms.DataGridView> denetim. <xref:System.Data.DataView> Kırmızı renkli ürünleri ve sıralı için sorgulanır sonuçları bağlı bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
