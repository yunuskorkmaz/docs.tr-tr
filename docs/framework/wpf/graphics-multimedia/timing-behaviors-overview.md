---
title: Zamanlama Davranışlarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: a85f980a0cefaa282e9e92d533a2306a9009e3e7
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559956"
---
# <a name="timing-behaviors-overview"></a>Zamanlama Davranışlarına Genel Bakış
Bu konu, animasyonların ve diğer <xref:System.Windows.Media.Animation.Timeline> nesnelerinin zamanlama davranışlarını açıklamaktadır.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konuyu anlamak için temel animasyon özellikleriyle ilgili bilgi sahibi olmanız gerekir. Daha fazla bilgi için [animasyona genel bakış](animation-overview.md)konusuna bakın.  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Zaman çizelgesi türleri  
 <xref:System.Windows.Media.Animation.Timeline> bir zaman kesimini temsil eder. Bu, segmentin uzunluğunu, ne zaman yineleneceğini, kaç kez yineleneceğini, bu kesimdeki zaman ne kadar hızlı bir şekilde ilerleme olduğunu ve daha fazlasını belirtmenizi sağlayan özellikler sunar.  
  
 Zaman Çizelgesi sınıfından kalıtımla alan sınıflar, animasyon ve medya yürütme gibi ek işlevler sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşağıdaki <xref:System.Windows.Media.Animation.Timeline> türlerini sağlar.  
  
|Zaman çizelgesi türü|Açıklama|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Hareketlendirilen özellikler için çıkış değerleri üreten <xref:System.Windows.Media.Animation.Timeline> nesneleri için soyut temel sınıf.|  
|<xref:System.Windows.Media.MediaTimeline>|Bir medya dosyasından çıktı üretir.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Alt <xref:System.Windows.Media.Animation.Timeline> nesnelerini gruplandıran ve denetleyen <xref:System.Windows.Media.Animation.TimelineGroup> türü.|  
|<xref:System.Windows.Media.Animation.Storyboard>|İçerdiği zaman çizelgesi nesneleri için hedefleme bilgilerini sağlayan <xref:System.Windows.Media.Animation.ParallelTimeline> türü.|  
|<xref:System.Windows.Media.Animation.Timeline>|Zamanlama davranışlarını tanımlayan soyut temel sınıf.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Diğer <xref:System.Windows.Media.Animation.Timeline> nesneleri içerebilen <xref:System.Windows.Media.Animation.Timeline> nesneleri için soyut sınıf.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Bir zaman çizelgesinin uzunluğunu denetleyen özellikler  
 <xref:System.Windows.Media.Animation.Timeline> bir zaman kesimini temsil eder ve zaman çizelgesinin uzunluğu farklı şekillerde açıklanabilir. Aşağıdaki tabloda, bir zaman çizelgesinin uzunluğunu açıklamak için çeşitli terimler tanımlanmaktadır.  
  
|Terim|Açıklama|Özellikler||||  
|----------|-----------------|----------------|-|-|-|  
|Basit süre|Bir zaman çizelgesinin tek bir iletme yinelemesi yapmak için geçen sürenin uzunluğu.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Bir yineleme|Bir zaman çizelgesinin bir kez oynatılacağı sürenin uzunluğu ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği true ise, bir kez geriye doğru yürütün.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Etkin dönem|Bir zaman çizelgesinin <xref:System.Windows.Media.Animation.RepeatBehavior> özelliği tarafından belirtilen tüm tekrarları tamamlaması için gereken süre uzunluğu.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration özelliği  
 Daha önce belirtildiği gibi, bir zaman çizelgesi bir zaman kesimini temsil eder. Bu segmentin uzunluğu, zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.Duration%2A>belirlenir. Bir zaman çizelgesi süresinin sonuna ulaştığında yürütmeyi sonlandırır. Zaman çizelgesinde alt zaman çizelgeleri varsa, oynamaları da durdurur. Animasyon söz konusu olduğunda <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, animasyonun başlangıç değerinden bitiş değerine geçişin ne kadar sürdüğünü belirtir. Bir zaman çizelgesinin süresi bazen *basit süresi*olarak adlandırılır, tek bir yinelemenin süresi ile animasyonun sürekliliği dahil olduğu sürenin toplam uzunluğu arasında ayrım yapar. Sınırlı bir zaman değeri veya <xref:System.Windows.Duration.Forever%2A><xref:System.Windows.Duration.Automatic%2A> özel değerleri kullanarak bir süre belirtebilirsiniz. Animasyonun süresi <xref:System.Windows.Duration.TimeSpan%2A> bir değere çözümlenmelidir, bu nedenle değerler arasında geçiş yapabilir.  
  
 Aşağıdaki örnekte, beş saniyelik <xref:System.Windows.Media.Animation.Timeline.Duration%2A> bir <xref:System.Windows.Media.Animation.DoubleAnimation> gösterilmektedir.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>gibi kapsayıcı zaman çizelgeleriyle varsayılan <xref:System.Windows.Duration.Automatic%2A>süresi vardır. Bu, son alt öğe yürütmeyi durdurduklarında otomatik olarak bitdikleri anlamına gelir. Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniyeye çözümleyen bir <xref:System.Windows.Media.Animation.Storyboard> gösterir, onun tüm alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesnelerinin tamamlanmasını zaman alır.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Bir kapsayıcı zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Duration.TimeSpan%2A> bir değere ayarlayarak, daha uzun veya daha kısa bir süre yürütmeye zorlayabilirsiniz <xref:System.Windows.Media.Animation.Timeline> nesneler oynatılabilir. <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kapsayıcı zaman çizelgesinin alt <xref:System.Windows.Media.Animation.Timeline> nesnelerinin uzunluğundan daha küçük bir değere ayarlarsanız, kapsayıcı zaman çizelgesi başlatıldığında alt <xref:System.Windows.Media.Animation.Timeline> nesneleri yürütmeyi durdurur. Aşağıdaki örnek, önceki örneklerdeki <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Timeline.Duration%2A> üç saniyeye ayarlar. Sonuç olarak, ilk <xref:System.Windows.Media.Animation.DoubleAnimation>, hedef dikdörtgenin genişliğini 60 olarak canlandırdıktan sonra üç saniyeden sonra ilerlemesini durduruyor.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior özelliği  
 Bir <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği, basit süresini kaç kez yineleyeceğini denetler. <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini kullanarak, zaman çizelgesinin kaç kez oynatılacağını (bir yineleme <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) veya oynaması gereken toplam süreyi (yineleme <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>) belirtebilirsiniz. Her iki durumda da, animasyon istenen sayıyı veya süreyi dolduracak kadar birçok baştan sona çalışır. Varsayılan olarak, zaman çizelgeleri `1.0`yineleme sayısına sahiptir, bu, bir kez oynadıkları ve hiç yinelenmediği anlamına gelir.  
  
 Aşağıdaki örnek, bir yineleme sayısı belirterek <xref:System.Windows.Media.Animation.DoubleAnimation> basit süresini iki kez yürütmek için <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini kullanır.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Sonraki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimation> basit süresi yarıya çalmak için <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği kullanılır.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Bir <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>olarak ayarlarsanız, <xref:System.Windows.Media.Animation.Timeline> etkileşimli olarak veya zamanlama sistemi tarafından durduruluncaya kadar yinelenir. Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimation> süresiz olarak oynatacak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini kullanır.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Ek bir örnek için bkz. [bir animasyonu tekrarlama](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>Oto ters özelliği  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, bir <xref:System.Windows.Media.Animation.Timeline> her bir ileri yinelemenin sonunda geriye doğru çalıp çalınmayacağını belirtir. Aşağıdaki örnek, `true`için bir <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliğine ayarlanır; Sonuç olarak, sıfırdan 100 'e ve ardından 100 ' den sıfıra hareketlenir. Toplam 10 saniyelik oynar.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Bir <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> belirtmek için bir <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> değeri kullandığınızda ve bu <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği `true`ise, tek bir yineleme bir ileri yinelemeden ve ardından bir geriye doğru yineleme tarafından oluşur.  Aşağıdaki örnek, önceki örnekteki <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> bir <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> olarak ayarlar. Sonuç olarak, <xref:System.Windows.Media.Animation.DoubleAnimation> 20 saniye boyunca oynatılır: beş saniye boyunca İleri, beş saniye boyunca geri doğru, 5 saniye boyunca İleri ve beş saniye boyunca geriye doğru.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Bir kapsayıcı zaman çizelgesinin alt <xref:System.Windows.Media.Animation.Timeline> nesneleri varsa, kapsayıcı zaman çizelgesi ne zaman bir işlem yapar. Ek örnekler için bkz. [bir zaman çizelgesinin otomatik olarak ters çevrilip çevrilmeyeceğini belirtme](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime özelliği  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> özelliği, bir zaman çizelgesinin ne zaman başlayacağını belirtmenizi sağlar.  Bir zaman çizelgesinin başlangıç zamanı, üst zaman çizelgesine göre belirlenir. Sıfır saniyelik başlangıç zamanı, ana zaman çizelgesinin başladığı anda başladığı anlamına gelir; diğer herhangi bir değer, üst zaman çizelgesinin oynatılmaya başladığı ve alt zaman çizelgesinin yürütüldüğü zaman arasında bir fark oluşturur. Örneğin, iki saniyelik bir başlangıç zamanı, üst öğesi iki saniyelik bir zamana ulaştığında zaman çizelgesinin oynatılmaya başladığı anlamına gelir. Varsayılan olarak, tüm zaman çizelgeleri sıfır saniyelik başlangıç zamanına sahiptir. Ayrıca, zaman çizelgesinin başlamasını önleyen `null`için bir zaman çizelgesi başlangıç zamanı ayarlayabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [X:null Işaretleme uzantısını](../../../desktop-wpf/xaml-services/xnull-markup-extension.md)kullanarak null değerini belirtirsiniz.  
  
 Başlangıç saatinin, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ayarı nedeniyle her bir zaman çizelgesi yinelenilişinde uygulanmadığını unutmayın. 10 saniyelik <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ve <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A><xref:System.Windows.Media.Animation.RepeatBehavior> sahip bir animasyon oluşturuyorsanız, animasyon ilk kez çalınmadan önce 10 saniyelik bir gecikme olur ancak her bir sonraki tekrarda kullanılamaz. Ancak, animasyonun üst zaman çizelgesi yeniden başlatılmaya veya tekrarlanması olduysa, 10 saniyelik gecikme meydana gelir.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> özelliği, kademelendirme zaman çizelgeleri için yararlıdır. Aşağıdaki örnek iki alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesine sahip bir <xref:System.Windows.Media.Animation.Storyboard> oluşturur. İlk animasyonun beş saniyelik bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ve ikincisi de 3 saniyelik bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> sahiptir. Örnek, ikinci <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, ilk <xref:System.Windows.Media.Animation.DoubleAnimation> sona erdikten sonra yürütülmeye başlaması için 5 saniyeye ayarlar.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior özelliği  
 Bir <xref:System.Windows.Media.Animation.Timeline> toplam etkin süresinin sonuna ulaştığında, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği, en son değerini durdurduğunu veya bulundurmadığını belirtir. <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> bir animasyon, çıkış değerini tutar: hareketlendirilen Özellik animasyonun son değerini korur. <xref:System.Windows.Media.Animation.FillBehavior.Stop> değeri, animasyonun bittikten sonra hedef özelliğini etkilemesini durdurmasına neden olur.  
  
 Aşağıdaki örnek iki alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesine sahip bir <xref:System.Windows.Media.Animation.Storyboard> oluşturur. Her iki <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesi, bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> 0 ' dan 100 ' e animasyon uygular. <xref:System.Windows.Shapes.Rectangle> öğeler, 500 [cihazdan bağımsız piksel] animasyon olmayan <xref:System.Windows.FrameworkElement.Width%2A> değerlerine sahiptir.  
  
- İlk <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği, varsayılan değer olan <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>olarak ayarlanmıştır. Sonuç olarak, <xref:System.Windows.Media.Animation.DoubleAnimation> sona erdikten sonra dikdörtgenin genişliği 100 ' de kalır.  
  
- İkinci <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği <xref:System.Windows.Media.Animation.FillBehavior.Stop>olarak ayarlanmıştır. Sonuç olarak, ikinci <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> sona erdikten sonra 500 ' e geri döner.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Bir zaman çizelgesinin hızını denetleyen özellikler  
 <xref:System.Windows.Media.Animation.Timeline> sınıfı, hızını belirtmek için üç özellik sağlar:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – bu oranı, üst öğesine göre, bir <xref:System.Windows.Media.Animation.Timeline>için ilerledikçe belirtir. Bir değerden büyük değerler <xref:System.Windows.Media.Animation.Timeline> ve alt <xref:System.Windows.Media.Animation.Timeline> nesnelerinin hızını artırır; Sıfır ve diğeri arasındaki değerler yavaşlar. Bir değeri, <xref:System.Windows.Media.Animation.Timeline> üst öğesiyle aynı hızda ilerlediği anlamına gelir. Bir kapsayıcı zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> ayarı tüm alt <xref:System.Windows.Media.Animation.Timeline> nesnelerini de etkiler.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – hızlandırıcı tarafından harcanan bir zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.Duration%2A> yüzdesini belirtir. Bir örnek için bkz. [nasıl yapılır: animasyonun hızını hızlandırma veya Yavaşlatma](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>-yavaşlatıcı bir zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.Duration%2A> yüzdesini belirtir. Bir örnek için bkz. [nasıl yapılır: animasyonun hızını hızlandırma veya Yavaşlatma](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)
- [Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
- [Animasyon Zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970)
