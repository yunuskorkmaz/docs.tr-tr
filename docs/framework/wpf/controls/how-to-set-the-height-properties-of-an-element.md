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
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124292"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama
## <a name="example"></a>Örnek  
 Bu örnek, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]' deki yükseklik ile ilgili dört özellik arasındaki işleme davranışının farklarını görsel olarak gösterir.  
  
 <xref:System.Windows.FrameworkElement> sınıfı, bir öğenin yükseklik özelliklerini tanımlayan dört özellik sunar. Bu dört Özellik çakışabilir ve ne zaman, öncelik veren değer aşağıdaki şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinHeight%2A> değeri <xref:System.Windows.FrameworkElement.MaxHeight%2A> değerine göre önceliklidir ve bu da <xref:System.Windows.FrameworkElement.Height%2A> değerinden önceliklidir. Dördüncü özellik <xref:System.Windows.FrameworkElement.ActualHeight%2A>, salt okunurdur ve düzen işlemiyle etkileşimler tarafından belirlendiği şekilde gerçek yüksekliği raporlar.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler, <xref:System.Windows.Controls.Canvas>alt öğesi olarak bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) çizer. <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve <xref:System.Windows.FrameworkElement.Height%2A>özellik değerlerini temsil eden bir dizi <xref:System.Windows.Controls.ListBox> öğesi kullanarak bir <xref:System.Windows.Shapes.Rectangle> 'ın yükseklik özelliklerini değiştirebilirsiniz. Bu şekilde, her bir özelliğin önceliği görsel olarak görüntülenir.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki arka plan kod örnekleri <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayının harekete geçirme olaylarını işler. Her işleyici <xref:System.Windows.Controls.ListBox>girişi alır, değeri bir <xref:System.Double>ayrıştırır ve değeri belirtilen yükseklik ile ilgili özelliğe uygular. Yükseklik değerleri aynı zamanda bir dizeye dönüştürülür ve çeşitli <xref:System.Windows.Controls.TextBlock> öğelerine yazılır (Bu öğelerin tanımı seçili XAML 'de gösterilmez).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Tüm örnek için bkz. [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Öğenin Genişlik Özelliklerini Ayarlama](how-to-set-the-width-properties-of-an-element.md)
- [Panellere Genel Bakış](panels-overview.md)
- [Yükseklik özellikleri örneği](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
