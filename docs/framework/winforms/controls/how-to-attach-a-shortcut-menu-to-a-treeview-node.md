---
title: 'Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 737e74184b0763ed84b4e585f2508d69944d0e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme
Windows Forms <xref:System.Windows.Forms.TreeView> denetimi, bir hiyerarşi düğümlerinin, dosya ve klasörleri Windows Explorer'ın sol bölmesinde görüntülenen benzer görüntüler. Ayarlayarak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliği sağlayabileceğiniz bağlama duyarlı işlemleri kullanıcıya bunlar sağ tıklattığınızda <xref:System.Windows.Forms.TreeView> denetim. İlişkilendirerek bir <xref:System.Windows.Forms.ContextMenuStrip> tek bileşeniyle <xref:System.Windows.Forms.TreeNode> öğeleri kısayol menüsünün işlevselliği için özelleştirilmiş bir düzeyini ekleyebilirsiniz, <xref:System.Windows.Forms.TreeView> kontrol eder.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Bir kısayol menüsü program aracılığıyla bir TreeNode ile ilişkilendirmek için  
  
1.  Örneği bir <xref:System.Windows.Forms.TreeView> denetiminde uygun özellik ayarlarla, bir kök oluşturma <xref:System.Windows.Forms.TreeNode>ve ardından alt düğümler ekleyin.  
  
2.  Örneği bir <xref:System.Windows.Forms.ContextMenuStrip> bileşeni ve ardından ekleyin bir <xref:System.Windows.Forms.ToolStripMenuItem> çalışma zamanında kullanılabilir hale getirmek istediğiniz her bir işlemin.  
  
3.  Ayarlama <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> uygun özelliğinin <xref:System.Windows.Forms.TreeNode> oluşturduğunuz kısayol menüsü.  
  
4.  Bu özelliği ayarlandığında düğümünü sağ tıklattığınızda kısayol menüsü görüntülenir.  
  
 Aşağıdaki kod örneğinde bir temel oluşturur <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ContextMenuStrip> kök ile ilişkili <xref:System.Windows.Forms.TreeNode> , <xref:System.Windows.Forms.TreeView>. Menü seçeneklerine uyan olanlar özelleştirmeniz gerekir <xref:System.Windows.Forms.TreeView> geliştirdiğinize. Ayrıca, işlemek için kod yazma isteyeceksiniz <xref:System.Windows.Forms.ToolStripItem.Click> bu menü öğeleri için olaylar.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
