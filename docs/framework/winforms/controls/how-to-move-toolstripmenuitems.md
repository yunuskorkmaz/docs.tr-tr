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
ms.openlocfilehash: 5cfaf87a59d27678cfb786633ed4c9a9f66bac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-move-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma
Tasarım zamanında tüm üst düzey menü ve bunların menü öğeleri farklı bir konuma taşıyabilir <xref:System.Windows.Forms.MenuStrip>. Ayrıca, tek tek menü öğeleri üst düzey menüler arasında Taşı veya menü öğeleri menü içinde konumunu değiştirebilirsiniz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Bir üst düzey menü ve menü öğelerinden en üst düzey başka bir konuma taşımak için  
  
1.  Tıklayın ve taşımak istediğiniz menüsünde sol fare düğmesini basılı tutun.  
  
2.  Hedeflenen yeni konumu önce en üst düzey menü ekleme noktasını sürükleyin ve sol fare düğmesini bırakın.  
  
     Seçili menü ekleme noktasını sağa taşır.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>En üst düzey menü ve menü öğelerinin açılan bir konuma taşımak için  
  
1.  Taşıma ve CTRL + X tuşlarına basın veya menüyü sağ tıklatın ve seçmek için istediğiniz menüyü sol **Kes** kısayol menüsünden.  
  
2.  Hedef en üst düzey menüde menü öğesi hedeflenen yeni konumu üstünde sol CTRL + V tuşuna basın veya hedeflenen yeni konumu yukarıda menü öğesini sağ tıklatın ve seçin **Yapıştır** kısayol menüsünden.  
  
     Kesme menü sonra seçili menü öğesi eklenir.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Menü öğesinin öğeleri koleksiyonu Düzenleyicisi'ni kullanarak bir menü içinde taşımak için  
  
1.  Taşımak istediğiniz menü öğesini içeren menüyü sağ tıklatın.  
  
2.  Kısayol menüsünden **Düzenle DropDownItems**.  
  
3.  İçinde **öğeleri koleksiyonu Düzenleyicisi**, taşımak istediğiniz menü öğesini tıklatın.  
  
4.  Menü öğesini menü içinde taşımak için yukarı ve aşağı ok tuşları'ı tıklatın.  
  
5.  **Tamam**'ı tıklatın.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Menü öğesi için klavyeyi kullanma menü içinde taşımak için  
  
1.  ALT tuşunu basılı yeniden açın.  
  
2.  ' A tıklayın ve taşımak istediğiniz menü öğesini sol fare düğmesini basılı tutun.  
  
3.  Menü öğesinin yeni bir konuma sürükleyin ve sol fare düğmesini bırakın.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Menü öğesi için başka bir menüyü taşımak için  
  
1.  Taşıma ve CTRL + X tuşlarına basın veya menü öğesini sağ tıklatın ve seçin istediğiniz menü öğesi sol **Kes** kısayol menüsünden.  
  
2.  Kesme menü öğesi içerecek menü sol tıklayın.  
  
3.  Önce hedeflenen yeni konumu menü öğesini tıklatın ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce menü öğesini sağ **Yapıştır** kısayol menüsünden.  
  
     Kesme menü öğesi seçili menü öğesi sonra eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
