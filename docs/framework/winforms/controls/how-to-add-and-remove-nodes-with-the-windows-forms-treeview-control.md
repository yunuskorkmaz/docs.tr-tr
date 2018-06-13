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
ms.openlocfilehash: 2491f4d4c40ea412ee42f8cd99c4c8682baa94a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525944"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma
Windows Forms <xref:System.Windows.Forms.TreeView> denetim depolar en üst düzey düğümlerin kendi <xref:System.Windows.Forms.TreeView.Nodes%2A> koleksiyonu. Her <xref:System.Windows.Forms.TreeNode> Ayrıca kendi sahip <xref:System.Windows.Forms.TreeNode.Nodes%2A> alt düğümlerinden depolamak için koleksiyon. Her iki koleksiyon özellikleri türlerinin <xref:System.Windows.Forms.TreeNodeCollection>, eklemenize olanak sağlayan standart koleksiyon üyeleri kaldırın ve düğüm hiyerarşisinin tek bir düzeyde düğümleri yeniden sağlar.  
  
### <a name="to-add-nodes-programmatically"></a>Program aracılığıyla düğümleri eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> ağaç görünümün yöntemi <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.  
  
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
  
1.  Kullanım <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> ağaç görünümün yöntemi <xref:System.Windows.Forms.TreeView.Nodes%2A> tek bir düğüm kaldırmak için özellik veya <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> tüm düğümleri temizlemek için yöntem.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
