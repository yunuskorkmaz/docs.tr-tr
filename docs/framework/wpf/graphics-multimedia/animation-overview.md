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
ms.openlocfilehash: e8717ca50f7275e2739be4d4ee5d677e081d552d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615985"
---
# <a name="animation-overview"></a>Animasyona Genel bakış
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] güçlü bir etkileyici kullanıcı arabirimleri ve çekici belgeler oluşturmanıza olanak sağlayan grafikleri ve düzeni özellikler kümesi sağlar. Animasyon etkileyici kullanıcı arabirimi daha muhteşem ve kullanışlı hale getirebilirsiniz. Animasyonlu bir uygulama veya yalnızca bir arka plan rengi animasyon tarafından <xref:System.Windows.Media.Transform>, etkileyici ekran geçişleri oluşturabilir ya da yararlı görsel ipuçlarını sağlama.  
  
 Bu genel bakışta tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon ve zamanlama sistemi. Animasyonu üzerinde odaklanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel Taslaklar kullanarak nesneleri.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Animasyonlar Tanıtımı  
 Animasyon hızla görüntüleri, son her biraz farklı bir dizi dönüşüm tarafından oluşturulan bir görünümü olur. Beyin, görüntü grubunun değişen tek bir Sahne algılar. Filmde, her saniye birçok fotoğraflar veya çerçeveleri kayıt Kameralar'ı kullanarak bu izlenimi oluşturulur. Çerçeve kayıttan projektörüne tarafından İzleyici hareketli resim görür.  
  
 Bir bilgisayarda animasyonu da benzerdir. Örneğin, çizim görünümü dışında bir dikdörtgen yavaşça kılan bir program gibi çalışabilir.  
  
- Zamanlayıcı bir program oluşturur.  
  
- Program, Zamanlayıcının ne kadar süre geçtiğini görmek için belirlenen aralıklarla denetler.  
  
- Zamanlayıcı, program denetler her zaman geçerli ne kadar zaman geçti bağlı olarak dikdörtgen opaklık değerini hesaplar.  
  
- Program dikdörtgen yeni değerle güncelleştirir ve onu yeniden çizer.  
  
 Öncesinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] geliştiriciler gerekiyordu oluşturup kendi zamanlama sistemleri yönetmek veya özel kitaplıkları kullanın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kod kullanıma sunulan bir etkin zamanlama sistemi içerir ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve derin bir şekilde tümleşmiş içine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon denetimleri ve diğer grafik nesneleri kolaylaştırır.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamanlama sistemi yönetme ve ekran verimli bir şekilde yeniden Sahne Arkası tüm işini gerçekleştirir. Bu, söz konusu efektler elde mekanizması yerine oluşturmak istediğiniz efektleri odaklanmak etkinleştirdiğiniz zamanlama sınıflar sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca animasyon temel sınıflarını sınıflarınızı devraldığı kendi animasyon oluşturmak için özelleştirilmiş animasyonları üretmek için kolaylaştırır. Bu özel animasyonlar birçok animasyon sınıfları performans avantajlarını elde edin.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>WPF özellik animasyon sistemi  
 Zamanlama sistemiyle ilgili birkaç önemli kavram anlarsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları kullanımı daha kolay olabilir. En önemli bulunduğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kendilerine özgü özelliklere animasyon uygulayarak nesnelere animasyon ekleme. Örneğin, çerçeve öğesini yapmak için animasyon, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri. Soldurma görünümünden bir nesne için animasyon ekleme, <xref:System.Windows.UIElement.Opacity%2A> özelliği.  
  
 Bir özellik animasyon özelliklerini kullanabilmek aşağıdaki üç gereksinimleri karşılaması gerekir:  
  
- Bağımlılık özelliği olmalıdır.  
  
- Devralınan bir sınıfa ait olmalıdır <xref:System.Windows.DependencyObject> ve uygulayan <xref:System.Windows.Media.Animation.IAnimatable> arabirimi.  
  
- Kullanılabilir uyumlu bir animasyon türü olmalıdır. (Varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir sağlamaz kendi oluşturabilirsiniz. Bkz: [özel animasyonlara genel bakış](custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sahip çok sayıda nesne içeren <xref:System.Windows.Media.Animation.IAnimatable> özellikleri. Gibi denetimler <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.TabControl>hem de <xref:System.Windows.Controls.Panel> ve <xref:System.Windows.Shapes.Shape> nesneleri devralmanız <xref:System.Windows.DependencyObject>. Bunların özelliklerinin çoğu bağımlılık özelliklerdir.  
  
 Animasyonları neredeyse her yerden, denetim şablonları ve stilleri de içeren kullanabilirsiniz. Animasyon, görsel olması gerekmez; Bunlar bu bölümde açıklanan ölçütleri karşıladığı durumlarda kullanıcı arabiriminin bir parçası olmayan nesneler animasyon uygulayabilirsiniz.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Örnek: Bir öğe Fade görünümü içine ve dışına olun  
 Bu örnek nasıl kullanılacağını gösterir. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir bağımlılık özelliğinin değeri canlandırmak için animasyon. Kullandığı bir <xref:System.Windows.Media.Animation.DoubleAnimation>, bir türü oluşturan bir animasyon <xref:System.Double> animasyon uygulamak için değerleri <xref:System.Windows.UIElement.Opacity%2A> özelliği bir <xref:System.Windows.Shapes.Rectangle>. Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> görünümü içine ve dışına kaybolur.  
  
 Örneğin ilk bölümünü oluşturur bir <xref:System.Windows.Shapes.Rectangle> öğesi. Bir animasyon oluşturmak ve dikdörtgenin uygulama adımları Göster <xref:System.Windows.UIElement.Opacity%2A> özelliği.
  
 Aşağıdakileri nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Shapes.Rectangle> öğesinde bir <xref:System.Windows.Controls.StackPanel> XAML içinde.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 Aşağıdakileri nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Shapes.Rectangle> öğesinde bir <xref:System.Windows.Controls.StackPanel> kod.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Bölüm 1: DoubleAnimation oluşturma  
 Öğenin içine ve dışına görünümü Soldurma yapmanın bir yolu olan animasyon uygulamak için kendi <xref:System.Windows.UIElement.Opacity%2A> özelliği. Çünkü <xref:System.Windows.UIElement.Opacity%2A> özelliği türüdür <xref:System.Double>, ihtiyacınız double değerleri üreten bir animasyonu. A <xref:System.Windows.Media.Animation.DoubleAnimation> bir animasyonun. A <xref:System.Windows.Media.Animation.DoubleAnimation> iki double değerleri arasında bir geçiş oluşturur. Başlangıç değerini belirtmek için ayarlamanız, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği. Bitiş değerini belirtmek için ayarlamanız, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.  
  
1. Bir opaklık değerini `1.0` nesneyi tamamen opak ve bir opaklık değerini getirir `0.0` tamamen görünmez hale getirir. Animasyon geçişi yapmaya `1.0` için `0.0` ayarladığınız kendi <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini `1.0` ve kendi <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini `0.0`. Aşağıdakileri nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.Animation.DoubleAnimation> XAML içinde.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     Aşağıdakileri nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.Animation.DoubleAnimation> kod.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2. Ardından, belirtmelisiniz bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Bir animasyon başlangıç değerine hedef değerine gidin ne kadar sürer belirtir. Aşağıdakileri nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> XAML içinde beş saniye.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     Aşağıdakileri nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kodda beş saniye.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3. Önceki kod, gelen geçiş animasyon gösterdi `1.0` için `0.0`, tamamen opak görünümden tamamen görünmez soluklaştırılacak hedef öğenin neden olur. Kaybolduktan sonra tekrar görüntüye Soldurma öğesi sağlamak için ayarlayın <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> animasyona özelliği `true`. Animasyon belirsiz bir süre boyunca yineleme yapmak için ayarlanmış kendi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Aşağıdakileri nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> XAML özellikleri.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     Aşağıdakileri nasıl ayarlanacağını gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> kod özellikleri.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Bölüm 2: Bir film şeridi oluşturun  
 Bir nesneye animasyon uygulamak için oluşturduğunuz bir <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> nesneyi belirlemek üzere özellikler ve animasyon uygulamak için özellik bağlı.  
  
1. Oluşturma <xref:System.Windows.Media.Animation.Storyboard> ve animasyonu alt öğe olarak ekleyin. Aşağıdakileri nasıl oluşturulacağını gösterir <xref:System.Windows.Media.Animation.Storyboard> XAML içinde.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]    
  
     Oluşturulacak <xref:System.Windows.Media.Animation.Storyboard> kodda bildirmek bir <xref:System.Windows.Media.Animation.Storyboard> sınıf düzeyinde değişken.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Ardından başlatmak <xref:System.Windows.Media.Animation.Storyboard> ve animasyonu alt öğe olarak ekleyin.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2. <xref:System.Windows.Media.Animation.Storyboard> Animasyon uygulamak nereye bilmesi gerekir. Kullanım <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ekli özellik animasyon uygulamak için nesne belirtmek için. Aşağıdaki hedef adını ayarlama işlemi gösterilmektedir <xref:System.Windows.Media.Animation.DoubleAnimation> için `MyRectangle` XAML içinde.  
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     Aşağıdaki hedef adını ayarlama işlemi gösterilmektedir <xref:System.Windows.Media.Animation.DoubleAnimation> için `MyRectangle` kod.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3. Kullanım <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> ekli özellik oynatmak özelliği belirtmek için. Aşağıdaki animasyon nasıl yapılandırıldığını gösterir. hedef <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Windows.Shapes.Rectangle> XAML içinde.
  
     [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     Aşağıdaki animasyon nasıl yapılandırıldığını gösterir. hedef <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Windows.Shapes.Rectangle> kod.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> söz dizimi ve ek örnekler için bkz: [görsel taslaklara genel bakış](storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Bölüm 3 (XAML): Film şeridini bir tetikleyici ile ilişkilendirme  
 Başlatmak ve uygulamak için en kolay yolu bir <xref:System.Windows.Media.Animation.Storyboard> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir olay tetikleyicisi kullanmaktır. Bu bölüm nasıl ilişkilendirildiğini gösterir <xref:System.Windows.Media.Animation.Storyboard> XAML içinde bir tetikleyici ile.  
  
1. Oluşturma bir <xref:System.Windows.Media.Animation.BeginStoryboard> nesne ve film şeridiniz ilişkilendirin. A <xref:System.Windows.Media.Animation.BeginStoryboard> bir tür <xref:System.Windows.TriggerAction> uygulayan ve başlatan bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2. Oluşturma bir <xref:System.Windows.EventTrigger> ve ekleme <xref:System.Windows.Media.Animation.BeginStoryboard> için kendi <xref:System.Windows.EventTrigger.Actions%2A> koleksiyonu. Ayarlama <xref:System.Windows.EventTrigger.RoutedEvent%2A> özelliği <xref:System.Windows.EventTrigger> başlatmak istediğiniz yönlendirilmiş olay <xref:System.Windows.Media.Animation.Storyboard>. (Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md).)  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3. Ekleme <xref:System.Windows.EventTrigger> için <xref:System.Windows.FrameworkElement.Triggers%2A> dikdörtgenin koleksiyonu.  
  
     [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>(Kod) 3. Bölüm: Film şeridini bir olay işleyicisi ile ilişkilendirme  
 Başlatmak ve uygulamak için en kolay yolu bir <xref:System.Windows.Media.Animation.Storyboard> kodda bir olay işleyicisi kullanmaktır. Bu bölüm nasıl ilişkilendirildiğini gösterir <xref:System.Windows.Media.Animation.Storyboard> olay işleyicisinde kodu ile.  
  
1. Kaydolun <xref:System.Windows.FrameworkElement.Loaded> dikdörtgenin olay.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2. Olay işleyicisi bildirin. Olay işleyicisinde kullanın <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> film şeridi uygulamak için yöntemi.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Tam Örnek  
 XAML görünümünde içine ve dışına belirerek bir dikdörtgen oluşturulacağını gösterir.  
  
 [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Aşağıdaki kod görünümünde içine ve dışına belirerek bir dikdörtgen oluşturulacağını gösterir.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Animasyon türü  
 Özellik değerlerini animasyonlar oluşturması nedeniyle farklı animasyon türlerinin farklı özellik türleri için mevcut. Alan özelliği oynatmak bir <xref:System.Double>, gibi <xref:System.Windows.FrameworkElement.Width%2A> bir öğe özelliğini kullanın üreten bir animasyon <xref:System.Double> değerleri. Alan özelliği oynatmak bir <xref:System.Windows.Point>, üreten bir animasyon kullanın <xref:System.Windows.Point> değerleri ve benzeri. Farklı özellik türleri sayısı nedeniyle, birçok animasyon sınıfları vardır <xref:System.Windows.Media.Animation> ad alanı. Neyse ki, bunları ayırt kolaylaştırır katı bir adlandırma kuralı izleyin:  
  
- \<*Tür*> animasyon  
  
     Bir "From/To/By" veya "temel" animasyon olarak bilinir, bunlar arasında bir başlangıç ve bitiş değeri ya da bir uzaklık değeri ekleyerek başlangıç değerine animasyon ekleme.  
  
    - Başlangıç değeri belirtmek için animasyonun başlangıç özelliğini ayarlayın.  
  
    - Bitiş değeri belirtmek için animasyonun To özelliğini ayarlayın.  
  
    - Bir uzaklık değeri belirtmek için animasyonun By özelliğini ayarlayın.  
  
     Kullanmak için en basit olduğundan bu genel bakışta örneklerde bu animasyonları kullanın. FROM/için/göre animasyonlarına u animasyonlarına genel bakış, ayrıntılı açıklanmıştır.  
  
- \<*Tür*> AnimationUsingKeyFrames  
  
     Anahtar çerçeve animasyon hedef değerleri herhangi bir sayıda belirtin ve hatta kendi ilişkilendirme yöntemini kontrol gelen/için/göre animasyonlarına daha güçlü özellikler. Bazı türleri yalnızca ana kare animasyonları ile animasyon uygulanabilir. Anahtar çerçeve animasyonları ayrıntılı olarak açıklanmıştır [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
- \<*Tür*> AnimationUsingPath  
  
     Yol animasyonları geometrik yol animasyonlu değerler üretmek için kullanmanızı sağlar.  
  
- \<*Tür*> AnimationBase  
  
     Soyut sınıf, uygularken canlandırır, bir \< *türü*> değeri. Bu sınıf için temel sınıf olarak hizmet veren \< *türü*> animasyon ve \< *türü*> AnimationUsingKeyFrames sınıflar. Yalnızca kendi özel animasyon oluşturmak istiyorsanız doğrudan bu sınıfları ile uğraşmak zorunda. Aksi durumda, bir \< *türü*> animasyon veya ana kare\<*türü*> animasyon.  
  
 Çoğu durumda, kullanmak istediğiniz \< *türü*> gibi animasyon sınıfları <xref:System.Windows.Media.Animation.DoubleAnimation> ve <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 Aşağıdaki tabloda, birkaç ortak animasyon türü ve ile kullanıldıklarından bazı özellikleri gösterir.  
  
|Özellik türü|Karşılık gelen (From/To/By) temel animasyon|Karşılık gelen anahtar çerçeve animasyonu|Karşılık gelen yol animasyonu|Kullanım örneği|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|None|Animasyon <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> veya <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animasyon <xref:System.Windows.FrameworkElement.Width%2A> , bir <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.FrameworkElement.Height%2A> , bir <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animasyon <xref:System.Windows.Media.EllipseGeometry.Center%2A> birini konumlandırmak bir <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Yok.|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|None|Animasyon <xref:System.Windows.Controls.TextBlock.Text%2A> , bir <xref:System.Windows.Controls.TextBlock> veya <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Animasyon zaman çizelgeleri olan  
 Tüm animasyon türleri devralınacak <xref:System.Windows.Media.Animation.Timeline> sınıfı; bu nedenle, tüm animasyon zaman çizelgelerini, özelleştirilmiş türleridir. A <xref:System.Windows.Media.Animation.Timeline> zaman bir parçasını tanımlar. Belirtebileceğiniz *zamanlama davranışları* zaman çizelgesinin: kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kaç kez olduğu için yinelenen ve hatta zaman ne kadar hızlı ilerler.  
  
 Bir animasyon olduğundan bir <xref:System.Windows.Media.Animation.Timeline>, ayrıca zaman kesimini temsil eder. Ancak, belirtilen zaman kesimi ilerledikçe animasyon de çıkış değerleri hesaplar (veya <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). Animasyon veya "çalar", ilişkili olduğu özelliğini güncelleştirir.  
  
 Üç sık kullanılan zamanlama özellikleri <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>Duration özelliği  
 Daha önce belirtildiği gibi bir zaman çizelgesi zaman kesimini temsil eder. Bu kesimin uzunluğu tarafından belirlenir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> genellikle kullanılarak belirtilen zaman çizelgesinin bir <xref:System.Windows.Duration.TimeSpan%2A> değeri. Zaman Çizelgesi süresinin sonuna ulaştığında, bir yineleme tamamlandı.  
  
 Bir animasyon kullanır, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliğinin geçerli değeri belirlemek için. Belirtmezseniz, bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> değeri isteğe bağlı olarak, animasyon için varsayılan olan 1 saniye kullanır.  
  
 Aşağıdaki sözdizimi basitleştirilmiş bir sürümünü gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] öznitelik sözdizimi <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği.  
  
*Saat* `:` *dakika* `:` *saniye*
  
 Aşağıdaki tabloda çeşitli gösterilmektedir <xref:System.Windows.Duration> ayarları ve sonuçta elde edilen değerleri.  
  
|Ayar|Sonuç değeri|  
|-------------|---------------------|  
|0:0:5.5|5.5 saniye.|  
|0:30:5.5|30 dakika ve 5.5 saniye.|  
|1:30:5.5|1 saat, 30 dakika, ve 5.5 saniye.|  
  
 Belirtmek için tek yönlü bir <xref:System.Windows.Duration> kodda kullanmaktır <xref:System.TimeSpan.FromSeconds%2A> yöntemi oluşturmak için bir <xref:System.TimeSpan>, ardından yeni bir bildirmek <xref:System.Windows.Duration> kullanan yapı <xref:System.TimeSpan>.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Duration> değerleri ve tam [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sözdizimine bakın <xref:System.Windows.Duration> yapısı.  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Özelliği, zaman çizelgesinin sonuna ulaştıktan sonra geriye dönük çalıp olup olmadığını belirtir, <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Bu animasyon özelliğini ayarlarsanız `true`, sonuna ulaştıktan sonra animasyon tersine çevirir. kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A>başlangıç değerine geri bitiş değerinden oynar. Varsayılan olarak, bu özellik, `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği, bir zaman çizelgesinin kaç kez belirtir. Varsayılan olarak, bir yineleme sayısı zaman çizelgelerine sahip `1.0`, bunlar oynayacağı anlamına gelir, zaman ve tüm tekrarlamayın.  
  
 Bu özellikler ve diğerleri hakkında daha fazla bilgi için bkz: [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Bir özelliğe animasyon uygulama  
 Önceki bölümlerde animasyon ve zamanlama özelliklerini farklı türleri açıklanmaktadır. Bu bölümde, animasyon uygulamak istediğiniz özelliğe animasyon uygulamak gösterilmektedir. <xref:System.Windows.Media.Animation.Storyboard> nesnelerin özelliklerine animasyon uygulamak için bir yol sağlar. A <xref:System.Windows.Media.Animation.Storyboard> olduğu bir *kapsayıcı zaman çizelgesi* içerdiği animasyon için hedefleme bilgileri sağlar.  
  
### <a name="targeting-objects-and-properties"></a>Nesnelerle ve özelliklerle hedefleme  
 <xref:System.Windows.Media.Animation.Storyboard> Sağlar sınıfını <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> iliştirilmiş özellikler. Bir animasyon üzerindeki bu özelliklerini ayarlayarak, animasyonun ne animasyon uygulamak söyleyin. Ancak, bir nesneyi bir animasyon hedefleyebilir önce nesne genellikle bir ad verilmelidir.  
  
 Bir ad atamak bir <xref:System.Windows.FrameworkElement> bir ad atamaktan farklı bir <xref:System.Windows.Freezable> nesne. Çoğu denetimler ve panolar framework öğeler; Ancak, Fırçalar, Dönüşüm ve geometriler gibi tamamen grafik nesnelerin çoğu freezable nesnelerine uygulanır. Bir tür olup olmadığından emin değilseniz, bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.Freezable>, başvurmak **devralma hiyerarşisi** başvuru belgesini bölümü.  
  
- Yapmak için bir <xref:System.Windows.FrameworkElement> bir animasyon hedef, ayarlayarak adlandırırsınız kendi <xref:System.Windows.FrameworkElement.Name%2A> özelliği. Kod içinde de kullanmalısınız <xref:System.Windows.FrameworkElement.RegisterName%2A> öğe adı ait olduğu için sayfa ile kaydetmek için yöntemi.  
  
- Yapmak için bir <xref:System.Windows.Freezable> içinde bir animasyon hedefi nesnesi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız [x: Name yönergesi](../../xaml-services/x-name-directive.md) bir ad atamak için. Kod içinde yalnızca kullandığınız <xref:System.Windows.FrameworkElement.RegisterName%2A> nesneyi ait olduğu için sayfa ile kaydetmek için yöntemi.  
  
 Aşağıdaki bölümlerde bir öğedeki adlandırma örneği sağlamak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod. Adlandırma ve hedefleme hakkında daha ayrıntılı bilgi için bkz. [görsel taslaklara genel bakış](storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Uygulama ve görsel Taslaklar başlatılıyor  
 İçinde bir film şeridi başlatmak için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], onunla ilişkilendirmek bir <xref:System.Windows.EventTrigger>. Bir <xref:System.Windows.EventTrigger> belirtilen bir olay meydana geldiğinde hangi eylemleri açıklayan bir nesnedir. Bu eylemlerden biri olabilir bir <xref:System.Windows.Media.Animation.BeginStoryboard> film şeridiniz başlatmak için kullanacağınız eylem. Uygulamanız için belirli bir olaya nasıl yanıt verdiğini belirlemek etkinleştirmek için olay tetikleyicilerini olay işleyicilerine kavram olarak benzerdir. Olay işleyicileri, olay tetikleyicilerini tam olarak açıklanan olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; başka bir kod gereklidir.  
  
 Başlamak için bir <xref:System.Windows.Media.Animation.Storyboard> kodda kullanabileceğiniz bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi <xref:System.Windows.Media.Animation.Storyboard> sınıfı.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Etkileşimli bir görsel taslak denetimi  
 Önceki örnekte gösterilen nasıl başlatılacağı bir <xref:System.Windows.Media.Animation.Storyboard> bir olay gerçekleştiğinde. Ayrıca etkileşimli bir şekilde denetleyebilirsiniz bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra: duraklatma, sürdürme, durdurabilir, dolgu süresinin ilerleyin, arama ve Kaldır <xref:System.Windows.Media.Animation.Storyboard>. Daha fazla bilgi ve etkileşimli olarak denetleme gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Storyboard>, bkz: [görsel taslaklara genel bakış](storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Bir animasyonu bittikten sonra ne olur?  
 <xref:System.Windows.Media.Animation.FillBehavior> Özelliği, sona erdiğinde zaman çizelgesi nasıl davranacağını belirtir. Varsayılan olarak, bir zaman çizelgesi başlatılır <xref:System.Windows.Media.Animation.ClockState.Filling> sona erdiğinde. Olan bir animasyon <xref:System.Windows.Media.Animation.ClockState.Filling> son çıktı değerini korur.  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation> Önceki örnekte, çünkü bitmez, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. Aşağıdaki örnek, benzer bir animasyon kullanarak bir dikdörtgen canlandırır. Önceki örnekte, farklı <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> varsayılan değerlerinde animasyon özellikleri değişmeden kalır. Bu nedenle, animasyon, 1. 0 olarak beş saniye içinde ilerler ve durur.  
  
 [!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Çünkü, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> olan kendi varsayılan değerinden değiştirilmedi <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, animasyon sona erdiğinde son değer, 0, tutar. Bu nedenle, <xref:System.Windows.UIElement.Opacity%2A> dikdörtgen inene 0 animasyon sonra sona erer. Ayarlarsanız <xref:System.Windows.UIElement.Opacity%2A> animasyon hala etkileyen çünkü başka bir değerle dikdörtgen, kodunuzu hiçbir etkisi görünüyor <xref:System.Windows.UIElement.Opacity%2A> özelliği.  
  
 Kodda bir animasyonlu özelliğin denetimi yeniden elde etmek için tek bir yolu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi için null belirtin <xref:System.Windows.Media.Animation.AnimationTimeline> parametresi. Daha fazla bilgi ve örnek için bkz. [bir özellik sonra animasyon film şeridi ile ayarlayın](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Olsa da bir özellik değerini not bir <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling> animasyon görünür herhangi bir etkisi yoktur, özellik değeri değiştirin. Daha fazla bilgi için [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Veri bağlama ve animasyonları animasyon ekleme  
 Animasyon özelliklerinin çoğu bağlı veya animasyon veri olabilir; Örneğin, animasyon uygulayabilirsiniz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği bir <xref:System.Windows.Media.Animation.DoubleAnimation>. Ancak, zamanlama sistemi çalışma biçimi nedeniyle ilişkili veya hareketli animasyonların gibi diğer veri davranmayabilir veri bağlı veya animasyon nesneleri. Davranışlarını anlamak için bu özelliğe animasyon uygulamak ne demek anlamanıza yardımcı olur.  
  
 Animasyon ekleme konusu gösterildi önceki bölümdeki örnek başvurmak <xref:System.Windows.UIElement.Opacity%2A> bir dikdörtgen. Önceki örnekteki dikdörtgenin yüklendiğinde olay tetikleyicisi geçerli <xref:System.Windows.Media.Animation.Storyboard>. Zamanlama sistemi bir kopyasını oluşturur <xref:System.Windows.Media.Animation.Storyboard> ve animasyonunun. Bu kopyalar dondurulmuş (salt okunur yapılır) ve <xref:System.Windows.Media.Animation.Clock> nesneleri bunlardan oluşturulur. Bu saatler, hedeflenen özellikleri, gerçek iş yapın.  
  
 Zamanlama sistemi için bir saat oluşturur <xref:System.Windows.Media.Animation.DoubleAnimation> ve nesnesi ve tarafından belirtilen özellik için geçerli <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> , <xref:System.Windows.Media.Animation.DoubleAnimation>. Bu durumda, zamanlama sistemi saati geçerli <xref:System.Windows.UIElement.Opacity%2A> "MyRectangle" adlı nesne özelliği  
  
 Bir saat için de oluşturulsa <xref:System.Windows.Media.Animation.Storyboard>, saat, herhangi bir özelliğe uygulanmaz. Kendi alt saati, oluşturulduğu saati amacı denetlemektir <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Bir animasyon veri bağlama veya animasyon değişiklikleri yansıtacak şekilde kendi saati üretilmelidir. Saatleri sizin için otomatik olarak yeniden oluşturulmaz. Animasyonun değişiklikleri yansıtacak sağlamak için görsel taslak kullanarak yeniden bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi. Bu yöntemlerden birini kullandığınızda, animasyonun yeniden başlatır. Kod içinde kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> back önceki konumuna film şeridi kaydırmak için yöntemi.  
  
 Örnek veri bağlama için bkz: [anahtar eğrisi animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160011). Animasyon ve zamanlama sistemi nasıl çalıştığı hakkında daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Diğer yolları animasyon ekleme  
 Bu genel bakışta örneklerde görsel Taslaklar kullanarak animasyon ekleme işlemini göstermektedir. Kod kullandığınızda, diğer çeşitli yollarla animasyon uygulayabilirsiniz. Daha fazla bilgi için [özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Animasyon örnekleri  
 Aşağıdaki örnekleri uygulamalarınıza animasyon ekleme başlamanıza yardımcı olabilir.  
  
- [Gelen, için ve göre animasyon hedef değerleri örneği](https://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Farklı From/To/By ayarları gösterir.  
  
- [Animasyon zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Bir animasyon zamanlama davranışını denetleyebileceğiniz farklı yollarını gösterir. Bu örnek ayrıca gösterir nasıl verilere animasyon hedef değeri bağlayın.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)|Zamanlama sistemi nasıl kullandığını açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> animasyonlar oluşturmanıza olanak sağlayan sınıflar.|  
|[Animasyon İpuçları ve Püf Noktaları](animation-tips-and-tricks.md)|Animasyonlarla performans gibi sorunları çözmek için yararlı ipuçları listeler.|  
|[Özel Animasyonlara Genel Bakış](custom-animations-overview.md)|Anahtar çerçeveler, animasyon sınıfları veya çerçeve başına geri çağırmaları animasyon sistemini genişletmek açıklar.|  
|Gelen/İçin/Göre Animasyonlarına Genel Bakış|İki değer geçişleri bir animasyon oluşturmayı açıklar.|  
|[Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)|Bir animasyon ilişkilendirme yöntemi denetleme olanağı dahil olmak üzere birden çok hedef değerle oluşturmayı açıklar.|  
|[Hızlandırma İşlevleri](easing-functions.md)|Matematik formülleri geçirmek gibi gerçekçi davranışını almak için animasyon uygulamak açıklanmaktadır.|  
|[Yol Animasyonlarına Genel Bakış](path-animations-overview.md)|Taşıma veya karmaşık bir yolda nesneyi döndürme işlemini açıklamaktadır.|  
|[Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)|Görsel Taslaklar kullanarak özellik animasyonları, yerel animasyonları, saatler ve başına-çerçeve animasyonlara açıklar.|  
|[Görsel Taslaklara Genel Bakış](storyboards-overview.md)|Görsel Taslaklar ile birden çok zaman çizelgesi karmaşık animasyon oluşturmak için nasıl kullanılacağını açıklar.|  
|[Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)|Açıklar <xref:System.Windows.Media.Animation.Timeline> türler ve Özellikler içinde animasyon kullanılır.|  
|[Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)|Kullanılabilir olaylarını açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> nesneleri gibi zaman çizelgesi noktalarında kod yürütmek başlamak, duraklatma, sürdürme, atlayın veya durdurmak.|  
|[Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)|Animasyonları ve zaman çizelgeleri uygulamanızda kullanmak için kod örneği içerir.|  
|[Saatler ile İlgili Nasıl Yapılır Konuları](clocks-how-to-topics.md)|Kullanmak için kod örnekleri içeren <xref:System.Windows.Media.Animation.Clock> uygulamanızdaki bir nesne.|  
|[Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)|Anahtar-çerçeve animasyonlara uygulamanızda kullanmak için kod örneği içerir.|  
|[Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)|Yol animasyonları uygulamanızdaki kullanma için kod örnekleri içerir.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>
