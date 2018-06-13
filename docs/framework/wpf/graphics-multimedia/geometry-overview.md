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
ms.openlocfilehash: 01c460ae18c489a21c860c6d2b10f551e6e68242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558078"
---
# <a name="geometry-overview"></a>Geometriye Genel Bakış
Bu genel bakışta nasıl kullanılacağını açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> şekiller açıklamak için sınıflar. Bu konu ayrıca arasındaki farkları karşılaştırır <xref:System.Windows.Media.Geometry> nesneleri ve <xref:System.Windows.Shapes.Shape> öğeleri.  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Geometri nedir?  
 <xref:System.Windows.Media.Geometry> Sınıfı ve bu sınıftan gibi türetilen sınıflar <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, ve <xref:System.Windows.Media.CombinedGeometry>, bir 2B şekli geometri açıklamak etkinleştir. Bu geometrik açıklamalar birçok kullanır, bu tür ekranı boyamak için bir şekil tanımlama veya isabet sınaması ve kırpma bölgeleri tanımlama sahip. Geometri bile animasyon yolunu tanımlamak için de kullanabilirsiniz.  
  
 <xref:System.Windows.Media.Geometry> dikdörtgenler ve daireler veya bileşik, iki veya daha fazla geometri nesnesinden oluşturulmuş gibi basit nesneler de olabilir.  Daha karmaşık geometri kullanarak oluşturulabilir <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> yaylar ve eğrileri açıklamanızı etkinleştirmek sınıfları.  
  
 Çünkü bir <xref:System.Windows.Media.Geometry> bir tür <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> nesneleri birkaç özel özellik sağlar: olarak bildirilebilir [kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)kopyalanması, performansı iyileştirmek için salt okunur yapılan birden fazla nesne arasında paylaşılan ve iş parçacığı açısından güvenli hale. Tarafından sağlanan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometri vs. Şekiller  
 <xref:System.Windows.Media.Geometry> Ve <xref:System.Windows.Shapes.Shape> sınıfları, her ikisi de 2B şekiller açıklamaktadır benzerdir (karşılaştırmak <xref:System.Windows.Media.EllipseGeometry> ve <xref:System.Windows.Shapes.Ellipse> gibi), ancak önemli farklılıklar vardır.  
  
 Birisi, <xref:System.Windows.Media.Geometry> sınıfının devraldığı <xref:System.Windows.Freezable> sırasında sınıfı <xref:System.Windows.Shapes.Shape> sınıfının devraldığı <xref:System.Windows.FrameworkElement>. Öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri kendilerini ve Düzen sistemine katılır sırada <xref:System.Windows.Media.Geometry> nesneler olamaz.  
  
 Ancak <xref:System.Windows.Shapes.Shape> nesneleri daha kullanılabilir <xref:System.Windows.Media.Geometry> nesneleri <xref:System.Windows.Media.Geometry> nesneleri çok yönlüdür. Sırada bir <xref:System.Windows.Shapes.Shape> nesne 2B grafik oluşturmak için kullanılan bir <xref:System.Windows.Media.Geometry> nesnesi, 2B grafik geometrik bölgesi tanımlamak, kırpma için bölge tanımlamak veya isabet test etmek için bir bölge örneğin tanımlamak için kullanılabilir.  
  
### <a name="the-path-shape"></a>Yol şekli  
 Bir <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> sınıfı, aslında kullanan bir <xref:System.Windows.Media.Geometry> içeriğini tanımlamak için. Ayarlayarak <xref:System.Windows.Shapes.Path.Data%2A> özelliği <xref:System.Windows.Shapes.Path> ile bir <xref:System.Windows.Media.Geometry> ve ayarı kendi <xref:System.Windows.Shapes.Shape.Fill%2A> ve <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliklerini işleyebilirsiniz bir <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Geometri ele ortak özellikleri  
 Önceki bölümlerde söz edilen geometri nesneleri diğer nesnelerle çeşitli şekiller çizme, animasyon ve kırpma gibi amaçlar için kullanılabilir. Aşağıdaki tabloda alan özellikleri olan birkaç sınıfı listeler bir <xref:System.Windows.Media.Geometry> nesnesi.  
  
|Tür|Özellik|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Basit geometri türleri  
 Soyut sınıf tüm geometri için temel sınıfı olan <xref:System.Windows.Media.Geometry>.  Türetilen sınıflar <xref:System.Windows.Media.Geometry> sınıfı üç kategoride kabaca da gruplandırılabilir: basit geometri, yol geometri ve bileşik geometri.  
  
 Basit geometri sınıfları dahil <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, ve <xref:System.Windows.Media.EllipseGeometry> ve çizgiler, dikdörtgenler ve daireler gibi temel geometrik şekiller oluşturmak için kullanılır.  
  
-   A <xref:System.Windows.Media.LineGeometry> başlangıç noktası satır ve uç noktası belirterek tanımlanır.  
  
-   A <xref:System.Windows.Media.RectangleGeometry> ile tanımlanmış bir <xref:System.Windows.Rect> göreli konumunu ve yüksekliğini ve genişliğini belirten yapısı. Ayarlayarak yuvarlak dikdörtgen oluşturabilirsiniz <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> özellikleri.  
  
-   Bir <xref:System.Windows.Media.EllipseGeometry> merkez nokta, bir x-radius ve y yarıçapı tarafından tanımlanır.  Aşağıdaki örnekler kırpma ve işleme için basit geometri oluşturulacağını gösterir.  
  
 Bu aynı şekiller yanı, daha karmaşık şekiller kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya geometrisi nesneleri birlikte, ancak bu sınıfların birleştirerek bu temel geometrik şekilleri üretmek için basit bir yol sağlar.  
  
 Aşağıdaki örnek oluşturma ve işleme gösterir bir <xref:System.Windows.Media.LineGeometry>.  Daha önce belirtildiği gibi bir <xref:System.Windows.Media.Geometry> nesnesi, örnek kullanan kendisini çizmek oluşturamıyor bir <xref:System.Windows.Shapes.Path> çizgiyi işlemek için şekli.  Bir satır alanı olmadığı için ayarı <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği <xref:System.Windows.Shapes.Path> hiçbir etkisi yoktur; bunun yerine, yalnızca <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri belirtilir. Aşağıdaki çizimde örnek çıktısını gösterir.  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
(10,20)'den (100,130) çizilen bir LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Sonraki örnek oluşturma ve işleme gösterir bir <xref:System.Windows.Media.EllipseGeometry>.  Örnekler kümeleri <xref:System.Windows.Media.EllipseGeometry.Center%2A> , <xref:System.Windows.Media.EllipseGeometry> noktasına ayarlamak `50,50` ve RADIUS x ve y RADIUS her ikisi de ayarlanır `50`, 100'ün bir çapının bir daire oluşturur.  Elips iç değeri bu durumda yol öğesinin Dolgu özelliğine atayarak boyanır <xref:System.Windows.Media.Brushes.Gold%2A>. Aşağıdaki çizimde örnek çıktısını gösterir.  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
(50,50) Çizilmiş EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Aşağıdaki örnek oluşturma ve işleme gösterir bir <xref:System.Windows.Media.RectangleGeometry>.  Konumu ve boyutları dikdörtgenin tarafından tanımlanan bir <xref:System.Windows.Rect> yapısı. Konumu `50,50` ve yüksekliğini ve genişliğini her ikisi de `25`, kare oluşturur. Aşağıdaki çizimde örnek çıktısını gösterir.  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
50,50 Çizilen RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.EllipseGeometry> görüntü kırpma bölgesinin olarak.  Bir <xref:System.Windows.Controls.Image> nesnesi ile tanımlanan bir <xref:System.Windows.FrameworkElement.Width%2A> 200 ve <xref:System.Windows.FrameworkElement.Height%2A> 150.  Bir <xref:System.Windows.Media.EllipseGeometry> ile bir <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 100 değeri, bir <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 75 değeri ve bir <xref:System.Windows.Media.EllipseGeometry.Center%2A> 100,75 değeri ayarlanmış <xref:System.Windows.UIElement.Clip%2A> görüntünün özelliği.  Yalnızca elipsin alanı içerisindeki resmin parçası görüntülenir. Aşağıdaki çizimde örnek çıktısını gösterir.  
  
 ![Bir görüntü ile ve kırpma olmadan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Küçük resim denetimi için kullanılan EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Yol geometri  
 <xref:System.Windows.Media.PathGeometry> Sınıfı ve hafif eşdeğeri <xref:System.Windows.Media.StreamGeometry> sınıfı, birden çok karmaşık şekilleri açıklamak için yaylar, eğriler ve satırlardan sağlar.  
  
 Merkezinde bir <xref:System.Windows.Media.PathGeometry> koleksiyonudur <xref:System.Windows.Media.PathFigure> merkezinde her şekil açıkladığı için nesnelerinin <xref:System.Windows.Media.PathGeometry>. Her <xref:System.Windows.Media.PathFigure> kendisini bir veya daha fazla oluşmaktadır <xref:System.Windows.Media.PathSegment> nesneleri, şekil bir parçasını her biri açıklanmaktadır.  
  
 Birçok türde segment vardır.  
  
|Segment türü|Açıklama|Örnek|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|İki nokta arasında elips bir yay oluşturur.|[Elips yay oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Bir küp Bezier eğrisini iki nokta arasındaki oluşturur.|[Küp Bezier eğrisi oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|İki nokta arasında bir çizgi oluşturur.|[PathGeometry İçinde LineSegment Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Küp Bezier eğrileri bir dizi oluşturur.|Bkz: <xref:System.Windows.Media.PolyBezierSegment> türü sayfası.|  
|<xref:System.Windows.Media.PolyLineSegment>|Bir dizi satır oluşturur.|Bkz: <xref:System.Windows.Media.PolyLineSegment> türü sayfası.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|İkinci derece Bezier eğrileri bir dizi oluşturur.|Bkz: <xref:System.Windows.Media.PolyQuadraticBezierSegment> sayfası.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|İkinci dereceden Bezier eğrisi oluşturur.|[İkinci dereceden Bezier eğrisi oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmentte bir <xref:System.Windows.Media.PathFigure> tek bir geometrik şekle segmentin başlangıç noktası olarak sonraki her segmentin bitiş noktası ile birleştirilir. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Özelliği bir <xref:System.Windows.Media.PathFigure> içinden ilk kesim çizilmez noktasını belirtir. Sonraki her segment önceki kesime uç noktada başlatır. Örneğin, dikey satırından `10,50` için `10,150` ayarlayarak tanımlanabilir <xref:System.Windows.Media.PathFigure.StartPoint%2A> özelliğine `10,50` ve oluşturma bir <xref:System.Windows.Media.LineSegment> ile bir <xref:System.Windows.Media.LineSegment.Point%2A> özellik ayarı `10,150`.  
  
 Aşağıdaki örnek, basit bir oluşturur <xref:System.Windows.Media.PathGeometry> bir tek oluşan <xref:System.Windows.Media.PathFigure> ile bir <xref:System.Windows.Media.LineSegment> ve kullanarak görüntüler bir <xref:System.Windows.Shapes.Path> öğesi. <xref:System.Windows.Media.PathFigure> Nesnenin <xref:System.Windows.Media.PathFigure.StartPoint%2A> ayarlanır `10,20` ve <xref:System.Windows.Media.LineSegment> bir bitiş noktası ile tanımlanan `100,130`. Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.PathGeometry> Bu örnek tarafından oluşturuldu.  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Tek bir LineSegment İçeren PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Bu örnek önceki ile çakışan değer olan <xref:System.Windows.Media.LineGeometry> örnek.  İçin kullanılan sözdizimi bir <xref:System.Windows.Media.PathGeometry> için basit bir kullanılan daha çok daha ayrıntılıdır <xref:System.Windows.Media.LineGeometry>, ve bunu kullanmak için daha anlamlı olabilir <xref:System.Windows.Media.LineGeometry> bu durumda, ayrıntılı sözdizimi sınıf <xref:System.Windows.Media.PathGeometry> için oldukça karmaşık ve karmaşık sağlar Geometrik bölgeleri.  
  
 Bir birleşimini kullanarak daha karmaşık geometri oluşturulabilir <xref:System.Windows.Media.PathSegment> nesneleri.  
  
 Sonraki örnek kullanan bir <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>ve bir <xref:System.Windows.Media.ArcSegment> şekil oluşturmak için. Örnek ilk eğri dört noktası tanımlayarak küp Bezier oluşturur: bir uç noktası önceki kesiminin uç noktası bir başlangıç noktası (<xref:System.Windows.Media.BezierSegment.Point3%2A>), ve iki denetim noktası (<xref:System.Windows.Media.BezierSegment.Point1%2A> ve <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Küp Bezier eğrisini iki denetim noktalarının ne eğri üreterek bir çizgide doğrultusunda, aksi durumda olacak, bölümleri etkileyen mıknatıs gibi davranır. İlk denetim noktası <xref:System.Windows.Media.BezierSegment.Point1%2A>, başına etkiler eğri bölümünü; ikinci bir denetim noktası <xref:System.Windows.Media.BezierSegment.Point2%2A>, eğri bitiş bölümünü etkiler.  
  
 Örnek daha sonra bir <xref:System.Windows.Media.LineSegment>, bitiş noktası arasında çizilmiş <xref:System.Windows.Media.BezierSegment> öncesi tarafından belirtilen noktası kendi <xref:System.Windows.Media.LineSegment> özelliği.  
  
 Örnek daha sonra bir <xref:System.Windows.Media.ArcSegment>, uç noktası bir önceki çizilmiş <xref:System.Windows.Media.LineSegment> tarafından belirtilen noktasına kendi <xref:System.Windows.Media.ArcSegment.Point%2A> özelliği. Bu örnek ayrıca yayın x ve y-yarıçapını belirtir (<xref:System.Windows.Media.ArcSegment.Size%2A>), döndürme açısını (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), sonuçta elde edilen Yayın açısı ne kadar büyük olmalıdır belirten bir bayrak (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) ve hangi yönde Yayı çizilir belirten bir değer (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Bu örnek tarafından oluşturulmuş şekli aşağıda gösterilmektedir.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Birden çok kullanarak daha karmaşık geometri oluşturulabilir <xref:System.Windows.Media.PathFigure> içindeki nesneleri bir <xref:System.Windows.Media.PathGeometry>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.PathGeometry> iki <xref:System.Windows.Media.PathFigure> nesneleri, her biri içeren birden çok <xref:System.Windows.Media.PathSegment> nesneleri.  <xref:System.Windows.Media.PathFigure> Yukarıdaki örnekteki ve <xref:System.Windows.Media.PathFigure> ile bir <xref:System.Windows.Media.PolyLineSegment> ve <xref:System.Windows.Media.QuadraticBezierSegment> kullanılır.  A <xref:System.Windows.Media.PolyLineSegment> noktalar dizisi ile tanımlanır ve <xref:System.Windows.Media.QuadraticBezierSegment> bir denetim noktası ve bir uç noktası ile tanımlanır. Bu örnek tarafından oluşturulmuş şekli aşağıda gösterilmektedir.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
Birden çok şekil ile PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Gibi <xref:System.Windows.Media.PathGeometry> sınıfı, bir <xref:System.Windows.Media.StreamGeometry> Eğriler, yaylar ve satırları içeren karmaşık bir geometrik şekli tanımlar. Farklı bir <xref:System.Windows.Media.PathGeometry>, içeriğini bir <xref:System.Windows.Media.StreamGeometry> veri bağlama, animasyon veya değişimi desteklemez. Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde ancak veri bağlama, animasyon veya değişimi destekleme ek yükünü istemiyorsanız. Verimlilik nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıftır donarıcıları açıklamak için iyi bir seçimdir.  
  
 Bir örnek için bkz: [kullanarak bir şekli bir StreamGeometry oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi  
 <xref:System.Windows.Media.PathGeometry> Ve <xref:System.Windows.Media.StreamGeometry> türleri destek bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] öznitelik taşıma özel bir dizi kullanarak sözdizimi ve komutları çizin. Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Bileşik geometri  
 Bileşik geometri nesneleri kullanılarak oluşturulabilir bir <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>, ya da statik çağırarak <xref:System.Windows.Media.Geometry> yöntemi <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   <xref:System.Windows.Media.CombinedGeometry> Nesne ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi iki geometri tarafından tanımlanan alanı birleştirmek için Boolean işlemi gerçekleştirir. <xref:System.Windows.Media.Geometry> Hiçbir alana sahip olmayan nesneler atılır. Yalnızca iki <xref:System.Windows.Media.Geometry> (Bu iki geometri de bileşik geometri olabilir ancak) nesneleri birleştirilebilir.  
  
-   <xref:System.Windows.Media.GeometryGroup> Sınıfı oluşturur bir birleştirmeden <xref:System.Windows.Media.Geometry> içeren kendi alanları birleştirme olmadan nesneleri. Herhangi bir sayıda <xref:System.Windows.Media.Geometry> nesneleri eklenebilir bir <xref:System.Windows.Media.GeometryGroup>. Bir örnek için bkz: [bileşik bir şekil oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md).  
  
 Bir birleştirme işlemi gerçekleştirmediği için kullanarak <xref:System.Windows.Media.GeometryGroup> nesneler kullanmaya göre performans avantajı sağlar <xref:System.Windows.Media.CombinedGeometry> nesneleri veya <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Birleşik Geometri  
 Önceki bölümde <xref:System.Windows.Media.CombinedGeometry> nesne ve <xref:System.Windows.Media.Geometry.Combine%2A> yöntemi içerdikleri geometri tarafından tanımlanan alanı birleştirin. <xref:System.Windows.Media.GeometryCombineMode> Numaralandırmasını belirtir geometri nasıl birleştirilir. Olası değerler için <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> özelliği: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, ve <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> birleşim birleştirme modu ile tanımlanır.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Birleştirme modu UNION sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Birleştirme modu Xor sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Ek örnekler için bkz: [bileşik bir şekil oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md) ve [birleştirilmiş geometri oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable Özellikleri  
 Sınıfından devraldığı için <xref:System.Windows.Freezable> sınıfı, <xref:System.Windows.Media.Geometry> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Geometry> nesneleri olarak bildirilebilir [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)artırmak için salt okunur yapılan birden fazla nesne arasında paylaşılan performans, kopyalanabilen ve iş parçacığı yapılan. Tarafından sağlanan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Diğer geometri özellikleri  
 <xref:System.Windows.Media.Geometry> Sınıfı aşağıdaki gibi yararlı yardımcı program yöntemleri sağlar:  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -Alanını alır <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> -Geometri başka içerip içermediğini belirler <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> -Belirler olup olmadığını, vuruşun bir <xref:System.Windows.Media.Geometry> belirli bir noktaya içerir.  
  
 Bkz: <xref:System.Windows.Media.Geometry> sınıfı yöntemlerinin tam listesi için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Geometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Yol İşaretleme Söz Dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
