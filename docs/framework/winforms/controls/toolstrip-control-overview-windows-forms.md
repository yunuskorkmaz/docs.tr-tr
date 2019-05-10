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
ms.openlocfilehash: 75df256f852b45af4bc6cf519c13ccd62ae1d689
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654767"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolStrip> denetimi ve ilişkili sınıflarının sağlayan ortak bir çerçeve kullanıcı arabirimi öğeleri araç çubukları, durum çubukları ve menüler birleştirmek için. <xref:System.Windows.Forms.ToolStrip> denetimleri yatay veya dikey boşluk paylaşma olanağı, araç çubuklarının olduğu yerinde etkinleştirme ve düzenleme, özel düzen ve radye, içeren zengin bir tasarım zamanı deneyimi sunar.  
  
 Ancak <xref:System.Windows.Forms.ToolStrip> değiştirir ve önceki sürümlerde, denetim için işlevsellik ekler <xref:System.Windows.Forms.ToolBar> geriye dönük uyumluluk ve gelecekte kullanım için isterseniz korunur.  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip denetimlerinin özellikleri  
 Kullanım <xref:System.Windows.Forms.ToolStrip> denetimi:  
  
- Kapsayıcılar arasında ortak bir kullanıcı arabirimi sunar.  
  
- Özelleştirilmiş kolayca oluşturabilir, destek yaygın olarak çalıştırılan araç çubukları kullanıcı arabirimi ve düzen özellikleri, Gelişmiş metin ve görüntüleri, aşağı açılır düğmeler ve denetimleri yerleştirme, radye, düğmeler gibi taşma düğmeler ve çalışma zamanı, yeniden sıralama <xref:System.Windows.Forms.ToolStrip> öğeleri.  
  
- Taşma ve çalışma zamanı öğeyi yeniden sıralamayı destekler. Bunları görüntülemek için yeterli alan olmadığında taşma özellik öğeleri açılan menüye taşır. bir <xref:System.Windows.Forms.ToolStrip>.  
  
- Tipik bir görünümünü ve davranışını bir ortak işleme modeliyle işletim sisteminin destekler.  
  
- Diğer denetimlerin olaylarını işlemek aynı şekilde tüm kapsayıcılar ve içerilen öğelerin için tutarlı bir şekilde olayları işleyin.  
  
- Sürükleyin öğeleri birinden <xref:System.Windows.Forms.ToolStrip> diğerine veya içinde bir <xref:System.Windows.Forms.ToolStrip>.  
  
- Aşağı açılan denetimleri ve kullanıcı arabirimi tür düzenleyicileri Gelişmiş düzenleri oluşturmak bir <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Kullanma <xref:System.Windows.Forms.ToolStripControlHost> sınıfı diğer denetimleri kullanmak üzere bir <xref:System.Windows.Forms.ToolStrip> ve geçirmesine <xref:System.Windows.Forms.ToolStrip> onlar için işlev.  
  
 İşlevlerini genişletmek ve kullanarak görünümünü ve davranışını değiştirme <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ve <xref:System.Windows.Forms.ToolStripManager> ile birlikte <xref:System.Windows.Forms.ToolStripRenderMode> ve <xref:System.Windows.Forms.ToolStripManagerRenderMode> numaralandırma.  
  
 <xref:System.Windows.Forms.ToolStrip> Denetimidir son derece yapılandırılabilir ve genişletilebilir ve birçok özellikleri, yöntemleri ve görünümünü ve davranışını özelleştirmek için olayları sağlar. Bazı önemli üyeleri aşağıda verilmiştir:  
  
### <a name="important-toolstrip-members"></a>Önemli ToolStrip üyeleri  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Alır veya ayarlar üst kapsayıcı hangi kenarı bir <xref:System.Windows.Forms.ToolStrip> için yerleştirilir.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Sürükle ve bırak ve öğeyi yeniden sıralamayı göre özel olarak işlenip olup olmadığını belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.ToolStrip> sınıfı.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Belirten bir değeri alır veya ayarlar nasıl <xref:System.Windows.Forms.ToolStrip> alt öğeleri yerleştirir.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Alır veya ayarlar olup olmadığını bir <xref:System.Windows.Forms.ToolStripItem> iliştirildiği <xref:System.Windows.Forms.ToolStrip> veya <xref:System.Windows.Forms.ToolStripOverflowButton> veya ikisi arasında kaydırabilirsiniz.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Belirten bir değer alır olup olmadığını bir <xref:System.Windows.Forms.ToolStripItem> diğer öğeleri bir açılan menü görüntüler listesinde <xref:System.Windows.Forms.ToolStripItem> tıklandığında.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Alır <xref:System.Windows.Forms.ToolStripItem> taşma düğmesi için diğer bir deyişle bir <xref:System.Windows.Forms.ToolStrip> etkin taşması ile.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Alır veya ayarlar bir <xref:System.Windows.Forms.ToolStripRenderer> (Görünüm) davranışını ve görünümünü özelleştirmek için kullanılan bir <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Alır veya ayarlar uygulanmaya boyama stilleri <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Arandığında <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özellik değişiklikleri.|  
  
 <xref:System.Windows.Forms.ToolStrip> Denetimin esneklik bir dizi yardımcı sınıfları kullanılarak elde edilir. En önemli bazıları aşağıda verilmiştir:  
  
### <a name="important-toolstrip-companion-classes"></a>Önemli ToolStrip yardımcı sınıfları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.MainMenu> sınıfı.|  
|<xref:System.Windows.Forms.StatusStrip>|Değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.StatusBar> sınıfı.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ContextMenu> sınıfı.|  
|<xref:System.Windows.Forms.ToolStripItem>|Soyut olaylar ve tüm öğeler için Düzen yöneten temel sınıf, bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, veya <xref:System.Windows.Forms.ToolStripDropDown> içerebilir.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Bir panel denetimleri çeşitli şekillerde düzenlenebilir formu her iki tarafında bir kapsayıcı sağlar.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Boyama işlevselliği için işleme <xref:System.Windows.Forms.ToolStrip> nesneleri.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Microsoft Office stili görünümünü sağlar.|  
|<xref:System.Windows.Forms.ToolStripManager>|Denetimleri <xref:System.Windows.Forms.ToolStrip> işleme ve radye ve, birleştirme <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, ve <xref:System.Windows.Forms.ToolStripMenuItem> nesneleri.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Birden fazla siteye uygulanan boyama stili (özel, Windows XP veya Microsoft Office Professional) belirtir <xref:System.Windows.Forms.ToolStrip> formda bulunan nesneler.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Bir boyama stili (özel, Windows XP veya Microsoft Office Professional) belirtir <xref:System.Windows.Forms.ToolStrip> formda bulunan nesne.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Özellikle olmayan diğer denetimleri barındıran <xref:System.Windows.Forms.ToolStrip> denetimleri ancak istediğiniz <xref:System.Windows.Forms.ToolStrip> işlevselliği.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Belirtir olup olmadığını bir <xref:System.Windows.Forms.ToolStripItem> ana üzerinde düzenlendiği için <xref:System.Windows.Forms.ToolStrip>, taşmada <xref:System.Windows.Forms.ToolStrip>, ya da hiçbiri.|  
  
 Daha fazla bilgi için [ToolStrip teknoloji özeti](toolstrip-technology-summary.md) ve [ToolStrip denetim mimarisi](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
