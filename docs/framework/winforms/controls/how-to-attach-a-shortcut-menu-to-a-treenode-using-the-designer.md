---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir TreeNode Öğesine Kısayol Menüsü Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040453"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="8a536-102">Nasıl yapılır: Tasarımcı Kullanarak bir TreeNode Öğesine Kısayol Menüsü Ekleme</span><span class="sxs-lookup"><span data-stu-id="8a536-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="8a536-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetim, Windows işletim sistemlerindeki Windows Gezgini özelliğinin sol bölmesinde görüntülenen dosya ve klasörlere benzer bir düğüm hiyerarşisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8a536-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="8a536-104"><xref:System.Windows.Forms.Control.ContextMenuStrip%2A> Özelliği ayarlayarak, <xref:System.Windows.Forms.TreeView> denetime sağ tıkladıklarında kullanıcıya bağlama duyarlı işlemler sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a536-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="8a536-105">Bir <xref:System.Windows.Forms.ContextMenuStrip> bileşeni tek tek <xref:System.Windows.Forms.TreeNode> öğelerle ilişkilendirerek, denetimlerinize <xref:System.Windows.Forms.TreeView> özelleştirilmiş bir kısayol menü işlevi düzeyi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a536-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="8a536-106">Tasarım zamanında bir kısayol menüsünü bir TreeNode ile ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="8a536-106">To associate a shortcut menu with a TreeNode at design time</span></span>

1. <span data-ttu-id="8a536-107">Formunuza bir <xref:System.Windows.Forms.TreeView> denetim ekleyin ve sonra gerektiği <xref:System.Windows.Forms.TreeView> gibi düğümleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a536-107">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="8a536-108">Daha fazla bilgi için [nasıl yapılır: Windows Forms TreeView denetimiyle](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)düğüm ekleyin ve kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8a536-108">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>

2. <span data-ttu-id="8a536-109">Formunuza bir <xref:System.Windows.Forms.ContextMenuStrip> bileşen ekleyin ve ardından menü öğelerini, çalışma zamanında kullanılabilir hale getirmek istediğiniz düğüm düzeyi işlemleri temsil eden kısayol menüsüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a536-109">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="8a536-110">Daha fazla bilgi için [nasıl yapılır: Bir ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)öğesine menü öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a536-110">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>

3. <span data-ttu-id="8a536-111"><xref:System.Windows.Forms.TreeView> Denetim için **TreeNodeEditor** iletişim kutusunu yeniden açın, düzenlenecek düğümü seçin ve <xref:System.Windows.Forms.ContextMenuStrip> özelliğini eklediğiniz kısayol menüsü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a536-111">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>

4. <span data-ttu-id="8a536-112">Bu özellik ayarlandığında, düğüme sağ tıkladığınızda kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8a536-112">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>

     <span data-ttu-id="8a536-113">Ayrıca, bu menü öğelerinin <xref:System.Windows.Forms.ToolStripItem.Click> olaylarını işlemek için kod yazmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8a536-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a536-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a536-114">See also</span></span>

- [<span data-ttu-id="8a536-115">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="8a536-115">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="8a536-116">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8a536-116">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="8a536-117">ContextMenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="8a536-117">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
