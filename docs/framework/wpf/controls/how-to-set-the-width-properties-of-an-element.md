---
title: 'Nasıl yapılır: Öğenin Genişlik Özelliklerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124279"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Nasıl yapılır: Öğenin Genişlik Özelliklerini Ayarlama
## <a name="example"></a>Örnek  
 Bu örnek, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]içindeki dört Genişlik ile ilgili özellikler arasındaki işleme davranışlarındaki farkları görsel olarak gösterir.  
  
 <xref:System.Windows.FrameworkElement> sınıfı, bir öğenin genişlik özelliklerini tanımlayan dört özellik sunar. Bu dört Özellik çakışabilir ve ne zaman, öncelik veren değer aşağıdaki şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinWidth%2A> değeri <xref:System.Windows.FrameworkElement.MaxWidth%2A> değerine göre önceliklidir ve bu da <xref:System.Windows.FrameworkElement.Width%2A> değerinden önceliklidir. Dördüncü bir özellik <xref:System.Windows.FrameworkElement.ActualWidth%2A>, salt okunurdur ve düzen süreciyle etkileşimler tarafından belirlendiği şekilde gerçek genişliği raporlar.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler, <xref:System.Windows.Controls.Canvas>alt öğesi olarak bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) çizer. Bir <xref:System.Windows.Shapes.Rectangle> Width özelliklerini <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>ve <xref:System.Windows.FrameworkElement.Width%2A>özellik değerlerini temsil eden bir dizi <xref:System.Windows.Controls.ListBox> öğesi kullanarak değiştirebilirsiniz. Bu şekilde, her bir özelliğin önceliği görsel olarak görüntülenir.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki arka plan kod örnekleri <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayının harekete geçirme olaylarını işler. Her özel yöntem <xref:System.Windows.Controls.ListBox>girişi alır, değeri bir <xref:System.Double>ayrıştırır ve değeri belirtilen genişlik ile ilgili özelliğe uygular. Width değerleri Ayrıca bir dizeye dönüştürülür ve çeşitli <xref:System.Windows.Controls.TextBlock> öğelerine yazılır (Bu öğelerin tanımı seçili XAML 'de gösterilmez).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Tüm örnek için bkz. [Width özellikleri karşılaştırma örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Panellere Genel Bakış](panels-overview.md)
- [Öğenin Yükseklik Özelliklerini Ayarlama](how-to-set-the-height-properties-of-an-element.md)
- [Width özellikleri karşılaştırma örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
