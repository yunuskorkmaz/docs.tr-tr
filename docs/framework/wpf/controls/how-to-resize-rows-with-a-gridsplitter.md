---
title: 'Nasıl yapılır: GridSplitter ile Satırları Yeniden Boyutlandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 6760a7a691af4f666294556cae3bc95a4299730a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074280"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Nasıl yapılır: GridSplitter ile Satırları Yeniden Boyutlandırma
Bu örnek, yatay kullanmayı gösterir. <xref:System.Windows.Controls.GridSplitter> iki satır arasındaki boşluğu yeniden dağıtmak için bir <xref:System.Windows.Controls.Grid> boyutlarını değiştirmeden <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Örnek  
 **Bu yer GridSplitter nasıl bir satır ucuna**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> bitişik satır içinde yeniden boyutlandırır bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Row%2A> yeniden boyutlandırmak istediğiniz satırlardan birine ekli özellik. Varsa, <xref:System.Windows.Controls.Grid> birden fazla sütunu kümesi <xref:System.Windows.Controls.Grid.ColumnSpan%2A> ekli özellik sütun sayısını belirtmek için. Ardından <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> için <xref:System.Windows.VerticalAlignment.Top> veya <xref:System.Windows.VerticalAlignment.Bottom> (ayarladığınız hangi hizalama yeniden boyutlandırmak istediğiniz iki satıra bağlıdır). Son olarak, ayarlama <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 Aşağıdaki örnek, bir yatay tanımlamak gösterilmektedir <xref:System.Windows.Controls.GridSplitter> bitişik satır göre yeniden boyutlandırır.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> kendi satır kaplayabilir değil diğer denetimleri tarafından görünmeyebilir <xref:System.Windows.Controls.Grid>. Bu sorunu önlemek hakkında daha fazla bilgi için bkz. [bir GridSplitter'ın görünür olduğundan emin olun](how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Bir satır kaplayan bir GridSplitter'ın oluşturma**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> bir satır kaplayan bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Row%2A> yeniden boyutlandırmak istediğiniz satırlardan birine ekli özellik. Varsa, <xref:System.Windows.Controls.Grid> birden fazla sütunu kümesi <xref:System.Windows.Controls.Grid.ColumnSpan%2A> sütun sayısını ekli özellik. Ardından <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> için <xref:System.Windows.VerticalAlignment.Center>ayarlayın <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Stretch>, ayarlayıp <xref:System.Windows.Controls.RowDefinition.Height%2A> içeren satırın <xref:System.Windows.Controls.GridSplitter> için <xref:System.Windows.GridLength.Auto%2A>.  
  
 Aşağıdaki örnek, bir yatay tanımlamak gösterilmektedir <xref:System.Windows.Controls.GridSplitter> bir satır kaplayan ve her iki tarafında satırları yeniden boyutlandırır.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridSplitter>
- [Nasıl Yapılır Konuları](gridsplitter-how-to-topics.md)
