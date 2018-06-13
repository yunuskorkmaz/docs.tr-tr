---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: b0018516b9ac337cea3716c4b2eddc6eb859dbb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534372"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Gizleme
Menü öğelerini gizleme, uygulamanızın kullanıcı arabirimi (UI) denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur. Genellikle, tüm menü öğeleri kullanılamaz duruma geldiğinde tüm menüyü Gizle isteyeceksiniz. Bu kullanıcı için daha az karışıklıkları gösterir. Ayrıca, tek başına bir gizleme kullanıcı bir kısayol tuşu kullanarak menü komutu erişmesini engellemez gibi Gizle hem menüsü veya menü öğesini devre dışı bırakmak isteyebilirsiniz. Menü öğelerini devre dışı bırakma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Toolstripmenuıtems kullanarak Tasarımcısı'nı devre dışı](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>En üst düzey menü ve onun alt menü öğelerini gizleme  
  
1.  Üst düzey menü öğesini seçin ve ayarlayın, <xref:System.Windows.Forms.ToolStripItem.Visible%2A> veya <xref:System.Windows.Forms.ToolStripItem.Available%2A> özelliğine `false`.  
  
     Üst düzey menü öğesini gizlemek menüye içindeki tüm menü öğelerini de gizlidir. Dışındaki bir üzerinde tıklatırsanız <xref:System.Windows.Forms.MenuStrip> ayarlanmasından sonra <xref:System.Windows.Forms.ToolStripItem.Visible%2A> için `false`, böylece eyleminizi çalışma zamanı etkisini gösteren formdan, tüm üst düzey menü öğesi ve kendi alt öğelerini kaybolur. Tasarım zamanında gizli en üst düzey menü öğesini görüntülemek için tıklatın <xref:System.Windows.Forms.MenuStrip> içinde **bileşen**, **belge anahattı**, ya da özellik Kılavuzu üstünde.  
  
> [!NOTE]
>  Birden çok belge arabirimi (MDI) alt menüler birleştirme senaryosunda hariç tüm bir menü nadiren gizlenir.  
  
### <a name="to-hide-a-submenu-item"></a>Alt menü öğesini gizlemek için  
  
1.  Alt menü öğesini seçin ve ayarlayın, <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğine `false`.  
  
     Alt menü öğesini gizlemek, bunu kolayca için daha fazla iş seçebilmeniz tasarım zamanında formunuzda görünür kalır. Çalışma zamanında gerçekten gizlenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Devre Dışı Bırakma](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
