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
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141334"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
Bu konu, nesnelerle <xref:System.Windows.Shapes.Shape> nasıl çizilir eylene genel bir bakış sağlar. A, <xref:System.Windows.Shapes.Shape> ekrana <xref:System.Windows.UIElement> şekil çizmenizi sağlayan bir türdür. Bunlar UI öğeleri <xref:System.Windows.Shapes.Shape> olduğundan, nesneler öğelerin ve çoğu denetimin içinde <xref:System.Windows.Controls.Panel> kullanılabilir.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]grafik ve render hizmetlerine çeşitli katmanlar sunar. Üst katmanda, <xref:System.Windows.Shapes.Shape> nesnelerin kullanımı kolaydır ve düzen ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] etkinlik sistemine katılım gibi birçok yararlı özellik sağlar.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Nesneleri Şekillendir  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıma hazır <xref:System.Windows.Shapes.Shape> nesneler sağlar.  Tüm şekil nesneleri <xref:System.Windows.Shapes.Shape> sınıftan devralır. Kullanılabilir şekil nesneleri <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle>, , ve . <xref:System.Windows.Shapes.Shape>nesneler aşağıdaki ortak özellikleri paylaşır.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin anahattının nasıl boyandığını açıklar.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin anahattının kalınlığını açıklar.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Şeklin iç kısmı nasıl boyanır.  
  
- Aygıtlardan bağımsız piksellerde ölçülen koordinatları ve verticleri belirtmek için veri özellikleri.  
  
 Çünkü onlar türetilmiştir <xref:System.Windows.UIElement>, şekil nesneleri paneller ve en denetimleri içinde kullanılabilir. Panel, <xref:System.Windows.Controls.Canvas> alt nesnelerinin mutlak konumlandırılmasını desteklediği için karmaşık çizimler oluşturmak için özellikle iyi bir seçimdir.  
  
 Sınıf, <xref:System.Windows.Shapes.Line> iki nokta arasında bir çizgi çizmenizi sağlar. Aşağıdaki örnek, satır koordinatlarını ve kontur özelliklerini belirtmenin çeşitli yollarını gösterir.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Aşağıdaki resimde işlenen <xref:System.Windows.Shapes.Line>gösterir.  
  
 ![Çizgi çizimi](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 <xref:System.Windows.Shapes.Line> Sınıf bir <xref:System.Windows.Shapes.Shape.Fill%2A> özellik sağlasa da, bir <xref:System.Windows.Shapes.Line> alan olmadığından bunun bir etkisi yoktur.  
  
 Başka bir ortak <xref:System.Windows.Shapes.Ellipse>şeklidir .  Şeklin <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri tanımlayarak bir oluşturun. Bir daire çizmek için, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> kimin <xref:System.Windows.Shapes.Ellipse> ve değerlerin eşit olduğunu belirtin.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Aşağıdaki resimde işlenmiş bir örnek <xref:System.Windows.Shapes.Ellipse>gösterilmektedir.  
  
 ![Elips illüstrasyon](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Yolları ve Geometrileri Kullanma  
 Sınıf, <xref:System.Windows.Shapes.Path> eğriler ve karmaşık şekiller çizmenizi sağlar. Bu eğriler ve şekiller nesneler kullanılarak <xref:System.Windows.Media.Geometry> tanımlanır. Bir , <xref:System.Windows.Shapes.Path>bir kullanmak <xref:System.Windows.Media.Geometry> için bir oluşturmak <xref:System.Windows.Shapes.Path> ve <xref:System.Windows.Shapes.Path.Data%2A> nesnenin özelliğini ayarlamak için kullanabilirsiniz.  
  
 Aralarından <xref:System.Windows.Media.Geometry> seçim yapabileceğiniz çeşitli nesneler vardır. , <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>ve <xref:System.Windows.Media.EllipseGeometry> sınıflar nispeten basit şekilleri açıklar. Daha karmaşık şekiller oluşturmak veya eğriler oluşturmak için bir <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometri ve PathSegments  
 <xref:System.Windows.Media.PathGeometry>nesneler bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneden oluşur; her <xref:System.Windows.Media.PathFigure> biri farklı bir "şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure> biri, her biri <xref:System.Windows.Media.PathSegment> şekil veya şeklin bağlı bir bölümünü temsil eden bir veya daha fazla nesneden oluşur. Segment türleri <xref:System.Windows.Media.LineSegment>şunlardır: <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.ArcSegment>, ve .  
  
 Aşağıdaki örnekte, <xref:System.Windows.Shapes.Path> bir kuadratik Bezier eğrisi çizmek için kullanılır.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Aşağıdaki resim, işlenen şekli gösterir.  
  
 ![Yol çizimi](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Ve diğer <xref:System.Windows.Media.Geometry> <xref:System.Windows.Media.PathGeometry> sınıflar hakkında daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın.  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>XAML Kısaltılmış Sözdizimi  
 'de, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir <xref:System.Windows.Shapes.Path>. Aşağıdaki örnekte, karmaşık bir şekil çizmek için kısaltılmış sözdizimi kullanılır.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Aşağıdaki resimde işlenmiş bir <xref:System.Windows.Shapes.Path>görüntü gösterilmektedir.  
  
 ![Yol çizimi](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 Öznitelik <xref:System.Windows.Shapes.Path.Data%2A> dizesi, M ile gösterilen ve koordinat sistemindeki <xref:System.Windows.Controls.Canvas>yol için bir başlangıç noktası oluşturan "moveto" komutuyla başlar. <xref:System.Windows.Shapes.Path>veri parametreleri büyük/küçük harf duyarlıdır. Büyük M, yeni geçerli nokta için mutlak bir konum gösterir. Küçük bir m göreli koordinatları gösterir. İlk segment ,(100.200) başlayıp (400.175) ile biten ve iki kontrol noktası (100,25) ve (400.350) kullanılarak çizilen kübik Bezier eğrisidir. Bu kesim öznitelik dizesinde <xref:System.Windows.Shapes.Path.Data%2A> C komutu ile gösterilir. Yine, büyük C mutlak bir yol gösterir; küçük c göreli bir yolu gösterir.  
  
 İkinci bölüm, önceki alt adadan (400.175) yeni bir bitiş noktasına (280.175) çekilen bir çizgi belirten mutlak yatay "lineto" komutuyla başlar. Yatay bir "lineto" komutu olduğundan, belirtilen değer *x*-koordinattır.  
  
 Tam yol sözdizimi için <xref:System.Windows.Shapes.Path.Data%2A> başvuruyu görün ve [Yol Geometrisi kullanarak şekil oluşturun.](how-to-create-a-shape-by-using-a-pathgeometry.md)  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Şekilleri Boyama  
 <xref:System.Windows.Media.Brush>nesneler bir şeklin <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>. Aşağıdaki örnekte, kontur ve <xref:System.Windows.Shapes.Ellipse> dolgu belirtilir. Fırça özellikleri için geçerli girişin bir anahtar kelime veya hexadecimal renk değeri olabileceğini unutmayın. Kullanılabilir renk anahtar kelimeleri hakkında daha <xref:System.Windows.Media.Colors> fazla bilgi <xref:System.Windows.Media> için ad alanındaki sınıfın özelliklerine bakın.  
  
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
  
 Aşağıdaki resimde işlenen <xref:System.Windows.Shapes.Ellipse>gösterir.  
  
 ![Elips](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatif olarak, şekli düz bir renkle boyamak için açıkça bir <xref:System.Windows.Media.SolidColorBrush> nesne oluşturmak için özellik öğesi sözdizimini kullanabilirsiniz.  
  
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
  
 Aşağıdaki resimde işlenen şekli gösterilmektedir.  
  
 ![SolidColorBrush illüstrasyon](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Ayrıca bir şeklin konturunu boyayabilir veya degradeler, resimler, desenler ve daha fazlası ile doldurabilirsiniz. Daha fazla bilgi [için, Düz Renkler ve Degradeler Genel Bakış ile Resim](painting-with-solid-colors-and-gradients-overview.md)bakın.  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Gerilebilir Şekiller  
 , <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> ve sınıflar <xref:System.Windows.Shapes.Shape.Stretch%2A> tüm bir özelliği vardır. Bu özellik, nesnenin düzen alanını doldurmak için nesnenin <xref:System.Windows.Shapes.Shape> içeriğinin <xref:System.Windows.Shapes.Shape> (çizilecek şeklin) nasıl genişletildiğini belirler. Bir <xref:System.Windows.Shapes.Shape> nesnenin düzen alanı, açık <xref:System.Windows.Shapes.Shape> <xref:System.Windows.FrameworkElement.Width%2A> ve ayar veya onun <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarları nedeniyle, düzen sistemi tarafından ayrılan alan miktarıdır. Windows Sunu Temeli'ndeki düzen [Layout](../advanced/layout.md) hakkında daha fazla bilgi için Düzen'e genel bakış'a bakın.  
  
 Stretch özelliği aşağıdaki değerlerden birini alır:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Nesnenin içeriği uzatılmış değildir.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Nesnenin içeriği, düzen alanını doldurmak için uzatılır.  En boy oranı korunmaz.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Nesnenin içeriği, orijinal en boy oranını korurken yerleşim alanını doldurmak için mümkün olduğunca uzatılır.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Nesnenin içeriği, orijinal en boy oranını korurken düzen alanını tamamen doldurmak için uzatılır.  
  
 Bir <xref:System.Windows.Shapes.Shape> nesnenin içeriği gerildiğinde, nesnenin <xref:System.Windows.Shapes.Shape> anahattının germeden sonra boyandığını unutmayın.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Shapes.Polygon> a çok küçük bir üçgen çizmek için kullanılır (0,0) için (0,1) için (1,1). Nesnenin <xref:System.Windows.Shapes.Polygon> ve <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> 100 olarak ayarlanır ve streç özelliği Doldurmak için ayarlanır. Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içeriği (üçgen) büyük alanı doldurmak için gerilir.  
  
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
## <a name="transforming-shapes"></a>Şekilleri Dönüştürme  
 Sınıf, <xref:System.Windows.Media.Transform> şekilleri iki boyutlu bir düzlemde dönüştürmek için araçlar sağlar.  Farklı dönüşüm türleri döndürme<xref:System.Windows.Media.RotateTransform>( ),<xref:System.Windows.Media.ScaleTransform>ölçek (<xref:System.Windows.Media.SkewTransform>), eğriltme ( ), ve çeviri ( ) içerir.<xref:System.Windows.Media.TranslateTransform>  
  
 Bir şekle uygulanacak yaygın bir dönüşüm bir dönüşdür.  Bir şekli döndürmek için, <xref:System.Windows.Media.RotateTransform> bir <xref:System.Windows.Media.RotateTransform.Angle%2A>oluşturmak ve onun . 45'lik bir <xref:System.Windows.Media.RotateTransform.Angle%2A> elementi saat yönünde 45 derece döndürür; 90'lık bir açı eleman 90 derece saat yönünde döner; ve saire. Öğenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> döndürüldettiği noktayı denetlemek istiyorsanız, özellikleri ve özelliklerini ayarlayın. Bu özellik değerleri dönüştürülen öğenin koordinat alanında ifade edilir. <xref:System.Windows.Media.RotateTransform.CenterX%2A>ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> varsayılan değerleri sıfırdır. Son olarak, <xref:System.Windows.Media.RotateTransform> öğeyi uygulayın. Dönüşümün düzeni etkilemesini istemiyorsanız, şeklin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini ayarlayın.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.RotateTransform> bir şekli şekli sol üst köşe (0,0) hakkında 45 derece döndürmek için kullanılır.  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu sefer nokta (25,50) etrafında döndürülür.  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Aşağıdaki resimde iki dönüşümü uygulamanın sonuçları gösterilmektedir.  
  
 ![Farklı merkez noktaları ile 45 derece rotasyonlar](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Önceki örneklerde, her şekil nesnesine tek bir dönüştürme uygulanmıştır. Bir şekle (veya başka bir UI öğesine) <xref:System.Windows.Media.TransformGroup>birden çok dönüştürme uygulamak için bir .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Animasyona Genel bakış](animation-overview.md)
