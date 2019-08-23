---
title: WPF Fırçalarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 29f0bc77306df5639c188295f9f5dff7f18b4706
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962842"
---
# <a name="wpf-brushes-overview"></a>WPF Fırçalarına Genel Bakış
Ekranınızda görülebilen her şey, bir fırça tarafından boyandığı için görülebilir. Örneğin, bir düğmenin arka planını, metin ön kümesini ve bir şeklin dolgusunu betimleyen bir fırça kullanılır. Bu konu, fırçalarla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] boyama kavramlarını tanıtır ve örnekler sunar. Fırçalar, nesneleri basit, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] düz renklerle karmaşık desen ve görüntü kümelerine göre boyamanıza imkan tanır.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Fırça ile boyama  
 Bir <xref:System.Windows.Media.Brush> alanı çıktısı ile bir "boyar". Farklı fırçalar farklı türlerde çıktıya sahiptir. Bazı fırçalar, bir alanı düz renk ile, diğerleri ise gradyan, kalıp, resim veya çizim ile boyar. Aşağıdaki çizimde, farklı <xref:System.Windows.Media.Brush> türlerin her birinin örnekleri gösterilmektedir.  
  
 ![Fırça türleri](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Fırça örnekleri  
  
 Çoğu görsel nesne nasıl boyanmış olduğunu belirtmenizi sağlar. Aşağıdaki tabloda, içinde kullanabileceğiniz <xref:System.Windows.Media.Brush>bazı ortak nesneler ve özellikler listelenmiştir.  
  
|örneği|Fırça özellikleri|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Aşağıdaki bölümler, farklı <xref:System.Windows.Media.Brush> türleri anlatmaktadır ve her birine bir örnek sağlar.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Düz renk ile boyama  
 Bir <xref:System.Windows.Media.SolidColorBrush> alanı kesintisiz <xref:System.Windows.Media.Color>bir şekilde boyar. ' I belirtmek <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush>için çeşitli yollar vardır: Örneğin, Alfa, kırmızı, mavi ve yeşil kanallarını belirtebilir veya <xref:System.Windows.Media.Colors> sınıf tarafından sunulan önceden tanımlanmış renkten birini kullanabilirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Shapes.Shape.Fill%2A>'a boyamak için bir kullanır. <xref:System.Windows.Shapes.Rectangle> Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![SolidColorBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
SolidColorBrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <xref:System.Windows.Media.SolidColorBrush> Sınıfı hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Doğrusal gradyan ile boyama  
 , Doğrusal gradyan ile bir alanı boyar.<xref:System.Windows.Media.LinearGradientBrush> Doğrusal bir gradyan, gradyan ekseninde iki veya daha fazla rengi bir çizgi genelinde karıştırır. Gradyandaki <xref:System.Windows.Media.GradientStop> renkleri ve bunların konumlarını belirtmek için nesneleri kullanırsınız.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Shapes.Shape.Fill%2A>'a boyamak için bir kullanır. <xref:System.Windows.Shapes.Rectangle> Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![Bir Doğrgradientbrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Bir Doğrgradientbrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.LinearGradientBrush> Sınıfı hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Radyal gradyan ile boyama  
 Bir <xref:System.Windows.Media.RadialGradientBrush> radyal gradyan ile bir alanı boyar. Radyal gradyan bir daire içinde iki veya daha fazla rengi karıştırır. Sınıfında olduğu gibi, nesneleri Gradyandaki renkleri ve onların konumlarını belirtmek için kullanırsınız <xref:System.Windows.Media.GradientStop>. <xref:System.Windows.Media.LinearGradientBrush>  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.RadialGradientBrush> <xref:System.Windows.Shapes.Shape.Fill%2A>'a boyamak için bir kullanır. <xref:System.Windows.Shapes.Rectangle> Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![RadialGradientBrush kullanarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
RadialGradientBrush kullanarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.RadialGradientBrush> Sınıfı hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Görüntüyle boyama  
 , İle bir alanı <xref:System.Windows.Media.ImageBrush>boyar. <xref:System.Windows.Media.ImageSource>  
  
 Aşağıdaki örnek, <xref:System.Windows.Shapes.Shape.Fill%2A> ' a <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Shapes.Rectangle>boyamak için bir kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![ImageBrush tarafından boyanan dikdörtgen](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Görüntü kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <xref:System.Windows.Media.ImageBrush> Sınıfı hakkında daha fazla bilgi için bkz. [görüntü, çizim ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Çizim ile boyama  
 , İle bir alanı <xref:System.Windows.Media.DrawingBrush>boyar. <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.Drawing> , Şekil, resim, metin ve medya içerebilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Shapes.Shape.Fill%2A>'a boyamak için bir kullanır. <xref:System.Windows.Shapes.Rectangle> Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![DrawingBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <xref:System.Windows.Media.DrawingBrush> Sınıfı hakkında daha fazla bilgi için bkz. [görüntü, çizim ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Görselle boyama  
 Bir <xref:System.Windows.Media.VisualBrush> nesne<xref:System.Windows.Media.Visual> ile bir alanı boyar. Görsel nesne örnekleri, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Page>, ve <xref:System.Windows.Controls.MediaElement>içerir. <xref:System.Windows.Media.VisualBrush> Ayrıca, uygulamanızın bir bölümünden başka bir alana içerik yansımanızı sağlar; yansıma efektleri oluşturmak ve ekranın bölümlerini büyütme konusunda çok yararlı olur.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Shapes.Shape.Fill%2A>'a boyamak için bir kullanır. <xref:System.Windows.Shapes.Rectangle> Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![VisualBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <xref:System.Windows.Media.VisualBrush> Sınıfı hakkında daha fazla bilgi için bkz. [görüntü, çizim ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Önceden tanımlanmış ve sistem fırçalarını kullanarak boyama  
 Windows Presentation Foundation (WPF), nesneleri boyamak için kullanabileceğiniz önceden tanımlanmış ve sistem fırçaları kümesi sağlar.  
  
- Kullanılabilir önceden tanımlanmış fırçaların bir listesi için, <xref:System.Windows.Media.Brushes> sınıfına bakın. Önceden tanımlanmış bir fırçanın nasıl kullanılacağını gösteren bir örnek için bkz. [düz renk ile bir alanı boyama](how-to-paint-an-area-with-a-solid-color.md).  
  
- Kullanılabilir sistem fırçalarının bir listesi için, <xref:System.Windows.SystemColors> sınıfına bakın. Bir örnek için bkz. [Sistem fırçası ile bir alanı boyama](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Ortak fırça özellikleri  
 <xref:System.Windows.Media.Brush>nesneler, fırçayı <xref:System.Windows.Media.Brush.Opacity%2A> saydam veya kısmen saydam hale getirmek için kullanılabilecek bir özellik sağlar. 0 değeri fırçayla tamamen saydam hale gelir, 1 <xref:System.Windows.Media.Brush.Opacity%2A> değeri de fırçayı tamamen opak hale getirir. <xref:System.Windows.Media.Brush.Opacity%2A> Aşağıdaki örnek, yüzde <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush> 25 opak hale getirmek için özelliğini kullanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Fırça kısmen saydam renkler içeriyorsa, rengin opaklık değeri, fırçanın opaklık değeri ile çarpma ile birleştirilir. Örneğin, bir fırçanın opaklık değeri 0,5 ise ve fırçaya ilişkin bir rengin opaklık değeri 0,5 ise, çıkış rengi bir opaklık değeri olan 0,25.  
  
> [!NOTE]
> Bir fırçanın opaklık değerini değiştirmek, <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> özelliğini kullanarak bir öğenin tüm saydamlığını değiştirmek daha verimlidir.  
  
 <xref:System.Windows.Media.Brush.Transform%2A> Veya<xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliklerini kullanarak fırçanın içeriğini döndürebilir, ölçeklendirebilir, eğebilir ve çevirebilirsiniz. Daha fazla bilgi için bkz. [fırça dönüşümüne genel bakış](brush-transformation-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable> Nesnelerolduklarından<xref:System.Windows.Media.Brush> nesneler canlandırılabilirler. Daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable özellikleri  
 Sınıfından devraldığı <xref:System.Windows.Freezable> için <xref:System.Windows.Media.Brush> , sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Brush> nesneler [kaynak](../advanced/xaml-resources.md)olarak, birden fazla nesne arasında paylaşılan ve klonlanmış olabilir. Ayrıca, dışındaki <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.VisualBrush> tüm türler, performansı artırmak ve iş parçacığı açısından güvenli hale getirilbilmek için salt okunurdur.  
  
 Nesneler tarafından <xref:System.Windows.Freezable> sunulan farklı özellikler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
 Nesnelerin neden <xref:System.Windows.Media.VisualBrush> dondurulamadığı hakkında daha fazla bilgi için, <xref:System.Windows.Media.VisualBrush> tür sayfasına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Fırçalar örneği](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160049)
- [Nasıl Yapılır Konuları](brushes-how-to-topics.md)
- [Diğer Performans Önerileri](../advanced/optimizing-performance-other-recommendations.md)
