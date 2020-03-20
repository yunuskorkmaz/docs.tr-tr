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
ms.openlocfilehash: 1329f26e588b90fcd25052fb805058915b8825e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186469"
---
# <a name="geometry-overview"></a>Geometriye Genel Bakış
Bu genel bakış, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> şekilleri açıklamak için sınıfların nasıl kullanılacağını açıklar. Bu konu, nesneler ve <xref:System.Windows.Media.Geometry> <xref:System.Windows.Shapes.Shape> öğeler arasındaki farkları da zıt.  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>Geometri Nedir?  
 Sınıf <xref:System.Windows.Media.Geometry> ve ondan türeyen sınıflar, <xref:System.Windows.Media.EllipseGeometry>yani <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.CombinedGeometry>, ve , 2-B şeklin geometrisini tanımlamanızı sağlar. Bu geometrik tanımlamaların, ekrana boyamak için bir şekil tanımlama veya isabet testi ve klip bölgelerini tanımlama gibi birçok kullanımı vardır. Animasyon yolunu tanımlamak için geometri bile kullanabilirsiniz.  
  
 <xref:System.Windows.Media.Geometry>dikdörtgenler ve daireler veya iki veya daha fazla geometri nesnesinden oluşturulan bileşik gibi nesneler basit olabilir.  Yayları <xref:System.Windows.Media.PathGeometry> ve eğrileri tanımlamanızı <xref:System.Windows.Media.StreamGeometry> sağlayan ve sınıflar kullanılarak daha karmaşık geometriler oluşturulabilir.  
  
 A <xref:System.Windows.Media.Geometry> türü <xref:System.Windows.Freezable>olduğundan, <xref:System.Windows.Media.Geometry> nesneler çeşitli özel özellikler sağlar: bunlar [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak bildirilebilir, birden çok nesne arasında paylaşılabilir, performansı artırmak için salt okunur, klonlanabilir ve iş parçacığı güvenli hale getirilebilir. Nesneler tarafından <xref:System.Windows.Freezable> sağlanan farklı özellikler hakkında daha fazla bilgi için [Freezable Objects Overview](../advanced/freezable-objects-overview.md)'a bakın.  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>Geometriler ve Şekiller  
 <xref:System.Windows.Media.Geometry> Ve <xref:System.Windows.Shapes.Shape> sınıflar her ikisi de 2-B şekilleri <xref:System.Windows.Media.EllipseGeometry> (karşılaştırmak ve <xref:System.Windows.Shapes.Ellipse> örneğin) tanımlamak açısından benzer görünüyor, ancak önemli farklılıklar vardır.  
  
 İlk olarak, <xref:System.Windows.Media.Geometry> <xref:System.Windows.Freezable> <xref:System.Windows.Shapes.Shape> sınıf sınıftan devralırken, sınıf <xref:System.Windows.FrameworkElement>sınıftan devralır. Bunlar öğe oldukları <xref:System.Windows.Shapes.Shape> ndan, nesneler kendilerini işleyebilir ve <xref:System.Windows.Media.Geometry> düzen sistemine katılabilir, nesneler ise yapamaz.  
  
 Nesneler <xref:System.Windows.Shapes.Shape> nesnelerden <xref:System.Windows.Media.Geometry> daha kolay kullanılabilir olmasına rağmen, <xref:System.Windows.Media.Geometry> nesneler daha çok yönlüdür. Bir <xref:System.Windows.Shapes.Shape> nesne 2-B grafikleri işlemek <xref:System.Windows.Media.Geometry> için kullanılırken, bir nesne 2-B grafikler için geometrik bölgeyi tanımlamak, kırpma için bir bölge tanımlamak veya örneğin isabet testi için bir bölge tanımlamak için kullanılabilir.  
  
### <a name="the-path-shape"></a>Yol Şekli  
 Bir, <xref:System.Windows.Shapes.Shape> <xref:System.Windows.Shapes.Path> sınıf, aslında <xref:System.Windows.Media.Geometry> içeriğini açıklamak için a kullanır. A <xref:System.Windows.Media.Geometry> <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Media.Geometry>ile özelliğini ayarlayarak ve onun ve özelliklerini ayarlayarak, bir . <xref:System.Windows.Shapes.Path.Data%2A> <xref:System.Windows.Shapes.Path>  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>Geometri Alan Ortak Özellikler  
 Önceki bölümlerde Geometri nesnelerinin çizim şekilleri, animating ve kırpma gibi çeşitli amaçlarla diğer nesnelerle birlikte kullanılabileceğini belirtmiştir. Aşağıdaki tabloda, nesne <xref:System.Windows.Media.Geometry> alan özellikleri olan birkaç sınıf listelenilmiştir.  
  
|Tür|Özellik|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>Basit Geometri Türleri  
 Tüm geometriler için taban sınıf <xref:System.Windows.Media.Geometry>soyut sınıftır.  <xref:System.Windows.Media.Geometry> Sınıftan türeyen sınıflar kabaca üç kategoriye ayırılabilir: basit geometriler, yol geometrileri ve bileşik geometriler.  
  
 Basit geometri <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>sınıfları, <xref:System.Windows.Media.EllipseGeometry> çizgiler, dikdörtgenler ve daireler gibi temel geometrik şekiller oluşturmak için kullanılır ve içerir.  
  
- A, <xref:System.Windows.Media.LineGeometry> satırın başlangıç noktası ve bitiş noktası belirtilerek tanımlanır.  
  
- A, <xref:System.Windows.Media.RectangleGeometry> göreceli <xref:System.Windows.Rect> konumunu, yükseklik ve genişliğini belirten bir yapı ile tanımlanır. Ve <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> özelliklerini ayarlayarak yuvarlatılmış bir dikdörtgen oluşturabilirsiniz.  
  
- An <xref:System.Windows.Media.EllipseGeometry> bir merkez noktası, bir x yarıçapı ve y yarıçapı ile tanımlanır.  Aşağıdaki örnekler, işleme ve kırpma için basit geometrilerin nasıl oluşturulacak olduğunu gösterir.  
  
 Bu aynı şekiller, daha karmaşık şekiller, <xref:System.Windows.Media.PathGeometry> bir veya geometri nesneleri birleştirerek oluşturulabilir, ancak bu sınıflar bu temel geometrik şekilleri üretmek için daha basit bir araç sağlar.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.LineGeometry>.  Daha önce belirtildiği <xref:System.Windows.Media.Geometry> gibi, bir nesne kendini çizemez, <xref:System.Windows.Shapes.Path> bu nedenle örnek satırı işlemek için bir şekil kullanır.  Bir çizginin alanı olmadığından, <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini <xref:System.Windows.Shapes.Path> ayarı hiçbir etkiye sahip olmaz; bunun yerine, <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> yalnızca ve özellikleri belirtilir. Aşağıdaki resimde örnekteki çıktı gösterilmektedir.  
  
 ![A LineGeometri](./media/graphicsmm-line.gif "graphicsmm_line")  
(10,20) ile (100.130) arasında çizilen bir Çizgi Geometrisi  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Sonraki örnek, bir <xref:System.Windows.Media.EllipseGeometry>'nin nasıl oluşturulup oluşturulup oluşturulabildiğini gösterir.  Örnekler, x <xref:System.Windows.Media.EllipseGeometry.Center%2A> yarıçapı ve y-yarıçapı 100 çapında bir daire `50`oluşturur, ayarlanır noktasına <xref:System.Windows.Media.EllipseGeometry> `50,50` ayarlanır ayarlar.  Elipsin iç kısmı, bu durumda <xref:System.Windows.Media.Brushes.Gold%2A>Yol öğesinin Dolgu özelliğine bir değer atayarak boyanır. Aşağıdaki resimde örnekteki çıktı gösterilmektedir.  
  
 ![Bir ElipsGeometri](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Bir ElipsGeometri (50,50) çizilmiş  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.RectangleGeometry>.  Dikdörtgenin konumu ve boyutları bir <xref:System.Windows.Rect> yapı ile tanımlanır. Konum `50,50` ve yükseklik ve genişlik `25`her ikisi de , bir kare oluşturur. Aşağıdaki resimde örnekteki çıktı gösterilmektedir.  
  
 ![DikdörtgenGeometri](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
50,50'de çizilen bir DikdörtgenGeometri  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Aşağıdaki örnek, bir görüntü <xref:System.Windows.Media.EllipseGeometry> için küçük bölge olarak nasıl kullanılacağını gösterir.  Bir <xref:System.Windows.Controls.Image> nesne 200 ve 150'lik bir <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> nesne ile tanımlanır.  Değeri <xref:System.Windows.Media.EllipseGeometry> 100, <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> değeri 75 ve değeri 100,75 olan bir <xref:System.Windows.Media.EllipseGeometry.Center%2A> değer, <xref:System.Windows.UIElement.Clip%2A> görüntünün özelliğine ayarlanır.  Yalnızca görüntünün elips alanı içinde olan bölümü görüntülenir. Aşağıdaki resimde örnekteki çıktı gösterilmektedir.  
  
 ![Kırpma lı ve kırpmasız bir görüntü](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Görüntü denetimini kesmek için kullanılan bir ElipsGeometri  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>Yol Geometrileri  
 Sınıf <xref:System.Windows.Media.PathGeometry> ve onun hafif <xref:System.Windows.Media.StreamGeometry> eşdeğeri olan sınıf, yaylar, eğriler ve çizgilerden oluşan birden çok karmaşık figürü tanımlamak için araçlar sağlar.  
  
 A'nın <xref:System.Windows.Media.PathGeometry> kalbinde, her <xref:System.Windows.Media.PathFigure> şekil ayrı bir şekli açıkladığı için bu yüzden <xref:System.Windows.Media.PathGeometry>adlandırılmış nesneler topluluğudur. Her <xref:System.Windows.Media.PathFigure> biri, her biri <xref:System.Windows.Media.PathSegment> figürün bir kesimini açıklayan bir veya daha fazla nesneden oluşur.  
  
 Birçok segment türü vardır.  
  
|Segment Türü|Açıklama|Örnek|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|İki nokta arasında eliptik bir yay oluşturur.|[Bir Eliptik Yay oluşturun.](how-to-create-an-elliptical-arc.md)|  
|<xref:System.Windows.Media.BezierSegment>|İki nokta arasında kübik Bezier eğrisi oluşturur.|[Kübik Bezier Eğrisi oluşturun.](how-to-create-a-cubic-bezier-curve.md)|  
|<xref:System.Windows.Media.LineSegment>|İki nokta arasında bir çizgi oluşturur.|[PathGeometry İçinde LineSegment Oluşturma](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Bir dizi kübik Bezier eğrisi oluşturur.|Yazı <xref:System.Windows.Media.PolyBezierSegment> sayfasına bakın.|  
|<xref:System.Windows.Media.PolyLineSegment>|Bir dizi satır oluşturur.|Yazı <xref:System.Windows.Media.PolyLineSegment> sayfasına bakın.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Bir dizi kuadratik Bezier eğrisi oluşturur.|Sayfaya <xref:System.Windows.Media.PolyQuadraticBezierSegment> bakın.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Bir kuadratik Bezier eğrisi oluşturur.|[Bir Quadratic Bezier Eğrisi oluşturun.](how-to-create-a-quadratic-bezier-curve.md)|  
  
 A <xref:System.Windows.Media.PathFigure> içindeki segmentler, her bir kesimin bitiş noktası bir sonraki parçanın başlangıç noktası olmak için tek bir geometrik şekle ayrılır. Bir <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> özelliği, ilk kesimin çizildiği noktayı belirtir. Sonraki her segment önceki bölümün bitiş noktasında başlar. Örneğin, dikey bir `10,50` çizgi `10,150` özelliği <xref:System.Windows.Media.PathFigure.StartPoint%2A> ayarlayarak `10,50` ve <xref:System.Windows.Media.LineSegment> bir <xref:System.Windows.Media.LineSegment.Point%2A> özellik ayarı ile `10,150`bir tanımlanabilir.  
  
 Aşağıdaki <xref:System.Windows.Media.PathGeometry> örnek, a <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.LineSegment> ile tek bir oluşan basit bir <xref:System.Windows.Shapes.Path> oluşturur ve bir öğe kullanarak görüntüler. Nesnenin <xref:System.Windows.Media.PathFigure> ki <xref:System.Windows.Media.PathFigure.StartPoint%2A> ayarlanır `10,20` ve <xref:System.Windows.Media.LineSegment> a bir bitiş noktası `100,130`ile tanımlanır. Aşağıdaki resimde bu <xref:System.Windows.Media.PathGeometry> örnek tarafından oluşturulan gösterir.  
  
 ![A LineGeometri](./media/graphicsmm-line.gif "graphicsmm_line")  
Tek bir LineSegment içeren bir PathGeometri  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Bu örnekte bir <xref:System.Windows.Media.LineGeometry> önceki örnekle zıtlık tasnisi yapmakta değer.  Bir <xref:System.Windows.Media.PathGeometry> için kullanılan sözdizimi basit <xref:System.Windows.Media.LineGeometry>bir için kullanılan çok daha ayrıntılı , ve <xref:System.Windows.Media.LineGeometry> bu durumda sınıf kullanmak için daha mantıklı <xref:System.Windows.Media.PathGeometry> olabilir, ancak verbose sözdizimi son derece karmaşık ve karmaşık geometrik bölgelere izin verir.  
  
 <xref:System.Windows.Media.PathSegment> Nesnelerin bir birleşimi kullanılarak daha karmaşık geometriler oluşturulabilir.  
  
 Sonraki örnek, <xref:System.Windows.Media.BezierSegment>şekil <xref:System.Windows.Media.LineSegment>oluşturmak için <xref:System.Windows.Media.ArcSegment> bir , a ve bir kullanır. Örnek ilk kübik Bezier eğrisi oluşturur dört nokta tanımlayarak: bir başlangıç noktası, önceki segmentin bitiş<xref:System.Windows.Media.BezierSegment.Point3%2A>noktası, bir<xref:System.Windows.Media.BezierSegment.Point1%2A> bitiş <xref:System.Windows.Media.BezierSegment.Point2%2A>noktası ( ), ve iki kontrol noktası ( ve ).  Bir kübik Bezier eğrisinin iki kontrol noktası mıknatıs gibi, aksi takdirde kendilerine doğru düz bir çizgi olacak kısımları çeken, bir eğri üreten. İlk kontrol noktası, <xref:System.Windows.Media.BezierSegment.Point1%2A>eğrinin başlangıç kısmını etkiler; ikinci kontrol noktası, <xref:System.Windows.Media.BezierSegment.Point2%2A>eğrinin bitiş kısmını etkiler.  
  
 Örnek daha sonra, kendisinden öncekinin <xref:System.Windows.Media.LineSegment> <xref:System.Windows.Media.BezierSegment> bitiş noktası arasına, <xref:System.Windows.Media.LineSegment> özelliğitarafından belirtilen noktaya çizilen bir , ekler.  
  
 Örnek daha sonra, önceki <xref:System.Windows.Media.ArcSegment> <xref:System.Windows.Media.LineSegment> nin bitiş noktasından <xref:System.Windows.Media.ArcSegment.Point%2A> özelliği tarafından belirtilen noktaya çizilen bir , ekler. Örnek te arkın x- ve y-yarıçapı<xref:System.Windows.Media.ArcSegment.Size%2A>(), bir<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>dönüş açısı (), elde edilen arkaçısının ne<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>kadar büyük olması gerektiğini belirten bir bayrak<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>( ), ve yayhangi yönde çizildiğini gösteren bir değer ( ). Aşağıdaki resimde bu örnek tarafından oluşturulan şekil gösterilmektedir.  
  
 ![Bir Yol Geometrisi](./media/graphicsmm-path2.gif "graphicsmm_path2")  
Bir Yol Geometrisi  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Daha da karmaşık geometriler içinde <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.PathGeometry>birden çok nesne kullanılarak oluşturulabilir.  
  
 Aşağıdaki örnek, her <xref:System.Windows.Media.PathGeometry> biri <xref:System.Windows.Media.PathFigure> birden çok <xref:System.Windows.Media.PathSegment> nesne içeren iki nesneiçeren bir nesne oluşturur.  Yukarıdaki <xref:System.Windows.Media.PathFigure> örnekten a <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.PolyLineSegment> ve a <xref:System.Windows.Media.QuadraticBezierSegment> ile kullanılır.  A <xref:System.Windows.Media.PolyLineSegment> bir dizi nokta ile <xref:System.Windows.Media.QuadraticBezierSegment> tanımlanır ve bir denetim noktası ve bir bitiş noktası ile tanımlanır. Aşağıdaki resimde bu örnek tarafından oluşturulan şekil gösterilmektedir.  
  
 ![Bir Yol Geometrisi](./media/graphicsmm-path.gif "graphicsmm_path")  
Birden çok rakamlı bir YolGeometrisi  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 <xref:System.Windows.Media.PathGeometry> Sınıf gibi, <xref:System.Windows.Media.StreamGeometry> bir eğriler, yaylar ve çizgiler içeren karmaşık bir geometrik şekil tanımlar. Bir <xref:System.Windows.Media.PathGeometry>, bir <xref:System.Windows.Media.StreamGeometry> içeriğiveri bağlama, animasyon veya değişiklik desteklemez aksine. Karmaşık <xref:System.Windows.Media.StreamGeometry> bir geometriyi açıklamanız gerektiğinde ancak destekleyici veri bağlama, animasyon veya değişiklik ek yükü istemediğiniz zaman a kullanın. Verimliliği nedeniyle, <xref:System.Windows.Media.StreamGeometry> sınıf süsleyiciler tanımlamak için iyi bir seçimdir.  
  
 Örneğin, [bkz.](how-to-create-a-shape-using-a-streamgeometry.md)  
  
### <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi  
 Ve <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> türleri, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] özel bir taşıma ve çekme komutları serisini kullanarak bir öznitelik sözdizimini destekler. Daha fazla bilgi için Bkz. [Yol Biçimlendirme Sözdizimi.](path-markup-syntax.md)  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>Kompozit Geometriler  
 Bileşik geometri nesneleri , a <xref:System.Windows.Media.GeometryGroup> <xref:System.Windows.Media.CombinedGeometry>, veya statik <xref:System.Windows.Media.Geometry> yöntem <xref:System.Windows.Media.Geometry.Combine%2A>çağırarak oluşturulabilir.  
  
- Nesne <xref:System.Windows.Media.CombinedGeometry> ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntem, iki geometri tarafından tanımlanan alanı birleştirmek için bir Boolean işlemi gerçekleştirir. <xref:System.Windows.Media.Geometry>alanı olmayan nesneler atılır. Yalnızca <xref:System.Windows.Media.Geometry> iki nesne birleştirilebilir (ancak bu iki geometri de bileşik geometriler olabilir).  
  
- Sınıf, <xref:System.Windows.Media.GeometryGroup> kendi alanını birleştirmeden içerdiği <xref:System.Windows.Media.Geometry> nesnelerin bir birleşimini oluşturur. Herhangi bir <xref:System.Windows.Media.Geometry> sayıda nesne bir <xref:System.Windows.Media.GeometryGroup>. Örneğin, bkz. [Bileşik Şekil Oluştur.](how-to-create-a-composite-shape.md)  
  
 Birleştirme işlemi gerçekleştiremedikleri için, <xref:System.Windows.Media.GeometryGroup> nesneleri kullanmak nesneleri veya <xref:System.Windows.Media.CombinedGeometry> yöntemi kullanmanın <xref:System.Windows.Media.Geometry.Combine%2A> üzerinde performans avantajları sağlar.  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>Kombine Geometriler  
 Önceki bölümde <xref:System.Windows.Media.CombinedGeometry> nesne ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntem içerdikleri geometriler tarafından tanımlanan alanı birleştirin bahsedilen. Numaralandırma, <xref:System.Windows.Media.GeometryCombineMode> geometrilerin nasıl birleştirilebildiğini belirtir. <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> Özellik için olası değerler <xref:System.Windows.Media.GeometryCombineMode.Union>şunlardır: , <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, ve <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.CombinedGeometry> a Birliği birleştirme modu ile tanımlanır.  Her <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ikisi <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> de ve aynı yarıçap daireler olarak tanımlanır, ancak merkezleri 50 ile ofset ile.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Birliğin birleştirme modunun sonuçları](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.CombinedGeometry> bir birleştirme modu ile <xref:System.Windows.Media.GeometryCombineMode.Xor>tanımlanır.  Her <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ikisi <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> de ve aynı yarıçap daireler olarak tanımlanır, ancak merkezleri 50 ile ofset ile.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor birleştirme modunun sonuçları](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Ek örnekler için bkz: [Bileşik Şekil Oluştur](how-to-create-a-composite-shape.md) ve Birleşik Geometri [Oluştur.](how-to-create-a-combined-geometry.md)  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable Özellikler  
 Sınıftan <xref:System.Windows.Media.Geometry> devraldığı için, sınıf çeşitli özel <xref:System.Windows.Media.Geometry> özellikler sağlar: nesneler [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak bildirilebilir, birden çok nesne arasında paylaşılabilir, performansı artırmak için salt okunur hale getirilebilir, klonlanabilir ve iş parçacığı güvenli hale getirilebilir. <xref:System.Windows.Freezable> Nesneler tarafından <xref:System.Windows.Freezable> sağlanan farklı özellikler hakkında daha fazla bilgi için [Freezable Objects Overview](../advanced/freezable-objects-overview.md)'a bakın.  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>Diğer Geometri Özellikleri  
 Sınıf, <xref:System.Windows.Media.Geometry> aşağıdakiler gibi yararlı yardımcı program yöntemleri de sağlar:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- Alanı <xref:System.Windows.Media.Geometry>alır.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- Geometrinin başka bir <xref:System.Windows.Media.Geometry>tane bulunup bulunmayacağını belirler.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- Bir <xref:System.Windows.Media.Geometry> konturun belirli bir nokta yıkıp içermediğini belirler.  
  
 Yöntemlerinin <xref:System.Windows.Media.Geometry> tam bir listesi için sınıfa bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Yol Biçimlendirme Sözdizimi](path-markup-syntax.md)
- [Nasıl Dır Konular](geometries-how-to-topics.md)
- [Animasyona Genel bakış](animation-overview.md)
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
