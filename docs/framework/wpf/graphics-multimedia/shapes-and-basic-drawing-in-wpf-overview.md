---
title: WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
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
ms.openlocfilehash: 47df352c3b001f088f34ea057b34698efc4f4b53
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845808"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
Bu konu ile nasıl genel bir fikir veren <xref:System.Windows.Shapes.Shape> nesneleri. A <xref:System.Windows.Shapes.Shape> bir tür <xref:System.Windows.UIElement> ekrana bir şekil çizme olanak sağlar. Kullanıcı Arabirimi öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri içinde kullanılabilir <xref:System.Windows.Controls.Panel> öğeleri ve çoğu denetim.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] birkaç grafik ve işleme hizmetlerine erişim katmanı sunar. En üst katmanında <xref:System.Windows.Shapes.Shape> nesneleri düzen ve katılım gibi birçok yararlı özellik sağlar ve kullanmak kolay [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Şekil nesneleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çok sayıda kullanıma hazır sunar <xref:System.Windows.Shapes.Shape> nesneleri.  Tüm şekil nesneleri devralınacak <xref:System.Windows.Shapes.Shape> sınıfı. Kullanılabilir şekil nesneleri dahil etme <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, ve <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> nesneleri, aşağıdaki genel özellikleri paylaşır.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin ana hat nasıl boyanacağını açıklar.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin ana hat kalınlığı açıklar.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: Şeklin içinin nasıl boyanacağını açıklar.  
  
-   Koordinatları ve köşeleri belirtmek için veri özellikleri, CİHAZDAN bağımsız piksel cinsinden ölçülür.  
  
 Oldukları türetilmesi çünkü <xref:System.Windows.UIElement>, şekil nesneleri, paneller ve çoğu denetimleri içinde kullanılabilir. <xref:System.Windows.Controls.Canvas> Masasıdır karmaşık çizimleri oluşturmak için mutlak alt nesnelerinin konumlandırma desteklediğinden özellikle iyi bir seçimdir.  
  
 <xref:System.Windows.Shapes.Line> Sınıfı iki nokta arasında bir çizgi çizmek sağlar. Aşağıdaki örnek, satır koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Line>.  
  
 ![Çizim satırı](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Ancak <xref:System.Windows.Shapes.Line> sağlamasına bir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği, bu ayarın hiçbir etkisi nedeniyle bir <xref:System.Windows.Shapes.Line> alanı vardır.  
  
 Başka bir ortak şekli <xref:System.Windows.Shapes.Ellipse>.  Oluşturma bir <xref:System.Windows.Shapes.Ellipse> şeklin tanımlayarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri. Bir daire çizmek için belirtin bir <xref:System.Windows.Shapes.Ellipse> olan <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerler eşit.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 İşlenen bir örneği aşağıdaki resimde gösterilmektedir <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elips çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Yolları ve geometrileri kullanma  
 <xref:System.Windows.Shapes.Path> Sınıfı, eğriler ve karmaşık şekiller çizme olanak tanır. Bu eğriler ve şekiller kullanarak açıklanan <xref:System.Windows.Media.Geometry> nesneleri. Kullanılacak bir <xref:System.Windows.Shapes.Path>, oluşturduğunuz bir <xref:System.Windows.Media.Geometry> ve ayarlamak için kullanın <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Path.Data%2A> özelliği.  
  
 Var olan çeşitli <xref:System.Windows.Media.Geometry> aralarından seçim nesneleri. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, Ve <xref:System.Windows.Media.EllipseGeometry> görece Basit şekiller sınıfları açıklar. Daha karmaşık şekiller veya eğriler oluşturmak için kullanmak bir <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry ve PathSegments  
 <xref:System.Windows.Media.PathGeometry> nesneleri oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure> kendisi bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şekil bağlı bir bölümünü temsil eden nesneleri. Kesim türleri aşağıdakileri kapsamaktadır: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.ArcSegment>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisi çizmek için kullanılır.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Aşağıdaki görüntüde, işlenen şekli gösterilmektedir.  
  
 ![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> ve diğer <xref:System.Windows.Media.Geometry> sınıfları için bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>XAML söz dizimi olarak kısaltılır  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], özel bir kısaltılmış sözdizimi tanımlamak için kullanabilirsiniz bir <xref:System.Windows.Shapes.Path>. Aşağıdaki örnekte, kısaltılmış sözdizimi, karmaşık bir şekil çizmek için kullanılır.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Aşağıdaki görüntüde bir işlenen gösterilmektedir <xref:System.Windows.Shapes.Path>.  
  
 ![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> Öznitelik dize başlar yolu için bir başlangıç noktası koordinat sistemi oluşturan M tarafından gösterilen "moveto" komutu ile <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> Parametreler büyük/küçük harfe duyarlıdır. M büyük harf, geçerli bir yeni nokta için bir mutlak konumu belirtir. Bir küçük harf m göreli koordinatları belirtir. Bir üçüncü dereceden Bezier eğrisi başına (100,200) ilk parça olan ve (400,175) son iki çizilen kullanarak kontrol noktaları (100,25) ve (400,350). Bu kesimin C komutta belirtilir <xref:System.Windows.Shapes.Path.Data%2A> dize özniteliği. Yeniden Büyük Harf C mutlak bir yol belirtir; küçük harf c göreli bir yol gösterir.  
  
 Bir önceki alt yolun bitiş noktasından (400,175) yeni bir bitiş noktasına (280,175) çizgi belirten H mutlak yatay "lineto" komutu ile ikinci kesim başlar. Yatay "lineto" komutu olduğundan, belirtilen değeri olan bir *x*-koordine edin.  
  
 Tam yol sözdizimi için bkz. <xref:System.Windows.Shapes.Path.Data%2A> başvuru ve [PathGeometry kullanarak şekil oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Şekilleri Boyama  
 <xref:System.Windows.Media.Brush> bir şeklin boyamak için kullanılan nesneleri <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>. Aşağıdaki örnek, vuruş ve dolgu bir <xref:System.Windows.Shapes.Ellipse> belirtilir. Geçerli giriş Fırça özellikleri için bir anahtar sözcük ya da onaltılık renk değeri olabileceğini unutmayın. Özellikleri kullanılabilir rengi anahtar sözcükler hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.Colors> sınıfını <xref:System.Windows.Media> ad alanı.  
  
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
  
 Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Bir elips](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatif olarak, açıkça oluşturmak için bir özellik öğesi sözdizimini kullanabilirsiniz bir <xref:System.Windows.Media.SolidColorBrush> şekli düz renk ile boyamak için kullanılan nesne.  
  
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
  
 İşlenen şekli aşağıda gösterilmiştir.  
  
 ![SolidColorBrush çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Bir şeklin vuruş veya gradyanlar, görüntüleri, desenleri ve daha fazlasıyla dolgu boyama de yapabilirsiniz. Daha fazla bilgi için [düz renkler ve gradyanlar genel bakış boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Esneyebilen şekiller  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, Ve <xref:System.Windows.Shapes.Rectangle> tüm sınıflar bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliği. Bu özellik belirler nasıl bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğini (çizilecek Şekil) esnetilmiş doldurmak için <xref:System.Windows.Shapes.Shape> nesnenin düzen alanı. A <xref:System.Windows.Shapes.Shape> nesnenin Düzen yer alan miktarı <xref:System.Windows.Shapes.Shape> düzen sistemi tarafından sonlandırıldığından açık bir ayrılmış <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayarı nedeniyle veya kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarları. Windows Presentation Foundation'da Düzen hakkında ek bilgi için bkz: [Düzen](../../../../docs/framework/wpf/advanced/layout.md) genel bakış.  
  
 Uzat özelliği şu değerlerden birini alır:  
  
-   <xref:System.Windows.Media.Stretch.None><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini değil uzatılır.  
  
-   <xref:System.Windows.Media.Stretch.Fill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini kendi düzen alanı dolduracak şekilde uzatılır.  En boy oranı korunur değil.  
  
-   <xref:System.Windows.Media.Stretch.Uniform><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini mümkün olduğunca, özgün en boy oranını korurken kendi düzen alanı dolduracak şekilde uzatılır.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini, tamamen kendi özgün en boy oranını korurken kendi düzen alanı dolduracak şekilde uzatılır.  
  
 Unutmayın, bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğini uzatılır <xref:System.Windows.Shapes.Shape> nesnenin anahat uzatma sonra boyanır.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Polygon> (1,1) (0,1) için çok küçük bir üçgen (0,0) öğesinden çizmek için kullanılır. <xref:System.Windows.Shapes.Polygon> Nesnenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100 olarak ayarlanır ve kendi esnetme özelliğini doldurmak için ayarlanır. Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içeriğini (üçgen) daha büyük alanı dolduracak şekilde uzatılır.  
  
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
 <xref:System.Windows.Media.Transform> Sınıfı iki boyutlu düzlemde şekilleri dönüştürme bulunmasını sağlar.  Döndürme dönüşümü farklı türlerini içerir (<xref:System.Windows.Media.RotateTransform>), Ölçek (<xref:System.Windows.Media.ScaleTransform>), eğme (<xref:System.Windows.Media.SkewTransform>) ve çeviri (<xref:System.Windows.Media.TranslateTransform>).  
  
 Bir şekle uygulamak için ortak bir dönüştürme bir dönüş ' dir.  Bir şekli döndürmek için oluşturun bir <xref:System.Windows.Media.RotateTransform> ve belirtin, <xref:System.Windows.Media.RotateTransform.Angle%2A>. Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 45 derece 90 açı saat yönünde; vb. Bu öğe 90 derece döndürür; yönünde öğeyi döndürür. Ayarlama <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> öğe döndürüldüğü noktası denetlemek istiyorsanız özellikleri. Bu özellik değerleri, dönüştürülmekte olan öğenin koordinat ifade edilir. <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> sıfır varsayılan değerlerine sahiptir. Son olarak, uygulama <xref:System.Windows.Media.RotateTransform> öğeye. Şeklin düzenini etkileyen dönüşüm istemiyorsanız ayarlamak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.RotateTransform> şeklin sol üst köşedeki (0,0) bir şekil 45 derece döndürmek için kullanılır.  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu kez noktası hakkında (25,50) döndürülür.  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Aşağıdaki çizimde, iki dönüşümler uygulanırken sonuçlarını gösterir.  
  
 ![farklı merkezi noktalarıyla 45 derece döndürme](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Önceki örneklerde, her şekil nesnesi için tek bir dönüştürme uygulandı. Bir şekil (veya başka bir kullanıcı Arabirimi öğesi) birden çok dönüşüm uygulamak için bir <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [İzlenecek Yol: İlk WPF masaüstü uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
