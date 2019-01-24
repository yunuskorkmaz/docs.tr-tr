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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="5df08-102">Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama</span><span class="sxs-lookup"><span data-stu-id="5df08-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="5df08-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetim her düğümün yanındaki simge görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5df08-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="5df08-104">Simgeleri hemen düğüm metnin solunda yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5df08-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="5df08-105">Bu simgeleri göstermek için ağaç görünümü ile ilişkilendirmek bir <xref:System.Windows.Forms.ImageList> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5df08-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="5df08-106">Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="5df08-106">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5df08-107">Microsoft .NET Framework sürüm 1.1 bir hata görüntüleri üzerinde görüntülenmesini engeller <xref:System.Windows.Forms.TreeView> uygulamanız çağırdığında düğümleri <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5df08-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5df08-108">Bu hata geçici olarak çözmek için çağrı <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> içinde `Main` yöntemi çağırma hemen sonra <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="5df08-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="5df08-109">İçinde bu hatanın giderilmesidir [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5df08-109">This bug is fixed in [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="5df08-110">Görüntüleri bir ağaç görünümünde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="5df08-110">To display images in a tree view</span></span>  
  
1.  <span data-ttu-id="5df08-111">Ayarlama <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.ImageList%2A> varolan özellik <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz denetimi.</span><span class="sxs-lookup"><span data-stu-id="5df08-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="5df08-112">Bu özellikleri Özellikler penceresi ile Tasarımcısı'nda veya kod içinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5df08-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  <span data-ttu-id="5df08-113">Düğümün ayarlamak <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5df08-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="5df08-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Düğümün normal ve genişletilmiş durumları için görüntülenen resim özelliği belirler ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> düğümün Seçili durum için görüntülenen resim özelliği belirler.</span><span class="sxs-lookup"><span data-stu-id="5df08-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="5df08-115">Bu özellikler, kod veya TreeNode Düzenleyicisi'nin içinden ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5df08-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="5df08-116">TreeNode Düzenleyicisi'ni açmak için üç nokta düğmesini ( ![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> Özellikler penceresinde özelliği.</span><span class="sxs-lookup"><span data-stu-id="5df08-116">To open the TreeNode Editor, click the ellipsis button ( ![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5df08-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5df08-117">See also</span></span>
- [<span data-ttu-id="5df08-118">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5df08-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="5df08-119">Nasıl yapılır: Ekleme ve Windows Forms TreeView denetimi ile düğüm kaldırma</span><span class="sxs-lookup"><span data-stu-id="5df08-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="5df08-120">Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme</span><span class="sxs-lookup"><span data-stu-id="5df08-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="5df08-121">Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="5df08-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="5df08-122">Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme</span><span class="sxs-lookup"><span data-stu-id="5df08-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
