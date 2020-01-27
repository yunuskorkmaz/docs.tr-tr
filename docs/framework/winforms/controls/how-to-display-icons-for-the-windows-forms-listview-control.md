---
title: ListView denetimi için simgeler görüntüleme
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
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744512"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme
Windows Forms <xref:System.Windows.Forms.ListView> denetimi üç görüntü listesinden simgeleri görüntüleyebilir. Liste, Ayrıntılar ve Smallıon görünümleri, <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliğinde belirtilen görüntü listesindeki görüntüleri görüntüler. LargeIcon görünümü, <xref:System.Windows.Forms.ListView.LargeImageList%2A> özelliğinde belirtilen görüntü listesindeki görüntüleri görüntüler. Liste görünümü, büyük veya küçük simgelerin yanında <xref:System.Windows.Forms.ListView.StateImageList%2A> özelliğinde ayarlanan ek bir simge kümesi de gösterebilir. Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Resimleri bir liste görünümünde görüntülemek için  
  
1. Uygun özelliği (<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>veya <xref:System.Windows.Forms.ListView.StateImageList%2A>) kullanmak istediğiniz varolan <xref:System.Windows.Forms.ImageList> bileşenine ayarlayın.  
  
     Bu özellikler, Özellikler penceresi veya kod ile tasarımcıda ayarlanabilir.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. İlişkili simgesi olan her liste öğesi için <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> veya <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> özelliğini ayarlayın.  
  
     Bu özellikler kod içinde veya **ListViewItem koleksiyon Düzenleyicisi**içinde ayarlanabilir. **ListViewItem koleksiyon düzenleyicisini**açmak Için, **Özellikler** penceresindeki <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin yanındaki üç nokta düğmesini (...) ve Visual Studio 'nun Özellikler penceresi![.](./media/visual-studio-ellipsis-button.png)) tıklayın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList Bileşeni](imagelist-component-windows-forms.md)
