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
ms.openlocfilehash: 12b8354890f0ba613b35615dc5cf3a5b3555e7ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097635"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="3b7a2-102">Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3b7a2-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="3b7a2-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetim her düğümün yanındaki simge görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="3b7a2-104">Simgeleri hemen düğüm metnin solunda yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="3b7a2-105">Bu simgeleri göstermek için ağaç görünümü ile ilişkilendirmek bir <xref:System.Windows.Forms.ImageList> denetimi.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="3b7a2-106">Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="3b7a2-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b7a2-107">Microsoft .NET Framework sürüm 1.1 bir hata görüntüleri üzerinde görüntülenmesini engeller <xref:System.Windows.Forms.TreeView> uygulamanız çağırdığında düğümleri <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3b7a2-108">Bu hata geçici olarak çözmek için çağrı <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> içinde `Main` yöntemi çağırma hemen sonra <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="3b7a2-109">İçinde bu hatanın giderilmesidir [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b7a2-109">This bug is fixed in [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="3b7a2-110">Görüntüleri bir ağaç görünümünde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="3b7a2-110">To display images in a tree view</span></span>  
  
1.  <span data-ttu-id="3b7a2-111">Ayarlama <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.ImageList%2A> varolan özellik <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz denetimi.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="3b7a2-112">Bu özellikleri Özellikler penceresi ile Tasarımcısı'nda veya kod içinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  <span data-ttu-id="3b7a2-113">Düğümün ayarlamak <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="3b7a2-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Düğümün normal ve genişletilmiş durumları için görüntülenen resim özelliği belirler ve <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> düğümün Seçili durum için görüntülenen resim özelliği belirler.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="3b7a2-115">Bu özellikler, kod veya TreeNode Düzenleyicisi'nin içinden ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="3b7a2-116">TreeNode Düzenleyicisi'ni açmak için üç nokta düğmesini ( ![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> Özellikler penceresinde özelliği.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-116">To open the TreeNode Editor, click the ellipsis button ( ![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b7a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b7a2-117">See also</span></span>

- [<span data-ttu-id="3b7a2-118">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b7a2-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="3b7a2-119">Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="3b7a2-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="3b7a2-120">Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme</span><span class="sxs-lookup"><span data-stu-id="3b7a2-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="3b7a2-121">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="3b7a2-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="3b7a2-122">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3b7a2-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
