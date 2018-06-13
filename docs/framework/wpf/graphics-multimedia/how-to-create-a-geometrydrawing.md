---
title: 'Nasıl yapılır: GeometryDrawing Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 713cecd10bfa62494c50c96cb8cbece69f7e5660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560666"
---
# <a name="how-to-create-a-geometrydrawing"></a>Nasıl yapılır: GeometryDrawing Oluşturma
Bu örnek oluşturmak ve görüntülemek nasıl gösterir bir <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> şekil dolgu ve anahat ile ilişkilendirerek oluşturmanızı sağlayan bir <xref:System.Windows.Media.Pen> ve <xref:System.Windows.Media.Brush> ile bir <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Şeklin yapısını açıklar <xref:System.Windows.Media.GeometryDrawing.Brush%2A> şeklin dolgu açıklar ve <xref:System.Windows.Media.GeometryDrawing.Pen%2A> şeklin anahat açıklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.GeometryDrawing> şekil işlemek için. Şeklin tarafından açıklanan bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesneleri. Şeklin iç ile boyanır bir <xref:System.Windows.Media.LinearGradientBrush> ve anahattı ile çizilmiş bir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Kullanılarak görüntülenen bir <xref:System.Windows.Media.ImageDrawing> ve bir <xref:System.Windows.Controls.Image> öğesi.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Elde edilen aşağıda gösterilmiştir <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![İki elips GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Daha karmaşık çizimler oluşturmak için tek bir bileşik kullanarak çizim birden çok çizim nesneleri birleştirebilirsiniz bir <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingGroup>  
 [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Bileşik Çizim Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
