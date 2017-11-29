---
title: "Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d9a8bdc54f3f321b37bda897aac1f340f7a46aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme
Windows Forms <xref:System.Windows.Forms.ListView> denetim, üç görüntü listelerinden simgeler görüntüleyebilir. Belirtilen görüntü listesinden görüntü listesi, Ayrıntılar ve SmallIcon görünümleri görüntülemek <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliği. Belirtilen görüntü listesinden görüntü LargeIcon görüntüleyen <xref:System.Windows.Forms.ListView.LargeImageList%2A> özelliği. Bir liste görünümü de kümesinde simgeler, ek bir dizi görüntüleyebilirsiniz <xref:System.Windows.Forms.ListView.StateImageList%2A> büyük veya küçük simgeleri yanındaki özelliği. Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri ekleme veya kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Görüntüleri listesini görüntülemek için  
  
1.  Uygun özelliğini ayarlayın —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, veya <xref:System.Windows.Forms.ListView.StateImageList%2A>— varolan <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz bileşeni.  
  
     Bu özellikleri Özellikler penceresini tasarımcıyla veya kodu ayarlayabilirsiniz.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  Ayarlama <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> veya <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> ilişkili bir simgesi var her liste öğesi için özelliği.  
  
     Bu özellikler ayarlanabilir, kod veya içinde **ListViewItem Koleksiyonu Düzenleyicisi**. Açmak için **ListViewItem Koleksiyonu Düzenleyicisi**, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki<xref:System.Windows.Forms.ListView.Items%2A>özelliği **özellikleri** penceresi.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ListView denetimine genel bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Nasıl yapılır: ekleme ve kaldırma öğeleri Windows Forms ListView denetimi](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: sütunları Windows Forms ListView denetimine ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
