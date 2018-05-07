---
title: 'Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 467cd57c728be015fb9eb9b974ca6e81e4fd7754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama
## <a name="example"></a>Örnek  
 Bu örnek görsel olarak işleme davranışı dört yüksekliği ile ilgili özelliklerin arasındaki farklar gösterilmektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Sınıfı, bir öğenin yüksekliği özelliklerini tanımlayan dört özelliği sunar. Bu dört özellikleri çakışabilir ve bunu yaptıklarında, önceliklidir değeri şu şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinHeight%2A> değer önceliklidir <xref:System.Windows.FrameworkElement.MaxHeight%2A> sırayla önceliklidir değeri <xref:System.Windows.FrameworkElement.Height%2A> değeri. Dördüncü bir özellik <xref:System.Windows.FrameworkElement.ActualHeight%2A>salt okunurdur ve gerçek yükseklik düzen işlemine ile etkileşim tarafından belirlendiği şekilde bildirir.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler çizin bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) bir alt öğesi olarak <xref:System.Windows.Controls.Canvas>. Yükseklik özelliklerini değiştirebilirsiniz bir <xref:System.Windows.Shapes.Rectangle> bir dizi kullanarak <xref:System.Windows.Controls.ListBox> özellik değerlerini temsil eden öğeleri <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, ve <xref:System.Windows.FrameworkElement.Height%2A>. Bu şekilde, her özelliğin önceliği görsel olarak görüntülenir.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki arka plan kodu örnekleri olayları işlemek, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayını başlatır. Her işleyici girdisinden alan <xref:System.Windows.Controls.ListBox>, değer olarak ayrıştırır bir <xref:System.Double>ve değeri belirtilen yükseklik ilgili özellik için geçerlidir. Yükseklik değerleri de bir dizeye dönüştürülür ve çeşitli yazılmış <xref:System.Windows.Controls.TextBlock> öğelerine (Bu öğelerin tanımları seçilen XAML'de gösterilmez).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Tam bir örnek için bkz: [yükseklik özellikleri örneği](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [Öğenin Genişlik Özelliklerini Ayarlama](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Yükseklik özellikleri örneği](http://go.microsoft.com/fwlink/?LinkID=159993)
