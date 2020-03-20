---
title: Görüntüler, Çizimler ve Görsellerle Boyama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186917"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Görüntüler, Çizimler ve Görsellerle Boyama
Bu <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>konu, <xref:System.Windows.Media.VisualBrush> bir alanı bir görüntü, bir <xref:System.Windows.Media.Drawing>veya bir <xref:System.Windows.Media.Visual>.  

<a name="prereqs"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, sağladığı farklı fırça [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] türlerine ve temel özelliklerine aşina olmalısınız. Giriş için [WPF Fırçaları Genel Bakış'a](wpf-brushes-overview.md)bakın.  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>Görüntü ile bir Alanı Boyama  
 Bir <xref:System.Windows.Media.ImageBrush> alan boyar. <xref:System.Windows.Media.ImageSource> Bir ile <xref:System.Windows.Media.ImageSource> <xref:System.Windows.Media.ImageBrush> kullanmak için en yaygın <xref:System.Windows.Media.Imaging.BitmapImage>türü bir , bir bitmap grafik açıklar. Bir <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.Drawing> nesneyi kullanarak boyamak için a kullanabilirsiniz, <xref:System.Windows.Media.DrawingBrush> ancak bunun yerine kullanmak daha kolaydır. Nesneler hakkında <xref:System.Windows.Media.ImageSource> daha fazla bilgi için [Görüntülemegenel bakış'a](imaging-overview.md)bakın.  
  
 Bir <xref:System.Windows.Media.ImageBrush>ile boyamak <xref:System.Windows.Media.Imaging.BitmapImage> için, bir oluşturmak ve bitmap içeriği yüklemek için kullanabilirsiniz. Daha sonra, <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği ayarlamak için <xref:System.Windows.Media.ImageBrush>kullanın. Son olarak, <xref:System.Windows.Media.ImageBrush> boyamak istediğiniz nesneye uygulayın.  Içinde, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]aynı zamanda sadece <xref:System.Windows.Media.ImageBrush.ImageSource%2A> yüklemek <xref:System.Windows.Media.ImageBrush> için görüntünün yolu ile özelliğiayarlayabilirsiniz.  
  
 Tüm <xref:System.Windows.Media.Brush> nesneler gibi, <xref:System.Windows.Media.ImageBrush> şekiller, paneller, denetimler ve metin gibi nesneleri boyamak için bir kullanılabilir. Aşağıdaki resimde bir <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush çıktı örnekleri](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush tarafından boyanmış nesneler  
  
 Varsayılan olarak, <xref:System.Windows.Media.ImageBrush> bir resim, boyanmakta olan alanı tamamen doldurmak için görüntüyü genişleterek, boyalı alan görüntüden farklı bir en boy oranına sahipse görüntüyü bozabilir. Bu <xref:System.Windows.Media.TileBrush.Stretch%2A> davranışı, özelliği varsayılan değerinden <xref:System.Windows.Media.Stretch.Fill> <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>veya <xref:System.Windows.Media.Stretch.UniformToFill>. <xref:System.Windows.Media.ImageBrush> Bir tür olduğundan, görüntü fırçasının <xref:System.Windows.Media.TileBrush>çıkış alanını tam olarak nasıl doldurduğunu ve hatta desenler oluşturduğunu belirtebilirsiniz. Gelişmiş <xref:System.Windows.Media.TileBrush> özellikler hakkında daha fazla bilgi için [TileBrush Genel Bakış'a](tilebrush-overview.md)bakın.  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Örnek: Bitmap Görüntüsüyle Nesne Boyama  
 Aşağıdaki örnekte <xref:System.Windows.Media.ImageBrush> bir <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>Çizim ile bir Alanı Boyama  
 A, <xref:System.Windows.Media.DrawingBrush> bir alanı şekiller, metin, resimler ve videolarla boyamanızı sağlar. Çizim fırçası içindeki şekiller kendilerini düz bir renk, degrade, <xref:System.Windows.Media.DrawingBrush>görüntü, hatta başka bir ile boyanmış olabilir. Aşağıdaki resimde bir <xref:System.Windows.Media.DrawingBrush>.  
  
 ![DrawingFırça çıktı örnekleri](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush ile boyanmış nesneler  
  
 Bir <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing> nesne ile bir alan boyar. Nesne, <xref:System.Windows.Media.Drawing> şekil, biteş, video veya metin satırı gibi görünür içeriği açıklar. Farklı çizim türleri farklı içerik türlerini açıklar. Aşağıda, farklı çizim nesnetürlerinin listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>– Bir görüntü çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing>– Ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup>– Diğer çizimleri çizer. Diğer çizimleri tek bir bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 Nesneler hakkında <xref:System.Windows.Media.Drawing> daha fazla bilgi için [Çizim Nesnelerine Genel Bakış'a](drawing-objects-overview.md)bakın.  
  
 Bir <xref:System.Windows.Media.ImageBrush>gibi <xref:System.Windows.Media.DrawingBrush> , bir <xref:System.Windows.Media.DrawingBrush.Drawing%2A> çıkış alanını doldurmak için uzanır. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği varsayılan ayarından değiştirerek bu davranışı <xref:System.Windows.Media.Stretch.Fill>geçersiz kılabilirsiniz. Daha fazla bilgi <xref:System.Windows.Media.TileBrush.Stretch%2A> için tesise bakın.  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>Örnek: Çizimle Nesne Boyama  
 Aşağıdaki örnek, bir nesnenin üç elipslik bir çizimle nasıl boyanacağı gösterilmektedir. A <xref:System.Windows.Media.GeometryDrawing> elipstanımlamak için kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>Görsel ile bir Alanı Boyama  
 En çok yönlü ve tüm fırçalar <xref:System.Windows.Media.VisualBrush> güçlü, boyalar <xref:System.Windows.Media.Visual>bir alan . A, <xref:System.Windows.Media.Visual> birçok yararlı grafik bileşeninin atası olarak hizmet veren düşük düzeyli bir grafik türüdür. Örneğin, <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Controls.Control> ve sınıflar nesnelerin <xref:System.Windows.Media.Visual> tüm türleridir. Bir <xref:System.Windows.Media.VisualBrush>kullanarak, hemen hemen her [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik nesneile alanları boyayabilirsiniz.  
  
> [!NOTE]
> Bir <xref:System.Windows.Media.VisualBrush> nesne türü <xref:System.Windows.Freezable> olmasına rağmen, <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği ' den başka `null`bir değere ayarlandığında dondurulamaz (salt okunur)  
  
 Bir <xref:System.Windows.Media.VisualBrush>'nin içeriğini <xref:System.Windows.Media.VisualBrush.Visual%2A> belirtmenin iki yolu vardır.  
  
- Yeni <xref:System.Windows.Media.Visual> bir oluşturun ve özelliğini <xref:System.Windows.Media.VisualBrush.Visual%2A> ayarlamak <xref:System.Windows.Media.VisualBrush>için kullanın. Örneğin, [Bkz. Örnek: Aşağıdaki Görsel bölümüyle bir Nesneyi boyama.](#examplevisualbrush1)  
  
- Hedefin <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.Visual>yinelenen bir görüntüsünü oluşturan varolan bir , kullanın. Daha sonra yansıma <xref:System.Windows.Media.VisualBrush> ve büyütme gibi ilginç efektler oluşturmak için kullanabilirsiniz. Örneğin, [Bkz. Örnek: Yansıma](#examplevisualbrush2) bölümü oluştur.  
  
 Bir <xref:System.Windows.Media.VisualBrush.Visual%2A> a <xref:System.Windows.Media.VisualBrush> için yeni tanımladığınızda ve bu <xref:System.Windows.Media.Visual> bir <xref:System.Windows.UIElement> (panel veya denetim gibi) olduğunda, düzen <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> sistemi özellik `true`ayarlandığında alt öğeleri üzerinde <xref:System.Windows.UIElement> çalışır. Ancak, kök <xref:System.Windows.UIElement> aslında sistemin geri kalanından izole edilir: stilleri ve dış düzeni bu sınır nüfuz edemez. Bu nedenle, kökün boyutunu açıkça <xref:System.Windows.UIElement>belirtmeniz gerekir, çünkü <xref:System.Windows.Media.VisualBrush> tek üst öğesi ve bu nedenle otomatik olarak boyanmakta olan alana kendini boyutlandıramaz. Düzen hakkında daha [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fazla bilgi için [Düzen'e](../advanced/layout.md)bakın.  
  
 Gibi <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>ve <xref:System.Windows.Media.VisualBrush> , bir çıkış alanını doldurmak için içeriğini genişletir. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği varsayılan ayarından değiştirerek bu davranışı <xref:System.Windows.Media.Stretch.Fill>geçersiz kılabilirsiniz. Daha fazla bilgi <xref:System.Windows.Media.TileBrush.Stretch%2A> için tesise bakın.  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>Örnek: Nesneyi Görsel Olarak Boyama  
 Aşağıdaki örnekte, bir dikdörtgen boyamak için çeşitli denetimler ve bir panel kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>Örnek: Yansıma Oluşturma  
 Önceki örnekte, arka plan <xref:System.Windows.Media.Visual> olarak kullanılmak üzere yeni bir yeninin nasıl oluşturultuğu göstermişt Varolan bir <xref:System.Windows.Media.VisualBrush> görseli görüntülemek için de a kullanabilirsiniz; bu özellik yansımalar ve büyütme gibi ilginç görsel efektler üretmenizi sağlar. Aşağıdaki örnek, <xref:System.Windows.Media.VisualBrush> birkaç öğe içeren <xref:System.Windows.Controls.Border> bir yansıması oluşturmak için a kullanır. Aşağıdaki resimde, bu örnekte üreten çıktı gösterilmektedir.  
  
 ![Yansıyan Görsel nesne](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Yansıyan Görsel nesne  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Ekranın bölümlerini nasıl büyüteceklerini ve yansımaları nasıl oluşturup oluştursurlarını gösteren ek örnekler için [VisualBrush Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)bakın.  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>TileFırça Özellikleri  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>ve <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Media.TileBrush> nesne türleridir. <xref:System.Windows.Media.TileBrush>nesneler, bir alanın görüntü, çizim veya görselle nasıl boyandığı üzerinde büyük bir denetim sağlar. Örneğin, bir alanı tek bir uzatılmış görüntüyle boyamak yerine, bir desen oluşturan bir dizi resim kutucadı ile bir alanı boyayabilirsiniz.  
  
 A'nın <xref:System.Windows.Media.TileBrush> üç ana bileşeni vardır: içerik, döşemeler ve çıkış alanı.  
  
 ![TileFırça bileşenleri](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Tek bir döşemeile Bir Kiremit Fırçabileşenleri  
  
 ![Karo Fayans Fırçasının Bileşenleri](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Birden çok karo içeren bir Kiremit Fırçasının bileşenleri  
  
 <xref:System.Windows.Media.TileBrush> Nesnelerin döşeme özellikleri hakkında daha fazla bilgi [için, TileBrush Genel Bakış](tilebrush-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush’a Genel Bakış](tilebrush-overview.md)
- [WPF Fırçalarına Genel Bakış](wpf-brushes-overview.md)
- [Görüntülemeye Genel Bakış](imaging-overview.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [Opaklık Maskelerine Genel Bakış](opacity-masks-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [ImageBrush Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
