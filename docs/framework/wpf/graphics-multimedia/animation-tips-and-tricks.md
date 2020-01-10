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
ms.openlocfilehash: ef59631663e6cf1c98adfed77a2dbdb6ca124fa1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636035"
---
# <a name="animation-tips-and-tricks"></a>Animasyon İpuçları ve Püf Noktaları
WPF 'de animasyonlarla çalışırken, animasyonlarınızın daha iyi bir şekilde çalışmasını ve sizi daha da gerçekleştirmenizi sağlayan çeşitli ipuçları ve püf noktaları vardır.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Genel Sorunlar  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Bir kaydırma çubuğunun veya kaydırıcının konumunu hareketlendirmek bunu dondurur  
 Bir kaydırma çubuğunun veya kaydırıcının konumunu <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> <xref:System.Windows.Media.Animation.FillBehavior> (varsayılan değer) olan bir animasyon kullanarak hareketlendirmek durumunda, Kullanıcı artık kaydırma çubuğunu veya kaydırıcıyı taşıyamayacaktır. Yani, animasyon sona erse de hedef özelliğin temel değerini geçersiz kılmış olur. Animasyonun özelliğin geçerli değerini geçersiz kılmasını durdurmak için, bunu kaldırın veya <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.FillBehavior> verin. Daha fazla bilgi ve bir örnek için bkz. [Görsel Taslakla animasyon uygulandıktan sonra özelliği ayarlama](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animasyonun çıktısının animasyon ekleme etkisi yoktur  
 Başka bir animasyonun çıktısı olan bir nesneyi hareketlendiremezsiniz. Örneğin, bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Media.RadialGradientBrush> bir <xref:System.Windows.Media.SolidColorBrush>hareketlendirmek için <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> kullanırsanız, <xref:System.Windows.Media.RadialGradientBrush> veya <xref:System.Windows.Media.SolidColorBrush>özelliklerinin herhangi bir özelliğini hareketlendiremezsiniz.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Hareketlendirilen bir özelliğin değeri değiştirilemez  
 Bazı durumlarda, animasyon sona erdikten sonra bile, bir özelliğin değerini, hareketlendirildikten sonra değiştiremeyebilirsiniz. Yani, animasyon sona erse de özelliğin temel değerini geçersiz kılmış olur. Animasyonun özelliğin geçerli değerini geçersiz kılmasını durdurmak için, bunu kaldırın veya <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.FillBehavior> verin. Daha fazla bilgi ve bir örnek için bkz. [Görsel Taslakla animasyon uygulandıktan sonra özelliği ayarlama](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Bir zaman çizelgesinin değiştirilmesinin etkisi yoktur  
 <xref:System.Windows.Media.Animation.Timeline> özelliklerinin çoğu Animatable olmasına rağmen veri sınırı içerebilse de, etkin bir <xref:System.Windows.Media.Animation.Timeline> özellik değerlerinin değiştirilmesi hiçbir etkisi olmaz. Bunun nedeni, bir <xref:System.Windows.Media.Animation.Timeline> başlatıldığında, zamanlama sisteminin <xref:System.Windows.Media.Animation.Timeline> bir kopyasını yapması ve bir <xref:System.Windows.Media.Animation.Clock> nesnesi oluşturmak için kullanması. Orijinalin değiştirilmesi sistemin kopyasını etkilemez.  
  
 Değişiklikleri yansıtması için bir <xref:System.Windows.Media.Animation.Timeline> için, bu saatin yeniden oluşturulması ve daha önce oluşturulan saatin yerine kullanılması gerekir. Saatler sizin için otomatik olarak yeniden oluşturulmaz. Aşağıda, zaman çizelgesi değişikliklerini uygulamak için çeşitli yollar verilmiştir:  
  
- Zaman çizelgesi bir <xref:System.Windows.Media.Animation.Storyboard>aitse veya bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi kullanarak film şeridini yeniden uygulayarak değişiklikleri yansıtabilir. Bu, animasyonun yeniden başlatılmasına de yönelik yan etkiye sahiptir. Kod içinde, film şeridini önceki konumuna geri ilerletmek için <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemini kullanabilirsiniz.  
  
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanarak doğrudan bir özelliği bir animasyon uyguladıysanız, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemini yeniden çağırın ve değiştirilmiş animasyonu geçirin.  
  
- Doğrudan saat düzeyinde çalışıyorsanız, yeni bir saat kümesi oluşturup uygulayın ve bunları önceki bir üretilen saat kümesini değiştirmek için kullanın.  
  
 Zaman çizelgeleri ve saatler hakkında daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior. Stop, beklendiği gibi çalışmıyor  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğinin <xref:System.Windows.Media.Animation.FillBehavior.Stop> olarak ayarlanması, bir animasyonun bir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> ayarı olduğu için başka bir animasyon (örneğin, bir animasyon "olduğu gibi) gibi görünse durumlar vardır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>, bir <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Media.TranslateTransform>oluşturur. <xref:System.Windows.Media.TranslateTransform>, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Canvas>etrafında hareket ettirmek için canlandırılır.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Bu bölümdeki örneklerde, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğinin ' de beklediği gibi davranmadığının birkaç durumu göstermek için önceki nesneler kullanılır.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Durdur" ve birden çok Animasyonle HandoffBehavior  
 Bazen bir animasyon ikinci bir animasyonla değiştirildiğinde <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğini yok saymış gibi görünüyor. İki <xref:System.Windows.Media.Animation.Storyboard> nesnesi oluşturan ve bunları önceki örnekte gösterilen <xref:System.Windows.Media.TranslateTransform> hareketlendirmek için kullanan aşağıdaki örneği alın.  
  
 İlk <xref:System.Windows.Media.Animation.Storyboard>`B1`, <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.X%2A> özelliğinin 0 ' dan 350 ' e taşınması ve bu dikdörtgeni 350 piksel sağa taşıdır. Animasyon süresinin sonuna ulaştığında ve yürütmeyi durdurduktan sonra, <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği özgün değerine döner, 0. Sonuç olarak, dikdörtgen doğru 350 piksele gider ve sonra özgün konumuna geri atlar.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 İkinci <xref:System.Windows.Media.Animation.Storyboard>, `B2`aynı <xref:System.Windows.Media.TranslateTransform><xref:System.Windows.Media.TranslateTransform.X%2A> özelliğini de hareketlendirir. Bu <xref:System.Windows.Media.Animation.Storyboard> animasyonun yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği ayarlandığından animasyon, başlangıç değeri olarak canlandırdığı özelliğin geçerli değerini kullanır.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 İlk <xref:System.Windows.Media.Animation.Storyboard> oynatılırken ikinci düğmeye tıklarsanız, aşağıdaki davranışı bekleyebilir:  
  
1. İlk film şeridi sonlanır ve dikdörtgeni özgün konumuna geri gönderir çünkü animasyon <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>.  
  
2. İkinci film şeridi etkili olur ve şu anda 0 olan geçerli konumdan 500 'e hareketlenir.  
  
 **Ancak bu durum bu değildir.** Bunun yerine, dikdörtgen geri atlanmaz; sağa geçmeyi sürdürür. Bunun nedeni, ikinci animasyonun başlangıçtaki değeri olarak ilk animasyonun geçerli değerini kullanması ve bu değerden 500 ' e hareketlendirir. <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior> kullanıldığı için ikinci animasyon ilk yerini değiştirdiğine göre ilk animasyonun <xref:System.Windows.Media.Animation.FillBehavior> önemi yoktur.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior ve tamamlanan olay  
 Sonraki örneklerde <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> hiçbir etkisi olmadığı gibi başka bir senaryo gösterilmektedir. Yine, örnek, <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.X%2A> özelliğine 0 ' dan 350 ' a animasyon uygulamak için bir görsel taslak kullanır. Ancak, bu kez örnek <xref:System.Windows.Media.Animation.Timeline.Completed> olayına kaydolur.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> olay işleyicisi, aynı özelliği geçerli değerinden 500 ' e canlandıran başka bir <xref:System.Windows.Media.Animation.Storyboard> başlatır.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 İkinci <xref:System.Windows.Media.Animation.Storyboard> kaynak olarak tanımlayan biçimlendirme aşağıda verilmiştir.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 <xref:System.Windows.Media.Animation.Storyboard>çalıştırdığınızda, <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.X%2A> özelliğinin 0 ' dan 350 ' e animasyonunu bekleyebilir, ardından tamamlandıktan sonra 0 ' a döndürebilirsiniz (<xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.FillBehavior> ayarı vardır) ve ardından 0 ' dan 500 ' e animasyon uygulayabilirsiniz. Bunun yerine, <xref:System.Windows.Media.TranslateTransform> 0 ' dan 350 ' e ve ardından 500 ' e hareketlenir.  
  
 Bu, WPF 'nin olayları harekete geçirme sırası ve özellik değerlerinin önbelleğe alınması ve özellik geçersiz kılınmadığı takdirde yeniden hesaplanmaması nedeniyle oluşur. <xref:System.Windows.Media.Animation.Timeline.Completed> olay, kök zaman çizelgesi (ilk <xref:System.Windows.Media.Animation.Storyboard>) tarafından tetiklendiğinden önce işlenir. Şu anda <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği henüz geçersiz kılınmadığı için animasyon değerini döndürür. İkinci <xref:System.Windows.Media.Animation.Storyboard>, başlangıç değeri olarak önbelleğe alınan değeri kullanır ve animasyon kullanmaya başlar.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Performans  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animasyonlar bir sayfadan Uzaklaşdıktan sonra çalışmaya devam eder  
 Çalışan animasyonları içeren bir <xref:System.Windows.Controls.Page> uzağa gittiğinizde, bu animasyonlar <xref:System.Windows.Controls.Page> atık toplanana kadar oynatılmaya devam eder. Kullanmakta olduğunuz gezinti sistemine bağlı olarak, üzerinden gittiğiniz bir sayfa, sınırsız bir süre boyunca bellekte kalabilir ve bu da tüm kaynakları animasyonlarla tüketiyor. Bu, bir sayfa sürekli olarak çalışan ("çevresel") animasyonları içerdiğinde görülür.  
  
 Bu nedenle, bir sayfadan uzağa gittiğinizde animasyonları kaldırmak için <xref:System.Windows.FrameworkElement.Unloaded> olayını kullanmak iyi bir fikirdir.  
  
 Bir animasyonu kaldırmanın farklı yolları vardır. Aşağıdaki teknikler bir <xref:System.Windows.Media.Animation.Storyboard>ait olan animasyonları kaldırmak için kullanılabilir.  
  
- Bir olay tetikleyicisiyle başlattığınız <xref:System.Windows.Media.Animation.Storyboard> kaldırmak için bkz. [nasıl yapılır: görsel taslağı kaldırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- <xref:System.Windows.Media.Animation.Storyboard>kaldırmak için kodu kullanmak için <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> yöntemine bakın.  
  
 Sonraki Yöntem animasyonun nasıl başlatıldığına bakılmaksızın kullanılabilir.  
  
- Animasyonları belirli bir özellikten kaldırmak için <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> yöntemini kullanın. İlk parametre olarak hareketlendirilen özelliği ve ikinci olarak `null` belirtin. Bu, tüm animasyon saatlerini özellikten kaldırır.  
  
 Özellikleri hareketlendirmek için farklı yollar hakkında daha fazla bilgi için bkz. [özellik animasyon tekniklerine genel bakış](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Compose HandoffBehavior kullanmak sistem kaynaklarını kullanır  
 <xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>kullanarak bir özelliğe <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>veya <xref:System.Windows.Media.Animation.AnimationClock> uyguladığınızda, daha önce bu özellikle ilişkilendirilen tüm <xref:System.Windows.Media.Animation.Clock> nesneleri sistem kaynaklarını kullanmaya devam eder; zamanlama sistemi bu saatleri otomatik olarak kaldırmaz.  
  
 <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>kullanarak çok sayıda saat uyguladığınızda performans sorunlarından kaçınmak için, tamamlandıktan sonra animasyonlu özelliğinden saatleri oluşturmayı kaldırmanız gerekir. Saati kaldırmanın birkaç yolu vardır.  
  
- Bir özellikten tüm saatleri kaldırmak için, animasyonlu nesnenin <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> yöntemini kullanın. İlk parametre olarak hareketlendirilen özelliği ve ikinci olarak `null` belirtin. Bu, tüm animasyon saatlerini özellikten kaldırır.  
  
- Belirli bir <xref:System.Windows.Media.Animation.AnimationClock> saat listesinden kaldırmak için, <xref:System.Windows.Media.Animation.ClockController>almak için <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliğini kullanın ve ardından <xref:System.Windows.Media.Animation.ClockController.Remove%2A> <xref:System.Windows.Media.Animation.ClockController>yöntemini çağırın. Bu, genellikle bir saat için <xref:System.Windows.Media.Animation.Clock.Completed> olay işleyicisinde yapılır. Yalnızca kök saatlerinin bir <xref:System.Windows.Media.Animation.ClockController>tarafından denetlenebileceğini unutmayın; bir alt saatin <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği, `null`döndürür. Ayrıca, saatin geçerlilik süresi süresiz ise <xref:System.Windows.Media.Animation.Clock.Completed> olayının çağrılmadığını unutmayın.  Bu durumda, kullanıcının <xref:System.Windows.Media.Animation.ClockController.Remove%2A>ne zaman çağrılacağını belirlemesi gerekir.  
  
 Bu, öncelikle uzun ömürlü nesneler üzerindeki animasyonlar için bir sorundur.  Bir nesne atık olarak toplandığında, saatlerinin de bağlantısı kesilir ve atık olarak toplanır.  
  
 Saat nesneleri hakkında daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
