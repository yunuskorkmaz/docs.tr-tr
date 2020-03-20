---
title: Zamanlama Davranışlarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145403"
---
# <a name="timing-behaviors-overview"></a>Zamanlama Davranışlarına Genel Bakış
Bu konu, animasyonların ve diğer <xref:System.Windows.Media.Animation.Timeline> nesnelerin zamanlama davranışlarını açıklar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için temel animasyon özelliklerine aşina olmalısınız. Daha fazla bilgi için [Animasyona Genel Bakış'a](animation-overview.md)bakın.  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>Zaman Çizelgesi Türleri  
 A, <xref:System.Windows.Media.Animation.Timeline> zamanın bir bölümünü temsil eder. Bu kesimin uzunluğunu, ne zaman başlaması gerektiğini, kaç kez tekraredeceğini, o segmentte ne kadar hızlı ilerlediğini ve daha fazlasını belirtmenizi sağlayan özellikler sağlar.  
  
 Zaman çizelgesi sınıfından devralan sınıflar animasyon ve ortam oynatma gibi ek işlevler sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki <xref:System.Windows.Media.Animation.Timeline> türleri sağlar.  
  
|Zaman çizelgesi türü|Açıklama|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Animating <xref:System.Windows.Media.Animation.Timeline> özellikleri için çıktı değerleri üreten nesneler için soyut taban sınıfı.|  
|<xref:System.Windows.Media.MediaTimeline>|Bir ortam dosyasından çıktı üretir.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Alt <xref:System.Windows.Media.Animation.Timeline> nesneleri <xref:System.Windows.Media.Animation.TimelineGroup> gruplayan ve denetleyen bir tür.|  
|<xref:System.Windows.Media.Animation.Storyboard>|İçerdiği <xref:System.Windows.Media.Animation.ParallelTimeline> Zaman Çizelgesi nesneleri için hedefleme bilgileri sağlayan bir tür.|  
|<xref:System.Windows.Media.Animation.Timeline>|Zamanlama davranışlarını tanımlayan soyut taban sınıf.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Diğer <xref:System.Windows.Media.Animation.Timeline> nesneleri <xref:System.Windows.Media.Animation.Timeline> içerebilen nesneler için soyut sınıf.|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>Zaman Çizelgesinin Uzunluğunu Kontrol Eden Özellikler  
 A, <xref:System.Windows.Media.Animation.Timeline> zaman dilimini temsil eder ve zaman çizelgesinin uzunluğu farklı şekillerde açıklanabilir. Aşağıdaki tabloda bir zaman çizelgesinin uzunluğunu açıklamak için çeşitli terimler tanımlanır.  
  
|Sözleşme Dönemi|Açıklama|Özellikler||||  
|----------|-----------------|----------------|-|-|-|  
|Basit süre|Bir zaman çizelgesinin tek bir ileri yineleme yapmak için gereken süre.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Bir tekrar|Bir zaman çizelgesinin bir kez ileri oynaması ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özellik doğruysa, bir kez geriye doğru oynaması için gereken süre.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Etkin dönem|<xref:System.Windows.Media.Animation.RepeatBehavior> Özelliği tarafından belirtilen tüm yinelemeleri tamamlamak için bir zaman çizelgesi için gereken süre.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>Süre Özelliği  
 Daha önce de belirtildiği gibi, zaman çizelgesi zaman dilimini temsil eder. Bu segmentin uzunluğu zaman <xref:System.Windows.Media.Animation.Timeline.Duration%2A>çizelgesinin. Bir zaman çizelgesi süresinin sonuna ulaştığında, çalmayı durdurur. Zaman çizelgesinde alt zaman çizelgeleri varsa, onlar da oynamayı durdurur. Animasyon söz konusu olduğunda, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyonun başlangıç değerinden bitiş değerine geçişinin ne kadar süreceğini belirtir. Bir zaman çizelgesinin süresi bazen *basit süresi*olarak adlandırılır , tek bir yinelemenin süresi ile animasyonun yinelemeler de dahil olmak üzere oynadığı toplam süreyi ayırt etmek için. Sonlu bir zaman değerini veya özel değerleri <xref:System.Windows.Duration.Automatic%2A> kullanarak <xref:System.Windows.Duration.Forever%2A>bir süre belirtebilirsiniz veya. Bir animasyonun süresi bir <xref:System.Windows.Duration.TimeSpan%2A> değere çözülmelidir, böylece değerler arasında geçiş yapabilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimation> a'yı <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye ile gösterir.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Kapsayıcı zaman çizelgeleri, gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, <xref:System.Windows.Duration.Automatic%2A>varsayılan bir süre var , hangi otomatik olarak son çocuk oynamayı durdurdu anlamına gelir. Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Storyboard> kimin <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniyeye kadar çözülür, tüm alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesneleri tamamlamak için gereken süreyi gösterir.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Bir kapsayıcı <xref:System.Windows.Media.Animation.Timeline.Duration%2A> zaman çizelgesini <xref:System.Windows.Duration.TimeSpan%2A> bir değere ayarlayarak, alt <xref:System.Windows.Media.Animation.Timeline> nesnelerin oynayacağından daha uzun veya daha kısa oynamaya zorlayabilirsiniz. Kapsayıcı zaman <xref:System.Windows.Media.Animation.Timeline.Duration%2A> çizelgesinin alt <xref:System.Windows.Media.Animation.Timeline> nesnelerinin uzunluğundan daha küçük bir değere ayarlarsanız, kapsayıcı zaman çizelgesi geldiğinde alt <xref:System.Windows.Media.Animation.Timeline> nesneler çalmayı durdurur. Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> önceki <xref:System.Windows.Media.Animation.Storyboard> örneklerden üç saniyeye ayarlar. Sonuç olarak, hedef <xref:System.Windows.Media.Animation.DoubleAnimation> dikdörtgenin genişliğini 60'a yükseltildiğinde ilk duraküç saniye sonra ilerlemeyi durdurur.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>Yinelenen Davranış Özelliği  
 Bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> denetimin özelliği, basit süresini kaç kez yineler. <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği kullanarak, zaman çizelgesinin kaç kez oynadığını <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>(yineleme) veya toplam süreyi (yineleme) <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>belirtebilirsiniz. Her iki durumda da, animasyon istenen sayıyı veya süreyi doldurmak için gerektiği kadar baştan sona çalışır. Varsayılan olarak, zaman çizelgeleri bir `1.0`yineleme sayısı var , bir kez oynamak ve hiç tekrarlamak anlamına gelir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> bir yineleme <xref:System.Windows.Media.Animation.DoubleAnimation> sayısı belirterek basit süresinin iki katı için bir oyun yapmak için özelliği kullanır.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Sonraki örnek, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> oyunu basit <xref:System.Windows.Media.Animation.DoubleAnimation> süresinin yarısı boyunca yapmak için özelliği kullanır.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği <xref:System.Windows.Media.Animation.Timeline> ayarlarsanız <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> etkileşimli olarak veya zamanlama sistemi tarafından durdurulana kadar tekrarlar. Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> oyunu süresiz olarak yapmak için özelliği kullanır.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Ek bir örnek için [bkz.](how-to-repeat-an-animation.md)  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>Otomatik Geri Dönüş Özelliği  
 Özellik, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> bir <xref:System.Windows.Media.Animation.Timeline> in her ileri yinelemesonunda geriye doğru oynanıp oynanmayacağını belirtir. Aşağıdaki örnek, a <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> to `true`özelliğini ayarlar; sonuç olarak, sıfırdan 100'e, sonra 100'den sıfıra animasyonyapar. Toplam 10 saniye boyunca çalar.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Bir değeri <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> belirtmek için <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> bir <xref:System.Windows.Media.Animation.Timeline> değer <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> kullandığınızda <xref:System.Windows.Media.Animation.Timeline> ve `true`bunun özelliğini belirttiğinde, tek bir yineleme bir ileri yinelemeden oluşur ve ardından geriye doğru yineleme yapılır.  Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> önceki <xref:System.Windows.Media.Animation.DoubleAnimation> örnekten ikinin a'sına <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> göre dir. Sonuç olarak, <xref:System.Windows.Media.Animation.DoubleAnimation> 20 saniye boyunca oynar: beş saniye ileri, beş saniye için geriye, tekrar 5 saniye ileri, ve sonra geri beş saniye.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Kapsayıcı zaman çizelgesinde <xref:System.Windows.Media.Animation.Timeline> alt nesneler varsa, kapsayıcı zaman çizelgesi olduğunda tersine çevirirler. Ek örnekler için [bkz.](how-to-specify-whether-a-timeline-automatically-reverses.md)  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>Başlangıç Zamanı Özelliği  
 Özellik, <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> bir zaman çizelgesinin ne zaman başlayacağını belirtmenizi sağlar.  Bir zaman çizelgesinin başlangıç zamanı, ana zaman çizelgesine göredir. Sıfır saniyelik bir başlangıç süresi, zaman çizelgesinin üst öğe başlar başlamaz başladığı anlamına gelir; başka bir değer, üst zaman çizelgesinin çalmaya başladığı ve alt zaman çizelgesinin oynatı lar arasında bir ofset oluşturur. Örneğin, iki saniyelik bir başlangıç süresi, üst öğesi iki saniyelik bir zamana ulaştığında zaman çizelgesinin çalmaya başladığı anlamına gelir. Varsayılan olarak, tüm zaman çizelgelerinin başlama süresi sıfır saniyedir. Zaman çizelgesinin başlama saatini `null`de ayarlayabilirsiniz, bu da zaman çizelgesinin başlatılmasını engeller. Içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [x:Null Biçimlendirme Uzantısı](../../../desktop-wpf/xaml-services/xnull-markup-extension.md)kullanarak null belirtirsiniz.  
  
 Başlangıç <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> zamanının, ayarı nedeniyle bir zaman çizelgesi her kez yineleninde uygulanmadığını unutmayın. Eğer 10 saniye ve <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> bir <xref:System.Windows.Media.Animation.RepeatBehavior> , <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>animasyon ilk kez oynatıldı önce 10 saniyelik bir gecikme olurdu, ancak her ardışık yineleme için bir animasyon oluşturmak için olsaydı. Ancak, animasyonun üst zaman çizelgesi yeniden başlatılırsa veya yinelerse, 10 saniyelik gecikme oluşur.  
  
 Özellik <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> şaşırtıcı zaman çizelgeleri için yararlıdır. Aşağıdaki örnekte iki <xref:System.Windows.Media.Animation.Storyboard> alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesi olan bir tane oluşturulur. İlk animasyon <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye, ikincisi ise 3 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> saniyedir. Örnek, ikinci <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> saniyeyi 5 saniye ye ayarlar, böylece <xref:System.Windows.Media.Animation.DoubleAnimation> ilk sona erdikten sonra çalmaya başlar.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>FillBehavior Özelliği  
 Bir <xref:System.Windows.Media.Animation.Timeline> toplam etkin süresinin sonuna ulaştığında, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özellik son değerini durdurup durdurmadığını veya tutup tutmayacağını belirtir. Çıkış değerini <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "tutan" bir animasyon: animasyonözelliği animasyonun son değerini korur. Animasyonun <xref:System.Windows.Media.Animation.FillBehavior.Stop> sona erdikten sonra hedef özelliğini etkilemeyi durdurmasının nedenlerinin değeri.  
  
 Aşağıdaki örnekte iki <xref:System.Windows.Media.Animation.Storyboard> alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesi olan bir tane oluşturulur. Her <xref:System.Windows.Media.Animation.DoubleAnimation> iki nesne de <xref:System.Windows.FrameworkElement.Width%2A> 0'dan 100'e kadar olan a'nın <xref:System.Windows.Shapes.Rectangle> animasyonuna. Öğeler500 <xref:System.Windows.Shapes.Rectangle> [aygıt bağımsız piksel] animasyonsuz <xref:System.Windows.FrameworkElement.Width%2A> değerlere sahiptir.  
  
- İlkinin <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> özelliği varsayılan <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>değer olarak ayarlanır. Sonuç olarak, Dikdörtgenin Genişliği <xref:System.Windows.Media.Animation.DoubleAnimation> sona erdikten sonra 100'de kalır.  
  
- İkinci <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> özelliği <xref:System.Windows.Media.Animation.FillBehavior.Stop>ayarlanır. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> ikinci <xref:System.Windows.Shapes.Rectangle> biter sonra 500 <xref:System.Windows.Media.Animation.DoubleAnimation> döner.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Zaman Çizelgesinin Hızını Kontrol Eden Özellikler  
 Sınıf <xref:System.Windows.Media.Animation.Timeline> hızını belirtmek için üç özellik sağlar:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– Bu oranı belirtir, üst göreli, hangi zaman <xref:System.Windows.Media.Animation.Timeline>için ilerler . Birden büyük değerler, alt <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline> nesnelerin hızını artırır; sıfır ve bir arasındaki değerler onu yavaşlattır. Bir değer, üst <xref:System.Windows.Media.Animation.Timeline> öğesi ile aynı oranda ilerlediğini gösterir. Kapsayıcı <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> zaman çizelgesinin ayarı, <xref:System.Windows.Media.Animation.Timeline> tüm alt nesnelerini de etkiler.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– Hızlanan bir Zaman <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Çizelgesinin yüzdesini belirtir. Örneğin, [bkz.](how-to-accelerate-or-decelerate-an-animation.md)
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- Yavaşlama için harcanan <xref:System.Windows.Media.Animation.Timeline.Duration%2A> zaman çizelgesinin yüzdesini belirtir. Örneğin, [bkz.](how-to-accelerate-or-decelerate-an-animation.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)
- [Nasıl Dır Konular](animation-and-timing-how-to-topics.md)
- [Animasyon Zamanlama Davranış Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
