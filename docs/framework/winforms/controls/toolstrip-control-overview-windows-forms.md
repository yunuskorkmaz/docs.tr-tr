---
title: ToolStrip Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3927f180e738541f2f2f8af6d03d281f6a601167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolStrip> denetim ve onun ilişkili sınıfları sağlar ortak bir çerçeve araç çubukları, durum çubukları ve menüleri kullanıcı arabirimi öğeleri birleştirme için. <xref:System.Windows.Forms.ToolStrip> denetimler araç çubukları yatay veya dikey boşluk paylaşma olanağı olduğu, yerinde etkinleştirme ve düzenleme, özel düzen ve radye, içeren zengin bir tasarım zamanı deneyimi sunar.  
  
 Ancak <xref:System.Windows.Forms.ToolStrip> değiştirir ve önceki sürümlerde, denetim için işlevsellik ekler <xref:System.Windows.Forms.ToolBar> geriye dönük uyumluluk ve gelecekte kullanım için isterseniz korunur.  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip denetimlerinin özellikleri  
 Kullanım <xref:System.Windows.Forms.ToolStrip> denetimini:  
  
-   Ortak bir kullanıcı arabirimi kapsayıcıları sunar.  
  
-   Kolayca özelleştirilmiş oluşturmak, destek, yaygın olarak kullanılan araç çubukları kullanıcı arabirimi ve yerleşim özellikleri, Gelişmiş metin ve görüntüler, aşağı açılır düğmeler ve denetimleri yerleştirme, radye, düğmeleri gibi taşması düğmeleri ve çalışma zamanı, yeniden sıralama <xref:System.Windows.Forms.ToolStrip> öğeler.  
  
-   Taşma ve çalışma zamanı öğesi yeniden sıralama destekler. Bunları görüntülemek için yeterli alan olmadığında taşma özelliği öğeleri açılan menüye taşır. bir <xref:System.Windows.Forms.ToolStrip>.  
  
-   Genel Görünümü ve davranışı işletim sisteminin bir ortak işleme modeli aracılığıyla destekler.  
  
-   Tüm kapsayıcıları ve içerilen öğelerin için tutarlı bir şekilde olayları işlemek, diğer denetimler için olayları işlemek aynı şekilde.  
  
-   Sürükleme öğeleri birinden <xref:System.Windows.Forms.ToolStrip> diğerine veya içinde bir <xref:System.Windows.Forms.ToolStrip>.  
  
-   Aşağı açılan denetimler ve kullanıcı arabirimi türü düzenleyicileri Gelişmiş düzenleri oluşturmak bir <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Kullanmak <xref:System.Windows.Forms.ToolStripControlHost> diğer denetimlerini sınıfı bir <xref:System.Windows.Forms.ToolStrip> ve geçirmesine <xref:System.Windows.Forms.ToolStrip> onlar için işlev.  
  
 İşlevlerini genişletmek ve kullanarak görünümünü ve davranışını değiştirme <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ve <xref:System.Windows.Forms.ToolStripManager> ile birlikte <xref:System.Windows.Forms.ToolStripRenderMode> ve <xref:System.Windows.Forms.ToolStripManagerRenderMode> numaralandırmalar.  
  
 <xref:System.Windows.Forms.ToolStrip> Denetimidir yüksek oranda yapılandırılabilir ve genişletilebilir ve birçok özellikleri, yöntemleri ve olayların görünümünü ve davranışını özelleştirmek için sağlar. Bazı önemli üyeler aşağıda verilmiştir:  
  
### <a name="important-toolstrip-members"></a>Önemli ToolStrip üyeleri  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Alır veya ayarlar üst kapsayıcı hangi kenarı bir <xref:System.Windows.Forms.ToolStrip> için yerleştirilir.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Sürükle ve bırak ve sıralamayı tarafından özel olarak işlenir olup olmadığını belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.ToolStrip> sınıfı.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Belirten değeri alır veya ayarlar nasıl <xref:System.Windows.Forms.ToolStrip> öğelerinden yerleştirir.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Alır veya ayarlar olup olmadığını bir <xref:System.Windows.Forms.ToolStripItem> bağlı <xref:System.Windows.Forms.ToolStrip> veya <xref:System.Windows.Forms.ToolStripOverflowButton> veya ikisi arasında float.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Belirten bir değer alır olup bir <xref:System.Windows.Forms.ToolStripItem> diğer öğeler bir açılan görüntüler ne zaman listesinde <xref:System.Windows.Forms.ToolStripItem> tıklandığında.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Alır <xref:System.Windows.Forms.ToolStripItem> diğer bir deyişle taşma düğmesi için bir <xref:System.Windows.Forms.ToolStrip> etkin taşması ile.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Alır veya ayarlar bir <xref:System.Windows.Forms.ToolStripRenderer> görünümünü ve davranışını (Görünüm) özelleştirmek için kullanılan bir <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Alır veya ayarlar uygulanacak boyama stilleri <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Ne zaman yükseltilmiş <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özellik değişikliği.|  
  
 <xref:System.Windows.Forms.ToolStrip> Denetimin esneklik yardımcı sınıfları bir dizi kullanımı ile elde edilir. En önemli bazıları aşağıda verilmiştir:  
  
### <a name="important-toolstrip-companion-classes"></a>Önemli ToolStrip yardımcı sınıfları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.MainMenu> sınıfı.|  
|<xref:System.Windows.Forms.StatusStrip>|Değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.StatusBar> sınıfı.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ContextMenu> sınıfı.|  
|<xref:System.Windows.Forms.ToolStripItem>|Soyut olaylar ve tüm öğeler için Düzen yönetir taban sınıf, bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, veya <xref:System.Windows.Forms.ToolStripDropDown> içerebilir.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Denetimleri çeşitli şekillerde düzenlenebilir form her tarafında paneliyle bir kapsayıcı sağlar.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Boyama işlevselliği için işleme <xref:System.Windows.Forms.ToolStrip> nesneleri.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Microsoft Office tarzındaki görünümü sağlar.|  
|<xref:System.Windows.Forms.ToolStripManager>|Denetimleri <xref:System.Windows.Forms.ToolStrip> işleme ve radye ve, birleştirme <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, ve <xref:System.Windows.Forms.ToolStripMenuItem> nesneleri.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Birden çok boyama stili (özel, Windows XP veya Microsoft Office Professional) belirtir <xref:System.Windows.Forms.ToolStrip> bir formda bulunan nesneler.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Birine uygulanan boyama stilini (özel, Windows XP veya Microsoft Office Professional) belirten <xref:System.Windows.Forms.ToolStrip> bir formda bulunan nesne.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Özellikle olmayan diğer denetimleri barındıran <xref:System.Windows.Forms.ToolStrip> denetimleri ancak istediğiniz <xref:System.Windows.Forms.ToolStrip> işlevselliği.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Belirtir olup bir <xref:System.Windows.Forms.ToolStripItem> üzerinde ana düzenlendiği için <xref:System.Windows.Forms.ToolStrip>, taşan <xref:System.Windows.Forms.ToolStrip>, veya hiçbiri.|  
  
 Daha fazla bilgi için bkz: [ToolStrip teknoloji özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) ve [ToolStrip denetim mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
