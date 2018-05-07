---
title: 'Nasıl yapılır: Çizgi Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: 1093e754912cd3ee3b8474ed7d190913079a9f9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line"></a>Nasıl yapılır: Çizgi Çizme
Bu örnek nasıl kullanarak satırları çizileceğini gösterir <xref:System.Windows.Shapes.Line> öğesi.  
  
 Bir çizgi çizmek için oluşturma bir <xref:System.Windows.Shapes.Line> öğesi. Kullanın, <xref:System.Windows.Shapes.Line.X1%2A> ve <xref:System.Windows.Shapes.Line.Y1%2A> özellikleri, başlangıç noktası; ve kullanmak için kendi <xref:System.Windows.Shapes.Line.X2%2A> ve <xref:System.Windows.Shapes.Line.Y2%2A> uç noktasını ayarlamak için özellikler. Son olarak ayarlamak, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> bir vuruş olmadan çizgi görünmez olduğundan.  
  
 Ayarı <xref:System.Windows.Shapes.Shape.Fill%2A> öğesi bir satır için bir satır hiçbir iç kısmı olmadığından hiçbir etkisi vardır.  
  
 Aşağıdaki örnek içinde üç çizgi çizilmiştir bir <xref:System.Windows.Controls.Canvas> öğesi.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Bu örnek daha büyük bir örneğin parçasıdır; tam bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Line>  
 [Şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037)
