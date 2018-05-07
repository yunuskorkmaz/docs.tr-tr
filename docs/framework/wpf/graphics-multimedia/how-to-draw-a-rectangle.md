---
title: 'Nasıl yapılır: Dikdörtgen Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 100f1a8062628e892e9a71b988bb2a8754ea6bad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-rectangle"></a>Nasıl yapılır: Dikdörtgen Çizme
Bu örnek kullanarak dikdörtgen çizmek nasıl gösterir <xref:System.Windows.Shapes.Rectangle> öğesi.  
  
 Dikdörtgen çizmek için oluşturma bir <xref:System.Windows.Shapes.Rectangle> öğesi ve kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>. Dikdörtgenin içini boyamak için ayarlanmış kendi <xref:System.Windows.Shapes.Shape.Fill%2A>. Dikdörtgene anahat vermek için kullanın, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri.  
  
 Yuvarlanmış köşeleri dikdörtgene vermek için isteğe bağlı belirtin <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> Ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri dikdörtgen köşelerinde yuvarlamak için kullanılan elipsin x ve y ekseni yarıçaplarını ayarlayın.  
  
 Aşağıdaki örnekte, iki <xref:System.Windows.Shapes.Rectangle> öğeleri içinde çizilmiştir bir <xref:System.Windows.Controls.Canvas>. İlk dikdörtgen sahip bir <xref:System.Windows.Media.Brushes.Blue%2A> iç. İkinci dikdörtgeni sahip bir <xref:System.Windows.Media.Brushes.Blue%2A> iç, bir <xref:System.Windows.Media.Brushes.Black%2A> anahat ve yuvarlak köşeleri.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Bu örnek kullansa da bir <xref:System.Windows.Controls.Canvas> dikdörtgenler içermek için dikdörtgen öğelerini (ve diğer tüm şekil öğelerini) tüm kullanabilirsiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> metin dışı içeriği destekler. Aslında, dikdörtgenler bölümlerini için arka plan sağlamak için özellikle yararlıdır <xref:System.Windows.Controls.Grid> paneller. Bir örnek için bkz: [tablo genel bakışı](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Bu örnek daha büyük bir örneğin parçasıdır; tam bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Rectangle>  
 [Şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Tabloya Genel Bakış](../../../../docs/framework/wpf/advanced/table-overview.md)
