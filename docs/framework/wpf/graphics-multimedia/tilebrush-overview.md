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
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187106"
---
# <a name="tilebrush-overview"></a>TileBrush Genel Bakışı
<xref:System.Windows.Media.TileBrush>nesneler, bir alanın bir görüntüyle nasıl boyandığı üzerinde <xref:System.Windows.Media.Drawing>büyük <xref:System.Windows.Media.Visual>bir denetim sağlar, ya da. Bu konu, bir <xref:System.Windows.Media.TileBrush> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>alanın nasıl boyanacağı veya <xref:System.Windows.Media.VisualBrush> nasıl boyanacağı üzerinde daha fazla denetim elde etmek için özelliklerin nasıl kullanılacağını açıklar.  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, <xref:System.Windows.Media.ImageBrush>sınıfın <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> temel özelliklerini nasıl kullanacağımı anlamak yararlıdır. Bu tür bir giriş için, [Resim, Çizim ve Görseller ile Resim](painting-with-images-drawings-and-visuals.md)bakın.  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>Fayans larla Alan Boyama  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Media.TileBrush> nesne türleridir. Döşeme fırçaları, bir alanın görüntü, çizim veya görselle nasıl boyandığı üzerinde büyük bir denetim sağlar. Örneğin, bir alanı tek bir uzatılmış görüntüyle boyamak yerine, bir desen oluşturan bir dizi resim kutucadı ile bir alanı boyayabilirsiniz.  
  
 Bir alanı döşeme fırçasıyla boyamak üç bileşeniçerir: içerik, taban döşemeve çıkış alanı.  
  
 ![TileFırça bileşenleri](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Tek bir döşemeile Bir Kiremit Fırçabileşenleri  
  
 ![Karo Fayans Fırçasının Bileşenleri](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Fayans Lı Bir Kiremit Modu na sahip Bir Kiremit Fırçasının Bileşenleri  
  
 Çıkış <xref:System.Windows.Shapes.Shape.Fill%2A> alanı, bir veya <xref:System.Windows.Shapes.Ellipse> bir <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>. Sonraki bölümlerde bir <xref:System.Windows.Media.TileBrush>.  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>Fırça İçeriği  
 Üç farklı türü <xref:System.Windows.Media.TileBrush> vardır ve her bir farklı içerik türüne sahip boyalar.  
  
- Fırça ise, <xref:System.Windows.Media.ImageBrush>bu içerik bir görüntü <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği içeriğini <xref:System.Windows.Media.ImageBrush>belirtir.  
  
- Fırça bir <xref:System.Windows.Media.DrawingBrush>ise, bu içerik bir çizimdir. Özellik <xref:System.Windows.Media.DrawingBrush.Drawing%2A> içeriğini <xref:System.Windows.Media.DrawingBrush>belirtir.  
  
- Fırça ise, <xref:System.Windows.Media.VisualBrush>bu içerik görseldir. Özellik <xref:System.Windows.Media.VisualBrush.Visual%2A> içeriğini <xref:System.Windows.Media.VisualBrush>belirtir.  
  
 Kümeyi varsayılan değerine <xref:System.Windows.Media.TileBrush> bırakmak yaygın <xref:System.Windows.Media.TileBrush.Viewbox%2A> olsa da, özelliği kullanarak içeriğin konumunu ve boyutlarını belirtebilirsiniz. <xref:System.Windows.Media.TileBrush.Viewbox%2A> Varsayılan olarak, <xref:System.Windows.Media.TileBrush.Viewbox%2A> fırçanın içeriğini tamamen içerecek şekilde yapılandırılır. Yapılandırma <xref:System.Windows.Controls.Viewbox>hakkında daha fazla bilgi <xref:System.Windows.Controls.Viewbox> için özellik sayfasına bakın.  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>Taban Karosu  
 Bir <xref:System.Windows.Media.TileBrush> temel döşeme üzerine içeriğini projeleri. Özellik, <xref:System.Windows.Media.TileBrush.Stretch%2A> temel <xref:System.Windows.Media.TileBrush> döşemeyi doldurmak için içeriğin nasıl uzadığını denetler. Özellik, <xref:System.Windows.Media.TileBrush.Stretch%2A> numaralandırma ile <xref:System.Windows.Media.Stretch> tanımlanan aşağıdaki değerleri kabul eder:  
  
- <xref:System.Windows.Media.Stretch.None>: Fırçanın içeriği döşemeyi doldurmak için uzatılmış değildir.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Fırçanın içeriği kiremite uyacak şekilde ölçeklendirilir. İçeriğin yüksekliği ve genişliği bağımsız olarak ölçeklendirildiği için, içeriğin orijinal en boy oranı korunmayabilir. Diğer bir deyişle, çıktı döşemesini tamamen doldurmak için fırçanın içeriği çarpıtılabilir.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Fırçanın içeriği, döşemenin içine tamamen sığsın şekilde ölçeklendirilir. İçeriğin en boy oranı korunur.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Fırçanın içeriği, içeriğin orijinal en boy oranını korurken çıktı alanını tamamen dolduracak şekilde ölçeklendirilir.  
  
 Aşağıdaki resim farklı <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarları göstermektedir.  
  
 ![Farklı TileFırça Streç ayarları](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 Aşağıdaki örnekte, bir in <xref:System.Windows.Media.ImageBrush> içeriği çıktı alanını doldurmak için germemeyen şekilde ayarlanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Varsayılan olarak, <xref:System.Windows.Media.TileBrush> a tek bir döşeme (temel döşeme) oluşturur ve çıktı alanını tamamen doldurmak için bu döşemeyi uzatır. Temel döşemenin boyutunu ve konumunu <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliklerini ayarlayarak değiştirebilirsiniz.  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>Taban Karo Boyutu  
 Özellik <xref:System.Windows.Media.TileBrush.Viewport%2A> temel döşemenin boyutunu ve konumunu belirler ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellik mutlak <xref:System.Windows.Media.TileBrush.Viewport%2A> veya göreli koordinatlar kullanılarak belirtilip belirtilmediğini belirler. Koordinatlar göreceliyse, çıktı alanının boyutuna göredir. Nokta (0,0) çıkış alanının sol üst köşesini, (1,1) ise çıkış alanının sağ alt köşesini temsil eder. Özelliğin <xref:System.Windows.Media.TileBrush.Viewport%2A> mutlak koordinatlar kullandığını belirtmek <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> için <xref:System.Windows.Media.BrushMappingMode.Absolute>özelliği ' ye göre ayarlayın.  
  
 Aşağıdaki resimde, göreceli ile mutlak <xref:System.Windows.Media.TileBrush> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>olan bir arasındaki çıktı farkı gösterilmektedir. Çizimlerin her birinin karo desen gösterdiğine dikkat edin; sonraki bölümde döşeme deseni nasıl belirtilir açıklanır.  
  
 ![Mutlak ve Bağıl Görüntüleme Noktası Birimleri](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 Aşağıdaki örnekte, bir görüntü genişliği ve yüksekliği%50 olan bir döşeme oluşturmak için kullanılır. Taban döşemesi çıkış alanının (0,0) adresinde bulunur.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 Sonraki örnek, bir <xref:System.Windows.Media.ImageBrush> 25'e kadar olan aygıt bağımsız piksellerinin kutucuklarını ayarlar. Mutlak <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> olduğundan, <xref:System.Windows.Media.ImageBrush> karolar her zaman 25'e 25 pikseldir, çizilen alanın boyutuna bakılmaksızın.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>Döşeme Davranışı  
 A, <xref:System.Windows.Media.TileBrush> taban döşemesi çıkış alanını tamamen doldurmadığında ve sonra <xref:System.Windows.Media.TileMode.None> başka bir döşeme modu belirtildiğinde karmalı bir desen üretir. Bir döşeme fırçasının döşemesi çıkış alanını tam olarak <xref:System.Windows.Media.TileBrush.TileMode%2A> doldurmadığında, özelliği çıktı alanını doldurmak için temel döşemenin çoğaltılıp çoğaltılmaması gerektiğini ve eğer öyleyse, temel döşemenin nasıl çoğaltılması gerektiğini belirtir. Özellik, <xref:System.Windows.Media.TileBrush.TileMode%2A> numaralandırma ile <xref:System.Windows.Media.TileMode> tanımlanan aşağıdaki değerleri kabul eder:  
  
- <xref:System.Windows.Media.TileMode.None>: Yalnızca taban döşemesi çizilir.  
  
- <xref:System.Windows.Media.TileMode.Tile>: Taban döşemesi çizilir ve kalan alan, bir döşemenin sağ kenarının bir sonraki nin sol kenarına bitişik, alt ve üst için de benzer şekilde temel döşemetekrarla doldurulur.  
  
- <xref:System.Windows.Media.TileMode.FlipX>: Aynı <xref:System.Windows.Media.TileMode.Tile>, ancak karoların alternatif sütunları yatay olarak çevrilmiş.  
  
- <xref:System.Windows.Media.TileMode.FlipY>: Aynı <xref:System.Windows.Media.TileMode.Tile>, ancak fayans alternatif satırları dikey olarak çevrilmiş.  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: Bir <xref:System.Windows.Media.TileMode.FlipX> arada <xref:System.Windows.Media.TileMode.FlipY>ve .  
  
 Aşağıdaki resim farklı döşeme modlarını göstermektedir.  
  
 ![Farklı TileFırça TileMode ayarları](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 Aşağıdaki örnekte, bir görüntü 100 piksel genişliğinde ve 100 piksel yüksekliğinde bir dikdörtgen boyamak için kullanılır. Fırçanın kisi0,0,0,25,0,25 <xref:System.Windows.Media.TileBrush.Viewport%2A> olarak ayarlanarak, fırçanın taban karosu çıkış alanının 1/4' ü olacak şekilde yapılır. Fırçanınki. <xref:System.Windows.Media.TileBrush.TileMode%2A> <xref:System.Windows.Media.TileMode.FlipXY> böylece dikdörtgeni karo satırlarıyla doldurur.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Nasıl Dır Konular](brushes-how-to-topics.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [ImageBrush Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
