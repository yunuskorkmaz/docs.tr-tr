---
title: 'Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma'
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
ms.openlocfilehash: 3899d06fce08eed5953181b9af232b6b2bb29e50
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305500"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma
Gruplandırma özelliğini de ile <xref:System.Windows.Forms.ListView> denetimi öğe kümeleri ilgili gruplar halinde görüntüleyebilirsiniz. Bu grupları ekranda grup başlıklarını içeren yatay grup üstbilgileri tarafından ayrılır. Kullanabileceğiniz <xref:System.Windows.Forms.ListView> öğeleri alfabetik olarak tarih veya diğer bir mantıksal gruplama gruplandırarak büyük listeler daha kolay gezinme olmak için grupları. Aşağıdaki resimde, bazı gruplandırılmış öğeler gösterilir.  
  
 ![ListView grupları](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
ListView gruplandırılmış öğeler  
  
 Gruplandırma etkinleştirmek için önce bir veya daha fazla Grup Tasarımcısı'nda veya programlama yoluyla oluşturmanız gerekir. Bir grubu tanımlandıktan sonra atayabilirsiniz <xref:System.Windows.Forms.ListView> gruplara öğeleri. Ayrıca öğeleri bir gruptan başka bir program aracılığıyla taşıyabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde herhangi bir kod gruplarına ilgili hiçbir etkisi yoktur ve grupları görüntülenmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Gruplar eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Grubu kaldırmak için  
  
1.  Kullanım <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonu.  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Yöntemi, tek bir grup kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi listeden tüm grupları kaldırır.  
  
    > [!NOTE]
    >  Grup kaldırma, o grup içindeki öğeleri kaldırmaz.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Öğeleri gruplara veya öğeleri grupları arasında taşıma  
  
1.  Ayarlama <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> tek tek öğelerin özelliği.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
