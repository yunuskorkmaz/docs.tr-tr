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
ms.openlocfilehash: 2203511e91254c270c59b5d298dd87a5b3737109
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308366"
---
# <a name="how-to-move-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma
Tasarım zamanında, tüm üst düzey menüler ve menü öğeleri, farklı bir konuma taşıyabilirsiniz <xref:System.Windows.Forms.MenuStrip>. Ayrıca, tek tek menü öğeleri üst düzey menüler arasında Taşı veya menü öğeleri içindeki konumunu değiştirebilirsiniz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Üst düzey menü ve menü öğelerinden, üst düzey başka bir konuma taşımak için  
  
1. ' A tıklayın ve taşımak istediğiniz menüsünde sol fare düğmesini basılı tutun.  
  
2. Ekleme noktasını amaçlanan yeni konum önce üst düzey menü sürükleyin ve sol fare düğmesini bırakın.  
  
     Seçili menü ekleme noktasını sağa taşır.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Üst düzey menü ve menü öğelerinden bir açılan konuma taşımak için  
  
1. Taşıma ve CTRL + X tuşlarına basın veya menü sağ tıklayıp istediğiniz menü sol **Kes** kısayol menüsünden.  
  
2. Hedef üst düzey menüsündeki menü öğesi üzerinde istenen yeni konumu sol ve CTRL + V tuşlarına basın veya menü öğesi üzerinde istenen konuma sağ tıklayıp **Yapıştır** kısayol menüsünden.  
  
     Kesme menü, seçili menü öğesini sonra eklenir.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Bir menü öğesi içinde öğeler Koleksiyonu Düzenleyicisi'ni kullanarak bir menüyü taşımak için  
  
1. Taşımak istediğiniz menü öğesini içeren menü sağ tıklayın.  
  
2. Kısayol menüsünden **Düzenle DropDownItems**.  
  
3. İçinde **öğeler Koleksiyonu Düzenleyicisi**, taşımak istediğiniz menü öğesini tıklatın.  
  
4. Menü öğesinin menü içinde taşımak için yukarı ve aşağı ok tuşlarını tıklayın.  
  
5. **Tamam**'ı tıklatın.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Bir menü öğesi içindeki klavyeyi kullanarak taşımak için  
  
1. ALT tuşunu basılı yeniden açın.  
  
2. Tıklayın ve taşımak istediğiniz menü öğesini sol fare düğmesini basılı tutun.  
  
3. Menü öğesi yeni konuma sürükleyin ve sol fare düğmesini bırakın.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Bir menü öğesi için başka bir menüyü taşımak için  
  
1. Taşıma ve CTRL + X tuşlarına basın veya menü öğesini sağ tıklatın ve seçin için istediğiniz menü öğesini sol **Kes** kısayol menüsünden.  
  
2. Kesme menü öğesini içeren menüsünü tıklatın.  
  
3. Önce hedeflenen yeni konum menü öğesini tıklatın ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce bir menü öğesini sağ **Yapıştır** kısayol menüsünden.  
  
     Kesme menü öğesi, seçili bir menü öğesi sonra eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
