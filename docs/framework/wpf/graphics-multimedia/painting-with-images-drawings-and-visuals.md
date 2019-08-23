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
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929603"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Görüntüler, Çizimler ve Görsellerle Boyama
Bu konu, bir görüntü, <xref:System.Windows.Media.ImageBrush>a <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing>veya a <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Media.Visual>ile bir alanı boyamak için, ve nesnelerinin nasıl kullanılacağını açıklar.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, farklı fırça [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] türleri ve temel özellikleri hakkında bilgi sahibi olmanız gerekir. Giriş için [WPF Fırçalarına Genel Bakış](wpf-brushes-overview.md)bölümüne bakın.  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Görüntü ile bir Alanı Boyama  
 , İle bir alanı <xref:System.Windows.Media.ImageBrush>boyar. <xref:System.Windows.Media.ImageSource> <xref:System.Windows.Media.ImageSource> İle<xref:System.Windows.Media.ImageBrush> kullanmak için en yaygın türü bir bit eşlem grafiğini tanımlar <xref:System.Windows.Media.Imaging.BitmapImage>. Bir <xref:System.Windows.Media.DrawingImage> nesnesi<xref:System.Windows.Media.Drawing> kullanarak boyamak için kullanabilirsiniz, ancak <xref:System.Windows.Media.DrawingBrush> bunun yerine kullanmak daha basittir. Nesneler hakkında <xref:System.Windows.Media.ImageSource> daha fazla bilgi için bkz. [görüntülemeye genel bakış](imaging-overview.md).  
  
 İle <xref:System.Windows.Media.ImageBrush>boyamak için, <xref:System.Windows.Media.Imaging.BitmapImage> oluşturun ve bit eşlem içeriğini yüklemek için kullanın. Ardından, <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliğini ayarlamakiçinöğesinikullanın.<xref:System.Windows.Media.ImageBrush> Son olarak, öğesini <xref:System.Windows.Media.ImageBrush> boyamak istediğiniz nesneye uygulayın.  ' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]De, <xref:System.Windows.Media.ImageBrush.ImageSource%2A> öğesinin<xref:System.Windows.Media.ImageBrush> özelliğini yüklemek için görüntünün yoluyla da ayarlayabilirsiniz.  
  
 Tüm <xref:System.Windows.Media.Brush> nesneler gibi <xref:System.Windows.Media.ImageBrush> , şekil, panel, denetim ve metin gibi nesneleri boyamak için kullanılabilir. Aşağıdaki çizimde, ile <xref:System.Windows.Media.ImageBrush>elde edilebilir bazı etkiler gösterilmektedir.  
  
 ![ImageBrush çıkış örnekleri](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush tarafından boyanan nesneler  
  
 Varsayılan olarak, <xref:System.Windows.Media.ImageBrush> boyanmış alanı tamamen doldurmak için görüntüsünü uzatır, boyanmış alanın görüntüye göre farklı bir en boy oranı varsa görüntüyü deforme edin. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği varsayılan <xref:System.Windows.Media.Stretch.None> <xref:System.Windows.Media.Stretch.Fill> değerinden, veya<xref:System.Windows.Media.Stretch.Uniform>değerine değiştirerek bu davranışıdeğiştirebilirsiniz.<xref:System.Windows.Media.Stretch.UniformToFill> ,Bir<xref:System.Windows.Media.TileBrush>türü olduğundan, tam olarak bir görüntü fırçasının çıkış alanını nasıl doldurduğunu ve hatta desenler oluşturduğunu belirtebilirsiniz. <xref:System.Windows.Media.ImageBrush> Gelişmiş <xref:System.Windows.Media.TileBrush> özellikler hakkında daha fazla bilgi için bkz. [TileBrush 'e genel bakış](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Örnek: Bit eşlem resmi ile nesne boyama  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Panel.Background%2A> ' a <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Controls.Canvas>boyamak için bir kullanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Çizim ile bir Alanı Boyama  
 Bir <xref:System.Windows.Media.DrawingBrush> alanı şekil, metin, resim ve video ile boyamanıza olanak sağlar. Çizim fırçasının içindeki şekillerin kendisi düz renk, gradyan, resim ve hatta başka <xref:System.Windows.Media.DrawingBrush>bir renkle boyanmaya başlayabilir. Aşağıdaki çizimde bazı bir <xref:System.Windows.Media.DrawingBrush>kullanımları gösterilmektedir.  
  
 ![DrawingBrush çıkış örnekleri](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush tarafından boyanan nesneler  
  
 Bir <xref:System.Windows.Media.DrawingBrush> nesne<xref:System.Windows.Media.Drawing> ile bir alanı boyar. Bir <xref:System.Windows.Media.Drawing> nesne, şekil, bit eşlem, video veya metin satırı gibi görünür içerikleri açıklar. Farklı türdeki çizimler farklı içerik türlerini anlatmaktadır. Aşağıda, çizim nesnelerinin farklı türlerinin bir listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>– Bir resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing>– Bir ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup>– Diğer çizimleri çizer. Diğer çizimleri tek bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 Nesneler hakkında <xref:System.Windows.Media.Drawing> daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
 Tıpkı bir <xref:System.Windows.Media.ImageBrush>gibi, <xref:System.Windows.Media.DrawingBrush> çıkış alanını <xref:System.Windows.Media.DrawingBrush.Drawing%2A> doldurmak için bir uzatılır. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği varsayılan<xref:System.Windows.Media.Stretch.Fill>ayarından değiştirerek bu davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için bkz <xref:System.Windows.Media.TileBrush.Stretch%2A> . özelliği.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Örnek: Çizim ile nesne boyama  
 Aşağıdaki örnek, üç elips çizimi ile bir nesnenin nasıl boyanacağını gösterir. Bir <xref:System.Windows.Media.GeometryDrawing> , üç noktayı anlatmak için kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Görsel ile bir Alanı Boyama  
 Tüm fırçaların en çok yönlü ve güçlü olması, <xref:System.Windows.Media.VisualBrush> ile bir <xref:System.Windows.Media.Visual>alanı boyar. <xref:System.Windows.Media.Visual> , Çok sayıda faydalı grafik bileşeninin üst öğesi görevi gören alt düzey bir grafik türüdür. Örneğin <xref:System.Windows.Window> <xref:System.Windows.Media.Visual> ,, ve<xref:System.Windows.Controls.Control> sınıfları tüm nesne türlerdir. <xref:System.Windows.FrameworkElement> Bir <xref:System.Windows.Media.VisualBrush>kullanarak, neredeyse tüm [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik nesneleri ile alan boyayabilirsiniz.  
  
> [!NOTE]
> Bir <xref:System.Windows.Media.VisualBrush> nesne<xref:System.Windows.Freezable> türü olsa da, <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği dışında `null`bir değere ayarlandığında dondurulamıyor (salt okunurdur).  
  
 <xref:System.Windows.Media.VisualBrush.Visual%2A> İçeriğini belirtmekiçin<xref:System.Windows.Media.VisualBrush>iki yol vardır.  
  
- Yeni <xref:System.Windows.Media.Visual> bir oluşturun ve <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliğini <xref:System.Windows.Media.VisualBrush>ayarlamak için kullanın. Örnek için bkz [. örnek: Aşağıdaki görsel](#examplevisualbrush1) bölüm ile bir nesneyi boyayın.  
  
- <xref:System.Windows.Media.Visual> Hedefin<xref:System.Windows.Media.Visual>yinelenen bir görüntüsünü oluşturan var olanı kullanın. Daha sonra, <xref:System.Windows.Media.VisualBrush> yansıma ve büyütme gibi ilginç etkileri oluşturmak için kullanabilirsiniz. Örnek için bkz [. örnek: Yansıma](#examplevisualbrush2) bölümü oluşturun.  
  
 <xref:System.Windows.Media.VisualBrush.Visual%2A> Bir <xref:System.Windows.UIElement> <xref:System.Windows.UIElement> `true`için yeni bir tanımlar (örneğin <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> , bir panel veya denetim),, özelliği olarak ayarlandığında düzen sistemi ve onun alt öğeleri üzerinde çalışır. <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.VisualBrush> Bununla birlikte, kök <xref:System.Windows.UIElement> aslında sistemin geri kalanından yalıtılmıştır: stiller ve dış düzen bu sınırı geçemez. Bu nedenle, yalnızca üst öğesi olduğu ve bu nedenle kendisini <xref:System.Windows.UIElement>boyanmış alana otomatik olarak boyutlandıramadığı için <xref:System.Windows.Media.VisualBrush> kök boyutunu açıkça belirtmeniz gerekir. İçindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]düzen hakkında daha fazla bilgi için, bkz. [Düzen](../advanced/layout.md).  
  
 Ve <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.VisualBrush> gibi, bir, kendi içeriğini, çıkış alanını dolduracak şekilde uzatır. <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği varsayılan<xref:System.Windows.Media.Stretch.Fill>ayarından değiştirerek bu davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için bkz <xref:System.Windows.Media.TileBrush.Stretch%2A> . özelliği.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Örnek: Görsel ile nesne boyama  
 Aşağıdaki örnekte, bir dikdörtgeni boyamak için birkaç denetim ve panel kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Örnek: Yansıma Oluşturma  
 Yukarıdaki örnekte, bir arka plan olarak kullanım için <xref:System.Windows.Media.Visual> yeni bir oluşturma yöntemi gösterildi. Ayrıca, var olan görseli <xref:System.Windows.Media.VisualBrush> göstermek için de kullanabilirsiniz; Bu özellik, yansıma ve büyütme gibi ilginç görsel etkiler üretmenizi sağlar. Aşağıdaki örnek, birkaç öğesi <xref:System.Windows.Media.VisualBrush> içeren bir <xref:System.Windows.Controls.Border> yansıması oluşturmak için bir kullanır. Aşağıdaki çizim, bu örneğin oluşturduğu çıktıyı gösterir.  
  
 ![Yansıtılan bir görsel nesne](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Yansıtılan bir görsel nesne  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Ekranın bölümlerini büyütme ve yansıma oluşturma işlemlerinin nasıl yapılacağını gösteren ek örnekler için, [VisualBrush örneğine](https://go.microsoft.com/fwlink/?LinkID=160049)bakın.  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush Özellikleri  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.TileBrush> ve <xref:System.Windows.Media.VisualBrush> , nesne türleridir. <xref:System.Windows.Media.TileBrush>nesneler, bir alanın görüntü, çizim veya görsel ile nasıl boyandığı hakkında harika bir denetim sağlar. Örneğin, yalnızca tek bir uzatılmış görüntüyle bir alanı boyamak yerine, bir model oluşturan bir dizi görüntü kutucuğa sahip bir alanı boyayabilirsiniz.  
  
 A <xref:System.Windows.Media.TileBrush> 'nın üç birincil bileşeni vardır: içerik, kutucuk ve çıktı alanı.  
  
 ![TileBrush bileşenleri](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Tek bir kutucuğa sahip bir TileBrush bileşenleri  
  
 ![Döşeli bir TileBrush bileşenleri](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Birden çok kutucuk içeren bir TileBrush bileşenleri  
  
 <xref:System.Windows.Media.TileBrush> Nesnelerin döşeme özellikleri hakkında daha fazla bilgi için bkz. [TileBrush 'e genel bakış](tilebrush-overview.md).  
  
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
- [ImageBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160049)
