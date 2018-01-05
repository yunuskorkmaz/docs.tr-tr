---
title: "Görüntüler, Çizimler ve Görsellerle Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01939eb8735e6764e0f0cba811091c7fdbd6797f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="painting-with-images-drawings-and-visuals"></a>Görüntüler, Çizimler ve Görsellerle Boyama
Bu konuda nasıl kullanılacağını açıklar <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ve <xref:System.Windows.Media.VisualBrush> bir alanı bir görüntü ile boyamak için nesneleri bir <xref:System.Windows.Media.Drawing>, veya bir <xref:System.Windows.Media.Visual>.  
    
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için farklı türden fırçalar tanımanız gerekir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar ve bunların temel özellikleri. Giriş için bkz [WPF Fırçaları Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Görüntü ile bir Alanı Boyama  
 Bir <xref:System.Windows.Media.ImageBrush> sahip bir alan boyar bir <xref:System.Windows.Media.ImageSource>. En yaygın türü <xref:System.Windows.Media.ImageSource> ile kullanılacak bir <xref:System.Windows.Media.ImageBrush> olan bir <xref:System.Windows.Media.Imaging.BitmapImage>, bit eşlem grafik açıklar. Kullanabileceğiniz bir <xref:System.Windows.Media.DrawingImage> kullanarak boyamak için bir <xref:System.Windows.Media.Drawing> nesnesi, ancak kullanmak basit bir <xref:System.Windows.Media.DrawingBrush> yerine. Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageSource> nesneleri bkz [Imaging genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
 İle boyamak için bir <xref:System.Windows.Media.ImageBrush>, oluşturma bir <xref:System.Windows.Media.Imaging.BitmapImage> ve bit eşlem içeriğini yüklemek için kullanın. Ardından, <xref:System.Windows.Media.Imaging.BitmapImage> ayarlamak için <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği <xref:System.Windows.Media.ImageBrush>. Son olarak, uygulama <xref:System.Windows.Media.ImageBrush> boyamak istediğiniz nesneye.  İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], aynı zamanda yalnızca ayarlayabilirsiniz <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği <xref:System.Windows.Media.ImageBrush> yüklenecek resmin yolu ile.  
  
 Tüm <xref:System.Windows.Media.Brush> nesneleri, bir <xref:System.Windows.Media.ImageBrush> şekiller, paneller, denetimleri ve metin gibi nesneleri boyamak için kullanılabilir. Aşağıdaki çizimde ile elde bazı efektleri gösterir bir <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush çıktı örnekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush tarafından boyandığında nesneleri  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.ImageBrush> uzatır tamamen alanı dolduracak şekilde görüntüsünü boyandığında, görüntünün daha farklı bir en boy oranı boyanmış alanının varsa, büyük olasılıkla resim bozulur. Değiştirerek bu davranışı değiştirebilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> varsayılan değerine özelliğinden <xref:System.Windows.Media.Stretch.Fill> için <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, veya <xref:System.Windows.Media.Stretch.UniformToFill>. Çünkü <xref:System.Windows.Media.ImageBrush> bir tür <xref:System.Windows.Media.TileBrush>, tam olarak bir resim fırçası çıktı alanını nasıl doldurduğunu belirtin ve hatta desenleri oluşturabilirsiniz. Gelişmiş hakkında daha fazla bilgi için <xref:System.Windows.Media.TileBrush> özellikleri, bkz. [TileBrush genel bakış](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Örnek: bir bit eşlem görüntüsü olan bir nesne boyama  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.ImageBrush> boyamak için <xref:System.Windows.Controls.Panel.Background%2A> , bir <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Çizim ile bir Alanı Boyama  
 A <xref:System.Windows.Media.DrawingBrush> şekiller, metin, görüntüler ve video sahip bir alan boyama olanak tanır. Çizim Fırçası içindeki şekiller kendilerini boyayabilirler bir düz renk, gradyan, resim veya hatta başka bir <xref:System.Windows.Media.DrawingBrush>. Bazı kullanımları aşağıdaki çizimde gösterilmektedir bir <xref:System.Windows.Media.DrawingBrush>.  
  
 ![DrawingBrush çıktı örnekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush tarafından boyandığında nesneleri  
  
 A <xref:System.Windows.Media.DrawingBrush> sahip bir alan boyar bir <xref:System.Windows.Media.Drawing> nesnesi. A <xref:System.Windows.Media.Drawing> nesne gibi bir şekil, bit eşlem, görüntü veya metin satırının görünür içeriği açıklar. Farklı türde çizimler farklı içerik türlerini açıklar. Çizim nesneleri farklı türlerinin bir listesi verilmiştir.  
  
-   <xref:System.Windows.Media.GeometryDrawing>Şekil çizer.  
  
-   <xref:System.Windows.Media.ImageDrawing>Resim çizer.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>Metin çizer.  
  
-   <xref:System.Windows.Media.VideoDrawing>– Bir ses veya video dosyası çalar.  
  
-   <xref:System.Windows.Media.DrawingGroup>Diğer çizimleri çizer. Diğer tek bileşik çizim çizimlerini birleştirmek için bir çizim grubu kullanın.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
 Gibi bir <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> uzatır kendi <xref:System.Windows.Media.DrawingBrush.Drawing%2A> çıkış alanını doldurmak için. Değiştirerek bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> kendi varsayılan özelliğinden <xref:System.Windows.Media.Stretch.Fill>. Daha fazla bilgi için bkz: <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Örnek: bir nesneyi çizim ile Boyama  
 Aşağıdaki örnekte, üç elips çizim sahip bir nesne boyama gösterilmektedir. A <xref:System.Windows.Media.GeometryDrawing> elipsleri açıklamak için kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Görsel ile bir Alanı Boyama  
 En çok yönlü ve güçlü Fırçalar <xref:System.Windows.Media.VisualBrush> sahip bir alan boyar bir <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> birçok yararlı grafik bileşeninin üst hizmet veren bir alt düzey grafik türüdür. Örneğin, <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, ve <xref:System.Windows.Controls.Control> sınıflarıdır tüm türleri <xref:System.Windows.Media.Visual> nesneleri. Kullanarak bir <xref:System.Windows.Media.VisualBrush>, neredeyse tüm alanları boyamak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik nesnesi.  
  
> [!NOTE]
>  Ancak <xref:System.Windows.Media.VisualBrush> bir tür <xref:System.Windows.Freezable> nesne dondurulamaz (salt okunur olduğunda yapılan) kendi <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği ayarlanmış bir değere dışında `null`.  
  
 Belirtmek için iki yolla <xref:System.Windows.Media.VisualBrush.Visual%2A> içeriğini bir <xref:System.Windows.Media.VisualBrush>.  
  
-   Yeni bir <xref:System.Windows.Media.Visual> ve ayarlamak için kullanın <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği <xref:System.Windows.Media.VisualBrush>. Bir örnek için bkz: [örnek: bir nesneyi görsel ile Boyama](#examplevisualbrush1) sonraki bölümünde.  
  
-   Var olan kullanmak <xref:System.Windows.Media.Visual>, hedef yinelenen bir görüntüsünü oluşturan <xref:System.Windows.Media.Visual>. Daha sonra kullanabilirsiniz <xref:System.Windows.Media.VisualBrush> yansıma ve büyütme gibi ilginç etkiler oluşturmak için. Bir örnek için bkz: [örnek: bir yansıma oluşturma](#examplevisualbrush2) bölümü.  
  
 Yeni bir tanımladığınızda <xref:System.Windows.Media.VisualBrush.Visual%2A> için bir <xref:System.Windows.Media.VisualBrush> ve <xref:System.Windows.Media.Visual> olan bir <xref:System.Windows.UIElement> (panel veya denetim gibi), düzen sistemi üzerinde çalıştığı <xref:System.Windows.UIElement> ve kendi alt öğelerini zaman <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> özelliği ayarlanmış `true`. Ancak, kök <xref:System.Windows.UIElement> sistem geri kalanından temelde yalıtılır: stilleri ve dış düzeni bu sınır permeate olamaz. Bu nedenle, açıkça kök boyutunu belirtmelisiniz <xref:System.Windows.UIElement>, yalnızca üst olduğundan <xref:System.Windows.Media.VisualBrush> ve bu nedenle, otomatik olarak kendisini boyandığında alan boyutu olamaz. Düzende hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md).  
  
 Gibi <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> çıkış alanını doldurmak için kendi içeriğini uzatır. Değiştirerek bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> kendi varsayılan özelliğinden <xref:System.Windows.Media.Stretch.Fill>. Daha fazla bilgi için bkz: <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Örnek: bir nesneyi görsel ile Boyama  
 Aşağıdaki örnekte, birkaç denetimleri ve bir panel dikdörtgen boyamak için kullanılır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Örnek: bir yansıma oluşturma  
 Önceki örnekte gösterilen yeni bir oluşturma <xref:System.Windows.Media.Visual> arka plan olarak kullanılacak. Aynı zamanda bir <xref:System.Windows.Media.VisualBrush> ; varolan görseli görüntülemek için yansıma ve büyütme gibi ilginç görsel efektler üretmek bu özelliği sağlar. Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.VisualBrush> yansımasını oluşturmak için bir <xref:System.Windows.Controls.Border> çeşitli öğeleri içerir. Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.  
  
 ![Bir görsel nesne yansıtılan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Yansıtılan Visual nesnesi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Ekran bölümlerinin nasıl ve yansımaların nasıl oluşturulacağını gösteren ek örnekler için bkz: [büyütüleceğini](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush Özellikleri  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ve <xref:System.Windows.Media.VisualBrush> türleridir <xref:System.Windows.Media.TileBrush> nesneleri. <xref:System.Windows.Media.TileBrush>nesneleri, çok yüksek bir alanı bir görüntü, çizim veya visual nasıl boyanır üzerinde denetim sağlar. Örneğin, yalnızca tek bir esnetilen görüntü sahip bir alan boyama yerine, bir dizi deseni oluşturan görüntü döşeme sahip bir alan boyama yapabilirsiniz.  
  
 A <xref:System.Windows.Media.TileBrush> üç birincil bileşenden oluşur: içerik, döşeme ve çıktı alanı.  
  
 ![TileBrush bileşenleri](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Tek bir döşeme TileBrush bileşenleri  
  
 ![Döşeli TileBrush bileşenleri](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Birden çok döşeme ile TileBrush bileşenleri  
  
 Döşeme özellikleri hakkında daha fazla bilgi için <xref:System.Windows.Media.TileBrush> nesneleri bkz [TileBrush genel bakış](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [TileBrush’a Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [WPF Fırçalarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)  
 [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Opaklık Maskelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [ImageBrush Örneği](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160049)
