---
title: MenuStrip Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 7cd761697a09205294727043efc6cf73816803ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761378"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip Denetimine Genel Bakış (Windows Forms)
Menüleri, ortak bir tema tarafından gruplandırılmış komutları tutarak kullanıcılarınıza işlevselliği kullanıma sunar.  
  
 <xref:System.Windows.Forms.MenuStrip> Denetimi bu Visual Studio ve .NET Framework sürümü için yenidir. Denetim ile Microsoft Office içinde bulunanlar gibi menüleri kolayca oluşturabilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> Çok Belgeli Arabirim (MDI) ve menü birleştirme, araç ipuçları ve taşma denetimini destekler. Erişim tuşları, kısayol tuşları, onay işaretleri, görüntüleri ve ayırıcı çubukları ekleyerek, menüler okunabilirliğini ve kullanılabilirliğini geliştirebilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.MainMenu> denetler; ancak, <xref:System.Windows.Forms.MainMenu> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip denetimi kullanmanın yolları  
 Kullanım <xref:System.Windows.Forms.MenuStrip> denetimi:  
  
- Özelleştirilmiş kolayca oluşturun, metin ve görüntü sıralama ve hizalama, sürükle ve bırak işlemleri, MDI, taşma ve menü komutları erişmenin alternatif modları gibi arabirimi ve düzen özelliklerini destekleyen yaygın olarak çalıştırılan menüleri gelişmiş kullanıcı.  
  
- Tipik bir görünümünü ve davranışını işletim sistemini destekler.  
  
- Diğer denetimlerin olaylarını işlemek aynı şekilde tüm kapsayıcılar ve içerilen öğelerin için tutarlı bir şekilde olayları işleyin.  
  
 Aşağıdaki tablo bazı özellikle önemli özellikleri gösterir <xref:System.Windows.Forms.MenuStrip> ve ilişkilendirilmiş sınıfları.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Alır veya ayarlar <xref:System.Windows.Forms.ToolStripMenuItem> MDI alt formlarını listesini görüntülemek için kullanılır.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Alır veya ayarlar alt menüler üst MDI uygulamaları menülerde nasıl birleştirilir.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Alır veya MDI uygulamaları içindeki birleştirilmiş bir öğenin konumunu ayarlar.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Alır veya form MDI alt formlarını için bir kapsayıcı olup olmadığını belirten bir değer ayarlar.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Araç ipuçları için gösterilip gösterilmeyeceğini belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Belirten bir değeri alır veya ayarlar olmadığını <xref:System.Windows.Forms.MenuStrip> overflow işlevselliği destekler.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Alır veya ayarlar ile ilişkili kısayol tuşlarını <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Alır veya ayarlar kısayol, anahtarları olup olmadığını belirten bir değer ile ilişkili <xref:System.Windows.Forms.ToolStripMenuItem> yanında görüntülenen <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Aşağıdaki tablo önemli gösterir <xref:System.Windows.Forms.MenuStrip> Yahoo! companion sınıfları.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Görüntülenen bir seçilebilir seçeneğini temsil eder bir <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Bir kısayol menüsü temsil eder.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Kullanıcı tıkladığında görüntülenen listeden tek bir öğe kullanıcıya veren bir denetimi temsil eder bir <xref:System.Windows.Forms.ToolStripDropDownButton> ya da daha üst düzey menü öğesi.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Türetilen denetimler için temel işlevleri sağlar <xref:System.Windows.Forms.ToolStripItem> tıklandığında açılan öğeleri görüntüler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
