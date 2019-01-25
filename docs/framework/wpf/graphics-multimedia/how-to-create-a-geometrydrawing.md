---
title: 'Nasıl yapılır: GeometryDrawing Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: c3312802b4a623afc10b620dbe2159d2c52a41a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646233"
---
# <a name="how-to-create-a-geometrydrawing"></a>Nasıl yapılır: GeometryDrawing Oluşturma
Bu örnek, oluşturmak ve görüntülemek nasıl gösterir. bir <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> ilişkilendirerek şeklin dolgu ile ana hat oluşturmanızı sağlayan bir <xref:System.Windows.Media.Pen> ve <xref:System.Windows.Media.Brush> ile bir <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Şeklin yapısını açıklar <xref:System.Windows.Media.GeometryDrawing.Brush%2A> şeklin dolgu açıklar ve <xref:System.Windows.Media.GeometryDrawing.Pen%2A> şeklin ana hat açıklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.GeometryDrawing> şekil işlemek için. Şekil tarafından açıklanan bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesneleri. Şeklin içinin ile boyanır bir <xref:System.Windows.Media.LinearGradientBrush> ve anahattı ile çizilen bir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Kullanarak görüntülenen bir <xref:System.Windows.Media.ImageDrawing> ve <xref:System.Windows.Controls.Image> öğesi.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Sonuç, aşağıdaki resimde gösterilmektedir <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing iki elips](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Daha karmaşık çizimler için tek bir bileşik kullanarak çizim birden çok çizim nesneleri birleştirebilirsiniz. bir <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.DrawingGroup>
- [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [Bileşik Çizim Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
