---
title: "Performansı İyileştirme: 2B Grafikleri ve Görüntüleme"
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
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30d0248c930f55a4f6d10e8cfa76a1d9b083b39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Performansı İyileştirme: 2B Grafikleri ve Görüntüleme
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Uygulamanızın gereksinimleri için çok çeşitli 2B grafik ve iyileştirilebilir görüntü işlevselliği sağlar. Bu konuda bu alanlarda performansı en iyi duruma getirme hakkında bilgi sağlar.  
  
  
<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Çizim ve şekiller  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]her ikisi de sağlar <xref:System.Windows.Media.Drawing> ve <xref:System.Windows.Shapes.Shape> nesneleri grafik çizim içeriğini temsil eder. Ancak, <xref:System.Windows.Media.Drawing> nesneleridir daha basit yapıları <xref:System.Windows.Shapes.Shape> nesneleri ve daha iyi performans özellikleri sağlar.  
  
 A <xref:System.Windows.Shapes.Shape> ekrana bir grafik şekil çizme olanak tanır. Öğesinden türetilen çünkü <xref:System.Windows.FrameworkElement> sınıfı, <xref:System.Windows.Shapes.Shape> nesneleri paneller ve çoğu denetim içinde kullanılabilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]birkaç grafik ve işleme hizmetlerine erişim katmanı sunar. En üst katmanında <xref:System.Windows.Shapes.Shape> nesneleri kolay kullanın ve düzeni ve olay işleme gibi birçok yararlı özellik sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıma hazır şekil nesneleri sayısını sağlar. Tüm şekil nesneleri devralınmalıdır <xref:System.Windows.Shapes.Shape> sınıfı. Kullanılabilir şekil nesneleri dahil <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, ve <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing>nesneleri, diğer yandan değil türetilen <xref:System.Windows.FrameworkElement> sınıfı ve işleme şekiller, görüntüler ve metin hafifletilmiş uygulama sağlama.  
  
 Dört tür vardır <xref:System.Windows.Media.Drawing> nesneler:  
  
-   <xref:System.Windows.Media.GeometryDrawing>Bir şekli çizer.  
  
-   <xref:System.Windows.Media.ImageDrawing>Bir resim çizer.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>Metin çizer.  
  
-   <xref:System.Windows.Media.DrawingGroup>Diğer çizimleri çizer. Diğer tek bileşik çizim çizimlerini birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.GeometryDrawing> Nesnesi geometri içeriğini işlemek için kullanılır. <xref:System.Windows.Media.Geometry> Sınıfı ve bu sınıftan gibi türetilen somut sınıflar <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, ve <xref:System.Windows.Media.PathGeometry>, 2B grafikleri işlemek için bir yol sağlar, yanı sıra vuruş sınaması ve kırpma desteği sağlar. Geometri nesneleri, bir denetim, örneğin, bölge tanımlamak için veya bir görüntüye uygulanacak kırpma bölgesinin tanımlamak için kullanılabilir. Geometri nesneleri dikdörtgenler ve daireler ya da iki veya daha fazla geometri nesnesinden oluşturulmuş bileşik bölgeler gibi basit bölgeler olabilir. Daha karmaşık geometrik bölgeler birleştirerek oluşturulabilir <xref:System.Windows.Media.PathSegment>-nesneleri gibi türetilen <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Yüzey üzerinde <xref:System.Windows.Media.Geometry> sınıfı ve <xref:System.Windows.Shapes.Shape> sınıfı oldukça benzer. Her ikisi de 2B grafik işlemede kullanılır ve her ikisi de, örneğin, aktarımlar benzer somut sınıflara sahip <xref:System.Windows.Media.EllipseGeometry> ve <xref:System.Windows.Shapes.Ellipse>. Ancak, bu iki sınıflar kümesi arasındaki önemli farklılıklar vardır. Birisi, <xref:System.Windows.Media.Geometry> sınıf işlevselliğini bazıları eksik <xref:System.Windows.Shapes.Shape> kendisini çizme yeteneği gibi sınıfı. Geometri nesnesi çizmek için DrawingContext, çizim ya da bir yol (Bu bir yolu bir şekli olduğunu dir) gibi başka bir sınıf çizim işlemi gerçekleştirmek için kullanılması gerekir. İşleme dolgu, vuruş ve vuruş kalınlığı gibi bir şekil nesnesi bu özellikleri içerirken, geometri nesnesi çizer sınıfı özelliklerdir. Bu farkı düşünmenin bir yoludur geometri nesnesi bir bölgeyi tanımlar, bir daire Örneğin, bir şekil nesnesi bir bölge açıklarken bu bölge nasıl doldurulacağını ve tanımlar ve Düzen sistemine katılır.  
  
 Bu yana <xref:System.Windows.Shapes.Shape> nesneleri türetilen <xref:System.Windows.FrameworkElement> kullanmadan sınıfı, uygulamanızda önemli ölçüde daha fazla bellek tüketimi ekleyebilirsiniz. Sizin gerçekten ihtiyacınız yoksa <xref:System.Windows.FrameworkElement> Grafik içeriğiniz için özelliklerini göz önünde bulundurun hafifletilmiş kullanarak <xref:System.Windows.Media.Drawing> nesneleri.  
  
 Daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry nesneleri  
 <xref:System.Windows.Media.StreamGeometry> Nesnesidir alternatifidir için <xref:System.Windows.Media.PathGeometry> geometrik şekiller oluşturma. Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde. <xref:System.Windows.Media.StreamGeometry>birçok işlemek için optimize edilmiştir <xref:System.Windows.Media.PathGeometry> nesneleri ve birçok kişi kullanmaya karşılaştırıldığında daha iyi gerçekleştirir <xref:System.Windows.Media.PathGeometry> nesneleri.  
  
 Aşağıdaki örnek, bir üçgen oluşturmak için öznitelik sözdizimini kullanır. <xref:System.Windows.Media.StreamGeometry> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Daha fazla bilgi için <xref:System.Windows.Media.StreamGeometry> nesneleri bkz [kullanarak bir şekli bir StreamGeometry oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual nesneleri  
 <xref:System.Windows.Media.DrawingVisual> Şekil, görüntü veya metin işlemek için kullanılan sınıf çizim basit bir nesnedir. Bu sınıf, kendi performansını artırır, düzen veya olay işleme sağlamadığından basit olarak değerlendirilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir. Daha fazla bilgi için bkz: [kullanarak DrawingVisual nesneleri](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Görüntüler  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Görüntü önceki sürümlerindeki görüntüleme yetenekleri üzerine önemli bir iyileştirme sağlar [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Bir bit eşlem görüntüleme veya ortak bir denetimde bir resim kullanma gibi özellikleri Imaging öncelikle işlendi Microsoft Windows grafik cihaz arabirimi (GDI) veya Microsoft Windows GDI + uygulama programlama arabirimi tarafından (API). Bu API, taban çizgisi görüntüleme işlevselliği sağlanan ancak codec genişletilebilirliği ve yüksek doğruluk resim desteği gibi özellikleri olmadığı. WPF görüntüleme API yeniden tasarlanmıştır GDI ve GDI + eksikliklerini aşmak ve API görüntülemek ve uygulamalarınızdaki resimleri kullanmak için yeni bir dizi sağlar.  
  
 Görüntüleri kullanırken daha iyi performans elde için aşağıdaki önerileri göz önünde bulundurun:  
  
-   Uygulamanız, küçük resim görüntüleri göstermek gerektiriyorsa, görüntünün küçültülmüş boyutlu sürümünü oluşturmayı düşünün. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntünüzü yükler ve tam boyutuna kodunu çözer. Küçük resim sürümünü yalnızca istiyorsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gereksiz kendi tam boyutlu görüntüyü kodunu çözer ve bir küçük resim boyutuna ölçeklendirir. Bu gereksiz yükünü önlemek için ya da istek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] küçük resimlerin boyutunu görüntüye kod çözme veya istemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] küçük resimlerin boyutunu resim yüklenemiyor.  
  
-   Her zaman varsayılan boyutu değil de, istenen boyuta görüntü kodunu çözer. Yukarıda belirtildiği gibi istek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yansımanıza varsayılan tam değil de istenen boyuta çözecek. Yalnızca uygulamanızın çalışma kümesi, ancak yürütme hızını da azaltır.  
  
-   Mümkünse, gibi birden çok görüntüsünü film şeridi oluşan görüntüleri tek bir görüntüde, birleştirin.  
  
-   Daha fazla bilgi için bkz: [Imaging genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Herhangi bir bit eşlem ölçeğini animasyon eklerken, algoritma yeniden örnekleme varsayılan yüksek kaliteli görüntü bazen etkin şekilde animasyonların titremesine neden kare hızı düşüşüne neden için yeterli sistem kaynakları kullanabilir. Ayarlayarak <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> özelliği <xref:System.Windows.Media.RenderOptions> nesnesine <xref:System.Windows.Media.BitmapScalingMode.LowQuality> bir bit eşlemi ölçeklendirdiğinizde daha yumuşak bir animasyon oluşturabilirsiniz. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>mod söyler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] resimler işlenirken bir kalite optimize algoritmadan hızı iyileştirilmiş bir algoritma geçmek için işleme altyapısı.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Media.BitmapScalingMode> için bir resim nesnesi.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlenmiş içeriğini önbelleğe almaz <xref:System.Windows.Media.TileBrush> gibi nesneleri <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>. Statik senaryolarda burada içeriği ne kullanımını <xref:System.Windows.Media.TileBrush> içinde Sahne değiştirme, video belleği korur beri bu mantıklıdır. Kadar mantıklı yapmaz bir <xref:System.Windows.Media.TileBrush> statik içerik ile bir statik olmayan biçimde kullanılır — Örneğin, bir statik <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> 3B bir döndürme nesneyi yüzeye eşlendi. Varsayılan davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tamamını yeniden içeriğini işlemek için <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> her çerçeve için bile içeriği işlemektir.  
  
 Ayarlayarak <xref:System.Windows.Media.RenderOptions.CachingHint%2A> özelliği <xref:System.Windows.Media.RenderOptions> nesnesine <xref:System.Windows.Media.CachingHint.Cache> döşeli fırça nesnelerin önbelleğe alınmış sürümlerini kullanarak performansı artırabilir.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> Ve <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> özellik değerlerini olduğunuz zaman belirlemek göreli boyutu değerleri <xref:System.Windows.Media.TileBrush> nesne yeniden ölçek değişiklikleri nedeniyle. Ayarlayarak Örneğin, <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 2.0, önbelleğin özelliğine <xref:System.Windows.Media.TileBrush> yalnızca boyutuna geçerli Önbellek boyutunun iki katı aştığında yeniden oluşturulması gerekir.  
  
 Aşağıdaki örnek için önbelleğe alma ipucu seçeneğinin nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama performansı en iyi duruma getirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama performansını planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanım yararlanarak](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Nesne davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer performans önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Animasyon ipuçları ve püf noktaları](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
