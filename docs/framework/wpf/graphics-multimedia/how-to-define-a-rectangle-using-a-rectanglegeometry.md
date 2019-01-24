---
title: 'Nasıl yapılır: RectangleGeometry Kullanarak Dikdörtgen Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 9c57f1536065af0bca1f3752179547daa502c066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511652"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Nasıl yapılır: RectangleGeometry Kullanarak Dikdörtgen Tanımlama
Bu örnek nasıl kullanılacağını açıklar <xref:System.Windows.Media.RectangleGeometry> dikdörtgen açıklamak için sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.RectangleGeometry>.  Göreli konum ve boyut dikdörtgenin tarafından tanımlanan bir <xref:System.Windows.Rect> yapısı. Göreli konumu `50,50` ve yüksekliğini ve genişliğini `25` kare oluşturma. Dikdörtgenin iç ile boyanacağını bir <xref:System.Windows.Media.Brushes.LemonChiffon%2A> fırça ve anahattı boyanır bir <xref:System.Windows.Media.Brushes.Black%2A> bir kalınlığı vuruşlu `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 Bu örnekte kullanılan olsa da bir <xref:System.Windows.Shapes.Path> işlemek için <xref:System.Windows.Media.RectangleGeometry>, kullanmak için başka birçok yöntemle <xref:System.Windows.Media.RectangleGeometry> nesneleri. Örneğin, bir <xref:System.Windows.Media.RectangleGeometry> belirtmek için kullanılan <xref:System.Windows.UIElement.Clip%2A> , bir <xref:System.Windows.UIElement> veya <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> , bir <xref:System.Windows.Media.GeometryDrawing>.  
  
 Diğer basit geometri sınıfları <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.EllipseGeometry>. Daha karmaşık olanları yanı sıra bu geometriler ayrıca kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [Bileşik Şekil Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [PathGeometry Kullanarak Şekil Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
