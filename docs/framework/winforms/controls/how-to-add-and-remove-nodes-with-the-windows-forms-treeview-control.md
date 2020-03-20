---
title: TreeView Denetimi ile Düğüm Ekleme ve Çıkarma
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
ms.openlocfilehash: f1e74e6d2f827167c32a6955b3010b59cb2f85b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142218"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma
Windows Forms <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.TreeView.Nodes%2A> denetimi, koleksiyonundaki üst düzey düğümleri depolar. Her <xref:System.Windows.Forms.TreeNode> biri de <xref:System.Windows.Forms.TreeNode.Nodes%2A> kendi alt düğümleri saklamak için kendi koleksiyonu vardır. Her iki koleksiyon <xref:System.Windows.Forms.TreeNodeCollection>özelliği de düğüm hiyerarşisinin tek bir düzeyinde düğüm eklemenize, kaldırmanıza ve yeniden düzenlemenize olanak tanıyan standart koleksiyon üyeleri sağlayan türdedir.  
  
### <a name="to-add-nodes-programmatically"></a>Düğümleri programlı olarak eklemek için  
  
1. Ağaç <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> görünümü <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliğiyöntemini kullanın.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Düğümleri programlı olarak kaldırmak için  
  
1. Tek <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> bir düğümü kaldırmak için <xref:System.Windows.Forms.TreeView.Nodes%2A> ağaç görünümü özelliğinin yöntemini <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> veya tüm düğümleri temizlemek için yöntemi kullanın.  
  
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
- [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
