---
title: 'Nasıl yapılır: PathGeometry İçinde LineSegment Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: fc7fbad1e534988a36d85c55c1b6a8249692ad67
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452090"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a>Nasıl yapılır: PathGeometry İçinde LineSegment Oluşturma

Bu örnek, bir çizgi segmentinin nasıl oluşturulacağını gösterir. Bir çizgi segmenti oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.LineSegment> sınıflarını kullanın.

## <a name="example"></a>Örnek

Aşağıdaki örneklerde (10, 50) öğesinden (200, 70) bir <xref:System.Windows.Media.LineSegment> çizilir. Aşağıdaki çizim, elde edilen <xref:System.Windows.Media.LineSegment>gösterir; koordinat sistemini göstermek için bir kılavuz arka planı eklenmiştir.

![PathFigure Içindeki bir LineSegment](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") (10, 50) konumundan (200, 70) çizilmiş bir LineSegment

xaml

[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için öznitelik sözdizimini kullanabilirsiniz.

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

xaml

(Bu öznitelik sözdiziminin aslında bir <xref:System.Windows.Media.PathGeometry>daha hafif bir sürümünü <xref:System.Windows.Media.StreamGeometry>oluşturduğunu unutmayın. Daha fazla bilgi için [yol biçimlendirme sözdizimi](path-markup-syntax.md) sayfasına bakın.)

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ayrıca nesne öğesi söz dizimini kullanarak bir çizgi kesimi çizebilirsiniz. Aşağıdaki, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğine eşdeğerdir.

```xaml
<Path Stroke="Black" StrokeThickness="1">
  <Path.Data>
    <PathGeometry>
      <PathFigure StartPoint="10,50">
        <LineSegment Point="200,70" />
      </PathFigure>
    </PathGeometry>
  </Path.Data>
</Path>
```

```csharp
PathFigure myPathFigure = new PathFigure();
myPathFigure.StartPoint = new Point(10, 50);

LineSegment myLineSegment = new LineSegment();
myLineSegment.Point = new Point(200, 70);

PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();
myPathSegmentCollection.Add(myLineSegment);

myPathFigure.Segments = myPathSegmentCollection;

PathFigureCollection myPathFigureCollection = new PathFigureCollection();
myPathFigureCollection.Add(myPathFigure);

PathGeometry myPathGeometry = new PathGeometry();
myPathGeometry.Figures = myPathFigureCollection;

Path myPath = new Path();
myPath.Stroke = Brushes.Black;
myPath.StrokeThickness = 1;
myPath.Data = myPathGeometry;
```

```vb
Dim myPathFigure As New PathFigure()
myPathFigure.StartPoint = New Point(10, 50)

Dim myLineSegment As New LineSegment()
myLineSegment.Point = New Point(200, 70)

Dim myPathSegmentCollection As New PathSegmentCollection()
myPathSegmentCollection.Add(myLineSegment)

myPathFigure.Segments = myPathSegmentCollection

Dim myPathFigureCollection As New PathFigureCollection()
myPathFigureCollection.Add(myPathFigure)

Dim myPathGeometry As New PathGeometry()
myPathGeometry.Figures = myPathFigureCollection

Dim myPath As New Path()
myPath.Stroke = Brushes.Black
myPath.StrokeThickness = 1
myPath.Data = myPathGeometry
```

Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [Geometriye Genel Bakış](geometry-overview.md)
