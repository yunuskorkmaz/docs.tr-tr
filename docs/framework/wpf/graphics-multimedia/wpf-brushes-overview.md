---
title: Fırçalara genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 18ca9b79a6ee801638a54fcb227c44e9aea21fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746214"
---
# <a name="wpf-brushes-overview"></a>WPF Fırçalarına Genel Bakış
Ekranınızda görülebilen her şey, bir fırça tarafından boyandığı için görülebilir. Örneğin, bir düğmenin arka planını, metin ön kümesini ve bir şeklin dolgusunu betimleyen bir fırça kullanılır. Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fırçalarla boyama kavramlarını tanıtır ve örnekler sağlar. Fırçalar, basit ve düz renklerle karmaşık desen ve resim kümelerine [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] nesneleri boyamanıza imkan tanır.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Fırça ile boyama  
 Bir <xref:System.Windows.Media.Brush> ", çıktısını içeren bir alanı boyar. Farklı fırçalar farklı türlerde çıktıya sahiptir. Bazı fırçalar, bir alanı düz renk ile, diğerleri ise gradyan, kalıp, resim veya çizim ile boyar. Aşağıdaki çizimde, farklı <xref:System.Windows.Media.Brush> türlerinin her birinin örnekleri gösterilmektedir.  
  
 ![Fırça türleri](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Fırça örnekleri  
  
 Çoğu görsel nesne nasıl boyanmış olduğunu belirtmenizi sağlar. Aşağıdaki tabloda, <xref:System.Windows.Media.Brush>kullanabileceğiniz bazı ortak nesneler ve özellikler listelenmiştir.  
  
|örneği|Fırça özellikleri|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Aşağıdaki bölümler, farklı <xref:System.Windows.Media.Brush> türlerini ve her birine bir örnek sağlar.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Düz renk ile boyama  
 <xref:System.Windows.Media.SolidColorBrush>, bir alanı düz <xref:System.Windows.Media.Color>boyar. <xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Media.SolidColorBrush.Color%2A> belirtmek için kullanabileceğiniz çeşitli yollar vardır: Örneğin, Alfa, kırmızı, mavi ve yeşil kanallarını belirtebilir veya <xref:System.Windows.Media.Colors> sınıfı tarafından sunulan önceden tanımlanmış renkten birini kullanabilirsiniz.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.SolidColorBrush> kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![SolidColorBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
SolidColorBrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <xref:System.Windows.Media.SolidColorBrush> sınıfı hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Doğrusal gradyan ile boyama  
 <xref:System.Windows.Media.LinearGradientBrush>, doğrusal gradyan ile bir alanı boyar. Doğrusal bir gradyan, gradyan ekseninde iki veya daha fazla rengi bir çizgi genelinde karıştırır. Gradyandaki renkleri ve bunların konumlarını belirtmek için <xref:System.Windows.Media.GradientStop> nesneleri kullanırsınız.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.LinearGradientBrush> kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![Bir Doğrgradientbrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Bir Doğrgradientbrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.LinearGradientBrush> sınıfı hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Radyal gradyan ile boyama  
 Bir <xref:System.Windows.Media.RadialGradientBrush> radyal degradeyle bir alanı boyar. Radyal gradyan bir daire içinde iki veya daha fazla rengi karıştırır. <xref:System.Windows.Media.LinearGradientBrush> sınıfında olduğu gibi, Gradyandaki renkleri ve bunların konumlarını belirtmek için <xref:System.Windows.Media.GradientStop> nesneleri kullanırsınız.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.RadialGradientBrush> kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![RadialGradientBrush kullanarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
RadialGradientBrush kullanarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.RadialGradientBrush> sınıfı hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Görüntüyle boyama  
 Bir <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageSource>bir alanı boyar.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.ImageBrush> kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![ImageBrush tarafından boyanan dikdörtgen](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Görüntü kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <xref:System.Windows.Media.ImageBrush> sınıfı hakkında daha fazla bilgi için bkz. [görüntü, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Çizim ile boyama  
 Bir <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing>bir alanı boyar. Bir <xref:System.Windows.Media.Drawing> şekil, resim, metin ve medya içerebilir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.DrawingBrush> kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![DrawingBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <xref:System.Windows.Media.DrawingBrush> sınıfı hakkında daha fazla bilgi için bkz. [görüntü, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Görselle boyama  
 <xref:System.Windows.Media.VisualBrush>, bir <xref:System.Windows.Media.Visual> nesnesi olan bir alanı boyar. Görsel nesne örnekleri <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>ve <xref:System.Windows.Controls.MediaElement>içerir. <xref:System.Windows.Media.VisualBrush> Ayrıca, uygulamanızın bir bölümünden başka bir alana içerik proje yapmanızı sağlar; Yansıma efektleri oluşturmak ve ekranın bölümlerini büyütme için çok kullanışlıdır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.VisualBrush> kullanır. Aşağıdaki çizimde boyanmış dikdörtgen gösterilmektedir.  
  
 ![VisualBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush kullanılarak boyanmış bir dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <xref:System.Windows.Media.VisualBrush> sınıfı hakkında daha fazla bilgi için bkz. [görüntü, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Önceden tanımlanmış ve sistem fırçalarını kullanarak boyama  
 Windows Presentation Foundation (WPF), nesneleri boyamak için kullanabileceğiniz önceden tanımlanmış ve sistem fırçaları kümesi sağlar.  
  
- Kullanılabilir önceden tanımlanmış fırçalar listesi için <xref:System.Windows.Media.Brushes> sınıfına bakın. Önceden tanımlanmış bir fırçanın nasıl kullanılacağını gösteren bir örnek için bkz. [düz renk ile bir alanı boyama](how-to-paint-an-area-with-a-solid-color.md).  
  
- Kullanılabilir sistem fırçalarının bir listesi için <xref:System.Windows.SystemColors> sınıfına bakın. Bir örnek için bkz. [Sistem fırçası ile bir alanı boyama](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Ortak fırça özellikleri  
 <xref:System.Windows.Media.Brush> nesneler, fırçayı saydam veya kısmen saydam hale getirmek için kullanılabilecek bir <xref:System.Windows.Media.Brush.Opacity%2A> özelliği sağlar. <xref:System.Windows.Media.Brush.Opacity%2A> 0 değeri, bir fırçayı tamamen saydam hale getirir, ancak 1 <xref:System.Windows.Media.Brush.Opacity%2A> değeri, fırçayı tamamen opak hale getirir. Aşağıdaki örnek, yüzde 25 oranında donuk bir <xref:System.Windows.Media.SolidColorBrush> yapmak için <xref:System.Windows.Media.Brush.Opacity%2A> özelliğini kullanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Fırça kısmen saydam renkler içeriyorsa, rengin opaklık değeri, fırçanın opaklık değeri ile çarpma ile birleştirilir. Örneğin, bir fırçanın opaklık değeri 0,5 ise ve fırçaya ilişkin bir rengin opaklık değeri 0,5 ise, çıkış rengi bir opaklık değeri olan 0,25.  
  
> [!NOTE]
> Bir fırçanın opaklık değerini değiştirmek, <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> özelliğini kullanarak tüm bir öğenin saydamlığını değiştirmek daha verimlidir.  
  
 <xref:System.Windows.Media.Brush.Transform%2A> veya <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliklerini kullanarak bir fırçanın içeriğini döndürebilir, ölçeklendirebilir, eğebilir ve çevirebilirsiniz. Daha fazla bilgi için bkz. [fırça dönüşümüne genel bakış](brush-transformation-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable> nesneler olduklarından <xref:System.Windows.Media.Brush> nesneleri canlandırılabilirler. Daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable özellikleri  
 <xref:System.Windows.Freezable> sınıfından devraldığı için <xref:System.Windows.Media.Brush> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Brush> nesneler [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak veya birden çok nesne arasında paylaşılan ve klonlanmış olabilir. Ayrıca, <xref:System.Windows.Media.VisualBrush> hariç tüm <xref:System.Windows.Media.Brush> türleri, performansı artırmak ve iş parçacığı açısından güvenli hale getirilbilmek için salt okunurdur.  
  
 <xref:System.Windows.Freezable> nesneleri tarafından sunulan farklı özellikler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.VisualBrush> nesnelerinin neden dondurulamadığı hakkında daha fazla bilgi için <xref:System.Windows.Media.VisualBrush> tür sayfasına bakın.  
  
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
