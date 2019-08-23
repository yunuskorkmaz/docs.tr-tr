---
title: 'Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama'
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
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966627"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama
<xref:System.Windows.Forms.ListView> Denetimin gruplandırma özelliği ile, gruplar içindeki ilgili öğe kümelerini görüntüleyebilirsiniz. Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır. Öğeleri alfabetik olarak <xref:System.Windows.Forms.ListView> , tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için grupları kullanabilirsiniz. Aşağıdaki görüntüde bazı gruplanmış öğeler gösteriliyor.  
  
 ![Tek ve hatta ListView gruplarının ekran görüntüsü.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha fazla grup oluşturmanız gerekir. Bir grup tanımlandıktan sonra gruplara öğe atayabilirsiniz <xref:System.Windows.Forms.ListView> . Ayrıca, öğeleri programlama yoluyla bir gruptan diğerine taşıyabilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir. Önceki işletim sistemlerinde, gruplarla ilgili herhangi bir kodun etkisi yoktur ve gruplar görünmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Grup eklemek için  
  
1. <xref:System.Windows.Forms.ListView.Groups%2A> Koleksiyonun <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemini kullanın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Grupları kaldırmak için  
  
1. <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> Koleksiyonun veya<xref:System.Windows.Forms.ListView.Groups%2A> yöntemini kullanın.  
  
     Yöntemi tek bir grubu kaldırır <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ; yöntemi listedeki tüm grupları kaldırır. <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>  
  
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
- [Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
