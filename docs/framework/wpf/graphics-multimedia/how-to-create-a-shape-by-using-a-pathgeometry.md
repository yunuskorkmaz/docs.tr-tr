---
title: 'Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: b0ab703596612524881ab892a1095b0f49cd1551
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904325"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma
Bu örnekte, kullanarak şekil oluşturma işlemi gösterilmektedir <xref:System.Windows.Media.PathGeometry> sınıfı. <xref:System.Windows.Media.PathGeometry> nesnelerinden oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure> kendisi bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şekil bağlı bir bölümünü temsil eden nesneleri. Segment türler <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, ve <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.PathGeometry> bir üçgen oluşturmak için. <xref:System.Windows.Media.PathGeometry> Kullanarak görüntülenen bir <xref:System.Windows.Shapes.Path> öğesi.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Önceki örnekte oluşturulan şekli aşağıda gösterilmiştir.  
  
 ![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
PathGeometry ile oluşturulan bir üçgen  
  
 Önceki örnekte, bir üçgen oldukça basit bir şekil nasıl oluşturulacağını gösterir. A <xref:System.Windows.Media.PathGeometry> yaylar ve eğriler gibi daha karmaşık şekiller oluşturmak için de kullanılabilir. Örnekler için bkz [elips yay oluşturma](how-to-create-an-elliptical-arc.md), [üçüncü dereceden Bezier eğrisi oluşturma](how-to-create-a-cubic-bezier-curve.md), ve [ikinci dereceden Bezier eğrisi oluşturma](how-to-create-a-quadratic-bezier-curve.md).  
  
 Bu örnek, daha büyük örnek bir parçasıdır; tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Geometriye Genel Bakış](geometry-overview.md)
- [Geometriler ile ilgili örnek](https://go.microsoft.com/fwlink/?LinkID=159989)
