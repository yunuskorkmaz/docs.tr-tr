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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909805"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama
Windows Forms <xref:System.Windows.Forms.TreeView> denetim her bir düğümün yanındaki simgeleri görüntüleyebilir. Simgeler, düğüm metninin hemen soluna yerleştirilir. Bu simgeleri görüntülemek için ağaç görünümünü bir <xref:System.Windows.Forms.ImageList> denetimle ilişkilendirmeniz gerekir. Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeniyle](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)görüntü ekleyin veya kaldırın.  
  
> [!NOTE]
> Microsoft .NET Framework sürüm 1,1 ' deki bir hata, uygulamanızın çağrı <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>yaptığı durumlarda resimlerin düğümlerde görünmesini engeller. Bu hatayı geçici olarak çözmek için, <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main` yöntemini çağırdıktan <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>hemen sonra çağırın. Bu hata .NET Framework 2,0 ' de düzeltilmiştir.  
  
### <a name="to-display-images-in-a-tree-view"></a>Görüntüleri ağaç görünümünde görüntülemek için  
  
1. Denetimin özelliğini kullanmak istediğiniz var olan <xref:System.Windows.Forms.ImageList> denetim olarak ayarlayın. <xref:System.Windows.Forms.TreeView.ImageList%2A> <xref:System.Windows.Forms.TreeView>  
  
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
  
2. Düğümün <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özelliklerini ayarlayın. Özelliği, düğümün normal ve genişletilmiş durumları için gösterilecek resmi belirler <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> ve bu özellik, düğümün seçili durumu için görüntülendiğini belirler. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A>  
  
     Bu özellikler kod içinde veya TreeNode Düzenleyicisi içinde ayarlanabilir. TreeNode düzenleyicisini açmak için, Özellikler penceresi ![ <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliğinin yanındaki üç nokta düğmesini (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi) tıklatın.  
  
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
- [Nasıl yapılır: Windows Forms TreeView denetimi ile düğüm ekleme ve kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
