---
title: WPF Fırçalarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 14e3d095d50f41e5b20a79d76c464bcf28c99327
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053099"
---
# <a name="wpf-brushes-overview"></a>WPF Fırçalarına Genel Bakış
Her şey, ekranda görünen fırça tarafından boyanan çünkü görülebilir. Örneğin, fırça bir düğme ve metin ön bir şeklin arka planı tanımlamak için kullanılır. Bu konu ile Boyama kavramları tanıtır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fırçaları ve örnekler sağlar. Fırçalar boyama etkinleştirme [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] basit, düz renk düzenleri ve görüntü karmaşık kümelerine nesneleri.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Fırça ile Boyama  
 A <xref:System.Windows.Media.Brush> "çıktısını ile bir alanı boyar". Farklı fırçalar farklı çıkış türleri vardır. Bazı Fırçalar, düz bir renk gradyanı, deseni, görüntü veya çizim başkalarıyla ile bir alanı boyama. Her biri farklı örnekleri aşağıda gösterilmiştir <xref:System.Windows.Media.Brush> türleri.  
  
 ![Fırça türü](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Fırça örnekleri  
  
 Çoğu görsel nesneler nasıl boyanacağını belirtmenize olanak verir. Aşağıdaki tabloda bazı ortak nesneleri ve özellikleri ile kullanabileceğiniz listeler bir <xref:System.Windows.Media.Brush>.  
  
|örneği|Fırça özellikleri|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Aşağıdaki bölümlerde farklı açıklanmaktadır <xref:System.Windows.Media.Brush> türleri ve her bir örneğini sağlayın.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Düz renk ile Boyama  
 A <xref:System.Windows.Media.SolidColorBrush> düz bir ile bir alanı boyar <xref:System.Windows.Media.Color>. Belirtmek için yol çeşitli vardır <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush>: Örneğin, alfa, kırmızı, mavi ve yeşil kanallarından belirtebilir veya tarafından sağlanan önceden tanımlanmış bir rengi birini <xref:System.Windows.Media.Colors> sınıfı.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.SolidColorBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizim boyanan dikdörtgen gösterir.  
  
 ![Bir dikdörtgen boyanan SolidColorBrush kullanarak](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
SolidColorBrush'ı kullanarak bir dikdörtgen boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.SolidColorBrush> sınıfı [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Doğrusal gradyan ile Boyama  
 A <xref:System.Windows.Media.LinearGradientBrush> doğrusal gradyan ile bir alanı boyar. Doğrusal gradyan bir çizgi gradyan ekseni iki veya daha fazla rengi karıştırır. Kullandığınız <xref:System.Windows.Media.GradientStop> renkler bir gradyan ve konumlarını belirtmek için nesneleri.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.LinearGradientBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizim boyanan dikdörtgen gösterir.  
  
 ![Bir dikdörtgen boyanan LinearGradientBrush kullanılarak](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Bir dikdörtgen LinearGradientBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.LinearGradientBrush> sınıfı [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Radyal gradyan ile Boyama  
 A <xref:System.Windows.Media.RadialGradientBrush> Radyal gradyan ile bir alanı boyar. Radyal gradyan arasında bir daire iki veya daha fazla rengi karıştırır. Olduğu gibi <xref:System.Windows.Media.LinearGradientBrush> sınıfı kullandığınız <xref:System.Windows.Media.GradientStop> renkler bir gradyan ve konumlarını belirtmek için nesneleri.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.RadialGradientBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizim boyanan dikdörtgen gösterir.  
  
 ![Bir dikdörtgen boyanan RadialGradientBrush kullanılarak](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Bir dikdörtgen RadialGradientBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.RadialGradientBrush> sınıfı [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Görüntü ile Boyama  
 Bir <xref:System.Windows.Media.ImageBrush> ile bir alanı boyar bir <xref:System.Windows.Media.ImageSource>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.ImageBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizim boyanan dikdörtgen gösterir.  
  
 ![Bir dikdörtgen boyanan ImageBrush tarafından](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Bir görüntü kullanarak bir dikdörtgen boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> sınıfı [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Çizim ile Boyama  
 A <xref:System.Windows.Media.DrawingBrush> ile bir alanı boyar bir <xref:System.Windows.Media.Drawing>. A <xref:System.Windows.Media.Drawing> şekiller, resimleri, metin ve medya içerebilir.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizim boyanan dikdörtgen gösterir.  
  
 ![Bir dikdörtgen boyanan DrawingBrush'ı kullanarak](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush'ı kullanarak bir dikdörtgen boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.DrawingBrush> sınıfı [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Görsel ile Boyama  
 A <xref:System.Windows.Media.VisualBrush> ile bir alanı boyar bir <xref:System.Windows.Media.Visual> nesne. Görsel nesneler örnekler <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, ve <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> , proje içeriği bir bölümünü başka bir alan; uygulamanıza olanak tanır, yansıma efektleri oluşturup ekranın bölümlerini büyütme için çok kullanışlıdır.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.VisualBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizim boyanan dikdörtgen gösterir.  
  
 ![Bir dikdörtgen boyanan VisualBrush kullanılarak](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush'ı kullanarak bir dikdörtgen boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.VisualBrush> sınıfı [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Önceden tanımlanmış ve sistem fırçaları ile Boyama  
 Kolaylık olması için Windows Presentation Foundation (WPF), bir dizi önceden tanımlanmış ve sistem nesneleri boyamak için kullanabileceğiniz fırçaları sağlar.  
  
- Kullanılabilir önceden tanımlanmış Fırçalar listesi için bkz. <xref:System.Windows.Media.Brushes> sınıfı. Önceden tanımlanmış bir fırçanın nasıl kullanılacağını gösteren bir örnek için bkz: [düz renk ile bir alanı boyama](how-to-paint-an-area-with-a-solid-color.md).  
  
- Kullanılabilir sistem fırçaları listesi için bkz. <xref:System.Windows.SystemColors> sınıfı. Bir örnek için bkz. [sistem fırçası ile bir alanı boyama](how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Ortak Fırça özellikleri  
 <xref:System.Windows.Media.Brush> nesneler sağlayan bir <xref:System.Windows.Media.Brush.Opacity%2A> fırça saydam veya kısmen saydam yapmak için kullanılan özellik. Bir <xref:System.Windows.Media.Brush.Opacity%2A> 0 değerini fırça çalışırken tamamen saydam yapar bir <xref:System.Windows.Media.Brush.Opacity%2A> 1 değerini fırça tamamen opak sağlar. Aşağıdaki örnekte <xref:System.Windows.Media.Brush.Opacity%2A> özelliğini bir <xref:System.Windows.Media.SolidColorBrush> donuk yüzde 25 '.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Fırça kısmen saydam olan renkleri içeriyorsa, renk opaklık değerini çarpma fırçanın geçirgenlik değeri ile birleştirilir. Örneğin, fırça 0,5 bir opaklık değerine sahiptir ve fırça içinde kullanılan rengi 0,5 bir opaklık değerini de varsa, Çıkış Rengi 0,25 saydamlık değerine sahiptir.  
  
> [!NOTE]
>  Bir öğenin tamamını kullanmanın değiştirmek çok daha fırça opaklığını değerini değiştirmek için daha verimlidir, <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> özelliği.  
  
 Döndürme, ölçeklendirme, eğme ve kullanarak bir fırçanın içeriği Çevir kendi <xref:System.Windows.Media.Brush.Transform%2A> veya <xref:System.Windows.Media.Brush.RelativeTransform%2A> özellikleri. Daha fazla bilgi için [fırça dönüşümüne genel bakış](brush-transformation-overview.md).  
  
 Çünkü bunlar <xref:System.Windows.Media.Animation.Animatable> nesneleri <xref:System.Windows.Media.Brush> nesneleri ettirilebilir. Daha fazla bilgi için [animasyona genel bakış](animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable Özellikleri  
 Öğesinden devralındığından <xref:System.Windows.Freezable> sınıfı <xref:System.Windows.Media.Brush> sınıfı birkaç özel özellikleri sağlar: <xref:System.Windows.Media.Brush> nesneleri olarak bildirilebilir [kaynakları](../advanced/xaml-resources.md), birden fazla nesne arasında paylaşılan ve kopyalanan. Ayrıca, tüm <xref:System.Windows.Media.Brush> dışında türleri <xref:System.Windows.Media.VisualBrush> performansını artırmak için salt okunur ve iş parçacığı güvenli.  
  
 Tarafından sağlanan farklı özellikleri hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
 Neden hakkında daha fazla bilgi için <xref:System.Windows.Media.VisualBrush> nesneler olamaz dondurulmuş, bkz: <xref:System.Windows.Media.VisualBrush> türü sayfası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Fırça örneği](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush Örneği](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160049)
- [Nasıl Yapılır Konuları](brushes-how-to-topics.md)
- [Diğer Performans Önerileri](../advanced/optimizing-performance-other-recommendations.md)
