---
title: Animasyon İpuçları ve Püf Noktaları
ms.date: 03/30/2017
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
ms.openlocfilehash: 6d79d3330154fff33abe5a401a70c6b9a20aad72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660430"
---
# <a name="animation-tips-and-tricks"></a>Animasyon İpuçları ve Püf Noktaları
İçinde animasyon ile çalışırken [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], birkaç ipucu vardır ve animasyonlarınızın püf noktaları daha iyi performans ve yükünden kurtarın.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Genel sorunlar  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Bir kaydırma çubuğunun konumuna animasyon ekleme veya kaydırıcı donuyor  
 Bir kaydırma çubuğuna ya da olan bir animasyon kullanarak kaydırıcı konumunu hareketlendirirseniz bir <xref:System.Windows.Media.Animation.FillBehavior> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (varsayılan değer), kullanıcı artık kaydırma çubuğu veya kaydırıcıyı mümkün olacaktır. Animasyon sona erse bile hedef özelliğin temel değerin hala geçersiz kılma olmasıdır. Özelliğin geçerli değerini geçersiz kılmasını animasyon durdurmak için kaldırın veya ona bir <xref:System.Windows.Media.Animation.FillBehavior> , <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Daha fazla bilgi ve örnek için bkz. [bir özellik sonra animasyon film şeridi ile ayarlayın](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Hiçbir etkisi olmaz animasyon çıktısını animasyon ekleme  
 Başka bir animasyon çıktısını bir nesneye animasyon uygulayamazsınız. Kullanırsanız, örneğin, bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> animasyon uygulamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> gelen bir <xref:System.Windows.Media.RadialGradientBrush> için bir <xref:System.Windows.Media.SolidColorBrush>, tüm özellikleri hareketlendiremezsiniz <xref:System.Windows.Media.RadialGradientBrush> veya <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Bir özelliğin değerini animasyon ekledikten sonra değiştiremezsiniz  
 Bazı durumlarda, sonra bile animasyon sona erdikten sonra bu, bir animasyon görünür bir özelliğin değerini değiştiremezsiniz görünebilir. Animasyon sona erse bile özelliğin temel değerin hala geçersiz kılma olmasıdır. Özelliğin geçerli değerini geçersiz kılmasını animasyon durdurmak için kaldırın veya ona bir <xref:System.Windows.Media.Animation.FillBehavior> , <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Daha fazla bilgi ve örnek için bkz. [bir özellik sonra animasyon film şeridi ile ayarlayın](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Bir zaman çizelgesi değiştirmenin etkisi olmaz  
 Ancak çoğu <xref:System.Windows.Media.Animation.Timeline> özellikleri canlandırılabilir ve etkin bir özellik değerlerini değiştirme veri bağlanabilen <xref:System.Windows.Media.Animation.Timeline> hiçbir etkisi yok gibi görünüyor. Çünkü, bir <xref:System.Windows.Media.Animation.Timeline> olan başladığında zamanlama sistemi bir kopyasını oluşturur <xref:System.Windows.Media.Animation.Timeline> ve oluşturmak için kullandığı bir <xref:System.Windows.Media.Animation.Clock> nesne. Özgün değiştirerek sistemin kopyası üzerinde etkisi yoktur.  
  
 İçin bir <xref:System.Windows.Media.Animation.Timeline> değişiklikleri yansıtacak şekilde kendi saat yeniden ve önceden oluşturulmuş saati değiştirmek için kullanılması gerekir. Saatleri sizin için otomatik olarak yeniden oluşturulmaz. Zaman Çizelgesi değişiklikleri uygulamak için birkaç yolu şunlardır:  
  
-   Zaman Çizelgesi veya ait bir <xref:System.Windows.Media.Animation.Storyboard>, bunu görsel taslak kullanarak uygulayarak değişiklikleri yansıtacak yapabileceğiniz bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi. Bu, yan etkisi, ayrıca animasyon yeniden vardır. Kod içinde kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> back önceki konumuna film şeridi ilerlemek için yöntemi.  
  
-   Animasyonun bir özellik kullanarak doğrudan uyguladıysanız <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi, çağrı <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yeniden yöntemi ve değiştirilmiş animasyonu geçirin.  
  
-   Doğrudan saat düzeyinde çalışıyorsanız ve saatler yeni bir uygulama oluşturup bunları oluşturulan saatler önceki kümesini değiştirmek için kullanabilirsiniz.  
  
 Zaman çizelgeleri ve saatler hakkında daha fazla bilgi için bkz: [animasyon ve zamanlama sistemine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop beklendiği gibi çalışmıyor  
 Bazı durumlarda ayarlarken <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.FillBehavior.Stop> ne zaman gibi hiçbir etkiye sahip gibi görünüyor. bir animasyon "uygulamalı kapalı" diğerine olduğundan bir <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> ayarıyla <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> Taşımak için animasyon <xref:System.Windows.Shapes.Rectangle> etrafında <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Bu bölümdeki örneklerde, bazı durumları göstermek için önceki nesneleri kullanır. burada <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği değil, kendisine bekleyebileceğiniz gibi davranır.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior "Durdur" ve birden çok animasyonlarla HandoffBehavior =  
 Bazen bir animasyon yoksayar gibi görünüyor, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ikinci bir animasyon tarafından değiştirildiğinde özelliği. İki oluşturan aşağıdaki örnekte, ele <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve bunları aynı animasyon uygulamak için kullandığı <xref:System.Windows.Media.TranslateTransform> önceki örnekte gösterilen.  
  
 İlk <xref:System.Windows.Media.Animation.Storyboard>, `B1`, canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> sağa dikdörtgen 350 piksel taşır 350 için 0 ile. Animasyon süresinin sonuna ulaştığında ve yürütmeyi, durdurduğunda <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği, özgün değer için 0'a döner. Sonuç olarak, dikdörtgen sağ 350 piksel taşır ve ardından özgün konumuna geri atlar.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 İkinci <xref:System.Windows.Media.Animation.Storyboard>, `B2`, ayrıca canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> aynı özellik <xref:System.Windows.Media.TranslateTransform>. Çünkü yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> bu animasyonun özellik <xref:System.Windows.Media.Animation.Storyboard> , animasyon kullanır, canlandırır özelliğinin geçerli değeri başlangıç değeri olarak ayarlanmış.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 İlk İkinci düğmeye tıklarsanız <xref:System.Windows.Media.Animation.Storyboard> olduğundan yürütme, aşağıdaki davranış bekleyebilirsiniz:  
  
1.  İlk film şeridi sona erer ve animasyon olduğundan dikdörtgeni özgün konumuna geri gönderir. bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  İkinci film şeridi etkili olur ve artık geçerli konumundan canlandırır 500 0.  
  
 **Ancak neler değil.** Bunun yerine, rectangle geri dönmez; sağa doğru ilerlendiğinde devam eder. Bunun nedeni, ikinci animasyonun başlangıç değeri geçerli değerin ilk animasyonun kullanır ve bu değeri 500'e canlandırır olmasıdır. Ne zaman ikinci animasyon değiştirir ilk çünkü <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> kullanılan <xref:System.Windows.Media.Animation.FillBehavior> ilk animasyon önemli değildir.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior ve tamamlanan olay  
 Sonraki örneklerde, başka bir senaryoyu göstermek <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> hiçbir etkisi yok gibi görünüyor. Yeniden animasyon uygulamak için bir görsel taslak örnek kullanır <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> 350 için 0. Ancak bu kez örnek için kayıtları <xref:System.Windows.Media.Animation.Timeline.Completed> olay.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Olay işleyicisini başlatır başka <xref:System.Windows.Media.Animation.Storyboard> , aynı özelliğin geçerli değerini 500 canlandırın.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 İkinci tanımlar biçimlendirme verilmiştir <xref:System.Windows.Media.Animation.Storyboard> bir kaynak olarak.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Çalıştırdığınızda <xref:System.Windows.Media.Animation.Storyboard>, beklediğiniz <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> tamamlandıktan sonra 350 için 0 ile animasyon uygulamak için ardından 0 olarak geri (olduğundan bir <xref:System.Windows.Media.Animation.FillBehavior> ayarıyla <xref:System.Windows.Media.Animation.FillBehavior.Stop>) ve ardından 0 ile 500'e animasyon ekleme. Bunun yerine, <xref:System.Windows.Media.TranslateTransform> 350'ye ve sonra 500 0'dan canlandırın.  
  
 Bir sırayı nedeniyle olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] olayları başlatır ve özellik değerlerini önbelleğe alınır ve değildir çünkü özelliği geçersiz kılınmadığı sürece yeniden hesaplanır. <xref:System.Windows.Media.Animation.Timeline.Completed> Olay kök Zaman Çizelgesi tarafından tetiklendi çünkü önce işlenir (ilk <xref:System.Windows.Media.Animation.Storyboard>). Şu anda <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği henüz kılınmamıştır değerini animasyonlu hala döndürür. İkinci <xref:System.Windows.Media.Animation.Storyboard> başlangıç değeri önbelleğe alınan değeri kullanır ve animasyonu başlar.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Performans  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Bir sayfadan ayrılmak geçtikten sonra çalıştırılacak animasyon devam edin  
 Gittiğinizde liste kutusundan bir <xref:System.Windows.Controls.Page> bu animasyonları kadar çalışmaya devam edecek, çalışan animasyonlar içeren <xref:System.Windows.Controls.Page> olan çöp olarak toplanacak. Kullanmakta olduğunuz Gezinti sistem UZAĞINIZDA gidin bir sayfa bağlı olarak düzeltmede kalma belirsiz bir zaman, tüm süre miktarı için bellek tüketen kendi animasyonları ile kaynakları. ("Ortam") animasyonlar sürekli olarak çalışan bir sayfa içerir, bu en belirgin olur.  
  
 Bu nedenle, bunu kullanmak için iyi bir fikirdir <xref:System.Windows.FrameworkElement.Unloaded> sayfadan ayrılmak gittiğinizde animasyonları kaldırılacağı olay.  
  
 Bir animasyonu kaldırmak için farklı yolu vardır. Aşağıdaki teknikler ait animasyonları kaldırmak için kullanılan bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Kaldırmak için bir <xref:System.Windows.Media.Animation.Storyboard> bir olay tetikleyicisi ile başlattığınız için bkz: [nasıl yapılır: Film şeridini kaldırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
-   Kaldırmak için kodu kullanmak için bir <xref:System.Windows.Media.Animation.Storyboard>, bkz: <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> yöntemi.  
  
 Sonraki yöntem, animasyon nasıl başlatıldığından bağımsız olarak kullanılabilir.  
  
-   Belirli bir özellikten animasyonları kaldırmak için <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> yöntemi. İlk parametre olarak, animasyon uygulanan bir özellik belirtin ve `null` ikinci olarak. Bu, tüm animasyon saatleri özelliği kaldırır.  
  
 Özelliklerine animasyon uygulamak için farklı yollar hakkında daha fazla bilgi için bkz. [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Kullanarak Compose HandoffBehavior kullanmak sistem kaynakları  
 Uyguladığınızda bir <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, veya <xref:System.Windows.Media.Animation.AnimationClock> kullanarak bir özelliğe <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, <xref:System.Windows.Media.Animation.Clock> daha önce bu özellik ile ilişkilendirilen nesneleri sistem kaynaklarının kullanılmasına devam; zamanlama sistemi sağlamaz Bu saatler otomatik olarak kaldırın.  
  
 Çok sayıda kullanarak saatler uyguladığınızda, performans sorunlarını önlemek için <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, tamamlandıktan sonra animasyonlu özelliğinden çıktısından saatler kaldırmanız gerekir. Bir saat kaldırmak için birkaç yol vardır.  
  
-   Tüm saatler bir özelliği kaldırmak için <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> yöntemi animasyonlu nesne. İlk parametre olarak, animasyon uygulanan bir özellik belirtin ve `null` ikinci olarak. Bu, tüm animasyon saatleri özelliği kaldırır.  
  
-   Belirli bir kaldırmak için <xref:System.Windows.Media.Animation.AnimationClock> saatler listesinden kullanmak <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.Animation.AnimationClock> almak için bir <xref:System.Windows.Media.Animation.ClockController>, ardından çağırın <xref:System.Windows.Media.Animation.ClockController.Remove%2A> yöntemi <xref:System.Windows.Media.Animation.ClockController>. Bu genellikle yapılabilir <xref:System.Windows.Media.Animation.Clock.Completed> bir saat için olay işleyicisi. Not yalnızca kök saatler tarafından denetlenebilir bir <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> alt saat özelliği döndürür `null`. Ayrıca <xref:System.Windows.Media.Animation.Clock.Completed> saatin geçerlilik süresi sonsuz ise olay çağrılmayacak.  Bu durumda, ne zaman çağrılacağını belirlemek kullanıcı gerekir <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Uzun ömürlü nesnelerine animasyon için öncelikle bir sorun budur.  Bir nesnenin çöp olarak toplanacak olduğunda, kendi saatler da kesilir ve atık olarak toplanmış.  
  
 Saat nesneleri hakkında daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
