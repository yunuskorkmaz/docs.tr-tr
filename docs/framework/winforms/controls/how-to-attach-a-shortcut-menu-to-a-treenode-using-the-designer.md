---
title: 'Nasıl yapılır: Tasarımcı kullanarak bir TreeNode öğesine kısayol menüsü ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: aa161af65b7e8e1f3636398cd02139b5623eb154
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721989"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak bir TreeNode öğesine kısayol menüsü ekleme
Windows Forms <xref:System.Windows.Forms.TreeView> denetimi düğümleri, Windows işletim sistemlerinde Windows Explorer özelliğinin sol bölmede görüntülenen klasörleri ve dosyaları benzer hiyerarşisini görüntüler. Ayarlayarak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliği sağlayabileceğiniz bağlama duyarlı işlemler kullanıcıya bunlar sağ tıkladığınızda <xref:System.Windows.Forms.TreeView> denetimi. İlişkilendirerek bir <xref:System.Windows.Forms.ContextMenuStrip> tek bileşeniyle <xref:System.Windows.Forms.TreeNode> öğeleri, özelleştirilmiş bir kısayol menüsü işlevsellik düzeyini ekleyebilirsiniz, <xref:System.Windows.Forms.TreeView> kontrol eder.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Bir kısayol menü tasarım zamanında bir TreeNode ile ilişkilendirmek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.TreeView> Formunuza denetim ve ardından düğüm ekleme <xref:System.Windows.Forms.TreeView> gerektiğinde. Daha fazla bilgi için [nasıl yapılır: Ekle ve Kaldır düğümleri ile Windows Forms TreeView denetimi](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Ekleme bir <xref:System.Windows.Forms.ContextMenuStrip> formunuza, bileşen ve çalışma zamanında kullanılabilir hale getirmek istediğiniz nodu düzeyinde işlemleri temsil etmekte kısayol menüsünü menü öğeleri ekleyin. Daha fazla bilgi için [nasıl yapılır: Bir Contextmenustrip'e menü öğeleri ekleme](how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Yeniden **TreeNodeEditor** iletişim kutusu için <xref:System.Windows.Forms.TreeView> denetleme, düzenleme ve ayarlamak için düğümü seçin, <xref:System.Windows.Forms.ContextMenuStrip> özelliğini, eklediğiniz kısayol menüsü.  
  
4.  Bu özelliği ayarlandığında, düğümüne sağ tıklayın, kısayol menüsünde görüntülenir.  
  
     Ayrıca, işlemek üzere kod yazmak isteyeceksiniz <xref:System.Windows.Forms.ToolStripItem.Click> bu menü öğeleri için olayları.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TreeView Denetimi](treeview-control-windows-forms.md)
- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip Denetimi](contextmenustrip-control.md)
