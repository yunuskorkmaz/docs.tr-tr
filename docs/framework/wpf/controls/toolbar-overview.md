---
title: ToolBar Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 816ac0d81ddcaa461a842c0f69fe5ed5b21a32d1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559839"
---
# <a name="toolbar-overview"></a>ToolBar Genel Bakışı
<xref:System.Windows.Controls.ToolBar> denetimler, genellikle kendi işlevleriyle ilgili komutlar veya denetimler grubu için kapsayıcılardır. A <xref:System.Windows.Controls.ToolBar> genellikle komutları çağırır düğmeler içerir.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar Denetimi  
 <xref:System.Windows.Controls.ToolBar> Denetim çubuğu benzeri düzenlemeleri düğmeler veya diğer denetimlerin bir tek bir satır veya sütun adını alır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimleri sağlar, doğal olarak bir boyut ile sınırlandırılmış içinde uymayan herhangi bir öğesi yerleştiren taşması mekanizması <xref:System.Windows.Controls.ToolBar> özel taşma alana. Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> denetimleri genellikle kullanılan ile ilgili <xref:System.Windows.Controls.ToolBarTray> denetimi, kullanıcı tarafından başlatılan boyutlandırma ve araç çubuklarını düzenleme için özel bir düzen davranışı ve bunun yanı sıra destek sağlar.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>ToolBarTray içindeki araç çubukları konumunu belirtme  
 Kullanım <xref:System.Windows.Controls.ToolBar.Band%2A> ve <xref:System.Windows.Controls.ToolBar.BandIndex%2A> konumlandırmak için özellikleri <xref:System.Windows.Controls.ToolBar> içinde <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> hangi konumunu belirten <xref:System.Windows.Controls.ToolBar> içinde üst yerleştirilir <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> bir sırayı gösterir <xref:System.Windows.Controls.ToolBar> kendi bandı içinde yer alır. Aşağıdaki örnekte gösterildiği nasıl yerleştirmek için bu özelliği kullanın <xref:System.Windows.Controls.ToolBar> içinde denetleyen bir <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Taşma Öğeleriyle Araç çubukları  
 Genellikle <xref:System.Windows.Controls.ToolBar> denetimler araç çubuğunun boyuta sığmazsa daha fazla öğe içeriyor. Bu durumda, <xref:System.Windows.Controls.ToolBar> taşma düğmesini görüntüler. Taşma öğeleri görmek için bir kullanıcı taşma düğmesini tıklar ve öğeler aşağıdaki açılır pencerede gösterilir <xref:System.Windows.Controls.ToolBar>. Aşağıdaki grafik gösterildiği bir <xref:System.Windows.Controls.ToolBar> taşma öğeleriyle.  
  
 ![Araç çubuğu taşma ile](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
Araç çubuğu taşma öğeleriyle  
  
 Bir öğe üzerinde bir araç çubuğu taşma panelinde ayarlayarak zaman yerleştirildiğini belirtebilirsiniz <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> özelliğine bağlı <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, veya <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Aşağıdaki örnek, taşma panelinde araç çubuğundaki son dört düğme her zaman kullanılması gerektiğini belirtir.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> Kullanan bir <xref:System.Windows.Controls.Primitives.ToolBarPanel> ve <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> içinde kendi <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> Araç çubuğundaki öğeler düzenini sorumludur.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> Üzerinde uymayan öğelerin düzeni sorumlu <xref:System.Windows.Controls.ToolBar>. Bir örneği bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ToolBar>, bkz:  
  
 [ToolBar stilleri ve şablonları](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [Araç Çubuğundaki Stil Denetimleri](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [WPF denetimleri Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160053)
