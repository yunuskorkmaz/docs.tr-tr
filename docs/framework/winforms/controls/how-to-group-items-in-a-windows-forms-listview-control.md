---
title: ListView Denetiminde Öğeleri Grupla
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141997"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama
<xref:System.Windows.Forms.ListView> Denetimin gruplandırma özelliğiyle, ilgili öğe kümelerini gruplar halinde görüntüleyebilirsiniz. Bu gruplar, grup başlıklarını içeren yatay grup başlıkları yla ekranda ayrılır. Büyük listelerde gezinmeyi, öğeleri alfabetik olarak, tarihe göre veya başka bir mantıksal gruplandırmaya göre gruplandırmayı kolaylaştırmak için grupları kullanabilirsiniz. <xref:System.Windows.Forms.ListView> Aşağıdaki resimde bazı gruplanmış öğeler gösterilmektedir.  
  
 ![Tek ve çift ListView gruplarının ekran görüntüsü.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 Gruplandırmayı etkinleştirmek için önce tasarımcıda veya programlı olarak bir veya daha fazla grup oluşturmanız gerekir. Bir grup tanımlandıktan sonra, gruplara öğe atayabilirsiniz. <xref:System.Windows.Forms.ListView> Öğeleri bir gruptan diğerine programlı olarak da taşıyabilirsiniz.  
  
### <a name="to-add-groups"></a>Grup eklemek için  
  
1. Toplama <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemini <xref:System.Windows.Forms.ListView.Groups%2A> kullanın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Grupları kaldırmak için  
  
1. Koleksiyonun <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemini <xref:System.Windows.Forms.ListView.Groups%2A> veya yöntemini kullanın.  
  
     Yöntem <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> tek bir grubu kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntem tüm grupları listeden kaldırır.  
  
    > [!NOTE]
    > Bir grubu kaldırmak, bu gruptaki öğeleri kaldırmaz.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Maddeleri gruplara atamak veya maddeleri gruplar arasında taşımak için  
  
1. Tek <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> tek öğelerin özelliğini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
