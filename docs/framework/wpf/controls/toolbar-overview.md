---
title: ToolBar Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 0c66867ce4d86a11424d7a7a859817d603b4227e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="toolbar-overview"></a>ToolBar Genel Bakışı
<xref:System.Windows.Controls.ToolBar> denetimleri, genellikle kendi işlevleriyle ilgili komutlar veya denetimler grubu için kapsayıcı görevi görür. A <xref:System.Windows.Controls.ToolBar> genellikle komutları çağıran düğmeler içerir.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar Denetimi  
 <xref:System.Windows.Controls.ToolBar> Denetimini çubuk benzeri düzenlemeleri düğmeler veya diğer denetimlerin tek bir satır veya sütun adını alır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimleri doğal kısıtlı boyutta içinde uymayan herhangi bir öğeyi yerleştiren taşma mekanizması sağlar <xref:System.Windows.Controls.ToolBar> özel taşma alanına. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimleri genellikle kullanılan ile ilgili <xref:System.Windows.Controls.ToolBarTray> kullanıcı tarafından başlatılan boyutlandırma ve araç çubuklarını düzenleme için özel düzen davranışı ve bunun yanı sıra destek sağlayan denetim.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Araç çubukları konumunu ToolBarTray içindeki belirtme  
 Kullanım <xref:System.Windows.Controls.ToolBar.Band%2A> ve <xref:System.Windows.Controls.ToolBar.BandIndex%2A> konumlandırmak için Özellikler <xref:System.Windows.Controls.ToolBar> içinde <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> konumu gösterir <xref:System.Windows.Controls.ToolBar> üst içinde yerleştirilir <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> bir sırayı gösterir <xref:System.Windows.Controls.ToolBar> kendi bandı içinde yerleştirilir. Aşağıdaki örnekte gösterildiği yerleştirmek için bu özelliği nasıl kullanmak <xref:System.Windows.Controls.ToolBar> içinde denetleyen bir <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Taşma Öğeleriyle Araç çubukları  
 Genellikle <xref:System.Windows.Controls.ToolBar> denetimler araç çubuğunun boyuta sığması daha fazla öğe içeriyor. Bu gerçekleştiğinde, <xref:System.Windows.Controls.ToolBar> taşma düğmesini görüntüler. Taşma öğeleri görmek için bir kullanıcı taşma düğmesine tıklar ve öğeleri aşağıdaki açılır pencerede gösterilen <xref:System.Windows.Controls.ToolBar>. Aşağıdaki grafik gösterildiği bir <xref:System.Windows.Controls.ToolBar> taşma öğeleriyle.  
  
 ![Araç çubuğu taşması ile](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
Taşma Öğeleriyle Araç çubuğu  
  
 Araç çubuğundaki öğeyi taşma panelinde ayarlayarak zaman yerleştirildiğini belirtebilirsiniz <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> özelliğine bağlı <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, veya <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Aşağıdaki örnek, araç çubuğundaki son dört düğmeleri her zaman taşma panelinde olması gerektiğini belirtir.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> Kullanan bir <xref:System.Windows.Controls.Primitives.ToolBarPanel> ve <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> içinde kendi <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> Araç çubuğundaki öğelerin düzenini sorumludur.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> Üzerinde sığmayan öğelerin düzeninden sorumludur <xref:System.Windows.Controls.ToolBar>. Bir örnek için bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ToolBar>, bkz:  
  
 [Araç çubuğu stilleri ve şablonları](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [Araç Çubuğundaki Stil Denetimleri](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [WPF denetimleri galeri örneği](http://go.microsoft.com/fwlink/?LinkID=160053)
