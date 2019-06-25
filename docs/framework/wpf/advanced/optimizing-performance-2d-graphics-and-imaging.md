---
title: 'Performansı iyileştirme: 2B Grafikleri ve Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 25803bd772832cd22e855f530d10a3f3639c180c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348440"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Performansı iyileştirme: 2B Grafikleri ve Görüntüleme
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulamanızın gereksinimleri için çok sayıda 2B grafikleri ve iyileştirilebilir görüntü işlevselliği sağlar. Bu konu, bu alanlarda performansı en iyi duruma getirme hakkında bilgi sağlar.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Çizim ve şekiller  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hem de <xref:System.Windows.Media.Drawing> ve <xref:System.Windows.Shapes.Shape> grafik çizim içeriğini temsil eden nesneleri. Ancak, <xref:System.Windows.Media.Drawing> nesnelerdir daha basit yapıları <xref:System.Windows.Shapes.Shape> nesneleri ve daha iyi performans özellikleri sağlar.  
  
 A <xref:System.Windows.Shapes.Shape> ekrana bir grafik şekil çizme olanak tanır. Öğesinden türetildiği <xref:System.Windows.FrameworkElement> sınıfı <xref:System.Windows.Shapes.Shape> paneller ve çoğu denetim nesneleri kullanılabilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birkaç grafik ve işleme hizmetlerine erişim katmanı sunar. En üst katmanında <xref:System.Windows.Shapes.Shape> nesnelerdir kolayca kullanın ve düzeni ve olay işleme gibi birçok yararlı özellik sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir dizi kullanıma hazır şekil nesneleri sağlar. Tüm şekil nesneleri devralınacak <xref:System.Windows.Shapes.Shape> sınıfı. Kullanılabilir şekil nesneleri dahil etme <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, ve <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> nesneleri, diğer yandan değil türetilen <xref:System.Windows.FrameworkElement> sınıfı ve işleme şekiller, görüntü ve metin için daha basit bir uygulama sağlayın.  
  
 Dört tür <xref:System.Windows.Media.Drawing> nesneler:  
  
- <xref:System.Windows.Media.GeometryDrawing> Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing> Bir resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> Metin çizer.  
  
- <xref:System.Windows.Media.DrawingGroup> Diğer çizimleri çizer. Çizim grubu, tek bir bileşik çizim diğer çizimlerini birleştirmek için kullanın.  
  
 <xref:System.Windows.Media.GeometryDrawing> Nesnesi, geometri içeriğini işlemek için kullanılır. <xref:System.Windows.Media.Geometry> Sınıfı ve gibi kendisinden türetilen somut sınıflar <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, ve <xref:System.Windows.Media.PathGeometry>, 2B grafikleri işlemek için bir yol sağlar, aynı zamanda isabet sınaması ve kırpma desteği sağlar. Geometri nesneleri, bir denetimin, örneğin, bölge tanımlamak veya bir resme uygulanacak kırpma bölgesini tanımlamak için kullanılabilir. Geometri nesneleri dikdörtgenler ve daireler ya da iki veya daha fazla geometri nesneleri oluşturulan bileşik bölgeleri gibi basit bölgelerde olabilir. Daha karmaşık bir geometrik bölgeler birleştirerek oluşturulabilir <xref:System.Windows.Media.PathSegment>-gibi türetilmiş nesneler, <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Yüzey üzerinde <xref:System.Windows.Media.Geometry> sınıfı ve <xref:System.Windows.Shapes.Shape> sınıfı da oldukça benzerdir. 2B grafikler işlemede kullanılan ve her ikisi de, örneğin, aktarımlar benzer somut sınıflar sahip <xref:System.Windows.Media.EllipseGeometry> ve <xref:System.Windows.Shapes.Ellipse>. Ancak, bu sınıfların iki kümesi arasında önemli farklılıklar vardır. Biri, <xref:System.Windows.Media.Geometry> sınıf işlevlerini bazıları eksik <xref:System.Windows.Shapes.Shape> kendisini çizme olanağı gibi bir sınıf. Geometri nesnesi çizmek için başka bir sınıf DrawingContext, çizim ya da (bir şekil bir yol olduğunu hatalarının ayıklanabileceğini belirtmekte yarar) yolu gibi çizim işlemi gerçekleştirmek için kullanılmalıdır. Dolgu ve vuruş vuruş kalınlığı gibi işleme özellikleri bir şekil nesnesi bu özellikler içerirken, geometri nesnesi çizer sınıfı ' dir. Bu fark etmeniz gereken bir yoludur geometri nesnesi bir bölgeyi tanımlar, bir daire Örneğin, bir şekil nesnesi bir bölge açıklarken bu bölge nasıl doldurulacağını ve tanımlar ve Düzen sistemde katılır.  
  
 Bu yana <xref:System.Windows.Shapes.Shape> nesneleri türetilen <xref:System.Windows.FrameworkElement> sınıfı, bunları kullanarak uygulamanızı önemli ölçüde daha fazla bellek tüketimi ekleyebilirsiniz. Sizin gerçekten ihtiyacınız yoksa <xref:System.Windows.FrameworkElement> Grafik içeriğiniz için özellikleri göz önünde bulundurun hafifletilmiş kullanarak <xref:System.Windows.Media.Drawing> nesneleri.  
  
 Daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelerine genel bakış](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry nesneleri  
 <xref:System.Windows.Media.StreamGeometry> Nesnedir, basit bir alternatif <xref:System.Windows.Media.PathGeometry> geometrik şekiller oluşturma. Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde. <xref:System.Windows.Media.StreamGeometry> birçok işlem için iyileştirilmiş <xref:System.Windows.Media.PathGeometry> nesneleri ve birçok kişinin kullanarak karşılaştırıldığında daha iyi sonuç verdiğini <xref:System.Windows.Media.PathGeometry> nesneleri.  
  
 Aşağıdaki örnek, bir üçgen oluşturmak için öznitelik sözdizimi kullanır. <xref:System.Windows.Media.StreamGeometry> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Daha fazla bilgi için <xref:System.Windows.Media.StreamGeometry> nesneleri bkz [StreamGeometry kullanarak şekil oluşturma](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual nesneleri  
 <xref:System.Windows.Media.DrawingVisual> Şekilleri, görüntü veya metin işlemek için kullanılan sınıfı çizim basit bir nesnedir. Bu sınıf, performansını artırır, düzen veya olay işleme sağlamadığı basit olarak değerlendirilir. Bu nedenle, çizimleri, arka plan ve küçük resim için idealdir. Daha fazla bilgi için [DrawingVisual nesnelerini kullanma](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Görüntüler  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleme, önceki sürümlerinde görüntüleme yetenekleri üzerinde önemli bir iyileştirme sağlar [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Bit eşlem görüntüleme veya ortak denetiminde resim kullanma gibi özellikleri Imaging öncelikle ele Microsoft Windows grafik cihaz arabirimi (GDI) ya da Microsoft Windows GDI + uygulama programlama arabirimi tarafından (API). Bu API görüntüleme işlevlerini temel sağlanan ancak koduk codec genişletilebilirlik ve yüksek uygunluğa sahip görüntü desteği gibi özellikleri. WPF Imaging API yeniden tasarlanmış GDI ve GDI + eksikliklerini aşmak ve yeni görüntülemek ve uygulamalarınızdaki resimleri kullanmak için API kümesi sağlar.  
  
 Görüntüleri kullanarak daha iyi performans elde etmeye yönelik aşağıdaki önerileri dikkate alın:  
  
- Uygulamanıza küçük resimleri görüntülemek gerekiyorsa, azaltılmış boyutlu bir görüntünün sürümünü oluşturma göz önünde bulundurun. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntünüzü yükler ve tam boyutuna getirir. Yalnızca bir küçük resim görüntüsü sürümü istiyorsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gereksiz kendi tam boyutlu görüntüyü kodunu çözer ve ardından, bir küçük resim boyutu aşağı ölçeklendirir. Bu gereksiz ek yükten kaçınmak için ya da istek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüyü bir küçük resim boyutu için kod çözme veya istemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir küçük resim boyutu resim yüklenemiyor.  
  
- Her zaman varsayılan boyutu değil de, istenen boyuta görüntü çözer. Yukarıda belirtildiği gibi istek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntünüzü istenen boyuta ve değil varsayılan tam boyutlu çözülecek. Yalnızca uygulamanızın çalışma kümesi, ancak yürütme hızını azaltır.  
  
- Mümkünse, gibi birden çok görüntülerini bir film şeridi oluşan tek bir görüntüye görüntüleri birleştirin.  
  
- Daha fazla bilgi için [Imaging genel bakış](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Herhangi bir bit eşlem ölçeğini animasyon ekleme, örnekleme algoritması varsayılan yüksek kaliteli görüntü, bazen etkili şekilde animasyonların titremesine neden kare oranı azalmasına neden için yeterli sistem kaynaklarına kullanabilir. Ayarlayarak <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> özelliği <xref:System.Windows.Media.RenderOptions> nesnesini <xref:System.Windows.Media.BitmapScalingMode.LowQuality> bir bit eşlem olduğunda daha yumuşak bir animasyon oluşturabilirsiniz. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> modu söyler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kalite açısından iyileştirilmiş algoritmasını kullanarak görüntüleri işlerken hızı için iyileştirilmiş bir algoritmaya geçiş yapmak için işleme altyapısı.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Media.BitmapScalingMode> için bir resim nesnesi.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlenmiş içeriği önbelleğe almaz <xref:System.Windows.Media.TileBrush> gibi nesneleri <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>. Statik senaryolarda burada içeriği ne kullanımını <xref:System.Windows.Media.TileBrush> içinde Sahne değiştirme, video belleği korur olduğundan bu mantıklıdır. Çok mantıklı yapmaz bir <xref:System.Windows.Media.TileBrush> statik içeriği ile bir statik olmayan şekilde kullanılır — Örneğin, bir statik <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> dönen bir 3B nesnenin yüzeyine eşlendi. Varsayılan davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tamamını yeniden içeriğini işlemek için <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> her karede olsa bile içeriği işlemektir.  
  
 Ayarlayarak <xref:System.Windows.Media.RenderOptions.CachingHint%2A> özelliği <xref:System.Windows.Media.RenderOptions> nesnesini <xref:System.Windows.Media.CachingHint.Cache> döşenmiş fırça nesnelerin önbelleğe alınmış sürümlerini kullanarak performansı artırabilirsiniz.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> Ve <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> özellik değerlerini değerler gerektiğini belirleyen göreli boyutu <xref:System.Windows.Media.TileBrush> nesne yeniden ölçek değişiklikleri nedeniyle. Ayarlayarak gibi <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 2.0, önbelleğin özelliğini <xref:System.Windows.Media.TileBrush> yalnızca iki kez geçerli önbellek boyutu boyutunu aştığında, yeniden oluşturulması gerekiyor.  
  
 Aşağıdaki örnek için önbelleğe alma ipucu seçeneğinin nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
- [Animasyon İpuçları ve Püf Noktaları](../graphics-multimedia/animation-tips-and-tricks.md)
