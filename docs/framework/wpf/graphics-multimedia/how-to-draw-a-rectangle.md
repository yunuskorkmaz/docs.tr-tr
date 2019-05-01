---
title: 'Nasıl yapılır: Dikdörtgen Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 261026b994b432565928b38ff1657115ff7cbe4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947634"
---
# <a name="how-to-draw-a-rectangle"></a>Nasıl yapılır: Dikdörtgen Çizme
Bu örnek gösterir kullanarak bir dikdörtgen çizmek nasıl <xref:System.Windows.Shapes.Rectangle> öğesi.  
  
 Bir dikdörtgen çizmek için oluşturma bir <xref:System.Windows.Shapes.Rectangle> öğesi ve kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>. Dikdörtgenin iç boyamak için ayarlanmış kendi <xref:System.Windows.Shapes.Shape.Fill%2A>. Anahat dikdörtgen vermek için kullanın, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri.  
  
 Yuvarlak köşeler dikdörtgene vermek için isteğe bağlı belirtin <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri. <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> Ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> dikdörtgenin köşelerini yuvarlatmak için kullanılacak olan elipsin yarıçaplarını x ve y ekseni özelliklerini ayarlayın.  
  
 Aşağıdaki örnekte, iki <xref:System.Windows.Shapes.Rectangle> öğeleri çizilmiştir bir <xref:System.Windows.Controls.Canvas>. İlk dikdörtgen sahip bir <xref:System.Windows.Media.Brushes.Blue%2A> iç. İkinci dikdörtgeni sahip bir <xref:System.Windows.Media.Brushes.Blue%2A> iç, bir <xref:System.Windows.Media.Brushes.Black%2A> yuvarlatılmış köşeler ve ana hat.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Bu örnek kullansa da bir <xref:System.Windows.Controls.Canvas> dikdörtgenler içermek için dikdörtgen öğelerini (ve diğer tüm şekil öğelerine) ile kullanabilirsiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> , metin olmayan içerikleri destekler. Aslında, dikdörtgenler kısımları için arka plan sağlamak için özellikle yararlıdır <xref:System.Windows.Controls.Grid> panelleri. Bir örnek için bkz. [tabloya genel bakış](../advanced/table-overview.md).  
  
 Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Rectangle>
- [Şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)
- [Tabloya Genel Bakış](../advanced/table-overview.md)
