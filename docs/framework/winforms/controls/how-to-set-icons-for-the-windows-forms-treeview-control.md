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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="3f086-102">Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3f086-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="3f086-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetimi her bir düğümün yanındaki simgeleri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3f086-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="3f086-104">Simgeler, düğüm metninin hemen soluna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f086-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="3f086-105">Bu simgeleri görüntülemek için ağaç görünümünü bir <xref:System.Windows.Forms.ImageList> denetimiyle ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f086-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="3f086-106">Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="3f086-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f086-107">Microsoft .NET Framework sürüm 1,1 ' deki bir hata, uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>çağırdığında <xref:System.Windows.Forms.TreeView> düğümlerde resimlerin görünmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="3f086-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f086-108">Bu hatayı geçici olarak çözmek için, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>çağrıldıktan hemen sonra `Main` yönteminizin <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="3f086-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="3f086-109">Bu hata .NET Framework 2,0 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f086-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="3f086-110">Görüntüleri ağaç görünümünde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="3f086-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="3f086-111"><xref:System.Windows.Forms.TreeView> denetiminin <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliğini kullanmak istediğiniz var olan <xref:System.Windows.Forms.ImageList> denetimine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3f086-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="3f086-112">Bu özellikler, Özellikler penceresi veya kod ile tasarımcıda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f086-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="3f086-113">Düğümün <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3f086-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="3f086-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A> özelliği, düğümün normal ve genişletilmiş durumları için gösterilecek resmi belirler ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özelliği, düğümün seçili durumu için görüntülendiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="3f086-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="3f086-115">Bu özellikler kod içinde veya TreeNode Düzenleyicisi içinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f086-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="3f086-116">TreeNode düzenleyicisini açmak için üç nokta düğmesini (...), Özellikler penceresi <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliğinin yanındaki Visual Studio.](./media/visual-studio-ellipsis-button.png)) Özellikler penceresi ![.</span><span class="sxs-lookup"><span data-stu-id="3f086-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f086-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f086-117">See also</span></span>

- [<span data-ttu-id="3f086-118">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3f086-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="3f086-119">Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="3f086-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="3f086-120">Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme</span><span class="sxs-lookup"><span data-stu-id="3f086-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="3f086-121">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="3f086-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="3f086-122">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3f086-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
