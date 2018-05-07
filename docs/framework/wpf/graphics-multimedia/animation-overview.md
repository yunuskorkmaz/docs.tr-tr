---
title: Animasyona Genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 5fb9550ddce4ead900206c2ece2f976ab8b42c4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="animation-overview"></a>Animasyona Genel bakış
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] güçlü bir etkileyici kullanıcı arabirimleri ve çekici belgeler oluşturmanıza olanak sağlayan grafikleri ve düzeni özellikler kümesi sağlar. Animasyon daha da muhteşem ve kullanışlı bir çekici kullanıcı arabirimi yapabilirsiniz. Yalnızca bir arka plan rengi animasyonu veya animasyonlu bir uygulama tarafından <xref:System.Windows.Media.Transform>, etkileyici ekran geçişleri oluşturabilir veya yararlı görsel yardımlar sağlayabilirsiniz.  
  
 Bu genel bakışta tanıtılmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon ve zamanlama sistemi. Animasyonu üzerinde odaklanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] film şeritleri kullanarak nesneleri.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Animasyon Tanıtımı  
 Animasyon görüntüleri, son her biraz farklı bir dizi hızla dolaşma tarafından oluşturulmuş bir görünümü ' dir. Beyin resim grubunu tek bir değişen görünüm algılar. Film içinde bu görünümü, her saniye birçok fotoğraf veya çerçeve kayıt kameralar kullanılarak oluşturulur. Çerçeve çalınma projektör ile İzleyici hareketli resim görür.  
  
 Animasyonun bir bilgisayara benzer. Örneğin, bir çizim dikdörtgeni yavaşça görünümü dışında sağlayan bir program gibi çalışabilir.  
  
-   Program bir zamanlayıcı oluşturur.  
  
-   Programın ne kadar süre dolduktan görmek için belirlenen aralıklarla Zamanlayıcı denetler.  
  
-   Program Zamanlayıcı denetler her zaman geçerli geçirgenlik değeri ne kadar süre dolduktan bağlı olarak dikdörtgen için hesaplar.  
  
-   Program dikdörtgen yeni değerle güncelleştirir ve onu yeniden çizer.  
  
 Öncesinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] geliştiriciler gerekiyordu oluşturabilir ve kendi zamanlama sistemlerini yönetmek veya özel kitaplıkları kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kod üzerinden kullanıma sunulan bir verimli zamanlama sistemi içerir ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve, son derece tümleşiktir içine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon denetimleri ve diğer grafik nesneleri hale getirmeyi daha kolay hale getirir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamanlama sistemi yönetme ve ekran verimli bir şekilde yeniden Perde Arkası tüm iş işler. Bu efektler elde mekanizması yerine oluşturmak istediğiniz etkileri odaklanmanıza olanak tanıyan zamanlama sınıfları sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca, kendi animasyonları içinden devrettiği temel animasyon sınıflarını göstererek oluşturmak için özelleştirilmiş animasyonları üretmek için kolaylaştırır. Özel animasyonlarına birçok performans avantajı standart animasyon sınıfların elde edilir.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>WPF özelliği animasyon sistemi  
 Zamanlama sistemi hakkında birkaç önemli kavramları anlarsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları kullanmak daha kolay olabilir. İçinde en önemli olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kendilerine özgü özelliklere animasyon uygulayarak nesnelere animasyon ekleme. Örneğin, çerçeve öğesini yapmak için animasyon kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri. Animasyon görünümünden silinerek bir nesne için kendi <xref:System.Windows.UIElement.Opacity%2A> özelliği.  
  
 Animasyon özelliklerine sahip bir özellik için aşağıdaki üç gereksinimleri karşılaması gerekir:  
  
-   Bu, bağımlılık özelliği olmalıdır.  
  
-   Öğesinden devralınan bir sınıfa ait olmalıdır <xref:System.Windows.DependencyObject> ve uygulayan <xref:System.Windows.Media.Animation.IAnimatable> arabirimi.  
  
-   Kullanılabilir uyumlu bir animasyon türü olmalıdır. (Varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biri sağlamaz kendi oluşturabilirsiniz. Bkz: [özel animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sahip çok sayıda nesne içeren <xref:System.Windows.Media.Animation.IAnimatable> özellikleri. Gibi denetimler <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.TabControl>hem de <xref:System.Windows.Controls.Panel> ve <xref:System.Windows.Shapes.Shape> nesneleri devralır <xref:System.Windows.DependencyObject>. Bunların özelliklerinin çoğu bağımlılık özelliklerdir.  
  
 Animasyon neredeyse her yerden, stilleri ve denetim şablonları içeren kullanabilirsiniz. Animasyon görsel olması gerekmez; Bu bölümde açıklanan ölçütlerini karşılıyorsa kullanıcı arabiriminin parçası olmayan nesneler animasyon ekleyebilirsiniz.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Örnek: bir öğe yavaşça görünümü ve olun  
 Bu örnek nasıl kullanılacağını gösteren bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir bağımlılık özelliğinin değeri animasyon animasyon. Kullandığı bir <xref:System.Windows.Media.Animation.DoubleAnimation>, oluşturur animasyon türündeki <xref:System.Double> hale getirmeyi değerleri, <xref:System.Windows.UIElement.Opacity%2A> özelliği bir <xref:System.Windows.Shapes.Rectangle>. Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> Görünüm ve bu moddan kaybolur.  
  
 Örneğin ilk bölümü oluşturur bir <xref:System.Windows.Shapes.Rectangle> öğesi. Bir animasyon oluşturmak ve dikdörtgenin uygulama izleyin adımları göstermek <xref:System.Windows.UIElement.Opacity%2A> özelliği.
  
 Aşağıdaki nasıl oluşturulacağını gösterir bir <xref:System.Windows.Shapes.Rectangle> öğesinde bir <xref:System.Windows.Controls.StackPanel> XAML'de.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 Aşağıdaki nasıl oluşturulacağını gösterir bir <xref:System.Windows.Shapes.Rectangle> öğesinde bir <xref:System.Windows.Controls.StackPanel> kod.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>1. Kısım: DoubleAnimation oluşturma  
 Görünüm ve bu moddan silinerek öğeyi yapmak için bir yoldur animasyon için kendi <xref:System.Windows.UIElement.Opacity%2A> özelliği. Çünkü <xref:System.Windows.UIElement.Opacity%2A> özelliği türüdür <xref:System.Double>, double değerleri üreten bir animasyon gerekir. A <xref:System.Windows.Media.Animation.DoubleAnimation> böyle bir animasyon. A <xref:System.Windows.Media.Animation.DoubleAnimation> iki double değeri arasında bir geçiş oluşturur. Başlangıç değerini belirtmek için ayarladığınız kendi <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği. Bitiş değerini belirtmek için ayarladığınız kendi <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.  
  
1.  Opaklık değeri `1.0` tamamen opak nesne ve opaklık değeri yapar `0.0` tamamen görünmez yapar. Animasyon geçiş yapmak için `1.0` için `0.0` ayarladığınız kendi <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğine `1.0` ve kendi <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğine `0.0`. Aşağıdaki nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.Animation.DoubleAnimation> XAML'de.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     Aşağıdaki nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.Animation.DoubleAnimation> kod.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  Ardından, belirtmelisiniz bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Bir animasyon başlangıç değerinden hedef değerine gitmek için gereken süreyi belirtir. Aşağıdaki nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> XAML'de beş saniye.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     Aşağıdaki nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kodda beş saniye.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  Önceki kod gelen geçiş bir animasyon gösterdi `1.0` için `0.0`, hedef öğe tamamen opak görünümden tamamen görünmez geçmesine neden olur. Kaybolduktan sonra geri görünüme silinerek öğeyi göstermek için ayarlanmış <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> animasyonun özellik `true`. Animasyonun süresiz olarak yineleme yapmak için ayarlanmış kendi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğine <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Aşağıdaki nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> XAML özelliklerinde.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     Aşağıdaki nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> kodda özellikleri.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>2. Kısım: film şeridi oluşturma  
 Bir nesneye bir animasyon uygulamak için oluşturduğunuz bir <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> nesne belirtmek için özellikler ve özellik animasyon bağlı.  
  
1.  Oluşturma <xref:System.Windows.Media.Animation.Storyboard> ve alt öğe olarak animasyonu ekleyin. Aşağıdaki nasıl oluşturulacağını gösterir <xref:System.Windows.Media.Animation.Storyboard> XAML'de.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Oluşturmak için <xref:System.Windows.Media.Animation.Storyboard> kodda bildirme bir <xref:System.Windows.Media.Animation.Storyboard> sınıf düzeyinde değişken.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Ardından başlatma <xref:System.Windows.Media.Animation.Storyboard> ve alt öğe olarak animasyonu ekleyin.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  <xref:System.Windows.Media.Animation.Storyboard> Animasyonun nereye uygulanacağını bilmesi gerekir. Kullanım <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ekli özellik animasyon nesnesine belirtin. Aşağıdaki hedef adını ayarlamak gösterilmiştir <xref:System.Windows.Media.Animation.DoubleAnimation> için `MyRectangle` XAML'de.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     Aşağıdaki hedef adını ayarlamak gösterilmiştir <xref:System.Windows.Media.Animation.DoubleAnimation> için `MyRectangle` kodu.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  Kullanım <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> animasyon eklenecek özelliği belirtmek için özelliği eklenmiş. Aşağıdaki animasyonun nasıl yapılandırıldığını gösterir hedef <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Windows.Shapes.Rectangle> XAML'de.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     Aşağıdaki animasyonun nasıl yapılandırıldığını gösterir hedef <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Windows.Shapes.Rectangle> kod.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> sözdizimi ve ek örnekler için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Bölüm 3 (XAML): İlişkilendirme bir tetikleyici ile film şeridi  
 Başlatmak ve uygulamak için en kolay yolu bir <xref:System.Windows.Media.Animation.Storyboard> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay tetikleyicisi kullanmaktır. Bu bölümde ile nasıl ilişkilendirildiğini gösterir <xref:System.Windows.Media.Animation.Storyboard> XAML'de bir tetikleyici ile.  
  
1.  Oluşturma bir <xref:System.Windows.Media.Animation.BeginStoryboard> nesne ve şeridinizin ile ilişkilendirebilirsiniz. A <xref:System.Windows.Media.Animation.BeginStoryboard> bir tür <xref:System.Windows.TriggerAction> uygulayan ve başlatan bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  Oluşturma bir <xref:System.Windows.EventTrigger> ve ekleme <xref:System.Windows.Media.Animation.BeginStoryboard> için kendi <xref:System.Windows.EventTrigger.Actions%2A> koleksiyonu. Ayarlama <xref:System.Windows.EventTrigger.RoutedEvent%2A> özelliği <xref:System.Windows.EventTrigger> başlatmak istediğiniz yönlendirilmiş olay <xref:System.Windows.Media.Animation.Storyboard>. (Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  Ekleme <xref:System.Windows.EventTrigger> için <xref:System.Windows.FrameworkElement.Triggers%2A> dikdörtgen koleksiyonu.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Bölüm 3 (kod): İlişkilendirme olay işleyici ile film şeridi  
 Başlatmak ve uygulamak için en kolay yolu bir <xref:System.Windows.Media.Animation.Storyboard> kodda bir olay işleyicisi kullanmaktır. Bu bölümde ile nasıl ilişkilendirildiğini gösterir <xref:System.Windows.Media.Animation.Storyboard> kodundaki olay işleyici ile.  
  
1.  Kaydolma <xref:System.Windows.FrameworkElement.Loaded> dikdörtgenin olay.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  Olay işleyicisini bildirin. Olay işleyicisi kullanmak <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> film şeridi uygulamak için yöntem.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Tam Örnek  
 XAML görünümünde ve belirerek dikdörtgene oluşturulacağını gösterir.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Aşağıdaki kod görünümünde ve belirerek dikdörtgene oluşturulacağını gösterir.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Animasyon türleri  
 Animasyon özellik değerleri oluşturması nedeniyle farklı özellik türleri için farklı animasyon türleri vardır. Alan bir özelliği animasyon uygulamak için bir <xref:System.Double>, gibi <xref:System.Windows.FrameworkElement.Width%2A> bir öğenin özelliğini kullanın üreten bir animasyon <xref:System.Double> değerleri. Alan bir özelliği animasyon uygulamak için bir <xref:System.Windows.Point>, üreten bir animasyon kullanın <xref:System.Windows.Point> değerleri ve benzeri. Farklı özellik türlerinin sayısı nedeniyle, birkaç animasyon sınıfları vardır <xref:System.Windows.Media.Animation> ad alanı. Neyse ki, aralarında ayırt etmek kolaylaşır sıkı bir adlandırma kuralı izleyin:  
  
-   \<*Tür*> animasyon  
  
     Bir "From/To/By" veya "temel" animasyon olarak bilinen bu bir başlangıç ve bitiş değeri arasında ya da bir uzaklık değeri başlangıç değerine ekleyerek animasyon.  
  
    -   Başlangıç değerini belirtmek için animasyonun From özelliğini ayarlayın.  
  
    -   Bitiş değeri belirtmek için animasyonun To özelliğini ayarlayın.  
  
    -   Bir uzaklık değeri belirtmek için animasyonun By özelliğini ayarlayın.  
  
     Kullanmak için en basit oldukları için bu genel bakıştaki örnekler bu animasyonları kullanın. From/To/By animasyonları ayrıntılı u animasyonları genel olarak açıklanmıştır.  
  
-   \<*Tür*> AnimationUsingKeyFrames  
  
     Herhangi bir sayıda hedef değerleri belirtin ve hatta kendi ilişkilendirme yöntemini denetlemek için anahtar çerçeve animasyonları From/To/By animasyonları daha güçlüdür. Bazı türleri yalnızca anahtar çerçeve animasyonları ile animasyon uygulanabilir. Anahtar çerçeve animasyonları ayrıntılı olarak açıklanmıştır [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   \<*Tür*> AnimationUsingPath  
  
     Yol animasyonları animasyonlu değerleri üretmek için geometrik yol kullanmanıza olanak verir.  
  
-   \<*Tür*> AnimationBase  
  
     Soyut, uyguladığınızda canlandırır, sınıf bir \< *türü*> değeri. Bu sınıf için temel sınıf olarak hizmet veren \< *türü*> animasyon ve \< *türü*> AnimationUsingKeyFrames sınıfları. Yalnızca kendi özel animasyon oluşturmak isterseniz, doğrudan bu sınıflarla ilgilenmek gerekir. Aksi durumda, bir \< *türü*> animasyon veya ana kare\<*türü*> animasyon.  
  
 Çoğu durumda, kullanmak istersiniz \< *türü*> gibi animasyon sınıfları <xref:System.Windows.Media.Animation.DoubleAnimation> ve <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 Aşağıdaki tabloda bazı genel animasyon türlerini ve ile kullanıldıkları bazı özellikleri gösterir.  
  
|Özellik türü|Karşılık gelen basic (From/To/By) animasyon|Karşılık gelen anahtar çerçeve animasyonu|Karşılık gelen yol animasyon|Kullanım örneği|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Yok.|Animasyon <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> veya <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animasyon <xref:System.Windows.FrameworkElement.Width%2A> , bir <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.FrameworkElement.Height%2A> , bir <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animasyon <xref:System.Windows.Media.EllipseGeometry.Center%2A> , getirin bir <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Yok.|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Yok.|Animasyon <xref:System.Windows.Controls.TextBlock.Text%2A> , bir <xref:System.Windows.Controls.TextBlock> veya <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Zaman çizelgelerini animasyonları olan  
 Tüm animasyon türleri devralınmalıdır <xref:System.Windows.Media.Animation.Timeline> sınıf; bu nedenle, tüm animasyonları zaman çizelgeleri, özelleştirilmiş türleridir. A <xref:System.Windows.Media.Animation.Timeline> zaman kesimini tanımlar. Belirleyebileceğiniz *zamanlama davranışlarını* zaman çizelgesinin: kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kaç kez olduğu için yinelenen ve hatta zaman ne kadar hızlı ilerler.  
  
 Bir animasyon olduğundan bir <xref:System.Windows.Media.Animation.Timeline>, ayrıca zaman kesimini temsil eder. Ancak, belirtilen zaman kesimi ilerledikçe animasyonun çıkış değerlerini de hesaplar (veya <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Animasyon ilerledikçe, veya "oynadığı" olarak, ilişkili olduğu özelliği güncelleştirir.  
  
 Üç sık kullanılan zamanlama özellikleri <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>Duration özelliği  
 Daha önce belirtildiği gibi bir zaman çizelgesi zaman kesimini temsil eder. Bu kesimin uzunluğu tarafından belirlenen <xref:System.Windows.Media.Animation.Timeline.Duration%2A> genellikle kullanılarak belirtilen zaman çizelgesi'nin bir <xref:System.Windows.Duration.TimeSpan%2A> değeri. Bir zaman çizelgesi süresinin sonuna ulaştığında, yineleme tamamlandı.  
  
 Bir animasyon kullanan kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A> geçerli değeri belirlemek için özellik. Belirtmezseniz, bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> değeri animasyonun için varsayılan değer olan 1 saniye kullanır.  
  
 Aşağıdaki sözdizimi basitleştirilmiş bir sürümünü gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] öznitelik sözdizimi için <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği.  
  
*Saat* `:` *dakika* `:` *saniye*
  
 Aşağıdaki tabloda çeşitli gösterilmektedir <xref:System.Windows.Duration> ayarları ve sonuçta elde edilen değerleri.  
  
|Ayar|Sonuç değeri|  
|-------------|---------------------|  
|0:0:5.5|5.5 saniye.|  
|0:30:5.5|30 dakika ve 5.5 saniye.|  
|1:30:5.5|1 saat, 30 dakika, ve 5.5 saniye.|  
  
 Belirlemenin bir yolu bir <xref:System.Windows.Duration> kodda kullanmaktır <xref:System.TimeSpan.FromSeconds%2A> yöntemi oluşturmak için bir <xref:System.TimeSpan>, yeni bir bildirme <xref:System.Windows.Duration> kullanan yapısı <xref:System.TimeSpan>.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Duration> değerleri ve tam [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sözdizimi, bkz: <xref:System.Windows.Duration> yapısı.  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Özelliği, sonuna ulaştıktan sonra bir zaman çizelgesi geriye dönük oynadığı olup olmadığını belirtir, <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Bu animasyon özelliğini ayarlamak, `true`, sonuna ulaştıktan sonra bir animasyon tersine çevirir kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A>' ü başlangıç değeri bitiş değerinden oynar. Bu özellik varsayılan olarak açık `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği, bir zaman çizelgesinin kaç kez belirtir. Varsayılan olarak, bir yineleme sayısı zaman çizelgelerini sahip `1.0`, hiç yineleniyor mu ve zaman bunlar oynayacağı anlamına gelir.  
  
 Bu özellikler ve diğerleri hakkında daha fazla bilgi için bkz: [Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Animasyonun bir özelliğe uygulama  
 Önceki bölümlerde animasyonları ve zamanlama özelliklerini farklı türleri açıklanmaktadır. Bu bölümde, animasyon eklemek istediğiniz özelliğe animasyon uygulamanın gösterilmektedir. <xref:System.Windows.Media.Animation.Storyboard> nesneleri özelliklere animasyonları uygulamak için bir yol sağlar. A <xref:System.Windows.Media.Animation.Storyboard> olan bir *kapsayıcı zaman çizelgesi* içerdiği animasyonları için hedefleme bilgileri sağlar.  
  
### <a name="targeting-objects-and-properties"></a>Hedefleme nesneleri ve özellikleri  
 <xref:System.Windows.Media.Animation.Storyboard> SAX <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> ekli özellikler. Bir animasyon üzerindeki şu özellikleri ayarlayarak, animasyonun animasyon gerekenler söyleyin. Ancak, bir animasyon nesneyi hedefleyebilir önce nesne genellikle bir ad verilmelidir.  
  
 Bir ad atamak bir <xref:System.Windows.FrameworkElement> ad atamak farklı bir <xref:System.Windows.Freezable> nesnesi. Çoğu denetimler ve panolar çerçeve öğeleridir; Ancak, Fırçalar, dönüşümler ve geometri, gibi çoğu tamamen grafik nesneleri freezable nesneleridir. Bir tür olup olmadığından emin değilseniz, bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.Freezable>, başvurmak **devralma hiyerarşisi** başvuru belgelerini bölümü.  
  
-   Yapmak için bir <xref:System.Windows.FrameworkElement> bir animasyon hedefi, bir ad ayarlayarak verin, <xref:System.Windows.FrameworkElement.Name%2A> özelliği. Kod içinde de kullanmanız gerekir <xref:System.Windows.FrameworkElement.RegisterName%2A> ait olduğu sayfayla öğe adını kaydetmek için yöntem.  
  
-   Yapmak için bir <xref:System.Windows.Freezable> bir animasyon hedef nesne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md) bir ad atamak için. Kod içinde yalnızca kullandığınız <xref:System.Windows.FrameworkElement.RegisterName%2A> ait olduğu sayfayla nesneyi kaydetmek için yöntem.  
  
 Öğe adlandırma örneği bölümlerde sağlamak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod. Adlandırma ve hedefleme hakkında daha ayrıntılı bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Film şeritleri başlangıç ve uygulama  
 Film şeridi başlatmak için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bu ilişkilendirmeyi bir <xref:System.Windows.EventTrigger>. Bir <xref:System.Windows.EventTrigger> belirtilen bir olay meydana geldiğinde hangi eylemlerin yapılacağını açıklayan bir nesnedir. Bu eylemlerden biri olabilir bir <xref:System.Windows.Media.Animation.BeginStoryboard> , film şeridi başlatmak için kullandığınız eylem. Olay tetikleyicileri olay işleyicilerine kavram olarak benzer olduklarından, uygulamanızın belirli bir olaya nasıl yanıt vereceğini belirtmenize olanak verir. Olay işleyicileri, olay tetikleyicileri tam olarak açıklanan olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; başka bir kod gereklidir.  
  
 Başlamak için bir <xref:System.Windows.Media.Animation.Storyboard> kodda, kullandığınız bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi <xref:System.Windows.Media.Animation.Storyboard> sınıfı.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Film şeridi etkileşimli olarak denetleme  
 Önceki örnekte gösterilen nasıl başlatılacağı bir <xref:System.Windows.Media.Animation.Storyboard> olay oluştuğunda. Ayrıca etkileşimli bir şekilde denetleyebilirsiniz bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra: duraklatma, sürdürme, durdurabilir, dolgu süresinin ilerleyin, arama ve kaldırma <xref:System.Windows.Media.Animation.Storyboard>. Daha fazla bilgi ve etkileşimli olarak denetlemek nasıl oluşturulduğunu gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Storyboard>, bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Bir animasyon sona erdikten sonra ne olur?  
 <xref:System.Windows.Media.Animation.FillBehavior> Özelliği, bir zaman çizelgesi sona erdiği zaman nasıl davranacağını belirtir. Varsayılan olarak, bir zaman çizelgesi başlatır <xref:System.Windows.Media.Animation.ClockState.Filling> sona erdiğinde. Olan bir animasyon <xref:System.Windows.Media.Animation.ClockState.Filling> son çıkış değerini tutar.  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> Önceki örnekte, çünkü bitmez kendi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği ayarlanmış <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Aşağıdaki örnek, benzer bir animasyon kullanarak bir dikdörtgen canlandırır. Önceki örnekte, farklı <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Bu animasyon özelliklerini varsayılan değerlerinde bırakılır. Bu nedenle, animasyonun 1'den 0 olarak beş saniye içinde ilerler ve durur.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Çünkü, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> olan kendi varsayılan değerinden değiştirilmedi <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animasyon sona erdiğinde son değeri, 0, tutar. Bu nedenle, <xref:System.Windows.UIElement.Opacity%2A> dikdörtgen kalır 0 animasyonun sonra sona erer. Ayarlarsanız <xref:System.Windows.UIElement.Opacity%2A> animasyon hala etkileyen olduğundan başka bir değerle dikdörtgen, kodunuzu herhangi bir etkisi yoktur görünüyor <xref:System.Windows.UIElement.Opacity%2A> özelliği.  
  
 Kodda animasyonlu bir özelliğin denetimini yeniden kazanmak için bir yol kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi için null belirtin <xref:System.Windows.Media.Animation.AnimationTimeline> parametresi. Daha fazla bilgi ve bir örnek için bkz: [bir özellik sonra animasyonu Film şeridi ile ayarlayın](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Bir özellik değeri ayarına sahip olsa da, Not bir <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling> animasyon etkisinin görünüyor, özellik değeri değişmez. Daha fazla bilgi için bkz: [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Veri bağlama ve animasyonları animasyon ekleme  
 Animasyon özelliklerinin çoğu bağlı veya animasyonlu veri olabilir; Örneğin, animasyon <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği bir <xref:System.Windows.Media.Animation.DoubleAnimation>. Ancak, zamanlama sistemi çalışma biçimi nedeniyle ilişkili veya hareketli animasyonların diğer verileri gibi davranır değil veri ilişkili veya bu nesneleri animasyonlu. Davranışlarını anlamak için onu bir özelliğe bir animasyon uygulamak ne anlama geldiğini anlamak için yardımcı olur.  
  
 Animasyon nasıl oluşturulacağını gösterir önceki bölümdeki örnek başvurmak <xref:System.Windows.UIElement.Opacity%2A> dikdörtgenin. Önceki örnekte dikdörtgen yüklendiğinde, olay tetikleyicisi geçerlidir <xref:System.Windows.Media.Animation.Storyboard>. Zamanlama sistemi bir kopyasını oluşturur <xref:System.Windows.Media.Animation.Storyboard> ve animasyonunun. Bu kopyalar dondurulmuş (salt okunur yapılmış) ve <xref:System.Windows.Media.Animation.Clock> nesneleri bunlardan oluşturulur. Bu saatler hedeflenen özelliklerin animasyonunun gerçek iş yapın.  
  
 Zamanlama sistemi için saat oluşturur <xref:System.Windows.Media.Animation.DoubleAnimation> tarafından belirtilen özellik ve nesne geçerli ve <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> , <xref:System.Windows.Media.Animation.DoubleAnimation>. Bu durumda, zamanlama sistem saati uygular <xref:System.Windows.UIElement.Opacity%2A> "MyRectangle" adlı nesne özelliği  
  
 Bir saat için de oluşturulur, ancak <xref:System.Windows.Media.Animation.Storyboard>, saat için herhangi bir özellik uygulanmıyor. Kendi alt saati için oluşturulan saat denetlemek için amacı olan <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Bir animasyon veri bağlama veya animasyon değişiklikleri yansıtacak şekilde kendi saatinin yeniden oluşturulması gerekir. Saatler sizin için otomatik olarak yeniden oluşturulmaz. Animasyonun değişiklikleri yansıtacak sağlamak için şeridini kullanarak yeniden bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi. Bu yöntemlerden birini kullandığınızda, animasyonun yeniden başlatır. Kodda, kullandığınız <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> film şeridi kaydırılacak yöntemi önceki konumuna yedekleyin.  
  
 Örnek veri bağlama için bkz: [anahtar eğri animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160011). Animasyon ve zamanlama sisteminin nasıl çalıştığı hakkında daha fazla bilgi için bkz: [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Animasyon etmenin diğer yolları  
 Bu genel bakıştaki örnekler film şeritleri kullanarak animasyon gösterilmektedir. Kod kullandığınızda, diğer çeşitli yollarla animasyon ekleyebilirsiniz. Daha fazla bilgi için bkz: [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Animasyon örnekleri  
 Aşağıdaki örnekleri uygulamalarınıza animasyon ekleme başlamanıza yardımcı olabilir.  
  
-   [Öğesinden, için ve animasyon hedef değerleri örneği](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Farklı From/To/By ayarlarını gösterir.  
  
-   [Animasyon zamanlama davranışı örneği](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Animasyonun zamanlama davranışını kontrol edebilirsiniz farklı yollarını gösterir. Bu örnek ayrıca gösterir nasıl verilere hedef değeri animasyonun bağlayın.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Animasyon ve Zamanlama Sistemine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|Zamanlama sistemi nasıl kullandığını açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> animasyonları oluşturmanızı sağlayan sınıflar.|  
|[Animasyon İpuçları ve Püf Noktaları](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|Performans gibi animasyonları ile ilgili sorunları çözmek için yararlı ipuçları listeler.|  
|[Özel Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|Anahtar çerçeveler, animasyon sınıfları veya çerçeve başına geri aramalar animasyon sistemini genişletmek açıklar.|  
|Gelen/İçin/Göre Animasyonlarına Genel Bakış|İki değer arasında geçişler animasyonun oluşturmayı açıklar.|  
|[Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|İlişkilendirme yöntemi denetleme olanağı dahil olmak üzere birden çok hedef değeri olan bir animasyon oluşturmayı açıklar.|  
|[Hızlandırma İşlevleri](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|Matematik formülleri geçirmek gibi gerçekçi davranışı elde etmek üzere, animasyonları uygulamak açıklanmaktadır.|  
|[Yol Animasyonlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|Taşımak veya karmaşık bir yolda bir nesne döndürmek açıklar.|  
|[Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|Film şeritleri kullanarak özellik animasyonları, yerel animasyonları, saatler ve çerçeve başına animasyonları açıklar.|  
|[Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|Film şeritleri ile birden çok zaman çizelgelerini karmaşık animasyon oluşturmak için nasıl kullanılacağını açıklar.|  
|[Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|Açıklar <xref:System.Windows.Media.Animation.Timeline> türleri ve animasyonları kullanılan özellik.|  
|[Zamanlama Olaylarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|Kullanılabilir olaylarını açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> gibi zaman çizelgesi noktalarında kod yürütmek için nesneleri başlamak, duraklatma, sürdürme, Atla veya durdurmak.|  
|[Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|Animasyonları ve zamanlamaları, uygulamanızda kullanmak için kod örnekleri içerir.|  
|[Saatler ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|Kullanmak için kod örnekleri içerir <xref:System.Windows.Media.Animation.Clock> uygulamanızda nesnesi.|  
|[Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|Anahtar çerçeve animasyonları, uygulamanızda kullanmak için kod örnekleri içerir.|  
|[Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|Yol animasyonları, uygulamanızda kullanmak için kod örnekleri içerir.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
