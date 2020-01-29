---
title: TreeView denetimi için simgeler ayarlama
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
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737270"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama
Windows Forms <xref:System.Windows.Forms.TreeView> denetimi her bir düğümün yanındaki simgeleri görüntüleyebilir. Simgeler, düğüm metninin hemen soluna yerleştirilir. Bu simgeleri görüntülemek için ağaç görünümünü bir <xref:System.Windows.Forms.ImageList> denetimiyle ilişkilendirmeniz gerekir. Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
> Microsoft .NET Framework sürüm 1,1 ' deki bir hata, uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>çağırdığında <xref:System.Windows.Forms.TreeView> düğümlerde resimlerin görünmesini engeller. Bu hatayı geçici olarak çözmek için, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>çağrıldıktan hemen sonra `Main` yönteminizin <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> çağırın. Bu hata .NET Framework 2,0 ' de düzeltilmiştir.  
  
### <a name="to-display-images-in-a-tree-view"></a>Görüntüleri ağaç görünümünde görüntülemek için  
  
1. <xref:System.Windows.Forms.TreeView> denetiminin <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliğini kullanmak istediğiniz var olan <xref:System.Windows.Forms.ImageList> denetimine ayarlayın.  
  
     Bu özellikler, Özellikler penceresi veya kod ile tasarımcıda ayarlanabilir.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. Düğümün <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özelliklerini ayarlayın. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> özelliği, düğümün normal ve genişletilmiş durumları için gösterilecek resmi belirler ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özelliği, düğümün seçili durumu için görüntülendiğini belirler.  
  
     Bu özellikler kod içinde veya TreeNode Düzenleyicisi içinde ayarlanabilir. TreeNode düzenleyicisini açmak için üç nokta düğmesini (...), Özellikler penceresi <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliğinin yanındaki Visual Studio.](./media/visual-studio-ellipsis-button.png)) Özellikler penceresi ![.  
  
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
- [Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
