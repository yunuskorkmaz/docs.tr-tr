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
ms.openlocfilehash: 4cbb5fbdb24790a7ddbce5c38060703c7ba7024a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326898"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma
Windows Forms <xref:System.Windows.Forms.TreeView> denetimi üst düzey düğümlerin depolar, <xref:System.Windows.Forms.TreeView.Nodes%2A> koleksiyonu. Her <xref:System.Windows.Forms.TreeNode> Ayrıca kendi bölümüne sahiptir <xref:System.Windows.Forms.TreeNode.Nodes%2A> alt düğümlerinden depolamak için koleksiyon. Her iki koleksiyon özellikleri türlerinin <xref:System.Windows.Forms.TreeNodeCollection>, eklemenize olanak sağlayan standart koleksiyon üyeleri kaldırın ve düğümler tek bir düğüm hiyerarşi düzeyini yeniden sağlar.  
  
### <a name="to-add-nodes-programmatically"></a>Program aracılığıyla düğümler eklemek için  
  
1. Kullanım <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> ağaç görünümünün yöntemi <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Düğümleri program aracılığıyla kaldırma  
  
1. Kullanım <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> ağaç görünümünün yöntemi <xref:System.Windows.Forms.TreeView.Nodes%2A> tek bir düğüm kaldırmak için özellik veya <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> tüm düğümleri temizlemek için yöntemi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](add-custom-information-to-a-treeview-or-listview-control-wf.md)
