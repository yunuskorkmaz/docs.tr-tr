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
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187645"
---
# <a name="animation-tips-and-tricks"></a>Animasyon İpuçları ve Püf Noktaları
WPF'deki animasyonlarla çalışırken, animasyonlarınızın daha iyi performans göstermesini ve sizi hayal kırıklığına uğrattırabileceği birkaç ipucu ve püf noktaları vardır.  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>Genel Sorunlar  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Kaydırma Çubuğunun Veya Kaydırıcının Konumunu Animating Dondurur  
 Bir kaydırma çubuğunun veya kaydırıcının konumunu bir <xref:System.Windows.Media.Animation.FillBehavior> animasyon <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (varsayılan değer) içeren bir animasyon kullanarak animasyona bağlarsanız, kullanıcı artık kaydırma çubuğunu veya kaydırıcıyı taşıyamaz. Bunun nedeni, animasyon sona ermiş olsa bile, yine de hedef özelliğin temel değerini geçersiz kılıyor olmasıdır. Animasyonun özelliğin geçerli değerini geçersiz kılarak durdurulması için, özelliği <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>kaldırın veya ''' nin bir ' sini verin Daha fazla bilgi ve örnek için [bkz.](how-to-set-a-property-after-animating-it-with-a-storyboard.md)  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animasyonun Çıktısını Canlandırmanın Etkisi Yoktur  
 Başka bir animasyonun çıktısı olan bir nesneyi canlandıramazsınız. Örneğin, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> <xref:System.Windows.Shapes.Shape.Fill%2A> a'nın <xref:System.Windows.Shapes.Rectangle> a'dan a'ya <xref:System.Windows.Media.RadialGradientBrush> <xref:System.Windows.Media.SolidColorBrush>animasyonu kullanmak için , <xref:System.Windows.Media.RadialGradientBrush> or' <xref:System.Windows.Media.SolidColorBrush>un herhangi bir özelliğini canlandıramazsınız.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Bir Özelliği Nansanırım Cana Vardıktan Sonra Değerini Değiştiremezsiniz  
 Bazı durumlarda, animasyon sona erdikten sonra bile bir özelliğin değerini değiştiremediğiniz görünebilir. Bunun nedeni, animasyon sona ermiş olsa bile, yine de özelliğin temel değerini geçersiz kılıyor olmasıdır. Animasyonun özelliğin geçerli değerini geçersiz kılarak durdurulması için, özelliği <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>kaldırın veya ''' nin bir ' sini verin Daha fazla bilgi ve örnek için [bkz.](how-to-set-a-property-after-animating-it-with-a-storyboard.md)  
  
### <a name="changing-a-timeline-has-no-effect"></a>Zaman Çizelgesi Değiştirmenin Etkisi Yoktur  
 Çoğu <xref:System.Windows.Media.Animation.Timeline> özellik animatable ve veri bağlı olabilir rağmen, etkin <xref:System.Windows.Media.Animation.Timeline> bir özellik değerlerini değiştirme hiçbir etkisi gibi görünüyor. Çünkü, bir başlatıldığında, <xref:System.Windows.Media.Animation.Timeline> zamanlama sistemi bir kopyasını yapar <xref:System.Windows.Media.Animation.Timeline> ve bir <xref:System.Windows.Media.Animation.Clock> nesne oluşturmak için kullanır. Orijinalin değiştirilmesinin sistemin kopyası üzerinde hiçbir etkisi yoktur.  
  
 Değişiklikleri <xref:System.Windows.Media.Animation.Timeline> yansıtmak için saatin yeniden oluşturulması ve önceden oluşturulan saatin değiştirilmesi için kullanılması gerekir. Saatler sizin için otomatik olarak yeniden oluşturulmaz. Zaman çizelgesi değişikliklerini uygulamanın birkaç yolu şunlardır:  
  
- Zaman çizelgesi bir <xref:System.Windows.Media.Animation.Storyboard>, bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntem kullanarak film şeridini yeniden uygulayarak değişiklikleri yansıtmasını sağlayabilirsiniz. Bu da animasyon yeniden başlatma yan etkisi vardır. Kod olarak, film <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> şeridini önceki konumuna geri ilerletmek için yöntemi kullanabilirsiniz.  
  
- Yöntemi kullanarak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> bir özelliği doğrudan bir animasyon uyguladıysanız, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi yeniden arayın ve değiştirilen animasyonu geçirin.  
  
- Doğrudan saat düzeyinde çalışıyorsanız, yeni bir saat kümesi oluşturun ve uygulayın ve bunları önceki oluşturulan saat kümesini değiştirmek için kullanın.  
  
 Zaman çizelgeleri ve saatler hakkında daha fazla bilgi için [Animasyon ve Zamanlama Sistemine Genel Bakış'a](animation-and-timing-system-overview.md)bakın.  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop Beklendiği Gibi Çalışmıyor  
 Özelliği, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> bir animasyonun <xref:System.Windows.Media.Animation.FillBehavior.Stop> bir ayarı olduğu için başka bir <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> animasyona "el leri" gibi <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>bir etkiye sahip görünmüyor gibi görünen zamanlar vardır.  
  
 Aşağıdaki örnek, a <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Shapes.Rectangle> ve a <xref:System.Windows.Media.TranslateTransform>. Etrafında <xref:System.Windows.Media.TranslateTransform> taşımak <xref:System.Windows.Shapes.Rectangle> için animasyonlu <xref:System.Windows.Controls.Canvas>olacak .  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Bu bölümdeki örnekler, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğin beklediğiniz gibi şekilde şekilde şekilde görünmediği birkaç durumda göstermek için önceki nesneleri kullanır.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" ve Birden Çok Animasyonla HandoffBehavior  
 Bazen, ikinci bir animasyonla <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> değiştirildiğinde bir animasyon özelliğini yok sayıyor gibi görünür. İki <xref:System.Windows.Media.Animation.Storyboard> nesne oluşturan ve bunları önceki örnekte gösterilen nesneyi <xref:System.Windows.Media.TranslateTransform> canlandırmak için kullanan aşağıdaki örneği ele alalım.  
  
 İlk <xref:System.Windows.Media.Animation.Storyboard>, `B1`, , <xref:System.Windows.Media.TranslateTransform.X%2A> 0 ile <xref:System.Windows.Media.TranslateTransform> 350, sağa dikdörtgen 350 piksel taşır özelliği animasyonlar. Animasyon süresinin sonuna ulaştığında ve oynatmayı <xref:System.Windows.Media.TranslateTransform.X%2A> durdurduğunda, özellik özgün değeri olan 0'a geri döner. Sonuç olarak, dikdörtgen sağ 350 piksele taşınır ve orijinal konumuna geri atlar.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 İkincisi <xref:System.Windows.Media.Animation.Storyboard>, `B2`aynı özelliği animasyonlar <xref:System.Windows.Media.TranslateTransform.X%2A> . <xref:System.Windows.Media.TranslateTransform> Bu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.Media.Animation.Storyboard> animasyonun yalnızca özelliği ayarlandığından, animasyon, animasyonu başlangıç değeri olarak canlandırdığı özelliğin geçerli değerini kullanır.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 İlki <xref:System.Windows.Media.Animation.Storyboard> çalarken ikinci düğmeyi tıklattığınızda, aşağıdaki davranışı bekleyebilirsiniz:  
  
1. İlk film şeridi sona erer ve dikdörtgeni orijinal konumuna geri <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> gönderir, çünkü animasyonda <xref:System.Windows.Media.Animation.FillBehavior.Stop>bir .  
  
2. İkinci storyboard etkili olur ve şu anda 0 olan mevcut konumdan 500'e animasyonlar.  
  
 **Ama olan bu değil.** Bunun yerine, dikdörtgen geri atlamaz; sağa doğru ilerlemeye devam ediyor. Bunun nedeni, ikinci animasyonun başlangıç değeri olarak ilk animasyonun geçerli değerini kullanması ve bu değerden 500'e animasyonlar kullanmasıdır. İkinci animasyon kullanıldığında, ilk animasyon <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> kullanıldığında, <xref:System.Windows.Media.Animation.FillBehavior> ilk animasyonun önemi yoktur.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>Doldurma Davranışı ve Tamamlanan Olay  
 Sonraki örnekler, <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> herhangi bir etkisi olmadığı başka bir senaryoyu göstermektedir. Yine, örnek 0 ile 350 <xref:System.Windows.Media.TranslateTransform.X%2A> arasında olan <xref:System.Windows.Media.TranslateTransform> özelliği canlandırmak için bir Storyboard kullanır. Ancak, bu kez örnek <xref:System.Windows.Media.Animation.Timeline.Completed> olay için kaydeder.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Olay işleyicisi, aynı özelliği geçerli değerinden 500'e animasyonlayan başka <xref:System.Windows.Media.Animation.Storyboard> bir özellik başlatır.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Aşağıda, ikinciyi <xref:System.Windows.Media.Animation.Storyboard> kaynak olarak tanımlayan biçimlendirme ve işaretleme yer adatır.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.TranslateTransform.X%2A> 0'dan <xref:System.Windows.Media.TranslateTransform> 350'ye animasyon özelliğini çalıştırdığınızda, tamamlanınca 0'a geri dönebilirsiniz (çünkü <xref:System.Windows.Media.Animation.FillBehavior> ayarı <xref:System.Windows.Media.Animation.FillBehavior.Stop>vardır) ve sonra 0'dan 500'e animasyona çevirebilirsiniz. Bunun yerine, 0'dan 350'ye ve sonra 500'e <xref:System.Windows.Media.TranslateTransform> animasyonlar.  
  
 Bunun nedeni, WPF'nin olayları yükseltme sırası ve özellik değerlerinin önbelleğe alınmaması ve özellik geçersiz kılınmadığı sürece yeniden hesaplanmamasıdır. Olay, <xref:System.Windows.Media.Animation.Timeline.Completed> kök zaman çizelgesi (ilk) <xref:System.Windows.Media.Animation.Storyboard>tarafından tetiklendiği için önce işlenir. Şu anda, <xref:System.Windows.Media.TranslateTransform.X%2A> henüz geçersiz kılınmadığı için özellik animasyon değerini yine de döndürür. İkinci <xref:System.Windows.Media.Animation.Storyboard> önbelleğe alınmış değeri başlangıç değeri olarak kullanır ve animating başlar.  
  
<a name="performancesection"></a>
## <a name="performance"></a>Performans  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animasyonlar Bir Sayfadan Uzaklaştıktan Sonra Çalışmaya Devam Ediyor  
 Çalışan animasyonlar içeren <xref:System.Windows.Controls.Page> bir animasyondan uzaklaştığınızda, bu animasyonlar <xref:System.Windows.Controls.Page> çöp toplanana kadar oynatmaya devam eder. Kullanmakta olduğunuz gezinme sistemine bağlı olarak, uzaklara gezindiğiniz bir sayfa, animasyonlarıyla kaynakları tüketirken belirsiz bir süre bellekte kalabilir. Bu, bir sayfa sürekli çalışan ("ortam") animasyonlar içerdiğinde en çok fark edilir.  
  
 Bu nedenle, bir sayfadan <xref:System.Windows.FrameworkElement.Unloaded> uzaklaştığınızda animasyonları kaldırmak için olayı kullanmak iyi bir fikirdir.  
  
 Animasyonu kaldırmanın farklı yolları vardır. Aşağıdaki teknikler bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Olay tetikleyicisiyle başladığınız bir şeyi <xref:System.Windows.Media.Animation.Storyboard> kaldırmak için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90))  
  
- Kodu kaldırmak için <xref:System.Windows.Media.Animation.Storyboard>kullanmak için, yönteme <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> bakın.  
  
 Sonraki teknik, animasyonun nasıl başlatıldıklarından bağımsız olarak kullanılabilir.  
  
- Animasyonları belirli bir özellikten kaldırmak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> için yöntemi kullanın. İlk parametre olarak, ikinci parametre `null` olarak animasyonlu özelliği belirtin. Bu özelliktüm animasyon saatleri kaldırır.  
  
 Özellikleri canlandırmanın farklı yolları hakkında daha fazla bilgi için, [Özellik Animasyon Tekniklerine Genel Bakış'a](property-animation-techniques-overview.md)bakın.  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Beste HandoffBehavior Kullanma Sistem Kaynaklarını Tüketir  
 Bir <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>veya <xref:System.Windows.Media.Animation.AnimationClock> bir özelliği kullanarak <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>bir <xref:System.Windows.Media.Animation.Clock> özellik uyguladığınız zaman, daha önce bu özellik ile ilişkili herhangi bir nesne sistem kaynaklarını tüketmeye devam; zamanlama sistemi bu saatleri otomatik olarak kaldırmaz.  
  
 Çok sayıda saat uyguladığınız <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>zaman performans sorunlarını önlemek için, tamamlanan saatler tamamlandıktan sonra animasyonlu özellikten oluşturan saatleri kaldırmanız gerekir. Bir saati kaldırmanın birkaç yolu vardır.  
  
- Bir özellikteki tüm saatleri kaldırmak <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> için <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> animasyonlu nesnenin veya yöntemini kullanın. İlk parametre olarak, ikinci parametre `null` olarak animasyonlu özelliği belirtin. Bu özelliktüm animasyon saatleri kaldırır.  
  
- Saatler listesinden <xref:System.Windows.Media.Animation.AnimationClock> belirli bir kaldırmak <xref:System.Windows.Media.Animation.Clock.Controller%2A> <xref:System.Windows.Media.Animation.AnimationClock> için, bir <xref:System.Windows.Media.Animation.ClockController>almak için özelliğini <xref:System.Windows.Media.Animation.ClockController.Remove%2A> kullanın , <xref:System.Windows.Media.Animation.ClockController>sonra yöntemini arayın . Bu genellikle bir saat <xref:System.Windows.Media.Animation.Clock.Completed> için olay işleyicisi yapılır. Yalnızca kök saatlerin bir <xref:System.Windows.Media.Animation.ClockController>; bir <xref:System.Windows.Media.Animation.Clock.Controller%2A> çocuk saatin özelliği `null`geri dönecektir. Saatin <xref:System.Windows.Media.Animation.Clock.Completed> etkili süresi sonsuza kadar ise olayın çağrılmadığını da unutmayın.  Bu durumda, kullanıcının ne zaman arayacağını <xref:System.Windows.Media.Animation.ClockController.Remove%2A>belirlemesi gerekir.  
  
 Bu, öncelikle uzun bir ömrü olan nesnelerüzerinde animasyonlar için bir sorundur.  Bir nesne çöp toplandığında, saatleri de kesilir ve çöp toplanır.  
  
 Saat nesneleri hakkında daha fazla bilgi için [Animasyon ve Zamanlama Sistemine Genel Bakış'a](animation-and-timing-system-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
