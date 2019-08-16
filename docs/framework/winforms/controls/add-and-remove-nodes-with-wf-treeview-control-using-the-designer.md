---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040071"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="fd134-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="fd134-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="fd134-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetimi düğümleri hiyerarşik bir şekilde görüntülediğinden, bir düğüm eklenirken, üst düğümünün ne olduğuna dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd134-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="fd134-104">Aşağıdaki yordam, bir <xref:System.Windows.Forms.TreeView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fd134-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="fd134-105">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fd134-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="fd134-106">Tasarımcıya düğüm eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="fd134-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="fd134-107"><xref:System.Windows.Forms.TreeView> Denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="fd134-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="fd134-108">**Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.TreeView.Nodes%2A> yanındaki Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi (...) üç nokta (...) düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fd134-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="fd134-109">**TreeNode Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="fd134-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="fd134-110">Düğüm eklemek için bir kök düğümün mevcut olması gerekir; birisi yoksa, önce **kök Ekle** düğmesine tıklayarak bir kök eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd134-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="fd134-111">Ardından, kökü veya diğer düğümleri seçerek ve **alt Ekle** düğmesine tıklayarak alt düğümler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd134-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="fd134-112">Düğümleri silmek için, silinecek düğümü seçin ve **Sil** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fd134-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd134-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd134-113">See also</span></span>

- [<span data-ttu-id="fd134-114">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="fd134-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="fd134-115">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fd134-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="fd134-116">Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama</span><span class="sxs-lookup"><span data-stu-id="fd134-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="fd134-117">Nasıl yapılır: Windows Forms TreeView denetiminin tüm düğümlerinde yineleme</span><span class="sxs-lookup"><span data-stu-id="fd134-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="fd134-118">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="fd134-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="fd134-119">Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fd134-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
