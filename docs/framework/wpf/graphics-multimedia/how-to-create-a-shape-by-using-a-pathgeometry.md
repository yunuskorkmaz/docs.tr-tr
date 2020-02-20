---
title: 'Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452051"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma
Bu örnek, <xref:System.Windows.Media.PathGeometry> sınıfını kullanarak bir şeklin nasıl oluşturulacağını gösterir. <xref:System.Windows.Media.PathGeometry> nesneler bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesnesinden oluşur; Her <xref:System.Windows.Media.PathFigure> farklı bir "şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure> bir veya daha fazla <xref:System.Windows.Media.PathSegment> nesnesinden oluşur ve her biri şekil veya şeklin bağlı bir bölümünü temsil eder. Segment türleri <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>ve <xref:System.Windows.Media.BezierSegment>içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir üçgen oluşturmak için <xref:System.Windows.Media.PathGeometry> kullanır. <xref:System.Windows.Media.PathGeometry>, bir <xref:System.Windows.Shapes.Path> öğesi kullanılarak görüntülenir.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Aşağıdaki çizimde, önceki örnekte oluşturulan Şekil gösterilmektedir.  
  
 ![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
PathGeometry ile oluşturulan üçgen  
  
 Önceki örnekte, bir üçgen olan görece basit bir şekil oluşturma gösterildi. <xref:System.Windows.Media.PathGeometry> yay ve eğriler de dahil olmak üzere daha karmaşık şekiller oluşturmak için de kullanılabilir. Örnekler için bkz. [elips yay oluşturma](how-to-create-an-elliptical-arc.md), [üçüncü dereceden Bezier eğrisi oluşturma](how-to-create-a-cubic-bezier-curve.md)ve [ikinci dereceden Bezier eğrisi](how-to-create-a-quadratic-bezier-curve.md)oluşturma.  
  
 Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Geometriye Genel Bakış](geometry-overview.md)
- [Geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
