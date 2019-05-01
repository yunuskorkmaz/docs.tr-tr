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
ms.openlocfilehash: f818cccb3103866af993f1aff527a9c1a7c82109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053021"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme
Windows Forms <xref:System.Windows.Forms.TreeView> denetimi düğümleri, Windows Explorer'ın sol bölmesinde görüntülenen klasörleri ve dosyaları benzer hiyerarşisini görüntüler. Ayarlayarak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliği sağlayabileceğiniz bağlama duyarlı işlemler kullanıcıya bunlar sağ tıkladığınızda <xref:System.Windows.Forms.TreeView> denetimi. İlişkilendirerek bir <xref:System.Windows.Forms.ContextMenuStrip> tek bileşeniyle <xref:System.Windows.Forms.TreeNode> öğeleri, özelleştirilmiş bir kısayol menüsü işlevsellik düzeyini ekleyebilirsiniz, <xref:System.Windows.Forms.TreeView> kontrol eder.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Bir kısayol menüsü TreeNode ile programlı olarak ilişkilendirmek için  
  
1. Örneği bir <xref:System.Windows.Forms.TreeView> denetimi ile ilgili özellik ayarları, bir kök oluşturmayı <xref:System.Windows.Forms.TreeNode>ve ardından alt düğümler ekleyin.  
  
2. Örneği bir <xref:System.Windows.Forms.ContextMenuStrip> bileşeni ve ardından bir <xref:System.Windows.Forms.ToolStripMenuItem> çalışma zamanında kullanılabilir hale getirmek istediğiniz her bir işlem için.  
  
3. Ayarlama <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> özelliğini uygun <xref:System.Windows.Forms.TreeNode> oluşturduğunuz kısayol menüsü.  
  
4. Bu özelliği ayarlandığında, düğümüne sağ tıklayın, kısayol menüsünde görüntülenir.  
  
 Aşağıdaki kod örneği bir temel oluşturur <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ContextMenuStrip> kök ile ilişkili <xref:System.Windows.Forms.TreeNode> , <xref:System.Windows.Forms.TreeView>. Uygun bu menü seçenekleri özelleştirmek ihtiyacınız olacak <xref:System.Windows.Forms.TreeView> geliştirdiğiniz. Ayrıca, işlemek üzere kod yazmak isteyeceksiniz <xref:System.Windows.Forms.ToolStripItem.Click> bu menü öğeleri için olayları.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContextMenuStrip>
- [TreeView Denetimi](treeview-control-windows-forms.md)
