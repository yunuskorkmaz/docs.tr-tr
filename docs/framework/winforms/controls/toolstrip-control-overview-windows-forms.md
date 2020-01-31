---
title: ToolStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741070"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolStrip> denetimi ve onunla ilişkili sınıfları, Kullanıcı arabirimi öğelerini araç çubuklarına, durum çubuklarına ve menülere birleştirmek için ortak bir çerçeve sağlar. <xref:System.Windows.Forms.ToolStrip> denetimleri, yerleşik etkinleştirme ve düzenleme, özel düzen ve Radye içeren ve araç çubuklarının yatay veya dikey bir alanı paylaşma özelliği olan zengin bir tasarım zamanı deneyimi sunar.  
  
 <xref:System.Windows.Forms.ToolStrip>, önceki sürümlerde denetime işlev koyar ve bu denetime işlevsellik eklemesine karşın, <xref:System.Windows.Forms.ToolBar> hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip denetimlerinin özellikleri  
 <xref:System.Windows.Forms.ToolStrip> denetimini şu şekilde kullanın:  
  
- Kapsayıcılar arasında ortak bir kullanıcı arabirimi sunun.  
  
- Gelişmiş Kullanıcı arabirimi ve yerleştirme, radye, metin ve görüntüler içeren düğmeler, açılan düğmeler ve denetimler, taşma düğmeleri ve <xref:System.Windows.Forms.ToolStrip> öğelerinin çalışma zamanı yeniden sıralamayı destekleyen kolayca özelleştirilmiş, yaygın olarak kullanılan araç çubukları oluşturun.  
  
- Taşma ve çalışma zamanı öğesi yeniden sıralamayı destekler. Taşma özelliği, bir <xref:System.Windows.Forms.ToolStrip>göstermek için yeterli alan olmadığında öğeleri bir açılan menüye taşımakta.  
  
- Ortak bir işleme modeli aracılığıyla işletim sisteminin tipik görünümünü ve davranışını destekler.  
  
- Olayları tüm kapsayıcılar ve içerilen öğeler için, diğer denetimler için de olayları idare ettiğiniz şekilde işleyin.  
  
- Öğeleri bir <xref:System.Windows.Forms.ToolStrip> diğerine veya <xref:System.Windows.Forms.ToolStrip>içine sürükleyin.  
  
- Bir <xref:System.Windows.Forms.ToolStripDropDown>gelişmiş düzenlerle açılır denetimler ve Kullanıcı arabirimi türü düzenleyiciler oluşturun.  
  
 <xref:System.Windows.Forms.ToolStripControlHost> sınıfını kullanarak <xref:System.Windows.Forms.ToolStrip> diğer denetimleri kullanın ve bunlar için <xref:System.Windows.Forms.ToolStrip> işlevsellik kazanın.  
  
 <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>ve <xref:System.Windows.Forms.ToolStripManager> <xref:System.Windows.Forms.ToolStripRenderMode> ve <xref:System.Windows.Forms.ToolStripManagerRenderMode> Numaralandırmalarla birlikte kullanarak işlevselliği genişletebilir ve görünümü değiştirebilirsiniz.  
  
 <xref:System.Windows.Forms.ToolStrip> denetimi yüksek oranda yapılandırılabilir ve genişletilebilir ve görünüm ve davranışı özelleştirmek için birçok özellik, yöntem ve olay sağlar. Aşağıda bazı önemli Üyeler verilmiştir:  
  
### <a name="important-toolstrip-members"></a>Önemli ToolStrip üyeleri  
  
|Name|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Üst kapsayıcının bir <xref:System.Windows.Forms.ToolStrip> hangi kenarından yerleştirildiğini alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Sürükle ve bırak ile öğe yeniden sıralamayı <xref:System.Windows.Forms.ToolStrip> sınıfı tarafından özel olarak işlenip işlenmediğini gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|<xref:System.Windows.Forms.ToolStrip> öğelerini nasıl düzenledini gösteren bir değer alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Bir <xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Forms.ToolStrip> veya <xref:System.Windows.Forms.ToolStripOverflowButton> bağlı olduğunu veya iki arasında kayıp kaymayacağını alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|<xref:System.Windows.Forms.ToolStripItem> tıklandığında bir <xref:System.Windows.Forms.ToolStripItem> açılan listede diğer öğeleri görüntüleyip görüntülemediğini gösteren bir değer alır.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Taşma özellikli bir <xref:System.Windows.Forms.ToolStrip> için taşma düğmesi olan <xref:System.Windows.Forms.ToolStripItem> alır.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Bir <xref:System.Windows.Forms.ToolStrip>görünüm ve davranışını (görünüm ve kullanım) özelleştirmek için kullanılan bir <xref:System.Windows.Forms.ToolStripRenderer> alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|<xref:System.Windows.Forms.ToolStrip>uygulanacak boyama stillerini alır veya ayarlar.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<xref:System.Windows.Forms.ToolStrip.Renderer%2A> özelliği değiştiğinde tetiklenir.|  
  
 <xref:System.Windows.Forms.ToolStrip> denetimin esnekliği, bir dizi yardımcı sınıfın kullanımı aracılığıyla elde edilir. Aşağıda, en önemli bir kısmı verilmiştir:  
  
### <a name="important-toolstrip-companion-classes"></a>Önemli ToolStrip yardımcı sınıfları  
  
|Name|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|, <xref:System.Windows.Forms.MainMenu> sınıfına işlevselliği ekler ve değiştirir.|  
|<xref:System.Windows.Forms.StatusStrip>|, <xref:System.Windows.Forms.StatusBar> sınıfına işlevselliği ekler ve değiştirir.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|, <xref:System.Windows.Forms.ContextMenu> sınıfına işlevselliği ekler ve değiştirir.|  
|<xref:System.Windows.Forms.ToolStripItem>|<xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>veya <xref:System.Windows.Forms.ToolStripDropDown> içerebilen tüm öğelerin olaylarını ve yerleşimini yöneten soyut temel sınıf.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Formun her tarafında, denetimlerin çeşitli yollarla düzenlenebileceği panel içeren bir kapsayıcı sağlar.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|<xref:System.Windows.Forms.ToolStrip> nesnelerinin boyama işlevini işler.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Microsoft Office stili görünüm sağlar.|  
|<xref:System.Windows.Forms.ToolStripManager>|<xref:System.Windows.Forms.ToolStrip> işleme ve Radye ve <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>ve <xref:System.Windows.Forms.ToolStripMenuItem> nesnelerinin birleştirilmesini denetler.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Bir formda bulunan birden çok <xref:System.Windows.Forms.ToolStrip> nesnesine uygulanan boyama stilini (özel, Windows XP veya Microsoft Office Professional) belirtir.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Bir formda bulunan bir <xref:System.Windows.Forms.ToolStrip> nesnesine uygulanan boyama stilini (özel, Windows XP veya Microsoft Office Professional) belirtir.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Özellikle <xref:System.Windows.Forms.ToolStrip> denetimleri olan, ancak <xref:System.Windows.Forms.ToolStrip> işlevlerini istediğiniz diğer denetimleri barındırır.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|<xref:System.Windows.Forms.ToolStripItem> ana <xref:System.Windows.Forms.ToolStrip>, taşma <xref:System.Windows.Forms.ToolStrip>mi yoksa yoksa değil mi yerleştirileceğini belirtir.|  
  
 Daha fazla bilgi için bkz. [ToolStrip teknoloji Özeti](toolstrip-technology-summary.md) ve [ToolStrip denetim mimarisi](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
