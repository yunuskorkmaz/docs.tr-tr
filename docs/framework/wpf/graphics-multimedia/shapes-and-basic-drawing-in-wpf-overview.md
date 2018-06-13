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
ms.openlocfilehash: adbf982da25ff445d277b7c1b5911217d9825c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566317"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
Bu konu ile çizmek nasıl genel bir fikir veren <xref:System.Windows.Shapes.Shape> nesneleri. A <xref:System.Windows.Shapes.Shape> bir tür <xref:System.Windows.UIElement> ekrana bir şekil çizme olanak sağlar. Kullanıcı Arabirimi öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri içinde kullanılabilir <xref:System.Windows.Controls.Panel> öğeleri ve çoğu denetim.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] birkaç grafik ve işleme hizmetlerine erişim katmanı sunar. En üst katmanında <xref:System.Windows.Shapes.Shape> nesneleridir kullanın ve düzeni ve katılım gibi çok sayıda kullanışlı özellikle sağlamak kolay [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Şekil nesneleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıma hazır bir dizi sağlar <xref:System.Windows.Shapes.Shape> nesneleri.  Tüm şekil nesneleri devralınmalıdır <xref:System.Windows.Shapes.Shape> sınıfı. Kullanılabilir şekil nesneleri dahil <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, ve <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> nesneleri aşağıdaki ortak özellikleri paylaşır.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin anahat nasıl boyanır açıklar.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin Anahat kalınlığı açıklar.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: Şeklin iç nasıl boyanır açıklar.  
  
-   Koordinatları ve köşeleri belirtmek için veri özellikleri aygıttan bağımsız piksel cinsinden ölçülür.  
  
 Öğesinden türetilen çünkü <xref:System.Windows.UIElement>, şekil nesneleri paneller ve çoğu denetim içinde kullanılabilir. <xref:System.Windows.Controls.Canvas> Panosudur mutlak alt nesnelerinin konumlandırma desteklediğinden karmaşık çizimler oluşturmak için özellikle iyi bir seçimdir.  
  
 <xref:System.Windows.Shapes.Line> Sınıfı, iki nokta arasında bir çizgi çizmek sağlar. Aşağıdaki örnek çizgi koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Aşağıdaki resimde işlenen gösterilmiştir <xref:System.Windows.Shapes.Line>.  
  
 ![Satır çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Ancak <xref:System.Windows.Shapes.Line> sağlamasına bir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği, onu ayarlamanın etkisi yoktur çünkü bir <xref:System.Windows.Shapes.Line> hiçbir alana sahip.  
  
 Başka bir ortak şekli <xref:System.Windows.Shapes.Ellipse>.  Oluşturma bir <xref:System.Windows.Shapes.Ellipse> şeklin tanımlayarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri. Bir daire çizmek için belirtmek bir <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri eşit.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Aşağıdaki resimde işlenen bir örnek gösterilmiştir <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elips çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Yolları ve geometri kullanma  
 <xref:System.Windows.Shapes.Path> Sınıfı, eğriler ve karmaşık şekiller çizmek sağlar. Bu eğriler ve şekiller kullanarak açıklanan <xref:System.Windows.Media.Geometry> nesneleri. Kullanılacak bir <xref:System.Windows.Shapes.Path>, oluşturduğunuz bir <xref:System.Windows.Media.Geometry> ve ayarlamak için kullanın <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Path.Data%2A> özelliği.  
  
 Çeşitli vardır <xref:System.Windows.Media.Geometry> nesneleri seçin. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, Ve <xref:System.Windows.Media.EllipseGeometry> sınıfları ilgili basit şekilleri açıklar. Daha karmaşık şekiller veya eğriler oluşturmak için kullanın bir <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry ve PathSegments  
 <xref:System.Windows.Media.PathGeometry> nesneleri oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder. Her <xref:System.Windows.Media.PathFigure> kendisini bir veya daha fazla oluşmaktadır <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şeklin bağlı bir bölümünü temsil eden nesneler. Kesim türleri şunlardır: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.ArcSegment>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisi çizmek için kullanılır.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Aşağıdaki resim işlenen şekli göstermektedir.  
  
 ![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> ve diğer <xref:System.Windows.Media.Geometry> sınıfları için bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>XAML kısaltılmış sözdizimi  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], tanımlamak için özel bir kısaltılmış sözdizimi kullanabilirsiniz bir <xref:System.Windows.Shapes.Path>. Aşağıdaki örnekte, karmaşık bir şekil çizmek için kısaltılmış sözdizimi kullanılır.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Aşağıdaki resimde bir işlenmiş gösterilmiştir <xref:System.Windows.Shapes.Path>.  
  
 ![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> Öznitelik dizesini başlar, M tarafından yol için bir başlangıç noktası koordinat sistemi oluşturan belirtilen "moveto" komutuyla <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> Veri parametreleri büyük/küçük harfe duyarlıdır. Büyük Harf M geçerli bir yeni nokta için mutlak bir konum belirtir. Küçük harf m koordinatlara göre gösterir. İlk kesim (100,200) küp bir Bezier eğrisi başında olduğundan ve (400,175) son çizilmiş iki kullanarak denetim noktası (100,25) ve (400,350). Bu kesimin C komutu ile belirtilir <xref:System.Windows.Shapes.Path.Data%2A> öznitelik dize. Yeniden, büyük harf C mutlak bir yol gösterir; küçük harf c göreli bir yol gösterir.  
  
 İkinci kesim mutlak yatay "lineto" komutu önceki alt yolun bitiş noktasından (400,175) yeni bir bitiş noktasına (280,175) içinden bir çizgi belirtir H ile başlar. Yatay "lineto" komutu olduğu için belirtilen değer bir *x*-koordinatı.  
  
 Tam yol sözdizimi için bkz: <xref:System.Windows.Shapes.Path.Data%2A> başvurusu ve [PathGeometry kullanarak bir şekil oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Şekilleri Boyama  
 <xref:System.Windows.Media.Brush> Şeklin boyamak için kullanılan nesneleri <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>. Aşağıdaki örnek, vuruş ve dolgusunu bir <xref:System.Windows.Shapes.Ellipse> belirtilir. Geçerli giriş Fırça özellikleri için bir anahtar sözcük veya onaltılık renk değeri olabileceğini unutmayın. Özelliklerini kullanılabilir renk anahtar sözcükler hakkında daha fazla bilgi için bkz: <xref:System.Windows.Media.Colors> sınıfını <xref:System.Windows.Media> ad alanı.  
  
```  
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
  
 Aşağıdaki resimde işlenen gösterilmiştir <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elips](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatif olarak, açıkça oluşturmak için bir özellik öğesi sözdizimini kullanabilirsiniz bir <xref:System.Windows.Media.SolidColorBrush> şekli düz renk ile boyamak için nesne.  
  
```  
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
  
 Aşağıdaki çizimde işlenen şekli göstermektedir.  
  
 ![SolidColorBrush çizimi](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Şeklin vuruş veya dolgu gradyan, görüntüler, desenleri ve daha fazla ile de boyama yapabilirsiniz. Daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Uzatılabilir şekiller  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, Ve <xref:System.Windows.Shapes.Rectangle> tüm sınıflar bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliği. Bu özellik belirler nasıl bir <xref:System.Windows.Shapes.Shape> doldurmak için nesnenin içeriğini (çizilecek Şekil) uzatılmış <xref:System.Windows.Shapes.Shape> nesnesinin düzen alanı. A <xref:System.Windows.Shapes.Shape> nesnenin düzeni yer alan miktarını <xref:System.Windows.Shapes.Shape> düzen sistemi tarafından sonlandırıldığından açık bir ayrılmış <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayarı veya nedeniyle kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarlar. Windows Presentation Foundation'da Düzen hakkında ek bilgi için bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md) genel bakış.  
  
 Stretch özelliği aşağıdaki değerlerden birini alır:  
  
-   <xref:System.Windows.Media.Stretch.None><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini değil uzatılır.  
  
-   <xref:System.Windows.Media.Stretch.Fill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini düzeni alanı dolduracak şekilde uzatılır.  En boy oranını korunmaz.  
  
-   <xref:System.Windows.Media.Stretch.Uniform><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini, özgün en boy oranını koruyarak kendi düzen alanını doldurmak mümkün olduğunca uzatılır.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini, tamamen kendi özgün en boy oranını koruyarak kendi düzen alanını doldurmak için uzatılır.  
  
 Unutmayın, bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğini uzatılır <xref:System.Windows.Shapes.Shape> nesnesinin anahattı uzatma sonra boyanır.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Polygon> (1,1) (0,1) için çok küçük bir üçgen (0,0) gelen çizmek için kullanılır. <xref:System.Windows.Shapes.Polygon> Nesnenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100'e ayarlanır ve doldurmak için esnetme özelliğini ayarlayın. Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içeriğini (üçgen) daha büyük alanı dolduracak şekilde uzatılır.  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
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
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Şekilleri dönüştürme  
 <xref:System.Windows.Media.Transform> Sınıfı, sistemi, iki boyutlu bir düzlem şekillerde dönüştürmenizi sağlar.  Farklı dönüştürme türleri döndürme içerir (<xref:System.Windows.Media.RotateTransform>), Ölçek (<xref:System.Windows.Media.ScaleTransform>), eğme (<xref:System.Windows.Media.SkewTransform>) ve çeviri (<xref:System.Windows.Media.TranslateTransform>).  
  
 Bir şekle uygulamak için ortak bir dönüşüm bir döndürme ' dir.  Bir şekli döndürmek için oluşturma bir <xref:System.Windows.Media.RotateTransform> ve belirtin, <xref:System.Windows.Media.RotateTransform.Angle%2A>. Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 90 bir açıda saat yönünde; vb. Bu öğe 90 derece döndürür saat yönünde 45 derece; öğeyi döndürür. Ayarlama <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> öğesi döndürüldüğü noktası denetlemek istiyorsanız özellikleri. Bu özellik değerlerini dönüştürülmekte olan öğenin koordinat ifade edilir. <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> sıfır varsayılan değerlerine sahiptir. Son olarak, uygulama <xref:System.Windows.Media.RotateTransform> öğesi. Düzen etkilemek için dönüştürme istemiyorsanız şeklin ayarlayın <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.RotateTransform> şeklin sol üst köşede (0,0) bir şekli 45 derece döndürmek için kullanılır.  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu kez (25,50) noktasına hakkında döndürülür.  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Aşağıdaki çizimde iki dönüşümler uygulanırken sonuçlarını gösterir.  
  
 ![farklı merkez nokta 45 derece döndürmeler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 Önceki örneklerde, tek bir dönüştürme her şekil nesnesine uygulandı. Bir şekle (veya başka bir UI öğesine) çoklu dönüşüm uygulamak için kullanmak bir <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [İzlenecek Yol: İlk WPF masaüstü uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
