---
title: ToolBar Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 460d4420d5faf849a8d05a94e0170aea384f69b4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452701"
---
# <a name="toolbar-overview"></a>ToolBar Genel Bakışı
<xref:System.Windows.Controls.ToolBar> denetimleri, genellikle işlevleriyle ilgili olan bir komut veya denetim grubu için kapsayıcılardır. <xref:System.Windows.Controls.ToolBar> genellikle komutları çağıran düğmeler içerir.  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar Denetimi  
 <xref:System.Windows.Controls.ToolBar> denetim, adını, düğme veya diğer denetimlerin tek bir satır veya sütun halinde çubuk benzeri düzenlemelerinden alır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimleri, doğal olarak uyumlu olmayan bir <xref:System.Windows.Controls.ToolBar> özel bir taşma alanına sığmayan öğeleri yerleştiren bir taşma mekanizması sağlar. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimleri genellikle ilgili <xref:System.Windows.Controls.ToolBarTray> denetimi ile birlikte kullanılır. Bu, özel düzen davranışı ve araç çubuklarının Kullanıcı tarafından başlatılan boyutlandırma ve düzenleme desteği sağlar.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Araç çubuklarının konumunu bir Toolbartepsi içinde belirtme  
 <xref:System.Windows.Controls.ToolBarTray><xref:System.Windows.Controls.ToolBar> konumlandırmak için <xref:System.Windows.Controls.ToolBar.Band%2A> ve <xref:System.Windows.Controls.ToolBar.BandIndex%2A> özelliklerini kullanın. <xref:System.Windows.Controls.ToolBar.Band%2A>, <xref:System.Windows.Controls.ToolBar> üst <xref:System.Windows.Controls.ToolBarTray>içinde yerleştirildiği konumu gösterir. <xref:System.Windows.Controls.ToolBar.BandIndex%2A>, <xref:System.Windows.Controls.ToolBar> bandı içinde yerleştirildiği sırayı gösterir. Aşağıdaki örnek, <xref:System.Windows.Controls.ToolBar> denetimlerinin <xref:System.Windows.Controls.ToolBarTray>içine yerleştirilmesi için bu özelliğin nasıl kullanıldığını gösterir.  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Taşma öğeleri içeren araç çubukları  
 Genellikle <xref:System.Windows.Controls.ToolBar> denetimleri araç çubuğunun boyutuna sığmayacak kadar çok öğe içeriyor. Bu durumda <xref:System.Windows.Controls.ToolBar> bir taşma düğmesi görüntüler. Taşma öğelerini görmek için, Kullanıcı taşma düğmesine tıklamıştır ve öğeler <xref:System.Windows.Controls.ToolBar>altında bir açılır pencerede gösterilir. Aşağıdaki grafik, taşma öğeleriyle bir <xref:System.Windows.Controls.ToolBar> gösterir:  
  
 ![Taşma öğeleri içeren bir araç çubuğunu gösteren ekran görüntüsü.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> ekli özelliği <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>veya <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>olarak ayarlayarak, bir araç çubuğundaki öğenin taşma paneline ne zaman yerleştirileceğini belirtebilirsiniz. Aşağıdaki örnek, araç çubuğundaki son dört düğmenin her zaman taşma panelinde nerede olması gerektiğini belirtir.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.ControlTemplate>bir <xref:System.Windows.Controls.Primitives.ToolBarPanel> ve <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> kullanır.  <xref:System.Windows.Controls.Primitives.ToolBarPanel>, araç çubuğundaki öğelerin düzeninden sorumludur.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>, <xref:System.Windows.Controls.ToolBar>sığmayan öğelerin düzeninden sorumludur. Bir <xref:System.Windows.Controls.ToolBar>için <xref:System.Windows.Controls.ControlTemplate> bir örnek için bkz.  
  
 [Araç çubuğu stilleri ve şablonları](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Araç Çubuğundaki Stil Denetimleri](how-to-style-controls-on-a-toolbar.md)
- [WPF denetimleri Galeri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
