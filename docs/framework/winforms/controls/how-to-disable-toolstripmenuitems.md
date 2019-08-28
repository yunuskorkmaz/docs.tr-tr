---
title: "Nasıl yapılır: ToolStripMenuItems'ı Devre Dışı Bırakma"
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
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046220"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems'ı Devre Dışı Bırakma
Kullanıcı etkinliklerine yanıt olarak menü öğelerini etkinleştirip devre dışı bırakarak bir kullanıcının yapabiliriz olan komutları sınırlayabilirsiniz veya genişletebilirsiniz. Menü öğeleri oluşturulduklarında varsayılan olarak etkindir, ancak bu <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özellik aracılığıyla ayarlanabilir. Bu özelliği tasarım zamanında **Özellikler** penceresinde veya program aracılığıyla kod içinde ayarlayarak düzenleyebilirsiniz.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Bir menü öğesini programlı olarak devre dışı bırakmak için  
  
- Menü öğesinin özelliklerini ayarladığınız yöntemi içinde, <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini olarak `false`ayarlamak için kod ekleyin.  
  
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
    > Bir menüdeki ilk veya üst düzey menü öğesini devre dışı bırakmak, menüdeki tüm menü öğelerini gizler, ancak devre dışı bırakır. Benzer şekilde, alt menü öğelerinin bulunduğu bir menü öğesini devre dışı bırakmak alt menü öğelerini gizler, ancak devre dışı bırakır. Belirli bir menüdeki tüm komutlar Kullanıcı için kullanılabilir durumda değilse, tüm menüyü gizleme ve devre dışı bırakma, bu da temiz bir kullanıcı arabirimi sunan için iyi bir programlama uygulaması kabul edilir. Menüyü gizlemeniz ve devre dışı bırakmanız ve menü içindeki her öğe ve alt menü öğesini devre dışı bırakmanız gerekir, çünkü tek tek gizleme, kısayol tuşu aracılığıyla bir menü komutuna erişimi engellemez. Tüm menüyü gizlemek için üst düzey menü öğesinin `false` özelliğiniolarakayarlayın.<xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Nasıl yapılır: ToolStripMenuItems 'ı gizle](how-to-hide-toolstripmenuitems.md)
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
