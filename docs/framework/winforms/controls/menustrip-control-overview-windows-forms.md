---
title: MenuStrip Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733452"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip Denetimine Genel Bakış (Windows Forms)
Menüler, ortak bir temaya göre gruplanmış komutları tutarak kullanıcılarınıza işlevselliği sunar.  
  
 <xref:System.Windows.Forms.MenuStrip> Denetim, .NET Framework sürüm 2,0 ' de tanıtılmıştı. <xref:System.Windows.Forms.MenuStrip> Denetimiyle, Microsoft Office bulunan gibi kolayca menüler oluşturabilirsiniz.  
  
 <xref:System.Windows.Forms.MenuStrip> Denetim, çoklu belge arabirimi (MDI) ve menü birleştirme, araç ipuçları ve taşmayı destekler. Erişim tuşları, kısayol tuşları, onay işaretleri, görüntüler ve ayırıcı çubuklar ekleyerek menülerinizi kullanılabilirliğini ve okunabilirliğini geliştirebilirsiniz.  
  
 Denetim yerini alır ve <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.MainMenu> denetime işlevsellik ekler; ancak, denetim geriye dönük uyumluluk için ve isterseniz daha sonra kullanılmak üzere tutulur. <xref:System.Windows.Forms.MenuStrip>  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip denetimini kullanmanın yolları  
 Şunları yapmak için denetimi kullanın: <xref:System.Windows.Forms.MenuStrip>  
  
- Metin ve görüntü sıralama ve hizalama, sürükle ve bırak işlemleri, MDI, taşma ve menü komutlarının diğer modları gibi gelişmiş kullanıcı arabirimi ve düzen özelliklerini destekleyen kolayca özelleştirilmiş, yaygın olarak kullanılan menüler oluşturun.  
  
- İşletim sisteminin tipik görünümünü ve davranışını destekler.  
  
- Olayları tüm kapsayıcılar ve içerilen öğeler için, diğer denetimler için de olayları idare ettiğiniz şekilde işleyin.  
  
 Aşağıdaki tabloda, <xref:System.Windows.Forms.MenuStrip> ve ilişkili sınıfların bazı özellikle önemli özellikleri gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|MDI alt formlarının listesini <xref:System.Windows.Forms.ToolStripMenuItem> göstermek için kullanılan öğesini alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Alt menülerin MDI uygulamalarında üst menülerle nasıl birleştirildiğini alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|MDI uygulamalarında bir menü içindeki birleştirilmiş öğenin konumunu alır veya ayarlar.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Formun MDI alt formları için bir kapsayıcı olup olmadığını gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|İçin araç ipuçlarının gösterilip gösterilmeyeceğini gösteren bir değer alır veya ayarlar <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|' Nin taşma işlevini <xref:System.Windows.Forms.MenuStrip> destekleyip desteklemediğini gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|İle ilişkili kısayol tuşlarını alır veya ayarlar <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|İle <xref:System.Windows.Forms.ToolStripMenuItem> ilişkili kısayol tuşlarının ' nin yanında <xref:System.Windows.Forms.ToolStripMenuItem>görüntülenip görüntülenmediğini gösteren bir değer alır veya ayarlar.|  
  
 Aşağıdaki tabloda, önemli <xref:System.Windows.Forms.MenuStrip> yardımcı sınıflar gösterilmektedir.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<xref:System.Windows.Forms.MenuStrip> Veya<xref:System.Windows.Forms.ContextMenuStrip>üzerinde görünen seçilebilir bir seçeneği temsil eder.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Bir kısayol menüsünü temsil eder.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Kullanıcının bir <xref:System.Windows.Forms.ToolStripDropDownButton> veya daha yüksek düzey menü öğesine tıkladığı zaman görüntülenen listeden tek bir öğe seçmesini sağlayan bir denetimi temsil eder.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Tıklandığında <xref:System.Windows.Forms.ToolStripItem> , açılan öğeden türetilmiş denetimler için temel işlevleri sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
