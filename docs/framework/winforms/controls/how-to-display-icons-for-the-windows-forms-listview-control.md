---
title: 'Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 3c3df1fb38c9fbcf672e9ffcd8c0aa3c881be00b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510630"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme
Windows Forms <xref:System.Windows.Forms.ListView> denetim, üç görüntü listeleri simgelerden görüntüleyebilirsiniz. Belirtilen görüntü listesinden görüntü listesi, Ayrıntılar ve SmallIcon görünümleri görüntüler <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliği. Belirtilen görüntü listesinden görüntü LargeIcon görüntüleyen <xref:System.Windows.Forms.ListView.LargeImageList%2A> özelliği. Bir liste görünümü de kümesinde simgeler, ek bir kümesini görüntüleyebilirsiniz <xref:System.Windows.Forms.ListView.StateImageList%2A> büyük veya küçük simgeleri yanındaki özelliği. Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Görüntüleri bir liste görünümünde görüntülemek için  
  
1.  Uygun özelliğini ayarlayın —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, veya <xref:System.Windows.Forms.ListView.StateImageList%2A>— varolan <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz bileşeni.  
  
     Bu özellikleri Özellikler penceresi ile Tasarımcısı'nda veya kod içinde ayarlayabilirsiniz.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  Ayarlama <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> veya <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> ilişkili bir simge içeren her bir liste öğesi için özelliği.  
  
     Kod veya içinde bu özellikleri ayarlanabilir **ListViewItem Koleksiyonu Düzenleyicisi**. Açmak için **ListViewItem Koleksiyonu Düzenleyicisi**, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki<xref:System.Windows.Forms.ListView.Items%2A>özellikte **özellikleri** penceresi.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList Bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
