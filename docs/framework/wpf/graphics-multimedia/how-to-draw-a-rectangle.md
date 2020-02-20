---
title: 'Nasıl yapılır: Dikdörtgen Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452941"
---
# <a name="how-to-draw-a-rectangle"></a>Nasıl yapılır: Dikdörtgen Çizme
Bu örnek, <xref:System.Windows.Shapes.Rectangle> öğesi kullanılarak nasıl dikdörtgen çizileceğini gösterir.  
  
 Bir dikdörtgen çizmek için bir <xref:System.Windows.Shapes.Rectangle> öğesi oluşturun ve <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>belirtin. Dikdörtgenin içini boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A>ayarlayın. Dikdörtgene bir ana hat vermek için, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliklerini kullanın.  
  
 Dikdörtgene yuvarlatılmış köşeler vermek için isteğe bağlı <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özelliklerini belirtin. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri, dikdörtgenin köşelerini yuvarlamak için kullanılan elipsin x ekseni ve y ekseni yarıçapı türünü ayarlar.  
  
 Aşağıdaki örnekte, iki <xref:System.Windows.Shapes.Rectangle> öğesi bir <xref:System.Windows.Controls.Canvas>çizilir. İlk dikdörtgenin iç <xref:System.Windows.Media.Brushes.Blue%2A> vardır. İkinci dikdörtgen <xref:System.Windows.Media.Brushes.Blue%2A> iç, <xref:System.Windows.Media.Brushes.Black%2A> ana hat ve yuvarlatılmış köşeler vardır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Bu örnek, dikdörtgenleri içermesi için bir <xref:System.Windows.Controls.Canvas> kullansa da metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte dikdörtgen öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz. Aslında, dikdörtgenler <xref:System.Windows.Controls.Grid> panellerin bölümleri için arka plan sağlamak üzere özellikle faydalıdır. Bir örnek için bkz. [tabloya genel bakış](../advanced/table-overview.md).  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Rectangle>
- [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)
- [Tabloya Genel Bakış](../advanced/table-overview.md)
