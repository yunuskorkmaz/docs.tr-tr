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
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="f34a8-102">Nasıl yapılır: PathGeometry İçinde LineSegment Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f34a8-102">How to: Create a LineSegment in a PathGeometry</span></span>

<span data-ttu-id="f34a8-103">Bu örnek, bir çizgi segmentinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f34a8-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="f34a8-104">Bir çizgi segmenti oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.LineSegment> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f34a8-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>

## <a name="example"></a><span data-ttu-id="f34a8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f34a8-105">Example</span></span>

<span data-ttu-id="f34a8-106">Aşağıdaki örneklerde (10, 50) öğesinden (200, 70) bir <xref:System.Windows.Media.LineSegment> çizilir.</span><span class="sxs-lookup"><span data-stu-id="f34a8-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="f34a8-107">Aşağıdaki çizim, elde edilen <xref:System.Windows.Media.LineSegment>gösterir; koordinat sistemini göstermek için bir kılavuz arka planı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f34a8-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>

<span data-ttu-id="f34a8-108">![PathFigure Içindeki bir LineSegment](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") (10, 50) konumundan (200, 70) çizilmiş bir LineSegment</span><span class="sxs-lookup"><span data-stu-id="f34a8-108">![A LineSegment in a PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") A LineSegment drawn from (10,50) to (200,70)</span></span>

<span data-ttu-id="f34a8-109">xaml</span><span class="sxs-lookup"><span data-stu-id="f34a8-109">[xaml]</span></span>

<span data-ttu-id="f34a8-110">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için öznitelik sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f34a8-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

<span data-ttu-id="f34a8-111">xaml</span><span class="sxs-lookup"><span data-stu-id="f34a8-111">[xaml]</span></span>

<span data-ttu-id="f34a8-112">(Bu öznitelik sözdiziminin aslında bir <xref:System.Windows.Media.PathGeometry>daha hafif bir sürümünü <xref:System.Windows.Media.StreamGeometry>oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f34a8-112">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="f34a8-113">Daha fazla bilgi için [yol biçimlendirme sözdizimi](path-markup-syntax.md) sayfasına bakın.)</span><span class="sxs-lookup"><span data-stu-id="f34a8-113">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>

<span data-ttu-id="f34a8-114">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ayrıca nesne öğesi söz dizimini kullanarak bir çizgi kesimi çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f34a8-114">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="f34a8-115">Aşağıdaki, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f34a8-115">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>

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

<span data-ttu-id="f34a8-116">Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="f34a8-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

## <a name="see-also"></a><span data-ttu-id="f34a8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f34a8-117">See also</span></span>

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="f34a8-118">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f34a8-118">Geometry Overview</span></span>](geometry-overview.md)
