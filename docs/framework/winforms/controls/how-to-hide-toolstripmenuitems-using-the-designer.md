---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 31c597a0e2cbf41484f19c8d4179823e9fb929ba
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317681"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme
Menü öğelerini gizleme, uygulamanızın kullanıcı arabirimini (UI) denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur. Genellikle, tüm menü öğeleri kullanılamadığında bir tüm menüyü Gizle isteyeceksiniz. Bu kullanıcı için daha az dikkat dağıtıcı faktör sunar. Ayrıca, tek başına bir gizleme kullanıcı bir menü komutu bir kısayol tuşu kullanarak erişmesini önlemez gibi hem gizleyebilir ve menü veya menü öğesi devre dışı bırakmak isteyebilirsiniz. Menü öğelerini devre dışı bırakma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Tasarımcıyı kullanarak toolstripmenuıtems öğelerini devre dışı](how-to-disable-toolstripmenuitems-using-the-designer.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Üst düzey menü ve onun alt öğelerini gizlemek için  
  
1. Üst düzey menü öğesini seçin ve ayarlayın, <xref:System.Windows.Forms.ToolStripItem.Visible%2A> veya <xref:System.Windows.Forms.ToolStripItem.Available%2A> özelliğini `false`.  
  
     Üst düzey menü öğesi gizlediğinizde, menünün içinde tüm menü öğelerini de gizlenir. Dışındaki bir üzerinde tıklarsanız <xref:System.Windows.Forms.MenuStrip> ayarlanmasından sonra <xref:System.Windows.Forms.ToolStripItem.Visible%2A> için `false`, tüm üst düzey menü öğesi ve onun alt öğelerini, böylece sizin eyleminizi çalışma zamanı etkisini gösteren formunuzun içinden kaybolur. Tasarım zamanında gizli en üst düzey menü öğesi görüntülemek için tıklayın <xref:System.Windows.Forms.MenuStrip> içinde **bileşeni Tepsi**, **belge anahattı**, ya da özellik kılavuzunda üstünde.  
  
> [!NOTE]
>  Birden çok belge arabirimi (MDI) alt menülerini birleştirme senaryosunda hariç tüm bir menü nadiren gizlenir.  
  
### <a name="to-hide-a-submenu-item"></a>Bir alt öğesini gizlemek için  
  
1. Alt menü öğesini seçin ve ayarlayın, <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`.  
  
     Bir alt öğesi gizlediğinizde, böylece bunu kolayca için daha fazla iş seçebilirsiniz tasarım zamanında formunuzda görünür kalır. Çalışma zamanında gerçekten gizlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma](how-to-disable-toolstripmenuitems-using-the-designer.md)
