---
title: 'Nasıl yapılır: GridSplitter ile Sütunları Yeniden Boyutlandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: f743e9ccf8a984a646a4b8f05ee99162e5bc73ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210444"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Nasıl yapılır: GridSplitter ile Sütunları Yeniden Boyutlandırma
Bu örnekte, dikey bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.GridSplitter> iki sütunları arasındaki boşluğu yeniden dağıtmak için bir <xref:System.Windows.Controls.Grid> boyutlarını değiştirmeden <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Örnek  
 **Bu yer GridSplitter nasıl bir sütun kenarı**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> bitişik sütunları yeniden boyutlandırır bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Column%2A> yeniden boyutlandırmak istediğiniz sütunlardan birine ekli özellik. Varsa, <xref:System.Windows.Controls.Grid> sahip birden fazla satır kümesi <xref:System.Windows.Controls.Grid.RowSpan%2A> satır sayısını ekli özellik. Ardından <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğini <xref:System.Windows.HorizontalAlignment.Left> veya <xref:System.Windows.HorizontalAlignment.Right> (ayarladığınız hangi hizalama yeniden boyutlandırmak istediğiniz iki sütuna bağlıdır). Son olarak, ayarlama <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğini <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> kendi sütun yok diğer denetimleri tarafından görünmeyebilir <xref:System.Windows.Controls.Grid>. Bu sorunu önlemek hakkında daha fazla bilgi için bkz. [bir GridSplitter'ın görünür olduğundan emin olun](how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Bir sütun kaplayan bir GridSplitter'ın oluşturma**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bir sütun kaplayan bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Column%2A> yeniden boyutlandırmak istediğiniz sütunlardan birine ekli özellik. Kılavuzunuzun birden fazla satır varsa Ayarla <xref:System.Windows.Controls.Grid.RowSpan%2A> satır sayısını ekli özellik. Ardından <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> için <xref:System.Windows.HorizontalAlignment.Center>ayarlayın <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğini <xref:System.Windows.VerticalAlignment.Stretch>, ayarlayıp <xref:System.Windows.Controls.ColumnDefinition.Width%2A> içeren sütunun <xref:System.Windows.Controls.GridSplitter> için <xref:System.Windows.GridLength.Auto%2A>.  
  
 Aşağıdaki örnek, dikey tanımlamak gösterilmektedir <xref:System.Windows.Controls.GridSplitter> bir sütun kaplayan ve her iki tarafında sütunları yeniden boyutlandırır.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridSplitter>
- [Nasıl Yapılır Konuları](gridsplitter-how-to-topics.md)
