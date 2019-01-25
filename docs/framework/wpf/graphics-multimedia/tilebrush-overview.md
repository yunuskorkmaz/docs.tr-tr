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
ms.openlocfilehash: 9058c6c3256efad15e0811fcc1f21f440e13edbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683027"
---
# <a name="tilebrush-overview"></a>TileBrush Genel Bakışı
<xref:System.Windows.Media.TileBrush> nesneleri sağlar, önemli bir görüntü ile bir alanı nasıl boyanacağını denetim <xref:System.Windows.Media.Drawing>, veya <xref:System.Windows.Media.Visual>. Bu konu nasıl kullanılacağını açıklar <xref:System.Windows.Media.TileBrush> özellikleri nasıl üzerinde daha fazla denetim kazanmak için bir <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.VisualBrush> alanı boyar.  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için ' ın temel özelliklerinin nasıl kullanılacağını anlamak faydalıdır <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.VisualBrush> sınıfı. Bu tür bir giriş için bkz [görüntüler, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>Kutucuklar ile bir alanı boyama  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, olan <xref:System.Windows.Media.VisualBrush> türleridir <xref:System.Windows.Media.TileBrush> nesneleri. Kutucuk Fırçalar, bir görüntü, çizim veya görsel ile bir alanı nasıl boyanacağını denetim harika bir fırsat sağlar. Örneğin, yalnızca tek bir esnetilen görüntü ile bir alanı boyama yerine, bir dizi deseni oluşturan resim kutucukları ile bir alanı boyama.  
  
 Döşeme fırçası ile bir alanı boyama üç bileşeni içerir: içeriği, taban döşemesi ve çıkış alanı.  
  
 ![TileBrush bileşenleri](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
TileBrush ile tek bir kutucuk bileşenleri  
  
 ![Döşenmiş TileBrush bileşenlerinin](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
TileBrush ile döşeme TileMode'u bileşenleri  
  
 Çıkış alanı, gibi boyanan alandır <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Ellipse> veya <xref:System.Windows.Controls.Control.Background%2A> , bir <xref:System.Windows.Controls.Button>. Diğer iki bileşenden sonraki bölümlerde bir <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>İçerik fırça  
 Üç farklı türde vardır <xref:System.Windows.Media.TileBrush> her farklı bir içerik türüyle boyar.  
  
-   Fırça ise bir <xref:System.Windows.Media.ImageBrush>, bu içeriği bir görüntüsüdür <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özellik belirtir içeriğini <xref:System.Windows.Media.ImageBrush>.  
  
-   Fırça ise bir <xref:System.Windows.Media.DrawingBrush>, çizim bu içeriktir. <xref:System.Windows.Media.DrawingBrush.Drawing%2A> Özellik belirtir içeriğini <xref:System.Windows.Media.DrawingBrush>.  
  
-   Fırça ise bir <xref:System.Windows.Media.VisualBrush>, bir görseli bu içeriktir. <xref:System.Windows.Media.VisualBrush.Visual%2A> Özellik belirtir içeriğini <xref:System.Windows.Media.VisualBrush>.  
  
 Konum ve boyut sayısını belirtebilirsiniz <xref:System.Windows.Media.TileBrush> kullanarak içerik <xref:System.Windows.Media.TileBrush.Viewbox%2A> özelliği bırakmak yaygın olsa <xref:System.Windows.Media.TileBrush.Viewbox%2A> varsayılan değerine ayarlayın. Varsayılan olarak, <xref:System.Windows.Media.TileBrush.Viewbox%2A> fırçanın içeriği tamamen içerecek şekilde yapılandırılmıştır. Yapılandırma hakkında daha fazla bilgi için <xref:System.Windows.Controls.Viewbox>, bkz: <xref:System.Windows.Controls.Viewbox> özellik sayfası.  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>Taban döşemesi  
 A <xref:System.Windows.Media.TileBrush> taban döşemesi içeriği. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özellik denetimleri nasıl <xref:System.Windows.Media.TileBrush> , içeriği esnetilmiş taban döşemesi doldurmak için. <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği tarafından tanımlanan aşağıdaki değerleri kabul eder <xref:System.Windows.Media.Stretch> sabit listesi:  
  
-   <xref:System.Windows.Media.Stretch.None>: Fırçanın içeriği kutucuğu dolduracak şekilde genişletilir değil.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Fırçanın içeriği kutucuğu sığacak şekilde ölçeklendirilir. İçeriğin yükseklik ve genişlik bağımsız olarak ölçeklendirilir çünkü içerik özgün en boy oranını korunmayabilir. Diğer bir deyişle, fırçanın içeriği tamamen çıkış kutucuk doldurmak için karışmış olabilir.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Fırçanın içeriği tamamen döşeme sığacak şekilde ölçeklendirilir. İçeriğin en boy oranı korunur.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Fırçanın içeriği, içeriğin özgün en boy oranını koruyarak tamamen çıkış alanı dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki görüntüde farklı gösterir <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarları.  
  
 ![TileBrush Esnetme ayarları farklı](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 Aşağıdaki örnekte, içeriği bir <xref:System.Windows.Media.ImageBrush> çıkış alanı dolduracak şekilde genişlemez şekilde ayarlanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.TileBrush> tek bir kutucuk (taban döşemesi) oluşturur ve bu döşeme tamamen çıkış alanı dolduracak şekilde uzatılır. Taban döşemesi konumunu ve boyutunu ayarlayarak değiştirebilirsiniz <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri.  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>Taban döşemesi boyutu  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliği, taban döşemesi, konumunu ve boyutunu belirler ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliği olup olmadığını <xref:System.Windows.Media.TileBrush.Viewport%2A> mutlak veya göreli koordinatları kullanarak belirtilir. Göreli koordinatları, çıkış alanı boyutunu göreli oldukları. Noktası (0,0) temsil sol üst köşesindeki köşe çıktı alanının yanı sıra, (1,1) temsil alt çıktı alanının sağ alt köşesinde. Belirtmek için <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliği mutlak koordinat kullanan, Ayarla <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliğini <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
 Çıkış fark aşağıdaki çizimde bir <xref:System.Windows.Media.TileBrush> ile göreli ve mutlak <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>. Çizimler her döşenmiş bir desen Göster dikkat edin. sonraki bölümde, kutucuk düzenini belirtmek açıklar.  
  
 ![Mutlak ve göreli Görünüm penceresi birim](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 Aşağıdaki örnekte, bir görüntü genişliği ve yüksekliği % 50 olan bir kutucuğu oluşturmak için kullanılır. Taban döşemesi (0,0) bulunduğu çıkış alanı.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 Sonraki örnekte kutucuklarında ayarlar bir <xref:System.Windows.Media.ImageBrush> 25'e 25 cihaz bağımsız piksel. Çünkü <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> mutlaktır <xref:System.Windows.Media.ImageBrush> kutucukları her zaman boyanan alanın boyutu ne olursa olsun, 25'e 25 piksel.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>Döşeme davranışı  
 A <xref:System.Windows.Media.TileBrush> taban döşemesi, çıkış alanı ve başka bir döşeme modu tamamen dolmaması olduğunda döşenmiş bir desen oluşturur <xref:System.Windows.Media.TileMode.None> belirtilir. Bir kutucuğu fırçanın kutucuk çıkış alanı tamamen dolmaması olduğunda kendi <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği, taban döşemesi çıkış alanı dolduracak şekilde çoğaltılacak ve bu durumda, temel döşemenin nasıl çoğaltılacak olup olmadığını belirtir. <xref:System.Windows.Media.TileBrush.TileMode%2A> Özelliği tarafından tanımlanan aşağıdaki değerleri kabul eder <xref:System.Windows.Media.TileMode> sabit listesi:  
  
-   <xref:System.Windows.Media.TileMode.None>: Yalnızca temel döşeme çizilir.  
  
-   <xref:System.Windows.Media.TileMode.Tile>: Taban döşemesi çizilmiş ve kalan alan bir kutucuğun sağ kenarı sol kenarına sonraki ve bitişik olacak şekilde taban döşemesi benzer şekilde alt ve üst için yinelenen tarafından doldurulur.  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: Aynı <xref:System.Windows.Media.TileMode.Tile>, ancak diğer sütunların döşemeleri yatay olarak çevrilmiştir.  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: Aynı <xref:System.Windows.Media.TileMode.Tile>, ancak diğer satırları kutucuk dikey olarak çevrilmiştir.  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: Bir birleşimi <xref:System.Windows.Media.TileMode.FlipX> ve <xref:System.Windows.Media.TileMode.FlipY>.  
  
 Aşağıdaki görüntüde, farklı döşeme modlarını gösterir.  
  
 ![Farklı TileBrush TileMode ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 Aşağıdaki örnekte, bir görüntü 100 piksel genişliğinde ve 100 piksel yüksekliktir bir dikdörtgen boyamak için kullanılır. Fırçanın ayarlayarak <xref:System.Windows.Media.TileBrush.Viewport%2A> ayarlandı u 0,0,0.25,0.25'a, 1/4 çıktı alanının fırçanın taban döşemesi yapılır. Fırçanın <xref:System.Windows.Media.TileBrush.TileMode%2A> ayarlanır <xref:System.Windows.Media.TileMode.FlipXY>. Böylece kutucukları satırlarla dikdörtgen doldurur.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)
- [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [ImageBrush Örneği](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush örneği](https://go.microsoft.com/fwlink/?LinkID=160049)
