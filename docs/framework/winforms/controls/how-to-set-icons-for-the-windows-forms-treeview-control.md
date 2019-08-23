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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="49cf6-102">Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama</span><span class="sxs-lookup"><span data-stu-id="49cf6-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="49cf6-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetim her bir düğümün yanındaki simgeleri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="49cf6-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="49cf6-104">Simgeler, düğüm metninin hemen soluna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="49cf6-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="49cf6-105">Bu simgeleri görüntülemek için ağaç görünümünü bir <xref:System.Windows.Forms.ImageList> denetimle ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="49cf6-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="49cf6-106">Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeniyle](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)görüntü ekleyin veya kaldırın.</span><span class="sxs-lookup"><span data-stu-id="49cf6-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49cf6-107">Microsoft .NET Framework sürüm 1,1 ' deki bir hata, uygulamanızın çağrı <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>yaptığı durumlarda resimlerin düğümlerde görünmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="49cf6-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49cf6-108">Bu hatayı geçici olarak çözmek için, <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main` yöntemini çağırdıktan <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>hemen sonra çağırın.</span><span class="sxs-lookup"><span data-stu-id="49cf6-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="49cf6-109">Bu hata .NET Framework 2,0 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="49cf6-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="49cf6-110">Görüntüleri ağaç görünümünde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="49cf6-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="49cf6-111">Denetimin özelliğini kullanmak istediğiniz var olan <xref:System.Windows.Forms.ImageList> denetim olarak ayarlayın. <xref:System.Windows.Forms.TreeView.ImageList%2A> <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="49cf6-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="49cf6-112">Bu özellikler, Özellikler penceresi veya kod ile tasarımcıda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="49cf6-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="49cf6-113">Düğümün <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="49cf6-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="49cf6-114">Özelliği, düğümün normal ve genişletilmiş durumları için gösterilecek resmi belirler <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> ve bu özellik, düğümün seçili durumu için görüntülendiğini belirler. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="49cf6-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="49cf6-115">Bu özellikler kod içinde veya TreeNode Düzenleyicisi içinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="49cf6-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="49cf6-116">TreeNode düzenleyicisini açmak için, Özellikler penceresi ![ <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliğinin yanındaki üç nokta düğmesini (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi) tıklatın.</span><span class="sxs-lookup"><span data-stu-id="49cf6-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49cf6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49cf6-117">See also</span></span>

- [<span data-ttu-id="49cf6-118">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="49cf6-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="49cf6-119">Nasıl yapılır: Windows Forms TreeView denetimi ile düğüm ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="49cf6-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="49cf6-120">Nasıl yapılır: Windows Forms TreeView denetiminin tüm düğümlerinde yineleme</span><span class="sxs-lookup"><span data-stu-id="49cf6-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="49cf6-121">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="49cf6-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="49cf6-122">Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="49cf6-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
