---
title: 'Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 1849e3ae88b9805f74b2f792ad53b02aa87e6569
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209521"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="58539-102">Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="58539-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="58539-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetimi üst düzey düğümlerin depolar, <xref:System.Windows.Forms.TreeView.Nodes%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="58539-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="58539-104">Her <xref:System.Windows.Forms.TreeNode> Ayrıca kendi bölümüne sahiptir <xref:System.Windows.Forms.TreeNode.Nodes%2A> alt düğümlerinden depolamak için koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="58539-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="58539-105">Her iki koleksiyon özellikleri türlerinin <xref:System.Windows.Forms.TreeNodeCollection>, eklemenize olanak sağlayan standart koleksiyon üyeleri kaldırın ve düğümler tek bir düğüm hiyerarşi düzeyini yeniden sağlar.</span><span class="sxs-lookup"><span data-stu-id="58539-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="58539-106">Program aracılığıyla düğümler eklemek için</span><span class="sxs-lookup"><span data-stu-id="58539-106">To add nodes programmatically</span></span>  
  
1.  <span data-ttu-id="58539-107">Kullanım <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> ağaç görünümünün yöntemi <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="58539-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="58539-108">Düğümleri program aracılığıyla kaldırma</span><span class="sxs-lookup"><span data-stu-id="58539-108">To remove nodes programmatically</span></span>  
  
1.  <span data-ttu-id="58539-109">Kullanım <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> ağaç görünümünün yöntemi <xref:System.Windows.Forms.TreeView.Nodes%2A> tek bir düğüm kaldırmak için özellik veya <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> tüm düğümleri temizlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58539-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="58539-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58539-110">See also</span></span>

- [<span data-ttu-id="58539-111">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="58539-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="58539-112">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58539-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="58539-113">Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama</span><span class="sxs-lookup"><span data-stu-id="58539-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="58539-114">Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme</span><span class="sxs-lookup"><span data-stu-id="58539-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="58539-115">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="58539-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="58539-116">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="58539-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
