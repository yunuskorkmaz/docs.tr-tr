---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 692b6c11f6d58c52a0af29ed04ada45c48cae058
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046233"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma
Kullanıcı etkinliklerine yanıt olarak menü öğelerini etkinleştirip devre dışı bırakarak bir kullanıcının yapabiliriz olan komutları sınırlayabilirsiniz veya genişletebilirsiniz. Menü öğeleri oluşturulduklarında varsayılan olarak etkindir, ancak bu <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özellik aracılığıyla ayarlanabilir. Bu özelliği tasarım zamanında **Özellikler** penceresinde veya program aracılığıyla kod içinde ayarlayarak düzenleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)'ı devre dışı bırakın.

## <a name="to-disable-a-menu-item-at-design-time"></a>Tasarım zamanında bir menü öğesini devre dışı bırakmak için

1. Formda menü öğesi seçiliyken, <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini olarak `false`ayarlayın.

    > [!TIP]
    > Bir menüdeki ilk veya üst düzey menü öğesini devre dışı bırakmak, menüde bulunan tüm menü öğelerini devre dışı bırakır. Benzer şekilde, alt menü öğelerinin bulunduğu bir menü öğesini devre dışı bırakmak alt menü öğelerini devre dışı bırakır Belirli bir menüdeki tüm komutlar Kullanıcı için kullanılabilir durumda değilse, tüm menüyü gizleme ve devre dışı bırakma, bu da temiz bir kullanıcı arabirimi sunan için iyi bir programlama uygulaması kabul edilir. Yalnızca gizleme menü komutuna kısayol tuşu aracılığıyla erişimi önlememek üzere menüyü gizlemeniz ve devre dışı bırakmanız gerekir. Tüm menüyü gizlemek için üst düzey menü öğesinin `false` özelliğiniolarakayarlayın.<xref:System.Windows.Forms.ToolStripItem.Visible%2A>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Nasıl yapılır: ToolStripMenuItems 'ı gizle](how-to-hide-toolstripmenuitems.md)
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
