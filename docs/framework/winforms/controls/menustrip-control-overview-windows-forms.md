---
title: MenuStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734473"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip Denetimine Genel Bakış (Windows Forms)
Menüler, ortak bir temaya göre gruplanmış komutları tutarak kullanıcılarınıza işlevselliği sunar.  
  
 <xref:System.Windows.Forms.MenuStrip> denetimi .NET Framework sürüm 2,0 ' de tanıtılmıştı. <xref:System.Windows.Forms.MenuStrip> denetimiyle, Microsoft Office bulunan gibi kolayca menüler oluşturabilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> denetimi, çoklu belge arabirimi (MDI) ve menü birleştirme, araç ipuçları ve taşmayı destekler. Erişim tuşları, kısayol tuşları, onay işaretleri, görüntüler ve ayırıcı çubuklar ekleyerek menülerinizi kullanılabilirliğini ve okunabilirliğini geliştirebilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> denetimi yerini alır ve <xref:System.Windows.Forms.MainMenu> denetimine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.MainMenu> denetimi geriye dönük uyumluluk için ve isterseniz ileride kullanılmak üzere tutulur.  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip denetimini kullanmanın yolları  
 <xref:System.Windows.Forms.MenuStrip> denetimini şu şekilde kullanın:  
  
- Metin ve görüntü sıralama ve hizalama, sürükle ve bırak işlemleri, MDI, taşma ve menü komutlarının diğer modları gibi gelişmiş kullanıcı arabirimi ve düzen özelliklerini destekleyen kolayca özelleştirilmiş, yaygın olarak kullanılan menüler oluşturun.  
  
- İşletim sisteminin tipik görünümünü ve davranışını destekler.  
  
- Olayları tüm kapsayıcılar ve içerilen öğeler için, diğer denetimler için de olayları idare ettiğiniz şekilde işleyin.  
  
 Aşağıdaki tabloda <xref:System.Windows.Forms.MenuStrip> ve ilişkili sınıfların bazı özellikle önemli özellikleri gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|MDI alt formlarının listesini göstermek için kullanılan <xref:System.Windows.Forms.ToolStripMenuItem> alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Alt menülerin MDI uygulamalarında üst menülerle nasıl birleştirildiğini alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|MDI uygulamalarında bir menü içindeki birleştirilmiş öğenin konumunu alır veya ayarlar.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Formun MDI alt formları için bir kapsayıcı olup olmadığını gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<xref:System.Windows.Forms.MenuStrip>için araç ipuçlarının gösterilip gösterilmeyeceğini gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<xref:System.Windows.Forms.MenuStrip> taşma işlevini destekleyip desteklemediğini gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<xref:System.Windows.Forms.ToolStripMenuItem>ilişkili kısayol tuşlarını alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<xref:System.Windows.Forms.ToolStripMenuItem> ilişkili kısayol tuşlarının <xref:System.Windows.Forms.ToolStripMenuItem>yanında görüntülenip görüntülenmediğini gösteren bir değer alır veya ayarlar.|  
  
 Aşağıdaki tabloda, önemli <xref:System.Windows.Forms.MenuStrip> yardımcı sınıflar gösterilmektedir.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ContextMenuStrip>üzerinde görünen seçilebilir bir seçeneği temsil eder.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Bir kısayol menüsünü temsil eder.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Kullanıcının bir <xref:System.Windows.Forms.ToolStripDropDownButton> veya daha yüksek düzey bir menü öğesini tıkladığı zaman görüntülenen listeden tek bir öğe seçmesini sağlayan bir denetimi temsil eder.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Tıklandığında açılan öğeleri görüntüleyen <xref:System.Windows.Forms.ToolStripItem> türetilen denetimlerin temel işlevlerini sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
