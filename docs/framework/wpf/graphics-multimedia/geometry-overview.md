---
title: Geometriye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: f45c13e1af9bc2d1f75da11b13a2c03936b136c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455015"
---
# <a name="geometry-overview"></a>Geometriye Genel Bakış
Bu genel bakışta, şekilleri açıklayan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> sınıflarının nasıl kullanılacağı açıklanmaktadır. Bu konu ayrıca <xref:System.Windows.Media.Geometry> nesneleri ve <xref:System.Windows.Shapes.Shape> öğeleri arasındaki farkları da karşıtlardır.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Geometri nedir?  
 <xref:System.Windows.Media.Geometry> sınıfı ve bundan türetilmiş sınıflar, örneğin <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>ve <xref:System.Windows.Media.CombinedGeometry>, bir 2-b şeklinin geometrisini açıklamanıza olanak sağlar. Bu geometrik açıklamaların birçok kullanımı vardır. bu tür, ekrana boyamak için bir şekil tanımlama veya isabet testi ile klip bölgelerini tanımlama. Bir animasyon yolu tanımlamak için geometriyi bile kullanabilirsiniz.  
  
 <xref:System.Windows.Media.Geometry> nesneler, dikdörtgenler ve daireler gibi basit veya iki ya da daha fazla geometri nesnesinden oluşturulan bileşik olabilir.  Daha karmaşık geometriler, <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> sınıfları kullanılarak oluşturulabilir ve bu da yay ve eğrileri açıklamanıza olanak tanır.  
  
 <xref:System.Windows.Media.Geometry> bir <xref:System.Windows.Freezable>türü olduğundan <xref:System.Windows.Media.Geometry> nesneleri birkaç özel özellik sağlar: [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak, birden fazla nesne arasında paylaşılan, performansı artırmak için salt okuma, klonlanmış ve iş parçacığı açısından güvenli hale getirilebilir. <xref:System.Windows.Freezable> nesneleri tarafından sunulan farklı özellikler hakkında daha fazla bilgi için, [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md)bölümüne bakın.  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometriler ve şekiller  
 <xref:System.Windows.Media.Geometry> ve <xref:System.Windows.Shapes.Shape> sınıfları, her ikisi de 2-b şekilleri (örneğin, <xref:System.Windows.Media.EllipseGeometry> karşılaştırın ve <xref:System.Windows.Shapes.Ellipse>) tanımladıklarından benzerdir, ancak önemli farklılıklar vardır.  
  
 Bir tane için, <xref:System.Windows.Shapes.Shape> sınıfı <xref:System.Windows.FrameworkElement>devralınırken <xref:System.Windows.Media.Geometry> sınıfı <xref:System.Windows.Freezable> sınıfından devralır. Öğeler olduklarından <xref:System.Windows.Shapes.Shape> nesneleri kendilerini işleyebilir ve Düzen sistemine katılabilir, ancak <xref:System.Windows.Media.Geometry> nesneler yapılamaz.  
  
 <xref:System.Windows.Shapes.Shape> nesneler <xref:System.Windows.Media.Geometry> nesnelerden daha kolay kullanılabilir olsa da <xref:System.Windows.Media.Geometry> nesneleri daha çok daha hızlıdır. 2-b grafikleri işlemek için bir <xref:System.Windows.Shapes.Shape> nesnesi kullanıldığında, bir <xref:System.Windows.Media.Geometry> nesnesi, 2-b grafikler için geometrik bölgeyi tanımlamak, kırpma için bir bölge tanımlamak veya isabet testi için bir bölge tanımlamak üzere kullanılabilir.  
  
### <a name="the-path-shape"></a>Yol şekli  
 Bir <xref:System.Windows.Shapes.Shape><xref:System.Windows.Shapes.Path> sınıfı, aslında içeriğini anlatmak için bir <xref:System.Windows.Media.Geometry> kullanır. <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Path.Data%2A> özelliğini bir <xref:System.Windows.Media.Geometry> ayarlayıp <xref:System.Windows.Shapes.Shape.Fill%2A> ve <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliklerini ayarlayarak bir <xref:System.Windows.Media.Geometry>işleyebilirsiniz.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Geometriyi alan ortak özellikler  
 Önceki bölümlerde, geometri nesnelerinin şekil çizme, hareketlendirme ve kırpma gibi çeşitli amaçlar için diğer nesnelerle birlikte kullanılabileceği belirtiliyor. Aşağıdaki tabloda, <xref:System.Windows.Media.Geometry> nesnesi alan özellikleri olan birkaç sınıf listelenmektedir.  
  
|Tür|Özellik|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Basit geometri türleri  
 Tüm geometrilerin temel sınıfı <xref:System.Windows.Media.Geometry>soyut sınıftır.  <xref:System.Windows.Media.Geometry> sınıfından türetilen sınıflar kabaca üç kategoride gruplandırılabilir: basit geometriler, yol geometrileri ve bileşik geometriler.  
  
 Basit geometri sınıfları <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>ve <xref:System.Windows.Media.EllipseGeometry> içerir ve çizgiler, dikdörtgenler ve daireler gibi temel geometrik şekiller oluşturmak için kullanılır.  
  
- <xref:System.Windows.Media.LineGeometry>, çizginin başlangıç noktası ve bitiş noktası belirtilerek tanımlanır.  
  
- <xref:System.Windows.Media.RectangleGeometry>, göreli konumunu ve yüksekliğini ve genişliğini belirten bir <xref:System.Windows.Rect> yapısıyla tanımlanır. <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> özelliklerini ayarlayarak yuvarlak bir dikdörtgen oluşturabilirsiniz.  
  
- Bir <xref:System.Windows.Media.EllipseGeometry>, bir orta nokta, bir x-radius ve y-Radius tarafından tanımlanır.  Aşağıdaki örneklerde, işleme ve kırpma için basit geometrilerin nasıl oluşturulacağı gösterilmektedir.  
  
 Aynı şekiller ve daha karmaşık şekiller, bir <xref:System.Windows.Media.PathGeometry> kullanılarak veya geometri nesnelerini birlikte birleştirerek oluşturulabilir, ancak bu sınıflar bu temel geometrik şekillerin oluşturulması için daha basit bir yol sağlar.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.LineGeometry>oluşturma ve işleme işlemlerinin nasıl yapılacağını gösterir.  Daha önce belirtildiği gibi, <xref:System.Windows.Media.Geometry> bir nesne kendisini çizemez, bu nedenle örnek satırı işlemek için bir <xref:System.Windows.Shapes.Path> şekli kullanır.  Bir çizginin alanı olmadığından, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin ayarlanması etkisizdir; Bunun yerine yalnızca <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri belirtilmiştir. Aşağıdaki çizimde, örneğin çıktısı gösterilmektedir.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
(10, 20) ile (100.130) çizilmiş bir LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Sonraki örnekte, bir <xref:System.Windows.Media.EllipseGeometry>oluşturma ve işleme işlemlerinin nasıl yapılacağı gösterilmektedir.  Örnekler, <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.EllipseGeometry.Center%2A> ayarlar `50,50` ve x-radius ve y-Radius, 100 çapına sahip bir daire oluşturan `50`olarak ayarlanır.  Elipsin iç kısmı, yol öğesinin Fill özelliğine bir değer atanarak, bu durumda <xref:System.Windows.Media.Brushes.Gold%2A>boyanır. Aşağıdaki çizimde, örneğin çıktısı gösterilmektedir.  
  
 ![Bir EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
EllipseGeometry (50, 50) çizilmiş bir  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.RectangleGeometry>oluşturma ve işleme işlemlerinin nasıl yapılacağını gösterir.  Dikdörtgenin konumu ve boyutları bir <xref:System.Windows.Rect> yapısı tarafından tanımlanır. Konum `50,50` ve yükseklik ve Genişlik hem `25`hem de bir kare oluşturur. Aşağıdaki çizimde, örneğin çıktısı gösterilmektedir.  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
50, 50 ' de çizilmiş bir RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Aşağıdaki örnek bir <xref:System.Windows.Media.EllipseGeometry> görüntü için klip bölgesi olarak nasıl kullanılacağını gösterir.  Bir <xref:System.Windows.Controls.Image> nesnesi 200 <xref:System.Windows.FrameworkElement.Width%2A> ve 150 <xref:System.Windows.FrameworkElement.Height%2A> ile tanımlanır.  100 <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> değerine sahip <xref:System.Windows.Media.EllipseGeometry>, 75 <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> değeri ve 100, 75 <xref:System.Windows.Media.EllipseGeometry.Center%2A> değeri görüntünün <xref:System.Windows.UIElement.Clip%2A> özelliğine ayarlanır.  Yalnızca elips alanının içindeki görüntünün bir kısmı görüntülenir. Aşağıdaki çizimde, örneğin çıktısı gösterilmektedir.  
  
 ![Kırpmadan ve kırpması olmayan bir görüntü](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Görüntü denetimini kırpmak için kullanılan bir EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Yol geometrileri  
 <xref:System.Windows.Media.PathGeometry> sınıfı ve hafif eşdeğeri olan <xref:System.Windows.Media.StreamGeometry> sınıfı, yaylar, eğrilerden ve satırlardan oluşan birden çok karmaşık rakamı açıklama sağlar.  
  
 <xref:System.Windows.Media.PathGeometry> kalp, <xref:System.Windows.Media.PathFigure> nesnelerin bir koleksiyonudur, bu nedenle her bir şekil <xref:System.Windows.Media.PathGeometry>ayrı bir şekil açıkladığı için adlandırılır. Her bir <xref:System.Windows.Media.PathFigure> bir veya daha fazla <xref:System.Windows.Media.PathSegment> nesnesinden oluşur ve her biri, şeklin bir kesimini açıklar.  
  
 Birçok segment türü vardır.  
  
|Segment türü|Açıklama|Örnek|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|İki punto arasında elips bir yay oluşturur.|[Elips bir yay oluşturun](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|İki punto arasında üçüncü dereceden Bezier eğrisi oluşturur.|[Üçüncü dereceden Bezier eğrisi oluşturun](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|İki noktayla bir çizgi oluşturur.|[PathGeometry İçinde LineSegment Oluşturma](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Üçüncü dereceden Bezier eğrileri dizisi oluşturur.|<xref:System.Windows.Media.PolyBezierSegment> türü sayfasına bakın.|  
|<xref:System.Windows.Media.PolyLineSegment>|Bir dizi satır oluşturur.|<xref:System.Windows.Media.PolyLineSegment> türü sayfasına bakın.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|İkinci dereceden Bezier eğrileri serisi oluşturur.|<xref:System.Windows.Media.PolyQuadraticBezierSegment> sayfasına bakın.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|İkinci dereceden Bezier eğrisi oluşturur.|[Ikinci dereceden Bezier eğrisi oluşturun](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Bir <xref:System.Windows.Media.PathFigure> segment bir sonraki segmentin başlangıç noktası olan her bir segmentin bitiş noktasıyla tek bir geometrik şekil halinde birleştirilir. Bir <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.PathFigure.StartPoint%2A> özelliği, ilk segmentin çizilme noktasını belirtir. Sonraki her segment, önceki segmentin bitiş noktasında başlar. Örneğin, `10,50` ' den `10,150` dikey bir çizgi <xref:System.Windows.Media.PathFigure.StartPoint%2A> özelliği `10,50` olarak ayarlanarak ve <xref:System.Windows.Media.LineSegment> <xref:System.Windows.Media.LineSegment.Point%2A> Özellik ayarıyla bir `10,150`oluşturarak tanımlanabilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.LineSegment> tek bir <xref:System.Windows.Media.PathFigure> oluşan basit bir <xref:System.Windows.Media.PathGeometry> oluşturur ve onu bir <xref:System.Windows.Shapes.Path> öğesi kullanarak görüntüler. <xref:System.Windows.Media.PathFigure> nesnesinin <xref:System.Windows.Media.PathFigure.StartPoint%2A> `10,20` olarak ayarlanır ve bir <xref:System.Windows.Media.LineSegment> bir `100,130`bitiş noktasıyla tanımlanır. Aşağıdaki çizimde bu örnek tarafından oluşturulan <xref:System.Windows.Media.PathGeometry> gösterilmektedir.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
Tek bir LineSegment içeren bir PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Bu örnekte, önceki <xref:System.Windows.Media.LineGeometry> örnekle karşı bir değer de vardır.  <xref:System.Windows.Media.PathGeometry> için kullanılan sözdizimi, basit bir <xref:System.Windows.Media.LineGeometry>kullanılandan çok daha ayrıntılıdır ve bu durumda <xref:System.Windows.Media.LineGeometry> sınıfının kullanılması daha anlamlı olabilir, ancak <xref:System.Windows.Media.PathGeometry> ayrıntılı sözdizimi, son derece karmaşık ve karmaşık geometrik bölgelere izin verir.  
  
 Daha karmaşık geometriler, <xref:System.Windows.Media.PathSegment> nesnelerinin bir birleşimi kullanılarak oluşturulabilir.  
  
 Sonraki örnekte şekil oluşturmak için bir <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>ve bir <xref:System.Windows.Media.ArcSegment> kullanılmaktadır. Örnek ilk olarak dört nokta tanımlayarak bir üçüncü dereceden Bezier eğrisi oluşturur: önceki segmentin bitiş noktası, bir uç nokta (<xref:System.Windows.Media.BezierSegment.Point3%2A>) ve iki denetim noktası olan bir başlangıç noktası (<xref:System.Windows.Media.BezierSegment.Point1%2A> ve <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Üçüncü dereceden Bezier eğrisinin iki denetim noktası, platformunuza çekmenin tutmanın gibi davranır, aksi takdirde kendi kendine doğru bir çizgi olmak üzere bir eğri üretir. İlk denetim noktası <xref:System.Windows.Media.BezierSegment.Point1%2A>, eğrinin başlangıç bölümünü etkiler; İkinci denetim noktası <xref:System.Windows.Media.BezierSegment.Point2%2A>, eğrinin bitiş bölümünü etkiler.  
  
 Örnek daha sonra, <xref:System.Windows.Media.LineSegment> özelliği tarafından belirtilen noktaya önünde olan önceki <xref:System.Windows.Media.BezierSegment> bitiş noktası arasına çizilmiş bir <xref:System.Windows.Media.LineSegment>ekler.  
  
 Örnek daha sonra, önceki <xref:System.Windows.Media.LineSegment> bitiş noktasından <xref:System.Windows.Media.ArcSegment.Point%2A> özelliği tarafından belirtilen noktaya çizilmiş bir <xref:System.Windows.Media.ArcSegment>ekler. Örnek ayrıca, yayı x ve y-yarıçap (<xref:System.Windows.Media.ArcSegment.Size%2A>), bir döndürme açısı (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), elde edilen yay açısının ne kadar büyük olması gerektiğini belirten bir bayrak (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) ve yayı çiztiği yönü belirten bir değer (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>) belirtir. Aşağıdaki çizimde bu örnek tarafından oluşturulan Şekil gösterilmektedir.  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Daha karmaşık geometriler, bir <xref:System.Windows.Media.PathGeometry>içindeki birden çok <xref:System.Windows.Media.PathFigure> nesnesi kullanılarak oluşturulabilir.  
  
 Aşağıdaki örnek, her biri birden çok <xref:System.Windows.Media.PathSegment> nesne içeren iki <xref:System.Windows.Media.PathFigure> nesne ile bir <xref:System.Windows.Media.PathGeometry> oluşturur.  Yukarıdaki örnekte <xref:System.Windows.Media.PathFigure> ve bir <xref:System.Windows.Media.PolyLineSegment> ve bir <xref:System.Windows.Media.QuadraticBezierSegment> <xref:System.Windows.Media.PathFigure> kullanılır.  Bir <xref:System.Windows.Media.PolyLineSegment> nokta dizisiyle tanımlanır ve <xref:System.Windows.Media.QuadraticBezierSegment> bir denetim noktası ve bir uç nokta ile tanımlanır. Aşağıdaki çizimde bu örnek tarafından oluşturulan Şekil gösterilmektedir.  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
Birden çok rakamı olan PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 <xref:System.Windows.Media.PathGeometry> sınıfı gibi, bir <xref:System.Windows.Media.StreamGeometry> eğri, yay ve satır içerebilen karmaşık bir geometrik şekli tanımlar. <xref:System.Windows.Media.PathGeometry>farklı olarak, bir <xref:System.Windows.Media.StreamGeometry> içerikleri veri bağlamayı, animasyonunu veya değiştirmeyi desteklemez. Karmaşık bir geometriyi açıklamanız, ancak veri bağlama, animasyon veya değişikliği destekleme ek yüküne gerek duymadığınızda <xref:System.Windows.Media.StreamGeometry> kullanın. Verimlilik nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıfı donatıcıları açıklamak için iyi bir seçimdir.  
  
 Bir örnek için bkz. [StreamGeometry kullanarak şekil oluşturma](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi  
 <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> türleri, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] öznitelik sözdizimini, özel bir Move ve Draw komutları serisi kullanarak destekler. Daha fazla bilgi için bkz. [yol biçimlendirme sözdizimi](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Bileşik geometriler  
 Bileşik geometri nesneleri <xref:System.Windows.Media.GeometryGroup>, bir <xref:System.Windows.Media.CombinedGeometry>kullanılarak veya statik <xref:System.Windows.Media.Geometry> yöntemi <xref:System.Windows.Media.Geometry.Combine%2A>çağırarak oluşturulabilir.  
  
- <xref:System.Windows.Media.CombinedGeometry> nesnesi ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi, iki geometri tarafından tanımlanan alanı birleştirmek için bir Boole işlemi gerçekleştirir. alanı olmayan <xref:System.Windows.Media.Geometry> nesneleri atılır. Yalnızca iki <xref:System.Windows.Media.Geometry> nesnesi birleştirilebilir (Bu iki geometrinin bileşik geometriler de olabileceği halde).  
  
- <xref:System.Windows.Media.GeometryGroup> sınıfı, kendi alanını birleştirmeden içerdiği <xref:System.Windows.Media.Geometry> nesnelerinin bir Amalgamation oluşturur. Herhangi bir sayıda <xref:System.Windows.Media.Geometry> nesne <xref:System.Windows.Media.GeometryGroup>eklenebilir. Bir örnek için bkz. [Bileşik şekil oluşturma](how-to-create-a-composite-shape.md).  
  
 Birleştirme işlemi gerçekleştirmediğinden <xref:System.Windows.Media.GeometryGroup> nesneleri kullanmak <xref:System.Windows.Media.CombinedGeometry> nesneleri veya <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi aracılığıyla performans avantajları sağlar.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Birleşik geometriler  
 Yukarıdaki bölümde <xref:System.Windows.Media.CombinedGeometry> nesnesi ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi, içerdikleri geometriler tarafından tanımlanan alanı birleştirdi. <xref:System.Windows.Media.GeometryCombineMode> numaralandırması, geometrilerin nasıl birleştirileceğini belirtir. <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> özelliği için olası değerler şunlardır: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>ve <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu birleşimi ile tanımlanmıştır.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> her ikisi de aynı yarıçapın daireleri olarak tanımlanır, ancak ortalar 50 ile denkleştirilir.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Birleşim birleştirme modunun sonuçları](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu <xref:System.Windows.Media.GeometryCombineMode.Xor>ile tanımlanmıştır.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> her ikisi de aynı yarıçapın daireleri olarak tanımlanır, ancak ortalar 50 ile denkleştirilir.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![XOR birleştirme modunun sonuçları](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Daha fazla örnek için bkz. [Bileşik şekil oluşturma](how-to-create-a-composite-shape.md) ve [Birleşik Geometri oluşturma](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable özellikleri  
 <xref:System.Windows.Freezable> sınıfından devraldığı için <xref:System.Windows.Media.Geometry> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Geometry> nesneleri [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak, birden fazla nesne arasında paylaşılan, performansı artırmak için salt okunurdur, klonlanmış ve yapılan iş parçacığı güvenli. <xref:System.Windows.Freezable> nesneleri tarafından sunulan farklı özellikler hakkında daha fazla bilgi için, [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md)bölümüne bakın.  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Diğer geometri özellikleri  
 <xref:System.Windows.Media.Geometry> sınıfı, aşağıdakiler gibi yararlı yardımcı program yöntemleri de sağlar:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>-<xref:System.Windows.Media.Geometry>alanını alır.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>-geometrinin başka bir <xref:System.Windows.Media.Geometry>içerip içermediğini belirler.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>-bir <xref:System.Windows.Media.Geometry> konturunun belirtilen noktayı içerip içermediğini belirler.  
  
 Yöntemlerinin tamamen listesi için bkz. <xref:System.Windows.Media.Geometry> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Yol İşaretleme Söz Dizimi](path-markup-syntax.md)
- [Nasıl Yapılır Konuları](geometries-how-to-topics.md)
- [Animasyona Genel bakış](animation-overview.md)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
