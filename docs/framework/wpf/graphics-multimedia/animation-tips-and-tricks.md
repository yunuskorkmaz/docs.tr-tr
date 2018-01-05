---
title: "Animasyon İpuçları ve Püf Noktaları"
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
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fceebbd3da7a0643e744d80a55cb1c953eba3bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="animation-tips-and-tricks"></a>Animasyon İpuçları ve Püf Noktaları
Animasyonları ile çalışırken [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir dizi ipuçları vardır ve, animasyonları yapabilirsiniz püf noktaları daha iyi performans ve yükünden kurtarın.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Genel sorunlar  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Bir kaydırma çubuğunun konumunu animasyon veya kaydırıcı donuyor  
 Kaydırma çubuğu veya sahip bir animasyon kullanarak kaydırıcı konumunu hareketli hale getirmeyi varsa bir <xref:System.Windows.Media.Animation.FillBehavior> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (varsayılan değer) kullanıcı artık kaydırma çubuğu veya kaydırıcıyı mümkün olmayacaktır. Animasyon sona olsa da, hedef özelliğin temel değerini hala geçersiz kılma nedeni. Özelliğin geçerli değeri geçersiz kılmasını animasyon durdurmak için kaldırmak veya bu verin bir <xref:System.Windows.Media.Animation.FillBehavior> , <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Daha fazla bilgi ve bir örnek için bkz: [bir özellik sonra animasyonu Film şeridi ile ayarlayın](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animasyonun çıktısını animasyon hiçbir etkisi yoktur  
 Başka bir animasyon çıktısını bir nesne animasyon olamaz. Kullanırsanız, örneğin, bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> animasyon için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> gelen bir <xref:System.Windows.Media.RadialGradientBrush> için bir <xref:System.Windows.Media.SolidColorBrush>, tüm özelliklerini hale getirmeyi <xref:System.Windows.Media.RadialGradientBrush> veya <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Bir özelliğin değerini animasyon sonra değiştiremezsiniz  
 Bazı durumlarda bile animasyon sona erdikten sonra animasyonlu sonra bir özelliğin değerini değiştiremezsiniz görünebilir. Animasyon sona olsa da, özelliğin temel değerini hala geçersiz kılma nedeni. Özelliğin geçerli değeri geçersiz kılmasını animasyon durdurmak için kaldırmak veya bu verin bir <xref:System.Windows.Media.Animation.FillBehavior> , <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Daha fazla bilgi ve bir örnek için bkz: [bir özellik sonra animasyonu Film şeridi ile ayarlayın](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Bir zaman çizelgesi değiştirmenin etkisi olmaz  
 Ancak çoğu <xref:System.Windows.Media.Animation.Timeline> özellikleri canlandırılabilir ve etkin bir özellik değerlerini değiştirme veri bağlanabilen <xref:System.Windows.Media.Animation.Timeline> etkisinin gibi görünüyor. Çünkü, bir <xref:System.Windows.Media.Animation.Timeline> olan başladığında zamanlama sistemi bir kopyasını oluşturur <xref:System.Windows.Media.Animation.Timeline> ve oluşturmak için kullandığı bir <xref:System.Windows.Media.Animation.Clock> nesnesi. Özgün değiştirme sistemin kopyası üzerinde etkisi yoktur.  
  
 İçin bir <xref:System.Windows.Media.Animation.Timeline> değişiklikleri yansıtacak şekilde kendi saati yeniden ve önceden oluşturulmuş saatle değiştirmek için kullanılması gerekir. Saatler sizin için otomatik olarak yeniden oluşturulmaz. Zaman Çizelgesi değişiklikleri uygulamak için çeşitli yollar şunlardır:  
  
-   Zaman Çizelgesi ait olduğu veya bir <xref:System.Windows.Media.Animation.Storyboard>, bunu kendi film şeridi kullanarak uygulayarak değişiklikleri yansıtacak yapabileceğiniz bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi. Bu da animasyonu yeniden başlatma yan etkisi vardır. Kodda, kullandığınız <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> film şeridi ilerletmek için yöntemi önceki konumuna yedekleyin.  
  
-   Bir animasyon doğrudan özelliğini kullanarak bir uyguladıysanız <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi, çağrı <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemini tekrar ve değiştirilmiş animasyon geçirin.  
  
-   Doğrudan saati düzeyinde çalışıyorsanız ve saatler yeni bir dizi uygulama oluşturup bunları oluşturulan saatler önceki kümesini değiştirmek için kullanabilirsiniz.  
  
 Zaman çizelgeleri ve saatler hakkında daha fazla bilgi için bkz: [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop beklendiği gibi çalışmıyor  
 Zamanlar ayarlarken <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğine <xref:System.Windows.Media.Animation.FillBehavior.Stop> ne zaman gibi herhangi bir etkisi yoktur görünüyor bir animasyon "aktarır devre dışı" diğerine içerdiğinden bir <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> ayarıyla <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> Taşımak için animasyonlu <xref:System.Windows.Shapes.Rectangle> geçici <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Bu bölümdeki örnekleri, bazı durumları göstermek için önceki nesneleri kullanır. burada <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği olmayan kendisine beklediğiniz gibi davranır.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Durdur" ve birden çok animasyon ile HandoffBehavior  
 Bazen bir animasyon yoksayar gibi görünüyor, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ikinci bir animasyon tarafından değiştirildiğinde özelliği. İki oluşturur aşağıdaki örneği ele <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve bunları aynı animasyon için kullandığı <xref:System.Windows.Media.TranslateTransform> önceki örnekte gösterilen.  
  
 İlk <xref:System.Windows.Media.Animation.Storyboard>, `B1`, canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> sağa dikdörtgen 350 piksel taşır 350 için 0 ile. Animasyon süresinin sonuna ulaştığında ve yürütmeyi durdurduğunda <xref:System.Windows.Media.TranslateTransform.X%2A> özelliğinin özgün değeri için 0 döner. Sonuç olarak, dikdörtgen sağa doğru 350 piksel taşır ve özgün konumuna geri atlar.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 İkinci <xref:System.Windows.Media.Animation.Storyboard>, `B2`, ayrıca canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği aynı <xref:System.Windows.Media.TranslateTransform>. Çünkü yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> bu animasyonun özellik <xref:System.Windows.Media.Animation.Storyboard> , animasyon kullanır, canlandırır özelliğinin geçerli değeri başlangıç değeri olarak ayarlanmış.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 İlk İkinci düğmeye tıklarsanız <xref:System.Windows.Media.Animation.Storyboard> olduğundan yürütme, aşağıdaki davranışı bekleyebilirsiniz:  
  
1.  İlk film şeridi sona erer ve animasyon olduğundan dikdörtgeni özgün konumuna geri gönderir. bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  İkinci film şeridi etkili olur ve artık geçerli konumundan canlandırır 500 0.  
  
 **Ancak, şey bu değildir.** Bunun yerine, dikdörtgeni geri dönmez; sağa taşıma devam eder. İkinci animasyon başlangıç değeri olarak ilk animasyon geçerli değeri kullanır ve bu değerden 500'e canlandırır olmasıdır. Ne zaman ikinci animasyon değiştirir ilk çünkü <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> kullanılan <xref:System.Windows.Media.Animation.FillBehavior> ilk animasyon önemli değildir.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior ve tamamlanmış olay  
 Başka bir senaryoda sonraki örnekler göstermek <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> etkisinin gibi görünüyor. Yeniden örnek animasyon için film şeridi kullanır <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> 350 için 0. Ancak, bu kez örnek için kayıtları <xref:System.Windows.Media.Animation.Timeline.Completed> olay.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Olay işleyicisini başlatır başka <xref:System.Windows.Media.Animation.Storyboard> geçerli değeri 500 aynı özelliğe canlandırır.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 İkinci tanımlayan biçimlendirme aşağıdadır <xref:System.Windows.Media.Animation.Storyboard> bir kaynak olarak.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Çalıştırdığınızda <xref:System.Windows.Media.Animation.Storyboard>, beklediğiniz <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> tamamlandıktan sonra 0'dan 350 için animasyon için ardından 0'a geri (içerdiğinden bir <xref:System.Windows.Media.Animation.FillBehavior> ayarıyla <xref:System.Windows.Media.Animation.FillBehavior.Stop>) ve 500 ' 0'dan hareketli hale getirmeyi. Bunun yerine, <xref:System.Windows.Media.TranslateTransform> 0'dan 350'ye ve sonra 500 canlandırır.  
  
 Olan bir sırayı nedeniyle [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] olayları başlatır ve özellik değerlerini önbelleğe alınır ve değil çünkü özelliği geçersiz kılınmadığı sürece yeniden hesaplanması. <xref:System.Windows.Media.Animation.Timeline.Completed> Olay kök Zaman Çizelgesi tarafından tetiklendi çünkü önce işlenir (ilk <xref:System.Windows.Media.Animation.Storyboard>). Şu anda <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği henüz geçersiz kurmadı çünkü animasyonlu değerini hala döndürür. İkinci <xref:System.Windows.Media.Animation.Storyboard> başlangıç değeri olarak önbelleğe alınan değeri kullanır ve animasyon başlar.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Performans  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Bir sayfadan ayrılmak sonra çalıştırılmak üzere animasyonları devam  
 Merkezden gidin ne zaman bir <xref:System.Windows.Controls.Page> çalışan animasyonları içeren, bu animasyonları kadar çalışmaya devam edecek <xref:System.Windows.Controls.Page> olan toplanacak. Kullanmakta olduğunuz gezinti sistemi merkezden gidin bir sayfa bağlı olarak belirsiz bir süre, tüm süre için bellekte kalabilir tüketen kendi animasyonları ile kaynakları. ("Ortam") animasyonları sürekli olarak çalışan bir sayfaya içerdiğinde, en sık görülen budur.  
  
 Bu nedenle, bunu kullanmak için iyi bir fikirdir <xref:System.Windows.FrameworkElement.Unloaded> bir sayfadan animasyonları kaldırmak için olay.  
  
 Bir animasyon kaldırmak için farklı yolu vardır. Aşağıdaki teknikler ait animasyonları kaldırmak için kullanılan bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Kaldırmak için bir <xref:System.Windows.Media.Animation.Storyboard> bir olay tetikleyicisi ile başlattığınız için bkz: [nasıl yapılır: bir film şeridi kaldırmak](http://msdn.microsoft.com/en-us/7fe39531-de2f-46a0-a69f-b783d04235ee).  
  
-   Kaldırmak üzere kod kullanmak için bir <xref:System.Windows.Media.Animation.Storyboard>, bkz: <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> yöntemi.  
  
 Bir sonraki teknik animasyonun nasıl başlatıldığından bağımsız olarak kullanılabilir.  
  
-   Belirli bir özellikten animasyonları kaldırmak için kullanın <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> yöntemi. Özelliğin ilk parametre olarak belirtin ve `null` ikinci olarak. Bu, tüm animasyon saatlerini özelliğinden kaldırır.  
  
 Özellikleri için farklı yollar hakkında daha fazla bilgi için bkz: [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Kullanarak oluşturan HandoffBehavior kullanmak sistem kaynakları  
 Uyguladığınızda bir <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, veya <xref:System.Windows.Media.Animation.AnimationClock> kullanarak bir özelliğe <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, her türlü <xref:System.Windows.Media.Animation.Clock> sistem kaynaklarını tüketebilir daha önce bu özellik ile ilişkili nesneleri kullanmaya devam; zamanlama sistemi almayacak Bu saatleri otomatik olarak kaldırın.  
  
 Çok sayıda kullanarak saatler uyguladığınızda performans sorunlarını önlemek için <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, tamamlandıktan sonra çıktısından saatler animasyonlu özellikten kaldırmanız gerekir. Bir saat kaldırmak için birkaç yolu vardır.  
  
-   Tüm saatler bir özellikten kaldırmak için kullanın <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> animasyonlu nesnesinin yöntemi. Özelliğin ilk parametre olarak belirtin ve `null` ikinci olarak. Bu, tüm animasyon saatlerini özelliğinden kaldırır.  
  
-   Belirli bir kaldırmak için <xref:System.Windows.Media.Animation.AnimationClock> saatler listesinden kullanmak <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.Animation.AnimationClock> almak için bir <xref:System.Windows.Media.Animation.ClockController>, ardından çağıran <xref:System.Windows.Media.Animation.ClockController.Remove%2A> yöntemi <xref:System.Windows.Media.Animation.ClockController>. Bu genellikle içinde yapılır <xref:System.Windows.Media.Animation.Clock.Completed> bir saat için olay işleyicisi. Yalnızca kök saatlerin tarafından denetlenebilir Not bir <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> bir alt saat özelliğinin döndürecektir `null`. Ayrıca <xref:System.Windows.Media.Animation.Clock.Completed> saatinin etkili süresi sonsuz ise olay çağrılmayacak.  Bu durumda, kullanıcının çağrısı yapıldığında belirlemek gerekecek <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Bu uzun ömürlü nesneler üzerinde animasyonları için öncelikle bir sorun var.  Bir nesne toplanacak olduğunda, kendi saatler de kesilecek ve atık toplanır.  
  
 Saat nesneleri hakkında daha fazla bilgi için bkz: [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
