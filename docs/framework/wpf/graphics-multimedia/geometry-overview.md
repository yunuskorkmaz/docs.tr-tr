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
ms.openlocfilehash: 5545e89f744c3874840a773556e0670abc0a46a9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348063"
---
# <a name="geometry-overview"></a>Geometriye Genel Bakış
Bu genel bakışta nasıl kullanılacağını açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> şekiller açıklamak için sınıflar. Bu konuda ayrıca arasındaki farkları karşılaştırır <xref:System.Windows.Media.Geometry> nesneleri ve <xref:System.Windows.Shapes.Shape> öğeleri.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Geometri nedir?  
 <xref:System.Windows.Media.Geometry> Sınıfı ve gibi kendisinden türetilen sınıflar <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, ve <xref:System.Windows.Media.CombinedGeometry>, geometri 2B şeklin tanımlamak olanak tanır. Bu geometrik açıklamalar pek çok kullanımı, böyle bir şekil ekrana boyama tanımlama veya isabet testi ve kırpma bölgeleri tanımlama vardır. Hatta geometri animasyon yolunu tanımlamak için de kullanabilirsiniz.  
  
 <xref:System.Windows.Media.Geometry> dikdörtgenler ve daireler veya bileşik, iki veya daha fazla geometri nesneleri oluşturulan gibi basit nesneler de olabilir.  Daha karmaşık geometriler kullanarak oluşturulabilir <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> yay ve eğriler açıklamak sağlayan sınıflar.  
  
 Çünkü bir <xref:System.Windows.Media.Geometry> bir tür <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> nesneleri birkaç özel özellik sağlar: olarak bildirilebilir [kaynakları](../advanced/xaml-resources.md)kopyalanan, performansı artırmak için salt okunur yapılan birden fazla nesne arasında paylaşılan ve iş parçacığı açısından güvenli hale. Tarafından sağlanan farklı özellikleri hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometriler vs. Şekiller  
 <xref:System.Windows.Media.Geometry> Ve <xref:System.Windows.Shapes.Shape> sınıfları, her ikisi de 2B şekiller açıklamaktadır benzerdir (karşılaştırma <xref:System.Windows.Media.EllipseGeometry> ve <xref:System.Windows.Shapes.Ellipse> gibi), ancak önemli farklar vardır.  
  
 Biri, <xref:System.Windows.Media.Geometry> sınıfının devraldığı <xref:System.Windows.Freezable> sınıfı çalışırken <xref:System.Windows.Shapes.Shape> sınıfının devraldığı <xref:System.Windows.FrameworkElement>. Öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneler kendilerini ve Düzen sisteme katılan sırada <xref:System.Windows.Media.Geometry> nesneler olamaz.  
  
 Rağmen <xref:System.Windows.Shapes.Shape> nesneleri daha kullanılabilir <xref:System.Windows.Media.Geometry> nesneleri <xref:System.Windows.Media.Geometry> nesneleri çok yönlüdür. Sırasında bir <xref:System.Windows.Shapes.Shape> nesne 2B grafikler oluşturmak için kullanılan bir <xref:System.Windows.Media.Geometry> nesne, 2B grafikler için geometrik bölge tanımlamasına, kırpma için bir bölge tanımlamak veya bir bölge için isabet testi, örneğin tanımlamak için kullanılabilir.  
  
### <a name="the-path-shape"></a>Yol şekli  
 Bir <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> sınıfı, gerçekte kullandığı bir <xref:System.Windows.Media.Geometry> içeriğini tanımlamak için. Ayarlayarak <xref:System.Windows.Shapes.Path.Data%2A> özelliği <xref:System.Windows.Shapes.Path> ile bir <xref:System.Windows.Media.Geometry> ve ayarı kendi <xref:System.Windows.Shapes.Shape.Fill%2A> ve <xref:System.Windows.Shapes.Shape.Stroke%2A> özellikleri işleyebilirsiniz bir <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Geometriyi alan ortak özellikler  
 Geometri nesneleri diğer nesnelerle şekiller çizme, animasyon ve kırpma gibi amacıyla, çeşitli kullanılabilir önceki bölümlerde belirtilen. Alan özellikleri olan bazı sınıfları aşağıdaki tabloda bir <xref:System.Windows.Media.Geometry> nesne.  
  
|Tür|Özellik|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Basit geometri türleri  
 Tüm geometriler için temel sınıfı soyut sınıftır <xref:System.Windows.Media.Geometry>.  Öğesinden türetilen sınıfları <xref:System.Windows.Media.Geometry> sınıfı üç kategoriye kabaca da gruplandırılabilir: Birleşik Geometri basit geometriler ve yol geometrileri.  
  
 Basit geometri sınıfları <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, ve <xref:System.Windows.Media.EllipseGeometry> ve çizgiler ve dikdörtgenler daireler gibi temel geometrik şekiller oluşturmak için kullanılır.  
  
- A <xref:System.Windows.Media.LineGeometry> başlangıç noktası satır ve uç noktası belirterek tanımlanır.  
  
- A <xref:System.Windows.Media.RectangleGeometry> ile tanımlanmış bir <xref:System.Windows.Rect> yapısının göreli konumunu ve yüksekliğini ve genişliğini belirtir. Yuvarlatılmış Dikdörtgen ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> özellikleri.  
  
- Bir <xref:System.Windows.Media.EllipseGeometry> merkez noktası, bir x RADIUS ve y yarıçapı tarafından tanımlanır.  Aşağıdaki örnekler, kırpma ve işleme için basit geometri oluşturma işlemini gösterir.  
  
 Bu aynı şekiller, hem de daha karmaşık şekiller kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya geometri nesneleri birlikte, ancak bu sınıfların birleştirerek bu temel geometrik şekiller üretmek için basit bir yol sağlar.  
  
 Aşağıdaki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.LineGeometry>.  Daha önce belirtildiği gibi bir <xref:System.Windows.Media.Geometry> örnek kullanacak şekilde kendisinde çizmek nesne alamıyor bir <xref:System.Windows.Shapes.Path> çizgiyi işlemek için şekli.  Bir satır bir alanı olduğundan, ayar <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği <xref:System.Windows.Shapes.Path> hiçbir etkisi yoktur; bunun yerine, yalnızca <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri belirtilir. Örneğin çıktısında aşağıda gösterilmiştir.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry (10,20)'den alınan (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Sonraki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.EllipseGeometry>.  Örnek ayarlar <xref:System.Windows.Media.EllipseGeometry.Center%2A> , <xref:System.Windows.Media.EllipseGeometry> noktasına ayarlanır `50,50` ve yarıçap x ve y yarıçapı her ikisi de ayarlanmış olan `50`, 100 bir çapı bir daire oluşturur.  Elipsin iç değeri bu durumda yol öğenin dolgu özelliğine atayarak boyanacağını <xref:System.Windows.Media.Brushes.Gold%2A>. Örneğin çıktısında aşağıda gösterilmiştir.  
  
 ![Ellipsegeometry'ye](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Ellipsegeometry'ye çizilmiş (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Aşağıdaki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.RectangleGeometry>.  Konum ve boyut dikdörtgenin tarafından tanımlanan bir <xref:System.Windows.Rect> yapısı. Konumu `50,50` ve yüksekliğini ve genişliğini her ikisi de `25`, kare oluşturulur. Örneğin çıktısında aşağıda gösterilmiştir.  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry 50,50 çizilmiş  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.EllipseGeometry> görüntü kırpma bölgesini olarak.  Bir <xref:System.Windows.Controls.Image> nesne ile tanımlanan bir <xref:System.Windows.FrameworkElement.Width%2A> 200 ve <xref:System.Windows.FrameworkElement.Height%2A> 150.  Bir <xref:System.Windows.Media.EllipseGeometry> ile bir <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 100 değeri, bir <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 75, değeri ve <xref:System.Windows.Media.EllipseGeometry.Center%2A> 100,75 değeri ayarı <xref:System.Windows.UIElement.Clip%2A> görüntü özelliği.  Yalnızca bir elipsin alanı içinde görüntü bölümü görüntülenir. Örneğin çıktısında aşağıda gösterilmiştir.  
  
 ![Görüntü kırpma olmadan ve](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Küçük resim denetimi için kullanılan Ellipsegeometry'ye  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Yol geometrileri  
 <xref:System.Windows.Media.PathGeometry> Sınıfı ve basit eşdeğeri <xref:System.Windows.Media.StreamGeometry> sınıfı, birden çok karmaşık şekiller açıklamak için yay, eğriler ve satırlardan oluşan sağlayın.  
  
 Temelini bir <xref:System.Windows.Media.PathGeometry> koleksiyonudur <xref:System.Windows.Media.PathFigure> nesneleri, her şekil merkezinde açıkladığı için bu şekilde adlandırılmış <xref:System.Windows.Media.PathGeometry>. Her <xref:System.Windows.Media.PathFigure> kendisi bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> nesneleri, her biri bir parçası şekilde açıklar.  
  
 Parçaların birçok türü vardır.  
  
|Segment türü|Açıklama|Örnek|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Elips yay iki nokta arasındaki oluşturur.|[Elips yay oluşturma](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Üçüncü dereceden Bezier eğrisi iki nokta arasındaki oluşturur.|[Üçüncü dereceden Bezier eğrisi oluşturma](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|İki nokta arasındaki bir satır oluşturur.|[PathGeometry İçinde LineSegment Oluşturma](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Üçüncü derece Bezier eğrileri bir dizi oluşturur.|Bkz: <xref:System.Windows.Media.PolyBezierSegment> türü sayfası.|  
|<xref:System.Windows.Media.PolyLineSegment>|Satırları bir dizi oluşturur.|Bkz: <xref:System.Windows.Media.PolyLineSegment> türü sayfası.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|İkinci derece Bezier eğrileri bir dizi oluşturur.|Bkz: <xref:System.Windows.Media.PolyQuadraticBezierSegment> sayfası.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|İkinci dereceden Bezier eğrisi oluşturur.|[İkinci dereceden Bezier eğrisi oluşturma](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmentte bir <xref:System.Windows.Media.PathFigure> tek bir geometrik şekli sonraki kesimin başlangıç noktası olan her bir segmentin bitiş noktası ile birleştirilir. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Özelliği bir <xref:System.Windows.Media.PathFigure> içinden ilk segment çizilmez noktasını belirtir. Önceki kesime bitiş noktasında izleyen her bir kesim başlatır. Örneğin, bir dikey çizgi `10,50` için `10,150` ayarlayarak tanımlanabilir <xref:System.Windows.Media.PathFigure.StartPoint%2A> özelliğini `10,50` ve oluşturma bir <xref:System.Windows.Media.LineSegment> ile bir <xref:System.Windows.Media.LineSegment.Point%2A> özelliğini `10,150`.  
  
 Aşağıdaki örnek, basit bir oluşturur <xref:System.Windows.Media.PathGeometry> oluşan bir tek <xref:System.Windows.Media.PathFigure> ile bir <xref:System.Windows.Media.LineSegment> ve kullanarak görüntüler bir <xref:System.Windows.Shapes.Path> öğesi. <xref:System.Windows.Media.PathFigure> Nesnenin <xref:System.Windows.Media.PathFigure.StartPoint%2A> ayarlanır `10,20` ve <xref:System.Windows.Media.LineSegment> bir bitiş noktası ile tanımlanan `100,130`. Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.PathGeometry> Bu örnek tarafından oluşturuldu.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry tek LineSegment içerir  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Bu örnek, önceki ile çakışan değer olduğu <xref:System.Windows.Media.LineGeometry> örnek.  İçin kullanılan sözdizimi bir <xref:System.Windows.Media.PathGeometry> daha basit bir için kullanılan çok daha ayrıntılıdır <xref:System.Windows.Media.LineGeometry>, ve onu kullanmak için daha anlamlı olabilir <xref:System.Windows.Media.LineGeometry> ayrıntılı sözdizimi bu durumda, sınıf <xref:System.Windows.Media.PathGeometry> için son derece karmaşık ve karmaşık sağlar Geometrik bölgeleri.  
  
 Bir bileşimini kullanarak daha karmaşık geometriler oluşturulabilir <xref:System.Windows.Media.PathSegment> nesneleri.  
  
 Sonraki örnekte bir <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>ve bir <xref:System.Windows.Media.ArcSegment> şekli oluşturmak için. Örneğin bir üçüncü derece Bezier eğrisi olan dört noktası tanımlayarak ilk oluşturur: uç noktasına önceki segmentin son noktası olan bir başlangıç noktası (<xref:System.Windows.Media.BezierSegment.Point3%2A>), ve iki denetim noktası (<xref:System.Windows.Media.BezierSegment.Point1%2A> ve <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Üçüncü dereceden Bezier eğrisi iki denetim noktalarının ne eğri üreterek düz bir çizgi doğrultusunda, aksi halde olması, bölümleri etkileyen mıknatıs gibi davranır. İlk denetim noktası <xref:System.Windows.Media.BezierSegment.Point1%2A>, başına etkiler eğri bölümünü; ikinci bir denetim noktası <xref:System.Windows.Media.BezierSegment.Point2%2A>, bitiş eğri bölümünü etkiler.  
  
 Örnek sonra ekler bir <xref:System.Windows.Media.LineSegment>, uç noktası arasında bir önceki çizilmiş <xref:System.Windows.Media.BezierSegment> öncesi tarafından belirtilen noktası kendi <xref:System.Windows.Media.LineSegment> özelliği.  
  
 Örnek sonra ekler bir <xref:System.Windows.Media.ArcSegment>, önceki, uç noktasından alınan <xref:System.Windows.Media.LineSegment> tarafından belirtilen noktasına kendi <xref:System.Windows.Media.ArcSegment.Point%2A> özelliği. Bu örnek ayrıca yayın x ve y-yarıçapını belirtir (<xref:System.Windows.Media.ArcSegment.Size%2A>), döndürme açısı (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), sonuçta elde edilen Yayı açısı ne kadar büyük olmalıdır belirten bir bayrak (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) ve hangi yönde Yayı çizilir belirten bir değer (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Bu örnek tarafından oluşturulan şekli aşağıda gösterilmiştir.  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Birden çok kullanarak daha karmaşık geometriler oluşturulabilir <xref:System.Windows.Media.PathFigure> içindeki nesneleri bir <xref:System.Windows.Media.PathGeometry>.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Media.PathGeometry> iki <xref:System.Windows.Media.PathFigure> nesneleri, her biri içeren birden çok <xref:System.Windows.Media.PathSegment> nesneleri.  <xref:System.Windows.Media.PathFigure> Yukarıdaki örnekten ve <xref:System.Windows.Media.PathFigure> ile bir <xref:System.Windows.Media.PolyLineSegment> ve <xref:System.Windows.Media.QuadraticBezierSegment> kullanılır.  A <xref:System.Windows.Media.PolyLineSegment> noktalar dizisi ile tanımlanır ve <xref:System.Windows.Media.QuadraticBezierSegment> bir denetim noktası ve bir uç noktası ile tanımlanır. Bu örnek tarafından oluşturulan şekli aşağıda gösterilmiştir.  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry birden çok şekil ile  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Gibi <xref:System.Windows.Media.PathGeometry> sınıfı, bir <xref:System.Windows.Media.StreamGeometry> eğrileri yaylar ve satırları içeren karmaşık bir geometrik şekli tanımlar. Farklı bir <xref:System.Windows.Media.PathGeometry>, içeriğini bir <xref:System.Windows.Media.StreamGeometry> veri bağlama, animasyon veya değiştirilmesine desteklemez. Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde ancak destekleme veri bağlama, animasyon veya değişikliği yükü istemiyorsanız. Verimlilik nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıftır donatıcıları açıklamak için iyi bir seçimdir.  
  
 Bir örnek için bkz. [StreamGeometry kullanarak şekil oluşturma](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi  
 <xref:System.Windows.Media.PathGeometry> Ve <xref:System.Windows.Media.StreamGeometry> türleri desteği bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] öznitelik sözdizimi taşıma özel bir dizi kullanarak ve komutları çizin. Daha fazla bilgi için [yol işaretleme söz dizimi](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Birleşik Geometri  
 Birleşik Geometri nesneleri kullanarak oluşturulabilir bir <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>, ya da statik çağırarak <xref:System.Windows.Media.Geometry> yöntemi <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
- <xref:System.Windows.Media.CombinedGeometry> Nesne ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi iki geometriler ile tanımlanan alanı birleştirmek için bir Boole işlemi gerçekleştirir. <xref:System.Windows.Media.Geometry> alanı olan nesneleri atılır. Yalnızca iki <xref:System.Windows.Media.Geometry> nesneleri (Bu iki geometri ayrıca Birleşik Geometri olabilse) birleştirilebilir.  
  
- <xref:System.Windows.Media.GeometryGroup> Sınıfı oluşturur bir birleştirmeden <xref:System.Windows.Media.Geometry> birleştirmeden içerdiği nesneler. Herhangi bir sayıda <xref:System.Windows.Media.Geometry> nesneler eklenebilir bir <xref:System.Windows.Media.GeometryGroup>. Bir örnek için bkz. [bileşik şekil oluşturma](how-to-create-a-composite-shape.md).  
  
 Birleştirme işlemi gerçekleştirmeyin çünkü kullanarak <xref:System.Windows.Media.GeometryGroup> kullanmaya göre nesneler performans avantajı sağlar <xref:System.Windows.Media.CombinedGeometry> nesneleri veya <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Birleşik Geometri  
 Önceki bölümde <xref:System.Windows.Media.CombinedGeometry> nesne ve <xref:System.Windows.Media.Geometry.Combine%2A> içerdikleri geometriler ile tanımlanan alanı combine yöntemi. <xref:System.Windows.Media.GeometryCombineMode> Numaralandırma belirtir geometriler nasıl birleştirilir. Olası değerler için <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> özellik şunlardır: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, ve <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> birleşimin birleştirme modu ile tanımlanır.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Birleştirme modu UNION sonuçları](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor sonuçlarını birleştirmek modu](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Diğer örnekler için [bileşik şekil oluşturma](how-to-create-a-composite-shape.md) ve [bir Birleşik Geometri oluşturma](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable Özellikleri  
 Öğesinden devralındığından <xref:System.Windows.Freezable> sınıfı <xref:System.Windows.Media.Geometry> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Geometry> nesneleri olarak bildirilebilir [XAML kaynakları](../advanced/xaml-resources.md)geliştirmek için salt okunur yapılan birden fazla nesne arasında paylaşılan performans, kopyalanan ve iş parçacığı açısından güvenli hale. Tarafından sağlanan farklı özellikleri hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Diğer geometri özellikleri  
 <xref:System.Windows.Media.Geometry> Sınıfı aşağıdaki gibi kullanışlı yardımcı yöntemler sağlar:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A> -Alanını alır <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A> -Geometri başka içerip içermediğini belirler <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A> -Belirler olmadığını vuruşunun bir <xref:System.Windows.Media.Geometry> belirli bir noktaya içerir.  
  
 Bkz: <xref:System.Windows.Media.Geometry> yöntemlerinin tam listesi için sınıf.  
  
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
