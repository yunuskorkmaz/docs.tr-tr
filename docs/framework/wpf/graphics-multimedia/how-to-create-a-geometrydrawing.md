---
title: 'Nasıl yapılır: GeometryDrawing Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 6eb604a8446000ef308c2b5a99480fb6a476c949
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373822"
---
# <a name="how-to-create-a-geometrydrawing"></a>Nasıl yapılır: GeometryDrawing Oluşturma
Bu örnek, oluşturmak ve görüntülemek nasıl gösterir. bir <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> ilişkilendirerek şeklin dolgu ile ana hat oluşturmanızı sağlayan bir <xref:System.Windows.Media.Pen> ve <xref:System.Windows.Media.Brush> ile bir <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Şeklin yapısını açıklar <xref:System.Windows.Media.GeometryDrawing.Brush%2A> şeklin dolgu açıklar ve <xref:System.Windows.Media.GeometryDrawing.Pen%2A> şeklin ana hat açıklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.GeometryDrawing> şekil işlemek için. Şekil tarafından açıklanan bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesneleri. Şeklin içinin ile boyanır bir <xref:System.Windows.Media.LinearGradientBrush> ve anahattı ile çizilen bir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Kullanarak görüntülenen bir <xref:System.Windows.Media.ImageDrawing> ve <xref:System.Windows.Controls.Image> öğesi.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Sonuç, aşağıdaki resimde gösterilmektedir <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing iki elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Daha karmaşık çizimler için tek bir bileşik kullanarak çizim birden çok çizim nesneleri birleştirebilirsiniz. bir <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.DrawingGroup>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [Bileşik Çizim Oluşturma](how-to-create-a-composite-drawing.md)
