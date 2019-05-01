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
ms.openlocfilehash: 826c5a0656a9a7e7cff0e96fc6755c5c9c717993
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002293"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Görüntüler, Çizimler ve Görsellerle Boyama
Bu konu nasıl kullanılacağını açıklar <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ve <xref:System.Windows.Media.VisualBrush> bir görüntü ile bir alanı boyama nesnelere bir <xref:System.Windows.Media.Drawing>, veya bir <xref:System.Windows.Media.Visual>.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için farklı türde fırçalar ile ilgili bilgi sahibi olmalısınız [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar ve temel özelliklerine. Bir giriş için bkz [WPF fırçalarına genel bakış](wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Görüntü ile bir Alanı Boyama  
 Bir <xref:System.Windows.Media.ImageBrush> ile bir alanı boyar bir <xref:System.Windows.Media.ImageSource>. En yaygın türü <xref:System.Windows.Media.ImageSource> ile kullanılacak bir <xref:System.Windows.Media.ImageBrush> olduğu bir <xref:System.Windows.Media.Imaging.BitmapImage>, bit eşlem grafik açıklar. Kullanabileceğiniz bir <xref:System.Windows.Media.DrawingImage> kullanarak boyamak için bir <xref:System.Windows.Media.Drawing> kullanılacak nesne, ancak daha basittir bir <xref:System.Windows.Media.DrawingBrush> yerine. Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageSource> nesneleri bkz [Imaging genel bakış](imaging-overview.md).  
  
 İle boyama için bir <xref:System.Windows.Media.ImageBrush>, oluşturun bir <xref:System.Windows.Media.Imaging.BitmapImage> ve bit eşlem içeriği yüklemek için kullanın. Ardından, <xref:System.Windows.Media.Imaging.BitmapImage> ayarlanacak <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği <xref:System.Windows.Media.ImageBrush>. Son olarak, uygulama <xref:System.Windows.Media.ImageBrush> istediğiniz boyamak için nesne.  İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], yalnızca ayarlayabilirsiniz <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği <xref:System.Windows.Media.ImageBrush> yüklemek için görüntünün yola sahip.  
  
 Tüm <xref:System.Windows.Media.Brush> nesneleri bir <xref:System.Windows.Media.ImageBrush> şekiller, paneller, denetimlerini ve metin gibi nesneleri boyamak için kullanılabilir. İle gerçekleştirilebilir bazı efektler aşağıdaki çizimde bir <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush çıkış örnekler](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush tarafından boyanan nesneleri  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.ImageBrush> uzatır tamamen alanı dolduracak şekilde görüntüsünü planı boyanmadan, görüntünün boyanan alanı resimden farklı bir en boy oranını varsa büyük olasılıkla bozulur. Değiştirerek bu davranışı değiştirebilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği varsayılan değerine <xref:System.Windows.Media.Stretch.Fill> için <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, veya <xref:System.Windows.Media.Stretch.UniformToFill>. Çünkü <xref:System.Windows.Media.ImageBrush> bir tür <xref:System.Windows.Media.TileBrush>, tam olarak bir resim fırçası çıkış alanı nasıl doldurduğunu belirtin ve hatta desenleri oluşturabilirsiniz. Gelişmiş hakkında daha fazla bilgi için <xref:System.Windows.Media.TileBrush> özellikler bkz [TileBrush'a Genel Bakış](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Örnek: Bit eşlem görüntüsüne sahip bir nesne boyama  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.ImageBrush> boyanacak <xref:System.Windows.Controls.Panel.Background%2A> , bir <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Çizim ile bir Alanı Boyama  
 A <xref:System.Windows.Media.DrawingBrush> şekiller, metin, görüntü ve video ile bir alanı boyama sağlar. Şekilleri iç çizim Fırçası kendilerini boyanan bir düz renk, gradyan, görüntü, veya hatta başka bir <xref:System.Windows.Media.DrawingBrush>. Aşağıda bazı kullanımlarını gösterir bir <xref:System.Windows.Media.DrawingBrush>.  
  
 ![DrawingBrush'ın örnek çıktı](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush tarafından boyanan nesneleri  
  
 A <xref:System.Windows.Media.DrawingBrush> ile bir alanı boyar bir <xref:System.Windows.Media.Drawing> nesne. A <xref:System.Windows.Media.Drawing> nesne gibi bir şekil, bit eşlem, görüntü veya metin satırı görünür içeriği açıklar. Farklı türde çizimler içeriği farklı türleri açıklanmaktadır. Çizim nesneleri farklı türlerinin bir listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing> Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing> Resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> Metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing> – Bir ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup> Diğer çizimler çizer. Çizim grubu, tek bir bileşik çizim diğer çizimlerini birleştirmek için kullanın.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
 Gibi bir <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> uzatır kendi <xref:System.Windows.Media.DrawingBrush.Drawing%2A> , çıkış alanı dolduracak şekilde. Değiştirerek bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> kendi varsayılan özelliğinden <xref:System.Windows.Media.Stretch.Fill>. Daha fazla bilgi için <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Örnek: Çizim ile bir nesne boyama  
 Aşağıdaki örnek, üç elips çizim ile bir nesne boyama gösterilmektedir. A <xref:System.Windows.Media.GeometryDrawing> üç noktayı tanımlamak için kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Görsel ile bir Alanı Boyama  
 En verimli ve güçlü Fırçalar <xref:System.Windows.Media.VisualBrush> ile bir alanı boyar bir <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> birçok faydalı grafik bileşen üst öğe hizmet veren düşük düzeyli bir grafik türü. Örneğin, <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.Controls.Control> sınıfları olmak üzere tüm tür <xref:System.Windows.Media.Visual> nesneleri. Kullanarak bir <xref:System.Windows.Media.VisualBrush>, neredeyse tüm alanları boyama yapabileceğiniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik nesnesi.  
  
> [!NOTE]
>  Ancak <xref:System.Windows.Media.VisualBrush> bir tür <xref:System.Windows.Freezable> nesne olamaz dondurulmuş (salt okunur oluşturulmasıyla) kendi <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği ayarlanmış bir değere dışında `null`.  
  
 Belirtmek için iki yolla <xref:System.Windows.Media.VisualBrush.Visual%2A> içeriğini bir <xref:System.Windows.Media.VisualBrush>.  
  
- Yeni bir <xref:System.Windows.Media.Visual> ve ayarlamak için kullanın <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği <xref:System.Windows.Media.VisualBrush>. Bir örnek için bkz [örneği: Görsel içeren bir nesne boyama](#examplevisualbrush1) aşağıdaki bölümü.  
  
- Mevcut bir kullanın <xref:System.Windows.Media.Visual>, yinelenen bir hedef görüntüsü oluşturur <xref:System.Windows.Media.Visual>. Ardından <xref:System.Windows.Media.VisualBrush> yansıma ve büyütme gibi ilginç etkiler oluşturmak için. Bir örnek için bkz [örneği: Yansıma oluşturma](#examplevisualbrush2) bölümü.  
  
 Yeni bir tanımladığınızda <xref:System.Windows.Media.VisualBrush.Visual%2A> için bir <xref:System.Windows.Media.VisualBrush> ve <xref:System.Windows.Media.Visual> olduğu bir <xref:System.Windows.UIElement> (bir panel veya denetim gibi) düzen sistemi üzerinde çalıştığı <xref:System.Windows.UIElement> ve onun alt öğeleri, <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> özelliği `true`. Ancak, kök <xref:System.Windows.UIElement> aslında sistemin geri kalanından ayrı tutulur: stilleri ve dış düzeni bu sınır permeate olamaz. Bu nedenle açıkça kök boyutu belirtmelidir <xref:System.Windows.UIElement>, yalnızca üst olduğundan <xref:System.Windows.Media.VisualBrush> ve bu nedenle kendi boyanan bölgesine otomatik olarak boyutu olamaz. Düzeni hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bkz: [Düzen](../advanced/layout.md).  
  
 Gibi <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> içeriğini, çıkış alanı dolduracak şekilde uzatılır. Değiştirerek bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> kendi varsayılan özelliğinden <xref:System.Windows.Media.Stretch.Fill>. Daha fazla bilgi için <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Örnek: Nesnenin görsel ile Boyama  
 Aşağıdaki örnekte, çeşitli denetimler ve bir paneli, bir dikdörtgen boyamak için kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Örnek: Yansıma Oluşturma  
 Önceki örnekte gösterilen yeni bir oluşturma <xref:System.Windows.Media.Visual> için arka plan olarak kullanın. Ayrıca bir <xref:System.Windows.Media.VisualBrush> mevcut bir görselin; görüntülemek için bu özelliği, yansıma ve büyütme gibi ilgi çekici görsel efektler üretmek olanak tanır. Aşağıdaki örnekte bir <xref:System.Windows.Media.VisualBrush> yansımasını oluşturmak için bir <xref:System.Windows.Controls.Border> , çeşitli öğeleri içerir. Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.  
  
 ![Bir görsel nesne yansıtılan](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Yansıtılan bir görsel nesneyi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Ekran bölümlerinin ve Oluştur yansımaları ek örnekler için bkz: [büyütüldüğünü](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush Özellikleri  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ve <xref:System.Windows.Media.VisualBrush> türleridir <xref:System.Windows.Media.TileBrush> nesneleri. <xref:System.Windows.Media.TileBrush> nesneleri, bir görüntü, çizim veya görsel ile bir alanı nasıl boyanacağını denetim harika bir fırsat sağlar. Örneğin, yalnızca tek bir esnetilen görüntü ile bir alanı boyama yerine, bir dizi deseni oluşturan resim kutucukları ile bir alanı boyama.  
  
 A <xref:System.Windows.Media.TileBrush> üç birincil bileşenden oluşur: içeriği, kutucuklar ve çıkış alanı.  
  
 ![TileBrush bileşenleri](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
TileBrush ile tek bir kutucuk bileşenleri  
  
 ![Döşenmiş TileBrush bileşenlerinin](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
TileBrush ile birden çok kutucuk bileşenleri  
  
 Döşeme özellikleri hakkında daha fazla bilgi için <xref:System.Windows.Media.TileBrush> nesneleri bkz [TileBrush'a Genel Bakış](tilebrush-overview.md).  
  
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
- [ImageBrush Örneği](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160049)
