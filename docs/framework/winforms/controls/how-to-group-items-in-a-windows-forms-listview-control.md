---
title: Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 1b716498ec5a45fbde499a1f53b2bdccd28a7176
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960168"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama
<xref:System.Windows.Forms.ListView> denetiminin gruplandırma özelliği ile, gruplar içindeki ilgili öğe kümelerini görüntüleyebilirsiniz. Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır. Öğeleri alfabetik olarak, tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için <xref:System.Windows.Forms.ListView> gruplarını kullanabilirsiniz. Aşağıdaki görüntüde bazı gruplanmış öğeler gösteriliyor.  
  
 ![Tek ve hatta ListView gruplarının ekran görüntüsü.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha fazla grup oluşturmanız gerekir. Bir grup tanımlandıktan sonra gruplara <xref:System.Windows.Forms.ListView> öğeleri atayabilirsiniz. Ayrıca, öğeleri programlama yoluyla bir gruptan diğerine taşıyabilirsiniz.  
  
### <a name="to-add-groups"></a>Grup eklemek için  
  
1. <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonunun <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemini kullanın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Grupları kaldırmak için  
  
1. <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonunun <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemini kullanın.  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> yöntemi tek bir grubu kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi, tüm grupları listeden kaldırır.  
  
    > [!NOTE]
    > Bir grubun kaldırılması bu gruptaki öğeleri kaldırmaz.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Gruplara öğe atamak veya öğeleri gruplar arasında taşımak için  
  
1. Ayrı öğelerin <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> özelliğini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
