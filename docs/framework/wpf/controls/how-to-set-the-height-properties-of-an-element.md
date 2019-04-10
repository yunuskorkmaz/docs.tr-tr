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
ms.openlocfilehash: fb655630336c3b69afdc726a2e3c5a2cb8838667
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221593"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama
## <a name="example"></a>Örnek  
 Bu örnek, görsel olarak işleme davranışı dört yükseklik ilgili özellikleri arasında farklılıklar gösterir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Sınıfı, bir öğenin yükseklik özelliklerini tanımlayan dört özelliği sunar. Bu dört özellik çakışabilir ve bunu yaptıklarında önceliklidir değeri aşağıdaki şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinHeight%2A> değeri önceliklidir <xref:System.Windows.FrameworkElement.MaxHeight%2A> sırayla önceliklidir değeri <xref:System.Windows.FrameworkElement.Height%2A> değeri. Dördüncü bir özellik <xref:System.Windows.FrameworkElement.ActualHeight%2A>, salt okunur ve düzen işlemine etkileşim tarafından belirlendiği gerçek yüksekliği bildirir.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler çizmek bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) bir alt öğesi olarak <xref:System.Windows.Controls.Canvas>. Yükseklik özelliklerini değiştirmek bir <xref:System.Windows.Shapes.Rectangle> bir dizi kullanarak <xref:System.Windows.Controls.ListBox> özellik değerlerini temsil eden öğeler <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, ve <xref:System.Windows.FrameworkElement.Height%2A>. Bu şekilde, her bir özellik önceliğini görsel olarak görüntülenir.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki arka plan kod örnekleri olaylarını işlemek, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayını başlatır. Her işleyici girişini alır <xref:System.Windows.Controls.ListBox>, değer olarak ayrıştırır bir <xref:System.Double>ve belirtilen yükseklik ilgili özellik için değer geçerlidir. Yükseklik değerleri de bir dizeye dönüştürülür ve çeşitli yazılan <xref:System.Windows.Controls.TextBlock> öğeleri (söz konusu öğelerin tanımı içinde seçili XAML gösterilmez).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Tam bir örnek için bkz. [yükseklik özellikleri örneği](https://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Öğenin Genişlik Özelliklerini Ayarlama](how-to-set-the-width-properties-of-an-element.md)
- [Panellere Genel Bakış](panels-overview.md)
- [Yükseklik özellikleri örneği](https://go.microsoft.com/fwlink/?LinkID=159993)
