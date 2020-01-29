---
title: Şekiller ve temel çizime genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: dfdbf67d35cbb13e80d0c5184f165b0cc660e2ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731627"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
Bu konu, <xref:System.Windows.Shapes.Shape> nesneleriyle nasıl çizileceğini gösteren bir genel bakış sunar. <xref:System.Windows.Shapes.Shape>, ekrana şekil çizmenizi sağlayan bir <xref:System.Windows.UIElement> türüdür. UI öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri <xref:System.Windows.Controls.Panel> öğeleri ve çoğu denetim içinde kullanılabilir.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], grafik ve işleme hizmetlerine birkaç farklı erişim katmanı sunar. Üst katmanda <xref:System.Windows.Shapes.Shape> nesnelerinin kullanımı kolaydır ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemine düzen ve katılım gibi birçok yararlı özellik sağlar.  

<a name="shapes"></a>   
## <a name="shape-objects"></a>Şekil nesneleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kullanıma yönelik birkaç <xref:System.Windows.Shapes.Shape> nesne sağlar.  Tüm şekil nesneleri <xref:System.Windows.Shapes.Shape> sınıfından devralınır. Kullanılabilir şekil nesneleri <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>ve <xref:System.Windows.Shapes.Rectangle>içerir. <xref:System.Windows.Shapes.Shape> nesneler aşağıdaki ortak özellikleri paylaşır.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin anahattının nasıl boyanacağını açıklar.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin anahattının kalınlığını açıklar.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: şeklin iç kısmının nasıl boyanacağını açıklar.  
  
- Cihazdan bağımsız piksellerde ölçülen koordinatları ve köşeleri belirtmek için veri özellikleri.  
  
 <xref:System.Windows.UIElement>türettikleri için, şekil nesneleri panellerin ve çoğu denetimin içinde kullanılabilir. <xref:System.Windows.Controls.Canvas> panel, alt nesnelerinin mutlak konumunu desteklediğinden karmaşık çizimler oluşturmak için özellikle iyi bir seçimdir.  
  
 <xref:System.Windows.Shapes.Line> sınıfı iki noktaya çizgi çizmenizi sağlar. Aşağıdaki örnek, çizgi koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Aşağıdaki görüntüde işlenen <xref:System.Windows.Shapes.Line>gösterilmektedir.  
  
 ![Çizgi çizimi](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 <xref:System.Windows.Shapes.Line> sınıfı bir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği sağlamasına karşın, bir <xref:System.Windows.Shapes.Line> alanı olmadığından, bu ayarın hiçbir etkisi olmaz.  
  
 Diğer bir yaygın şekil <xref:System.Windows.Shapes.Ellipse>.  Şeklin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini tanımlayarak <xref:System.Windows.Shapes.Ellipse> oluşturun. Bir daire çizmek için <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri eşit olan bir <xref:System.Windows.Shapes.Ellipse> belirtin.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Aşağıdaki görüntüde bir işlenen <xref:System.Windows.Shapes.Ellipse>örneği gösterilmektedir.  
  
 ![Elips çizimi](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Yolları ve geometrileri kullanma  
 <xref:System.Windows.Shapes.Path> sınıfı eğrileri ve karmaşık şekilleri çizmenizi sağlar. Bu eğriler ve şekiller <xref:System.Windows.Media.Geometry> nesneleri kullanılarak açıklanmıştır. Bir <xref:System.Windows.Shapes.Path>kullanmak için, bir <xref:System.Windows.Media.Geometry> oluşturup <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Path.Data%2A> özelliğini ayarlamak için bunu kullanırsınız.  
  
 Aralarından seçim yapabileceğiniz çeşitli <xref:System.Windows.Media.Geometry> nesneleri vardır. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>ve <xref:System.Windows.Media.EllipseGeometry> sınıfları görece basit şekilleri anlatmaktadır. Daha karmaşık şekiller oluşturmak veya Eğriler oluşturmak için <xref:System.Windows.Media.PathGeometry>kullanın.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry ve PathSegments  
 <xref:System.Windows.Media.PathGeometry> nesneler bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesnesinden oluşur; Her <xref:System.Windows.Media.PathFigure> farklı bir "şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure>, her biri şekil veya şeklin bağlı bir bölümünü temsil eden bir veya daha fazla <xref:System.Windows.Media.PathSegment> nesnesinden oluşur. Segment türleri şunları içerir: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>ve <xref:System.Windows.Media.ArcSegment>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisini çizmek için kullanılır.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Aşağıdaki görüntüde işlenmiş şekil gösterilmektedir.  
  
 ![Yol çizimi](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 <xref:System.Windows.Media.PathGeometry> ve diğer <xref:System.Windows.Media.Geometry> sınıfları hakkında daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>XAML kısaltılmış sözdizimi  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir <xref:System.Windows.Shapes.Path>anlatmak için özel kısaltılmış bir sözdizimi de kullanabilirsiniz. Aşağıdaki örnekte, karmaşık bir şekil çizmek için kısaltılmış sözdizimi kullanılır.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Aşağıdaki görüntüde işlenen bir <xref:System.Windows.Shapes.Path>gösterilmektedir.  
  
 ![Yol çizimi](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> öznitelik dizesi, <xref:System.Windows.Controls.Canvas>koordinat sistemindeki yol için bir başlangıç noktası kuran, M tarafından belirtilen "MoveTo" komutuyla başlar. <xref:System.Windows.Shapes.Path> veri parametreleri büyük/küçük harfe duyarlıdır. Büyük harf, yeni geçerli nokta için mutlak bir konum gösterir. Küçük harf m, göreli koordinatları gösterir. İlk kesim, (100.200) ve bitiş saati (400.175) ile başlayan üçüncü dereceden Bezier eğrisdir ve iki denetim noktası (100, 25) ve (400.350) kullanılarak çizilir. Bu segment <xref:System.Windows.Shapes.Path.Data%2A> öznitelik dizesinde C komutu tarafından belirtilir. Yine, büyük harf C mutlak bir yolu belirtir; küçük harfli c, göreli bir yol gösterir.  
  
 İkinci kesim, önceki alt yolun uç noktasından (400.175) yeni bir uç noktaya (280.175) çizilmiş bir çizgi belirten mutlak yatay "lineto" komutu H ile başlar. Yatay bir "lineto" komutu olduğundan, belirtilen değer bir *x*koordinatı.  
  
 Tüm yol sözdizimi için bkz. <xref:System.Windows.Shapes.Path.Data%2A> başvurusu ve [PathGeometry kullanarak şekil oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Şekilleri boyama  
 <xref:System.Windows.Media.Brush> nesneler, bir şeklin <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>boyamak için kullanılır. Aşağıdaki örnekte, <xref:System.Windows.Shapes.Ellipse> vuruş ve dolgusu belirtilmiştir. Fırça özelliklerinin geçerli girişinin bir anahtar sözcük veya onaltılık renk değeri olabileceğini unutmayın. Kullanılabilir renk anahtar sözcükleri hakkında daha fazla bilgi için, <xref:System.Windows.Media> ad alanındaki <xref:System.Windows.Media.Colors> sınıfının özelliklerine bakın.  
  
```xaml
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 Aşağıdaki görüntüde işlenen <xref:System.Windows.Shapes.Ellipse>gösterilmektedir.  
  
 ![Elips](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatif olarak, şekli düz bir renkle boyamak için açıkça bir <xref:System.Windows.Media.SolidColorBrush> nesnesi oluşturmak üzere özellik öğesi sözdizimini kullanabilirsiniz.  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 Aşağıdaki çizimde, işlenmiş şekil gösterilmektedir.  
  
 ![SolidColorBrush çizimi](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Ayrıca, bir şeklin konturunu veya degradelerini, resimleri, desenleri ve daha fazlasını boyayabilir. Daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Uzatılabilir şekiller  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>ve <xref:System.Windows.Shapes.Rectangle> sınıflarının hepsi bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliğine sahiptir. Bu özellik, bir <xref:System.Windows.Shapes.Shape> nesnesinin içeriğinin (çizilecek şekil) <xref:System.Windows.Shapes.Shape> nesnenin düzen alanını doldurmak için nasıl uzatılacağını belirler. <xref:System.Windows.Shapes.Shape> nesnenin düzen alanı, <xref:System.Windows.Shapes.Shape> bir <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayarı ya da <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarları nedeniyle, Düzen sistemi tarafından ayrılan alan miktarıdır. Windows Presentation Foundation düzen hakkında daha fazla bilgi için bkz. [düzene](../advanced/layout.md) genel bakış.  
  
 Esnetme özelliği aşağıdaki değerlerden birini alır:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> nesnenin içerikleri genişletilmedi.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> nesnenin içerikleri, düzen alanını doldurmak için uzatılır.  En boy oranı korunmaz.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> nesnenin içerikleri, özgün en boy oranını korurken düzen alanını doldurmak için mümkün olduğunca uzatılır.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> nesnenin içeriği, özgün en boy oranını korurken düzen alanını tamamen doldurmak için uzatılır.  
  
 <xref:System.Windows.Shapes.Shape> nesnenin içerikleri uzatıldığında, <xref:System.Windows.Shapes.Shape> nesnesinin anahattının uzatma sonrasında boyanmış olduğunu unutmayın.  
  
 Aşağıdaki örnekte, (0, 0) ile (0, 1) arasında (1, 1) çok küçük bir üçgen çizmek için bir <xref:System.Windows.Shapes.Polygon> kullanılır. <xref:System.Windows.Shapes.Polygon> nesnenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100 olarak ayarlanır ve Esnetme özelliği Fill olarak ayarlanır. Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içerikleri (üçgeni) daha büyük alanı dolduracak şekilde uzatılır.  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Şekilleri dönüştürme  
 <xref:System.Windows.Media.Transform> sınıfı, şekilleri iki boyutlu bir düzlemde dönüştürmek için yollar sağlar.  Farklı dönüştürme türleri arasında döndürme (<xref:System.Windows.Media.RotateTransform>), ölçek (<xref:System.Windows.Media.ScaleTransform>), eğriltme (<xref:System.Windows.Media.SkewTransform>) ve çeviri (<xref:System.Windows.Media.TranslateTransform>) bulunur.  
  
 Bir şekle uygulanacak ortak bir dönüşüm bir dönüşdir.  Bir şekli döndürmek için bir <xref:System.Windows.Media.RotateTransform> oluşturun ve <xref:System.Windows.Media.RotateTransform.Angle%2A>belirtin. 45 <xref:System.Windows.Media.RotateTransform.Angle%2A>, öğe 45 derece saat yönünde döner; 90 açısı öğe 90 derece saat yönünde döner; vb. Öğenin döndürüldüğü noktayı denetlemek istiyorsanız <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini ayarlayın. Bu özellik değerleri, dönüştürülmekte olan öğenin koordinat alanında ifade edilir. <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> varsayılan değerleri sıfır olmalıdır. Son olarak, <xref:System.Windows.Media.RotateTransform> öğesine uygulayın. Dönüşümün düzeni etkilemesini istemiyorsanız şeklin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini ayarlayın.  
  
 Aşağıdaki örnekte, şeklin sol üst köşesinden (0, 0) bir şekil 45 derece döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullanılır.  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu zaman nokta (25, 50) ile döndürülür.  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Aşağıdaki çizimde, iki dönüştürme uygulamanın sonuçları gösterilmektedir.  
  
 ![farklı orta noktaları olan 45 derece döndürme](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Önceki örneklerde, her şekil nesnesine tek bir dönüşüm uygulandı. Bir şekle (veya başka bir kullanıcı arabirimi öğesine) birden çok dönüşüm uygulamak için <xref:System.Windows.Media.TransformGroup>kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Animasyona Genel bakış](animation-overview.md)
