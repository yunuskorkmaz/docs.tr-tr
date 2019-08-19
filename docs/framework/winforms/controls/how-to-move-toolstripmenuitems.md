---
title: 'Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039803"
---
# <a name="how-to-move-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma
Tasarım zamanında, en üst düzey menülerin ve menü öğelerinin tamamını üzerinde <xref:System.Windows.Forms.MenuStrip>farklı bir yere taşıyabilirsiniz. Ayrıca, ayrı menü öğelerini üst düzey menüler arasında taşıyabilir veya menüdeki menü öğelerinin konumunu değiştirebilirsiniz.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Üst düzey menüyü ve menü öğelerini başka bir üst düzey konuma taşımak için

1. Taşımak istediğiniz menüdeki sol fare düğmesine tıklayın ve basılı tutun.

2. Ekleme noktasını amaçlanan yeni konumdan önce olan en üst düzey menüye sürükleyin ve sol fare düğmesini bırakın.

     Seçilen menü, ekleme noktasının sağına gider.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Üst düzey menüyü ve menü öğelerini açılan bir konuma taşımak için

1. Taşımak istediğiniz menüye sol tıklayın ve CTRL + X tuşlarına basın ya da menüye sağ tıklayıp kısayol menüsünden **Kes** ' i seçin.

2. Hedef üst düzey menüsünde, hedeflenen yeni konumun üzerindeki menü öğesine sağ tıklayın ve CTRL + V tuşlarına basın veya hedeflenen yeni konumun üzerindeki menü öğesine sağ tıklayıp kısayol menüsünden **Yapıştır** ' ı seçin.

     Kestiğiniz menü, seçilen menü öğesinden sonra eklenir.

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Öğeler koleksiyonu düzenleyicisini kullanarak bir menü öğesini bir menü içinde taşımak için

1. Taşımak istediğiniz menü öğesini içeren menüyü sağ tıklayın.

2. Kısayol menüsünde **DropDownItems Düzenle**' yi seçin.

3. **Öğe koleksiyonu düzenleyicisinde**, taşımak istediğiniz menü öğesine sol tıklayın.

4. Menüdeki menü öğesini taşımak için yukarı ve aşağı ok tuşlarına basın.

5.           **Tamam**'ı tıklatın.

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Bir menü öğesini klavyeyi kullanarak bir menü içinde taşımak için

1. ALT tuşuna basın ve basılı tutun.

2. Taşımak istediğiniz menü öğesindeki sol fare düğmesine tıklayın ve basılı tutun.

3. Menü öğesini yeni konuma sürükleyin ve sol fare düğmesini bırakın.

## <a name="to-move-a-menu-item-to-another-menu"></a>Bir menü öğesini başka bir menüye taşımak için

1. Taşımak istediğiniz menü öğesini sol tıklatın ve CTRL + X tuşlarına basın veya menü öğesine sağ tıklayıp kısayol menüsünden **Kes** ' i seçin.

2. Kestiğiniz menü öğesini içerecek menüye sol tıklayın.

3. Hedeflenen yeni konumdan önceki menü öğesine sağ tıklayın ve CTRL + V tuşlarına basın veya amaçlanan yeni konumdan önce gelen menü öğesine sağ tıklayıp kısayol menüsünden **Yapıştır** ' ı seçin.

     Kestiğiniz menü öğesi seçili menü öğesinden sonra eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
