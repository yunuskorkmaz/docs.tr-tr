---
title: Şekiller ve temel çizime genel bakış
description: Kullanım dışı şekiller ve Windows Presentation Foundation (WPF) içinde çeşitli işleme hizmetleri katmanları sayesinde kullanıcı arabiriminizi geliştirin.
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
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853693"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
Bu konu, nesneleri nasıl çizeceğiniz hakkında genel bakış sunar <xref:System.Windows.Shapes.Shape> . , <xref:System.Windows.Shapes.Shape> <xref:System.Windows.UIElement> Ekrana bir şekil çizmenizi sağlayan bir türüdür. UI öğeleri olduklarından, <xref:System.Windows.Shapes.Shape> nesneler <xref:System.Windows.Controls.Panel> öğeler ve çoğu denetim içinde kullanılabilir.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]grafik ve işleme hizmetlerine birçok farklı erişim katmanı sunar. Üst katmanda, <xref:System.Windows.Shapes.Shape> nesnelerin kullanımı kolaydır ve olay sistemine düzen ve katılım gibi birçok yararlı özellik sağlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .  

<a name="shapes"></a>
## <a name="shape-objects"></a>Şekil nesneleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir dizi kullanıma kullanım için çok sayıda nesne sağlar <xref:System.Windows.Shapes.Shape> .  Tüm şekil nesneleri <xref:System.Windows.Shapes.Shape> sınıfından devralınır. Kullanılabilir şekil nesneleri,,,, <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line> ve içerir <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> <xref:System.Windows.Shapes.Rectangle> . <xref:System.Windows.Shapes.Shape>nesneler aşağıdaki ortak özellikleri paylaşır.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin anahattının nasıl boyanacağını açıklar.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin anahattının kalınlığını açıklar.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Şeklin iç kısmının nasıl boyanacağını açıklar.  
  
- Cihazdan bağımsız piksellerde ölçülen koordinatları ve köşeleri belirtmek için veri özellikleri.  
  
 Öğesinden türetildiklerinden <xref:System.Windows.UIElement> , şekil nesneleri panolar ve çoğu denetim içinde kullanılabilir. <xref:System.Windows.Controls.Canvas>Panel, alt nesnelerinin mutlak konumunu desteklediğinden karmaşık çizimler oluşturmak için özellikle iyi bir seçimdir.  
  
 <xref:System.Windows.Shapes.Line>Sınıfı iki noktaya çizgi çizmenizi sağlar. Aşağıdaki örnek, çizgi koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Line> .  
  
 ![Çizgi çizimi](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 <xref:System.Windows.Shapes.Line>Sınıfı bir özellik sağlamasına rağmen <xref:System.Windows.Shapes.Shape.Fill%2A> , bir alanı olmadığından, bu özelliğin etkisi yoktur <xref:System.Windows.Shapes.Line> .  
  
 Diğer bir yaygın şekil <xref:System.Windows.Shapes.Ellipse> .  <xref:System.Windows.Shapes.Ellipse>Şeklin <xref:System.Windows.FrameworkElement.Width%2A> ve özelliklerini tanımlayarak oluşturun <xref:System.Windows.FrameworkElement.Height%2A> . Bir daire çizmek için, <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerlerini eşit olan bir değer belirtin.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Aşağıdaki görüntüde, işlenmiş bir örnek gösterilmektedir <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Elips çizimi](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Yolları ve geometrileri kullanma  
 <xref:System.Windows.Shapes.Path>Sınıfı eğrileri ve karmaşık şekilleri çizmenizi sağlar. Bu eğriler ve şekiller nesneler kullanılarak açıklanmıştır <xref:System.Windows.Media.Geometry> . Bir kullanmak için <xref:System.Windows.Shapes.Path> , oluşturup <xref:System.Windows.Media.Geometry> nesnenin özelliğini ayarlamak için bunu kullanırsınız <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Path.Data%2A> .  
  
 <xref:System.Windows.Media.Geometry>Aralarından seçim yapabileceğiniz çeşitli nesneler vardır. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry> Ve <xref:System.Windows.Media.EllipseGeometry> sınıfları görece basit şekilleri anlatmaktadır. Daha karmaşık şekiller oluşturmak veya Eğriler oluşturmak için bir kullanın <xref:System.Windows.Media.PathGeometry> .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry ve PathSegments  
 <xref:System.Windows.Media.PathGeometry>nesneler bir veya daha fazla nesneden oluşur <xref:System.Windows.Media.PathFigure> ; her biri <xref:System.Windows.Media.PathFigure> farklı bir "şekil" veya şekli temsil eder. Her biri <xref:System.Windows.Media.PathFigure> bir veya daha fazla nesneden oluşur <xref:System.Windows.Media.PathSegment> ve her biri şekil veya şeklin bağlı bir bölümünü temsil eder. Segment türleri şunları içerir: <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> , ve <xref:System.Windows.Media.ArcSegment> .  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisi çizmek için kullanılır.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Aşağıdaki görüntüde işlenmiş şekil gösterilmektedir.  
  
 ![Yol çizimi](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Ve diğer sınıflar hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.Geometry> bkz. [geometriye genel bakış](geometry-overview.md).  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>XAML kısaltılmış sözdizimi  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]' De, bir betimleyen özel bir kısaltılmış sözdizimi de kullanabilirsiniz <xref:System.Windows.Shapes.Path> . Aşağıdaki örnekte, karmaşık bir şekil çizmek için kısaltılmış sözdizimi kullanılır.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Path> .  
  
 ![Yol çizimi](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>Öznitelik dizesi, ' nin koordinat sistemindeki yol için bir başlangıç noktası kuran M ile gösterilen "MoveTo" komutuyla başlar <xref:System.Windows.Controls.Canvas> . <xref:System.Windows.Shapes.Path>veri parametreleri büyük/küçük harfe duyarlıdır. Büyük harf, yeni geçerli nokta için mutlak bir konum gösterir. Küçük harf m, göreli koordinatları gösterir. İlk kesim, (100.200) ve bitiş saati (400.175) ile başlayan üçüncü dereceden Bezier eğrisdir ve iki denetim noktası (100, 25) ve (400.350) kullanılarak çizilir. Bu segment, öznitelik dizesindeki C komutuyla belirtilir <xref:System.Windows.Shapes.Path.Data%2A> . Yine, büyük harf C mutlak bir yolu belirtir; küçük harfli c, göreli bir yol gösterir.  
  
 İkinci kesim, önceki alt yolun uç noktasından (400.175) yeni bir uç noktaya (280.175) çizilmiş bir çizgi belirten mutlak yatay "lineto" komutu H ile başlar. Yatay bir "lineto" komutu olduğundan, belirtilen değer bir *x*koordinatı.  
  
 Tüm yol sözdizimi için bkz <xref:System.Windows.Shapes.Path.Data%2A> . [bir PathGeometry kullanarak başvuru ve şekil oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Şekilleri boyama  
 <xref:System.Windows.Media.Brush>nesneler, bir şeklin ve ' ın boyamak için kullanılır <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.Fill%2A> . Aşağıdaki örnekte, öğesinin konturu ve dolgusu <xref:System.Windows.Shapes.Ellipse> belirtilmiştir. Fırça özelliklerinin geçerli girişinin bir anahtar sözcük veya onaltılık renk değeri olabileceğini unutmayın. Kullanılabilir renk anahtar sözcükleri hakkında daha fazla bilgi için bkz <xref:System.Windows.Media.Colors> . ad alanındaki sınıfının özellikleri <xref:System.Windows.Media> .  
  
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
  
 Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Elips](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatif olarak, <xref:System.Windows.Media.SolidColorBrush> şekli düz bir renkle boyamak için açıkça bir nesne oluşturmak üzere özellik öğesi sözdizimini kullanabilirsiniz.  
  
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
 <xref:System.Windows.Shapes.Line>,, <xref:System.Windows.Shapes.Path> , <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> Ve <xref:System.Windows.Shapes.Rectangle> sınıflarının hepsi bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliğine sahiptir. Bu özellik bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğinin (çizilecek şekil) nesnenin düzen alanını doldurmak için nasıl uzatılacağını belirler <xref:System.Windows.Shapes.Shape> . <xref:System.Windows.Shapes.Shape>Nesnenin düzen alanı, <xref:System.Windows.Shapes.Shape> bir açık <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayar ya da kendi ayarları nedeniyle, Düzen sistemi tarafından ayrılan alan miktarıdır <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> . Windows Presentation Foundation düzen hakkında daha fazla bilgi için bkz. [düzene](../advanced/layout.md) genel bakış.  
  
 Esnetme özelliği aşağıdaki değerlerden birini alır:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Nesnenin içerikleri genişletilmedi.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Nesnenin içerikleri, düzen alanını dolduracak şekilde uzatılır.  En boy oranı korunmaz.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Nesnenin içerikleri, orijinal en boy oranını korurken düzen alanını doldurmak için mümkün olduğunca uzatılır.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Nesnenin içerikleri, özgün en boy oranını korurken düzen alanını tamamen doldurmak üzere uzatılır.  
  
 Bir <xref:System.Windows.Shapes.Shape> nesnenin içerikleri uzatıldığında <xref:System.Windows.Shapes.Shape> nesnenin ana hattının uzatmadan sonra boyanmış olduğunu unutmayın.  
  
 Aşağıdaki örnekte, (0, 0) ile ( <xref:System.Windows.Shapes.Polygon> 1, 1) arasında çok küçük bir üçgen çizmek için kullanılır. <xref:System.Windows.Shapes.Polygon>Nesne <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100 olarak ayarlanır ve Esnetme özelliği Fill olarak ayarlanır. Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içerikleri (üçgeni) daha büyük alanı dolduracak şekilde uzatılır.  
  
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
 <xref:System.Windows.Media.Transform>Sınıfı, şekilleri iki boyutlu bir düzlemde dönüştürmek için yollar sağlar.  Farklı dönüştürme türleri arasında döndürme ( <xref:System.Windows.Media.RotateTransform> ), ölçek ( <xref:System.Windows.Media.ScaleTransform> ), eğriltme ( <xref:System.Windows.Media.SkewTransform> ) ve çeviri ( <xref:System.Windows.Media.TranslateTransform> ) bulunur.  
  
 Bir şekle uygulanacak ortak bir dönüşüm bir dönüşdir.  Bir şekli döndürmek için, oluşturun <xref:System.Windows.Media.RotateTransform> ve değerini belirtin <xref:System.Windows.Media.RotateTransform.Angle%2A> . Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 45, öğe 45 derece saat yönünde döner; bir 90 açı, öğe 90 derece saat yönünde döner ve bu şekilde devam eder. <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> Öğesinin döndürüldüğü noktayı denetlemek isterseniz ve özelliklerini ayarlayın. Bu özellik değerleri, dönüştürülmekte olan öğenin koordinat alanında ifade edilir. <xref:System.Windows.Media.RotateTransform.CenterX%2A>ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> varsayılan değerleri sıfır olmalıdır. Son olarak, <xref:System.Windows.Media.RotateTransform> öğesini öğesine uygulayın. Dönüşümün düzeni etkilemesini istemiyorsanız şeklin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini ayarlayın.  
  
 Aşağıdaki örnekte, şeklin <xref:System.Windows.Media.RotateTransform> sol üst köşesinden (0, 0) bir şekil 45 derece döndürmek için kullanılır.  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu zaman nokta (25, 50) ile döndürülür.  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Aşağıdaki çizimde, iki dönüştürme uygulamanın sonuçları gösterilmektedir.  
  
 ![farklı orta noktaları olan 45 derece döndürme](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Önceki örneklerde, her şekil nesnesine tek bir dönüşüm uygulandı. Bir şekle (veya başka bir kullanıcı arabirimi öğesine) birden çok dönüşüm uygulamak için bir kullanın <xref:System.Windows.Media.TransformGroup> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Animasyona Genel bakış](animation-overview.md)
