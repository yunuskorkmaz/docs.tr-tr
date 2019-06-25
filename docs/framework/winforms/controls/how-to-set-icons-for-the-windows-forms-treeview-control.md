---
title: 'Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama'
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
ms.openlocfilehash: c7c801242c7d5958cce9826a5f60d13a0b257add
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348050"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama
Windows Forms <xref:System.Windows.Forms.TreeView> denetim her düğümün yanındaki simge görüntüleyebilirsiniz. Simgeleri hemen düğüm metnin solunda yerleştirilir. Bu simgeleri göstermek için ağaç görünümü ile ilişkilendirmek bir <xref:System.Windows.Forms.ImageList> denetimi. Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Microsoft .NET Framework sürüm 1.1 bir hata görüntüleri üzerinde görüntülenmesini engeller <xref:System.Windows.Forms.TreeView> uygulamanız çağırdığında düğümleri <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Bu hata geçici olarak çözmek için çağrı <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> içinde `Main` yöntemi çağırma hemen sonra <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Bu hata, .NET Framework 2.0 sürümünde sabittir.  
  
### <a name="to-display-images-in-a-tree-view"></a>Görüntüleri bir ağaç görünümünde görüntülemek için  
  
1. Ayarlama <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.ImageList%2A> varolan özellik <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz denetimi.  
  
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
  
2. Düğümün ayarlamak <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özellikleri. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Düğümün normal ve genişletilmiş durumları için görüntülenen resim özelliği belirler ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> düğümün Seçili durum için görüntülenen resim özelliği belirler.  
  
     Bu özellikler, kod veya TreeNode Düzenleyicisi'nin içinden ayarlanabilir. TreeNode Düzenleyicisi'ni açmak için üç nokta düğmesini ( ![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> Özellikler penceresinde özelliği.  
  
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

- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [Nasıl yapılır: Ekleme ve Windows Forms TreeView denetimi ile düğüm kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](add-custom-information-to-a-treeview-or-listview-control-wf.md)
