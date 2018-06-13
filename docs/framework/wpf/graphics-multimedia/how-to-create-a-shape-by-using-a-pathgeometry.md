---
title: 'Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: 6c77844b054dd89a0c3f3cbecd0725968df9ae71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560188"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma
Bu örnek kullanılarak bir şeklin oluşturulacağını gösterir <xref:System.Windows.Media.PathGeometry> sınıfı. <xref:System.Windows.Media.PathGeometry> nesnelerinden oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure> kendisini bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şeklin bağlı bir bölümünü temsil eden nesneler. Segment türler <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, ve <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.PathGeometry> bir üçgen oluşturmak için. <xref:System.Windows.Media.PathGeometry> Kullanılarak görüntülenen bir <xref:System.Windows.Shapes.Path> öğesi.  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Aşağıdaki çizimde önceki örnekte oluşturulan şekli gösterir.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
PathGeometry ile oluşturulan bir üçgen  
  
 Önceki örnekte oldukça basit bir şekil, bir üçgen nasıl oluşturulacağını gösterir. A <xref:System.Windows.Media.PathGeometry> yaylar ve eğrileri gibi daha karmaşık şekilleri oluşturmak için de kullanılabilir. Örnekler için bkz: [elips yay oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [küp Bezier eğrisi oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), ve [ikinci dereceden Bezier eğrisi oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).  
  
 Bu örnek daha büyük bir parçasıdır; tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989)
