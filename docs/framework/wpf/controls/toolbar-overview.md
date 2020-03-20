---
title: ToolBar Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186610"
---
# <a name="toolbar-overview"></a>ToolBar Genel Bakışı
<xref:System.Windows.Controls.ToolBar>denetimler, işlevleriyle genellikle ilişkili olan bir grup komut veya denetim için kapsayıcılardır. Genellikle <xref:System.Windows.Controls.ToolBar> komutları çağıran düğmeler içerir.  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>ToolBar Denetimi  
 Denetim, <xref:System.Windows.Controls.ToolBar> adını düğmelerin veya diğer denetimlerin çubuk benzeri düzenlemesinden tek bir satıra veya sütuna alır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> denetimler, doğal olarak sığmayan maddeleri özel bir taşma alanına <xref:System.Windows.Controls.ToolBar> boyut kısıtlaması içine yerleştiren bir taşma mekanizması sağlar. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimler genellikle özel <xref:System.Windows.Controls.ToolBarTray> düzen davranışı yanı sıra kullanıcı tarafından başlatılan boyutlandırma ve araç çubukları düzenlenmesi için destek sağlayan ilgili denetim ile kullanılır.  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>ToolBarTray'deki Araç Çubuklarının Konumunu Belirtme  
 'deki <xref:System.Windows.Controls.ToolBar.Band%2A> <xref:System.Windows.Controls.ToolBar.BandIndex%2A> konumu ve özelliklerini <xref:System.Windows.Controls.ToolBarTray> <xref:System.Windows.Controls.ToolBar> <xref:System.Windows.Controls.ToolBar.Band%2A>üst <xref:System.Windows.Controls.ToolBarTray>öğesinin içinde <xref:System.Windows.Controls.ToolBar> yer aldığı konumu gösterir. <xref:System.Windows.Controls.ToolBar.BandIndex%2A>bandının içinde <xref:System.Windows.Controls.ToolBar> yerleştirilme sırasını gösterir. Aşağıdaki örnek, denetimleri <xref:System.Windows.Controls.ToolBar> bir <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>Taşma Öğeleri olan Araç Çubukları  
 Denetimler genellikle <xref:System.Windows.Controls.ToolBar> araç çubuğunun boyutuna sığabilecekten daha fazla öğe içerir. Bu durumda, <xref:System.Windows.Controls.ToolBar> taşma düğmesi görüntülenir. Taşma öğelerini görmek için, kullanıcı taşma düğmesini tıklatıyor ve öğeler aşağıdaki <xref:System.Windows.Controls.ToolBar>açılır pencerede gösterilir. Aşağıdaki grafik, <xref:System.Windows.Controls.ToolBar> taşma öğeleri ile bir gösterir:  
  
 ![Taşma öğeleri içeren bir araç çubuğu gösteren ekran görüntüsü.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Araç çubuğundaki bir öğenin taşma paneline ne zaman <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> yerleştirildiğini, <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>ekli <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>özelliği <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>, yani . Aşağıdaki örnekte, araç çubuğundaki son dört düğmenin her zaman taşma panelinde olması gerektiği belirtilmesinde belirtilir.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Onun <xref:System.Windows.Controls.ToolBar> kullanır <xref:System.Windows.Controls.Primitives.ToolBarPanel> a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> ve <xref:System.Windows.Controls.ControlTemplate>a .  Araç <xref:System.Windows.Controls.Primitives.ToolBarPanel> çubuğundaki öğelerin düzeninden sorumludur.  Bu <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> öğelerin düzeninden <xref:System.Windows.Controls.ToolBar>sorumludur. A için bir <xref:System.Windows.Controls.ControlTemplate> örnek <xref:System.Windows.Controls.ToolBar>için , bkz.  
  
 [Araç Çubuğu Stilleri ve Şablonları](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Araç Çubuğundaki Stil Denetimleri](how-to-style-controls-on-a-toolbar.md)
- [WPF Denetimleri Galeri Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
