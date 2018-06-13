---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 3ce18d40910145a076cc7084e2fba8ee0229c21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531560"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Devre Dışı Bırakma
Sınırlandırmak veya bir kullanıcı tarafından etkinleştirme ve kullanıcı etkinlikleri yanıtta menü öğelerini devre dışı bırakma hale getirebilir komutları genişletebilir. Menü öğeleri, varsayılan olarak etkinleştirilir, oluşturuldukları, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği. Tasarım zamanında bu özellik işleyebilir **özellikleri** penceresi veya programlı olarak ayarlayarak bu kodu. Daha fazla bilgi için bkz: [nasıl yapılır: Toolstripmenuıtems devre dışı](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Tasarım zamanında bir menü öğesini devre dışı bırakmak için  
  
1.  Menü öğesi formunda seçili ayarlamak <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğine `false`.  
  
    > [!TIP]
    >  Bir menüdeki ilk ya da üst düzey menü öğesini devre dışı bırakma menüsünün içinde yer alan tüm menü öğelerini devre dışı bırakır. Benzer şekilde, alt öğeleri alt öğelerine sahip bir menü öğesini devre dışı bırakma devre dışı bırakır. Verilen menüsünde tüm komutlar kullanıcıya kullanılabilir durumda değilse, bu bir temiz kullanıcı arabirimi sunar gibi Gizle hem tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir. Gizleme hem tek başına bir gizleme erişimi bir kısayol tuşu aracılığıyla menü komutu engellemez menüsünde devre dışı bırakın. Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> bir üst düzey menü öğesine özelliğinin `false` tüm menü gizlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Nasıl yapılır: ToolStripMenuItems Gizleme](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
