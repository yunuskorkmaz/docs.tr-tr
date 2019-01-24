---
title: 'Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: 49b44c604a8532c6d2beb39b917f3e5ade339c49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564035"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama
Windows Forms <xref:System.Windows.Forms.TreeView> denetim her düğümün yanındaki simge görüntüleyebilirsiniz. Simgeleri hemen düğüm metnin solunda yerleştirilir. Bu simgeleri göstermek için ağaç görünümü ile ilişkilendirmek bir <xref:System.Windows.Forms.ImageList> denetimi. Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Microsoft .NET Framework sürüm 1.1 bir hata görüntüleri üzerinde görüntülenmesini engeller <xref:System.Windows.Forms.TreeView> uygulamanız çağırdığında düğümleri <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Bu hata geçici olarak çözmek için çağrı <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> içinde `Main` yöntemi çağırma hemen sonra <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. İçinde bu hatanın giderilmesidir [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
### <a name="to-display-images-in-a-tree-view"></a>Görüntüleri bir ağaç görünümünde görüntülemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.ImageList%2A> varolan özellik <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz denetimi.  
  
     Bu özellikleri Özellikler penceresi ile Tasarımcısı'nda veya kod içinde ayarlayabilirsiniz.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  Düğümün ayarlamak <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özellikleri. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Düğümün normal ve genişletilmiş durumları için görüntülenen resim özelliği belirler ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> düğümün Seçili durum için görüntülenen resim özelliği belirler.  
  
     Bu özellikler, kod veya TreeNode Düzenleyicisi'nin içinden ayarlanabilir. TreeNode Düzenleyicisi'ni açmak için üç nokta düğmesini ( ![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> Özellikler penceresinde özelliği.  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TreeView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [Nasıl yapılır: Ekleme ve Windows Forms TreeView denetimi ile düğüm kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
