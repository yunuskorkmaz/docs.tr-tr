---
title: 'Nasıl yapılır: Toolstripmenuıtems öğelerini devre dışı bırak'
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
ms.openlocfilehash: 3c18935239a4355d5416a0a79d0fa9f5c504cc7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720221"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Nasıl yapılır: Toolstripmenuıtems öğelerini devre dışı bırak
Sınırlamak veya bir kullanıcı, kullanıcı etkinlikleri için yanıt menü öğelerini devre dışı bırakma ve etkinleştirme yapabilir komutları alanlarını genişletmeniz mümkün değildir. Menü öğeleri, varsayılan olarak etkinleştirilir, bunlar oluşturulur, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği. Bu özellik tasarım zamanında işleyebileceğiniz **özellikleri** penceresi veya program aracılığıyla kod içinde ayarlama.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Program aracılığıyla bir menü öğesi devre dışı bırakmak için  
  
-   Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak üzere kod eklemek <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini `false`.  
  
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
    >  Bir menü ilk veya üst düzey menü öğesi devre dışı bırakma içinde menüyü içeren bütün menü öğelerini gizler, ancak bunları devre dışı bırakmaz. Benzer şekilde, alt öğelerine sahip bir menü öğesi devre dışı bırakma alt öğeleri gizler, ancak bunları devre dışı bırakmaz. Kullanıcıya verilen menüsündeki tüm komutları kullanılamıyorsa, bunu bir temiz kullanıcı arabirimi sunar gibi hem gizlemek ve tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir. Gizleme ve menüsünü devre dışı bırak ve tek başına gizleme erişim için bir kısayol tuşu ile bir menü komutu engellemez çünkü her öğe ve alt öğesi menüsündeki devre dışı bırakmak gerekir. Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği için bir üst düzey menü öğesinin `false` tüm menü gizlemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Nasıl yapılır: Toolstripmenuıtems gizleme](how-to-hide-toolstripmenuitems.md)
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
