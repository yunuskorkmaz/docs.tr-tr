---
title: TileBrush Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: ac247a9caa54c40a31e3c78ba8537d60a333feb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="tilebrush-overview"></a>TileBrush Genel Bakışı
<xref:System.Windows.Media.TileBrush> nesneleri sağlar, çok yüksek bir alanı bir görüntü ile nasıl boyanır üzerinden denetiminin <xref:System.Windows.Media.Drawing>, veya <xref:System.Windows.Media.Visual>. Bu konuda nasıl kullanılacağını açıklar <xref:System.Windows.Media.TileBrush> özellikleri nasıl üzerinde daha fazla denetim kazanmak için bir <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.VisualBrush> bir alanı boyar.  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için bu temel özelliklerini kullanmayı öğrenmek yararlıdır <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.VisualBrush> sınıfı. Bu tür giriş için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Bir alanı döşeme ile Boyama  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, olan <xref:System.Windows.Media.VisualBrush> türleridir <xref:System.Windows.Media.TileBrush> nesneleri. Döşeme fırçaları, önemli bir alanı bir görüntü, çizim veya visual nasıl boyanır üzerinde denetim sağlar. Örneğin, yalnızca tek bir esnetilen görüntü sahip bir alan boyama yerine, bir dizi deseni oluşturan görüntü döşeme sahip bir alan boyama yapabilirsiniz.  
  
 Döşeme fırça sahip bir alan boyama üç bileşenleri içerir: içerik, temel döşeme ve çıktı alanı.  
  
 ![TileBrush bileşenleri](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Tek bir döşeme TileBrush bileşenleri  
  
 ![Döşeli TileBrush bileşenleri](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Döşemenin TileMode'u TileBrush bileşenleri  
  
 Çıkış alanı, gibi boyandığında alandır <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Ellipse> veya <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button>. Diğer iki bileşenden sonraki bölümlerde bir <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>İçerik fırça  
 Üç farklı türde vardır <xref:System.Windows.Media.TileBrush> ve her farklı bir içerik türüyle boyar.  
  
-   Fırça ise bir <xref:System.Windows.Media.ImageBrush>, bu içerik resimdir <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özellik belirtir içeriğini <xref:System.Windows.Media.ImageBrush>.  
  
-   Fırça ise bir <xref:System.Windows.Media.DrawingBrush>, çizim bu içeriktir. <xref:System.Windows.Media.DrawingBrush.Drawing%2A> Özellik belirtir içeriğini <xref:System.Windows.Media.DrawingBrush>.  
  
-   Fırça ise bir <xref:System.Windows.Media.VisualBrush>, bir görsel bu içeriktir. <xref:System.Windows.Media.VisualBrush.Visual%2A> Özellik belirtir içeriğini <xref:System.Windows.Media.VisualBrush>.  
  
 Konum ve boyutlarının belirtebilirsiniz <xref:System.Windows.Media.TileBrush> kullanarak içerik <xref:System.Windows.Media.TileBrush.Viewbox%2A> özelliği, bırakmak yaygın olsa <xref:System.Windows.Media.TileBrush.Viewbox%2A> varsayılan olarak ayarlı. Varsayılan olarak, <xref:System.Windows.Media.TileBrush.Viewbox%2A> tamamen fırça içeriği içerecek şekilde yapılandırılır. Yapılandırma hakkında daha fazla bilgi için <xref:System.Windows.Controls.Viewbox>, bkz: <xref:System.Windows.Controls.Viewbox> özellik sayfası.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>Temel döşeme  
 A <xref:System.Windows.Media.TileBrush> içeriğini temel döşemesi. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özellik denetimleri nasıl <xref:System.Windows.Media.TileBrush> temel döşemeyi doldurmak için içerik uzatılabilir. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği tarafından tanımlanan aşağıdaki değerleri kabul eder <xref:System.Windows.Media.Stretch> numaralandırma:  
  
-   <xref:System.Windows.Media.Stretch.None>: Fırça içeriği döşeme dolduracak şekilde genişletilir değil.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Fırça içeriği döşemeye uyacak şekilde ölçeklendirilir. İçeriğin yüksekliğini ve genişliğini bağımsız olarak ölçeklenir olduğundan, içeriği özgün en boy oranı korunmayabilir. Diğer bir deyişle, fırça içeriği çıkış döşemesini tamamen doldurmak için karışmış olabilir.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Fırça içeriği döşemenin içinde tamamen sığacak şekilde ölçeklendirilir. İçeriğin en boy oranını korunur.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Fırça içeriği, içeriğin özgün en boy oranını korurken tamamen çıkış alanı dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki resimde farklı gösterilmektedir <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarlar.  
  
 ![Farklı TileBrush Stretch ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 Aşağıdaki örnekte, içeriği bir <xref:System.Windows.Media.ImageBrush> çıktı alanını doldurmak için genişlemez şekilde ayarlanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.TileBrush> tek bir döşeme (temel döşeme) oluşturur ve bu döşeme tamamen çıkış alanı dolduracak şekilde uzatılır. Ayarlayarak boyutunu ve konumunu temel döşemenin değiştirebilirsiniz <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Temel döşeme boyutu  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliği, boyut ve temel döşeme konumunu belirler ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliği belirler olup olmadığını <xref:System.Windows.Media.TileBrush.Viewport%2A> mutlak veya göreli koordinatları kullanılarak belirtilir. Koordinatlar göreli ise, çıktı alanının boyutunu göreli oldukları. (0,0) noktası temsil üst çıktı alanının sol köşe ve (1,1) temsil alt çıktı alanının sağ alt köşesinde. Belirtmek için <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliği kullanan mutlak koordinatları, Ayarla <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliğine <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Aşağıdaki çizimde çıktısı arasındaki farkı gösterilir bir <xref:System.Windows.Media.TileBrush> ile göreli ve mutlak <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Her çizimler döşeli düzeni Göster dikkat edin. sonraki bölümde döşeme deseni belirtin açıklar.  
  
 ![Mutlak ve göreli görünüm penceresinin Birim](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 Aşağıdaki örnekte, bir görüntü genişliği ve yüksekliği % 50 sahip bir bölme oluşturmak için kullanılır. Temel döşeme (0,0) bulunduğu çıktı alanının.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 Sonraki örnek kutucuklarında ayarlar bir <xref:System.Windows.Media.ImageBrush> 25'e 25 aygıt bağımsız piksel. Çünkü <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> mutlak olduğundan <xref:System.Windows.Media.ImageBrush> döşeme her zaman 25'e 25 piksel cinsinden boyandığında alanının boyutunu ne olursa olsun.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Döşeme davranışı  
 A <xref:System.Windows.Media.TileBrush> temel döşemesinin tamamen çıkış alanı ve başka bir döşeme modu değil doldurduğunuzda döşeli bir desen oluşturur <xref:System.Windows.Media.TileMode.None> belirtilir. Döşeme fırça döşeme tamamen çıktı alanını doldurduğunuzda değil, kendi <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği, temel döşeme çıktı alanını doldurmak için çoğaltılacak ve bu durumda, temel döşemenin nasıl çoğaltılacak olup olmadığını belirtir. <xref:System.Windows.Media.TileBrush.TileMode%2A> Özelliği tarafından tanımlanan aşağıdaki değerleri kabul eder <xref:System.Windows.Media.TileMode> numaralandırma:  
  
-   <xref:System.Windows.Media.TileMode.None>: Yalnızca temel döşeme çizilir.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: Temel döşeme çizilir ve kalan alan bir kutucuğu sağ kenarı sol ucuna sonraki ve olacak şekilde, temel döşeme benzer şekilde alt ve üst için yinelenmesiyle doldurulur.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: Aynı <xref:System.Windows.Media.TileMode.Tile>, ancak diğer sütunların döşemeleri yatay olarak çevrilmiştir.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: Aynı <xref:System.Windows.Media.TileMode.Tile>, ancak diğer satırların döşemeleri dikey olarak çevrilmiştir.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Bir birleşimini <xref:System.Windows.Media.TileMode.FlipX> ve <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Aşağıdaki resim farklı döşeme modlarını gösterir.  
  
 ![Farklı TileBrush TileMode ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 Aşağıdaki örnekte, bir görüntü 100 piksel genişliğinde ve 100 piksel uzunluğunda bir dikdörtgen boyamak için kullanılır. Fırça ayarlayarak <xref:System.Windows.Media.TileBrush.Viewport%2A> ayarlanmış u 0,0,0.25,0.25'a, fırça temel döşeme 1/4 çıktı alanının yapılmıştır. Fırça <xref:System.Windows.Media.TileBrush.TileMode%2A> ayarlanır <xref:System.Windows.Media.TileMode.FlipXY>. Böylece dikdörtgen döşeme satırlarla doldurur.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [ImageBrush Örneği](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160049)
