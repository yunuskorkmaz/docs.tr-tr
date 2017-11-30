---
title: "Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3814e95ad2d91157181682984fc9b53254ba813
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="65faf-102">Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme</span><span class="sxs-lookup"><span data-stu-id="65faf-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="65faf-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetimi, bir hiyerarşi düğümlerinin, dosya ve klasörleri Windows Explorer'ın sol bölmesinde görüntülenen benzer görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65faf-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="65faf-104">Ayarlayarak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliği sağlayabileceğiniz bağlama duyarlı işlemleri kullanıcıya bunlar sağ tıklattığınızda <xref:System.Windows.Forms.TreeView> denetim.</span><span class="sxs-lookup"><span data-stu-id="65faf-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="65faf-105">İlişkilendirerek bir <xref:System.Windows.Forms.ContextMenuStrip> tek bileşeniyle <xref:System.Windows.Forms.TreeNode> öğeleri kısayol menüsünün işlevselliği için özelleştirilmiş bir düzeyini ekleyebilirsiniz, <xref:System.Windows.Forms.TreeView> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="65faf-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="65faf-106">Bir kısayol menüsü program aracılığıyla bir TreeNode ile ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="65faf-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="65faf-107">Örneği bir <xref:System.Windows.Forms.TreeView> denetiminde uygun özellik ayarlarla, bir kök oluşturma <xref:System.Windows.Forms.TreeNode>ve ardından alt düğümler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65faf-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="65faf-108">Örneği bir <xref:System.Windows.Forms.ContextMenuStrip> bileşeni ve ardından ekleyin bir <xref:System.Windows.Forms.ToolStripMenuItem> çalışma zamanında kullanılabilir hale getirmek istediğiniz her bir işlemin.</span><span class="sxs-lookup"><span data-stu-id="65faf-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="65faf-109">Ayarlama <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> uygun özelliğinin <xref:System.Windows.Forms.TreeNode> oluşturduğunuz kısayol menüsü.</span><span class="sxs-lookup"><span data-stu-id="65faf-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="65faf-110">Bu özelliği ayarlandığında düğümünü sağ tıklattığınızda kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65faf-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="65faf-111">Aşağıdaki kod örneğinde bir temel oluşturur <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ContextMenuStrip> kök ile ilişkili <xref:System.Windows.Forms.TreeNode> , <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="65faf-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="65faf-112">Menü seçeneklerine uyan olanlar özelleştirmeniz gerekir <xref:System.Windows.Forms.TreeView> geliştirdiğinize.</span><span class="sxs-lookup"><span data-stu-id="65faf-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="65faf-113">Ayrıca, işlemek için kod yazma isteyeceksiniz <xref:System.Windows.Forms.ToolStripItem.Click> bu menü öğeleri için olaylar.</span><span class="sxs-lookup"><span data-stu-id="65faf-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="65faf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65faf-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [<span data-ttu-id="65faf-115">TreeView denetimi</span><span class="sxs-lookup"><span data-stu-id="65faf-115">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
