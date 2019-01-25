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
ms.openlocfilehash: 2516080708bba207c3a1d028f2e5a2411974ae5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705342"
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
- [Nasıl yapılır: Toolstripmenuıtems gizleme](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)
- [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
