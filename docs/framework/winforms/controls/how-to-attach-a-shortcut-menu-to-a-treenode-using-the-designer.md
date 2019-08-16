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
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir TreeNode Öğesine Kısayol Menüsü Ekleme
Windows Forms <xref:System.Windows.Forms.TreeView> denetim, Windows işletim sistemlerindeki Windows Gezgini özelliğinin sol bölmesinde görüntülenen dosya ve klasörlere benzer bir düğüm hiyerarşisi görüntüler. <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> Özelliği ayarlayarak, <xref:System.Windows.Forms.TreeView> denetime sağ tıkladıklarında kullanıcıya bağlama duyarlı işlemler sağlayabilirsiniz. Bir <xref:System.Windows.Forms.ContextMenuStrip> bileşeni tek tek <xref:System.Windows.Forms.TreeNode> öğelerle ilişkilendirerek, denetimlerinize <xref:System.Windows.Forms.TreeView> özelleştirilmiş bir kısayol menü işlevi düzeyi ekleyebilirsiniz.

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Tasarım zamanında bir kısayol menüsünü bir TreeNode ile ilişkilendirmek için

1. Formunuza bir <xref:System.Windows.Forms.TreeView> denetim ekleyin ve sonra gerektiği <xref:System.Windows.Forms.TreeView> gibi düğümleri ekleyin. Daha fazla bilgi için [nasıl yapılır: Windows Forms TreeView denetimiyle](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)düğüm ekleyin ve kaldırın.

2. Formunuza bir <xref:System.Windows.Forms.ContextMenuStrip> bileşen ekleyin ve ardından menü öğelerini, çalışma zamanında kullanılabilir hale getirmek istediğiniz düğüm düzeyi işlemleri temsil eden kısayol menüsüne ekleyin. Daha fazla bilgi için [nasıl yapılır: Bir ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)öğesine menü öğeleri ekleyin.

3. <xref:System.Windows.Forms.TreeView> Denetim için **TreeNodeEditor** iletişim kutusunu yeniden açın, düzenlenecek düğümü seçin ve <xref:System.Windows.Forms.ContextMenuStrip> özelliğini eklediğiniz kısayol menüsü olarak ayarlayın.

4. Bu özellik ayarlandığında, düğüme sağ tıkladığınızda kısayol menüsü görüntülenir.

     Ayrıca, bu menü öğelerinin <xref:System.Windows.Forms.ToolStripItem.Click> olaylarını işlemek için kod yazmak isteyeceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip Denetimi](contextmenustrip-control.md)
