---
title: "Nasıl yapılır: ToolStripMenuItems'ni Devre Dışı Bırakma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: 20d0e13642aac3004a31ff416318cf6723207379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532034"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems'ni Devre Dışı Bırakma
Sınırlandırmak veya bir kullanıcı tarafından etkinleştirme ve kullanıcı etkinlikleri yanıtta menü öğelerini devre dışı bırakma hale getirebilir komutları genişletebilir. Menü öğeleri, varsayılan olarak etkinleştirilir, oluşturuldukları, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği. Tasarım zamanında bu özellik işleyebilir **özellikleri** penceresi veya programlı olarak ayarlayarak bu kodu.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Menü öğesi program aracılığıyla devre dışı bırakmak için  
  
-   Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak için kod ekleme <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğine `false`.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  Bir menüdeki ilk ya da üst düzey menü öğesini devre dışı bırakma menüsünün içinde yer alan tüm menü öğelerini gizler, ancak bunları devre dışı bırakmaz. Benzer şekilde, alt öğelerine sahip bir menü öğesini devre dışı bırakma alt öğeleri gizler, ancak bunları devre dışı bırakmaz. Verilen menüsünde tüm komutlar kullanıcıya kullanılabilir durumda değilse, bu bir temiz kullanıcı arabirimi sunar gibi Gizle hem tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir. Gizleme ve menüsünü devre dışı bırak ve tek başına gizleme erişimi için bir kısayol tuşu aracılığıyla menü komutu engellemez çünkü her öğeyi ve alt öğesi menüde devre dışı bırakmak gerekir. Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> bir üst düzey menü öğesine özelliğinin `false` tüm menü gizlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Nasıl yapılır: ToolStripMenuItems Gizleme](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
