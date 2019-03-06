---
title: Zamanlama Davranışlarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: f7c1aa81a5d3c283fdea06dd812f879f096c2ee2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355525"
---
# <a name="timing-behaviors-overview"></a>Zamanlama Davranışlarına Genel Bakış
Bu konuda, animasyonları ve diğer zamanlama davranışları açıklanmaktadır <xref:System.Windows.Media.Animation.Timeline> nesneleri.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için temel animasyon özellikleri tanımanız gerekir. Daha fazla bilgi için [animasyona genel bakış](animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Zaman Çizelgesi türleri  
 A <xref:System.Windows.Media.Animation.Timeline> zaman kesimini temsil eder. Bu, kaç kez yineleneceğini, ne kadar hızlı kesiminin ve daha fazla zaman ilerledikçe başlamalıdır, segment uzunluğunu belirtmenizi sağlayan özellikleri sağlar.  
  
 Zaman Çizelgesi sınıfından devralınan sınıflar, animasyon ve medya kayıttan yürütme gibi ek işlevler sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verilmiştir <xref:System.Windows.Media.Animation.Timeline> türleri.  
  
|Zaman çizelgesi türü|Açıklama|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|İçin soyut temel sınıf <xref:System.Windows.Media.Animation.Timeline> özelliklerine animasyon ekleme için çıkış değerleri oluşturun nesneleri.|  
|<xref:System.Windows.Media.MediaTimeline>|Çıkış medya dosyasından oluşturur.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Bir tür <xref:System.Windows.Media.Animation.TimelineGroup> , gruplar ve denetimler alt <xref:System.Windows.Media.Animation.Timeline> nesneleri.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Bir tür <xref:System.Windows.Media.Animation.ParallelTimeline> içerdiği zaman çizelgesi nesneleri için hedefleme bilgileri sağlar.|  
|<xref:System.Windows.Media.Animation.Timeline>|Zamanlama davranışları tanımlar soyut temel sınıf.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Soyut sınıf için <xref:System.Windows.Media.Animation.Timeline> diğer içerebilen nesneleri <xref:System.Windows.Media.Animation.Timeline> nesneleri.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Bir zaman çizelgesi uzunluğunu denetleyen özellikler  
 A <xref:System.Windows.Media.Animation.Timeline> zaman bir segmentini ve bir zaman çizelgesi uzunluğunu farklı şekillerde açıklanan temsil eder. Aşağıdaki tabloda bir zaman çizelgesi uzunluğunu tanımlamak için birkaç terimlerini tanımlar.  
  
|Terim|Açıklama|Özellikler||||  
|----------|-----------------|----------------|-|-|-|  
|Basit süresi|Tek bir ileriye doğru yineleme yapmak için bir zaman çizelgesi sürenin uzunluğunu alır.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Bir yineleme|İsteğe bağlı olarak sürenin uzunluğunu İleri sonra ve yürütmek bir zaman çizelgesinde geçen <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği true ise, geriye dönük bir kez Yürüt.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Etkin dönem|Bir zaman çizelgesi tarafından belirtilen tüm yinelemeleri tamamlanması için geçen sürenin uzunluğunu kendi <xref:System.Windows.Media.Animation.RepeatBehavior> özelliği.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration özelliği  
 Daha önce belirtildiği gibi bir zaman çizelgesi zaman kesimini temsil eder. Bu kesimin uzunluğu çizelgesinin tarafından belirlenir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Zaman Çizelgesi süresinin sonuna ulaştığında yürütmeyi durdurur. Zaman Çizelgesi alt öğe zaman çizelgelerini varsa, bunlar da yürütmeyi durdurur. Bir animasyon, söz konusu olduğunda <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyon bitiş değeri başlangıç değerinden geçişin ne kadar alacağını belirtir. Zaman çizelgesinin süresi adlandırılır, *basit süresi*tek bir yineleme süresini ve animasyon çalar repetitions dahil olmak üzere toplam süreyi ayırt etmek için. Sınırlı bir süre değeri ya da özel değerlerini kullanarak bir süre belirtebilirsiniz <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>. Animasyonun süresi için çözümlenmelidir bir <xref:System.Windows.Duration.TimeSpan%2A> değer böylece değerler arasında geçiş.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Media.Animation.DoubleAnimation> ile bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Kapsayıcı zaman çizelgeleri gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, varsayılan süre olan <xref:System.Windows.Duration.Automatic%2A>, bunlar otomatik olarak sonlandırmak son alt öğe yürütme durdurulduğunda anlamına gelir. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Media.Animation.Storyboard> olan <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye olarak, tüm alt süresi uzunluğu çözümler <xref:System.Windows.Media.Animation.DoubleAnimation> tamamlamak için nesneleri.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ayarlayarak <xref:System.Windows.Media.Animation.Timeline.Duration%2A> için kapsayıcı zaman çizelgesinin bir <xref:System.Windows.Duration.TimeSpan%2A> değeri zorlayabilirsiniz uzun veya kısa alt <xref:System.Windows.Media.Animation.Timeline> nesneleri Yürüt. Ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kapsayıcı çizelgesinin alt uzunluğundan daha küçük bir değere <xref:System.Windows.Media.Animation.Timeline> nesneleri, alt <xref:System.Windows.Media.Animation.Timeline> nesneleri Durdur kapsayıcı zaman çizelgesi yürütülürken yürütülüyor. Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , <xref:System.Windows.Media.Animation.Storyboard> önceki örneklerle üç saniye. Sonuç olarak, ilk <xref:System.Windows.Media.Animation.DoubleAnimation> ilerlediğini üç zaman animasyonlu hedef dikdörtgenin genişliği ile 60 saniye sonra durur.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior özelliği  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> , yinelenen basit süresinin kaç kez denetler. Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği, zaman çizelgesinin kaç kez belirtebilirsiniz (yineleme <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) veya yürütmesi gereken toplam süreyi (yineleme <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). İstenen sayı veya süresini doldurmak gerektiği gibi birçok başına sonuna çalışırken her iki durumda da animasyon geçer. Varsayılan olarak, bir yineleme sayısı zaman çizelgelerine sahip `1.0`, bir kez oynatmak ve hiç tekrarlamayın anlamına gelir.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini bir <xref:System.Windows.Media.Animation.DoubleAnimation> basit süresince iki kez bir yineleme sayısı belirterek Yürüt.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Sonraki örnekte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation> yarım basit süre için Yürüt.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> etkileşimli olarak veya zamanlama sistemi tarafından durdurulana kadar yinelenir. Aşağıdaki örnekte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation> süresiz olarak yürüt.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Ek bir örnek için bkz. [animasyonu yineleme](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse özelliği  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Özellik belirtir olup olmadığını bir <xref:System.Windows.Media.Animation.Timeline> iletme her yinelemenin sonunda yürütülüp yürütülmeyeceğini. Aşağıdaki örnekte ayarlar <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği bir <xref:System.Windows.Media.Animation.DoubleAnimation> için `true`; sonuç olarak, sıfırdan 100 ve 100'den sıfıra canlandırın. Bu, toplamda 10 saniye boyunca yürütür.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Kullandığınızda, bir <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> belirtmek için değer <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , bir <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> , söz konusu özellik <xref:System.Windows.Media.Animation.Timeline> olduğu `true`, tek bir yinelemeyi biri oluşur ileriye doğru yineleme tarafından izlenen bir geriye doğru yineleme.  Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , <xref:System.Windows.Media.Animation.DoubleAnimation> önceki örnekte bir <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> iki. Sonuç olarak, <xref:System.Windows.Media.Animation.DoubleAnimation> 20 saniye oynar: beş saniye için geriye doğru beş saniyede 5 saniye tekrar iletmek için İleri ve geriye doğru beş saniye boyunca.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Bir kapsayıcı zaman çizelgesi alt varsa <xref:System.Windows.Media.Animation.Timeline> nesnelerini kapsayıcı zaman çizelgesi yaptığında, ters. Diğer örnekler için [belirtin olup olmadığını bir zaman çizelgesinin otomatik olarak ters çevrilip](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime özelliği  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Özelliği bir zaman çizelgesi başladığında belirtmenize imkan tanır.  Zaman çizelgesinin başlayan, üst zaman çizelgesine göre olan. Zaman Çizelgesi üstü hemen sonra başlar sıfır saniye anlamına gelir başlama zamanı başlatır; bir uzaklık üst zaman çizelgesi oynatma başladığında ve alt çizelgesinin zaman arasında başka bir değer oluşturur. Örneğin, iki saniye başlama zamanı iki saniye süre üst sınırına ulaştığında yürütmeyi zaman çizelgesini başlatan anlamına gelir. Varsayılan olarak, tüm zaman çizelgeleri sıfır saniye başlama zamanı sahiptir. Zaman çizelgesinin da ayarlayabilir başlama zamanını `null`, engelleyen zaman çizelgesinin başlamasını. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], null kullanarak belirttiğiniz [x: Null işaretleme uzantısı](../../xaml-services/x-null-markup-extension.md).  
  
 Başlangıç zamanı olmadığına dikkat edin uygulanan bir zaman çizelgesi yineler nedeniyle her zaman kendi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ayarı. Bir animasyonu oluşturmak için olsaydı bir <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 saniye ve <xref:System.Windows.Media.Animation.RepeatBehavior> , <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, ilk kez ancak art arda gelen her yineleme için animasyon yürütülen önce 10 saniyelik gecikme olur. Ancak, animasyonun üst zaman çizelgesine yeniden başlatın veya yineleme için olsaydı, 10 saniyelik gecikme oluşacak.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Özelliği zaman çizelgeleri kademelendirme için yararlıdır. Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Media.Animation.Storyboard> olan iki alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesneleri. İlk animasyon bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye ve ikinci bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 3 saniye. Örnek <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ikinci <xref:System.Windows.Media.Animation.DoubleAnimation> 5 saniye olarak başlayacak şekilde birinciden sonra yürütmeyi <xref:System.Windows.Media.Animation.DoubleAnimation> sona erer.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior özelliği  
 Olduğunda bir <xref:System.Windows.Media.Animation.Timeline> toplam etkin süresinin sonuna ulaştığında <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özellik durdurur veya son değerini sağlayıp sağlamadığını belirtir. Bir animasyon içeren bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "çıkış değeri tutan": animasyon uygulanan özellik animasyonun son değerini korur. Değerini <xref:System.Windows.Media.Animation.FillBehavior.Stop> , bittikten sonra hedef özelliği etkileyen durdurmasına neden olur.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Media.Animation.Storyboard> olan iki alt <xref:System.Windows.Media.Animation.DoubleAnimation> nesneleri. Her ikisi de <xref:System.Windows.Media.Animation.DoubleAnimation> nesnelere animasyon <xref:System.Windows.FrameworkElement.Width%2A> , bir <xref:System.Windows.Shapes.Rectangle> 0-100. <xref:System.Windows.Shapes.Rectangle> Öğelere sahip olmayan animasyon <xref:System.Windows.FrameworkElement.Width%2A> 500 [cihaz bağımsız piksel] değerleri.  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Özelliği ilk <xref:System.Windows.Media.Animation.DoubleAnimation> ayarlanır <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, varsayılan değer. Sonuç olarak, sonra 100 dikdörtgenin genişliğini kalır <xref:System.Windows.Media.Animation.DoubleAnimation> sona erer.  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> İkinci özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> ayarlanır <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> ikinci <xref:System.Windows.Shapes.Rectangle> sonra 500 döner <xref:System.Windows.Media.Animation.DoubleAnimation> sona erer.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Zaman çizelgesinin hızını denetleyen özellikler  
 <xref:System.Windows.Media.Animation.Timeline> Sınıfı hızını belirtmek için üç özellikleri sağlar:  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – Zaman ilerledikçe için üst göre hızı belirtir bir <xref:System.Windows.Media.Animation.Timeline>. Birden büyük değerler hızını artırır <xref:System.Windows.Media.Animation.Timeline> ve alt <xref:System.Windows.Media.Animation.Timeline> nesneleri; değerleri sıfır ve bir arasındaki yavaşlamasına bu. Belirten bir değeri, <xref:System.Windows.Media.Animation.Timeline> üst işlemleriyle aynı fiyat ilerler. <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> Kapsayıcı zaman çizelgesinin ayar tüm alt etkiler <xref:System.Windows.Media.Animation.Timeline> nesneler de.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – Yüzdesini belirtir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> hızlandırma bir zaman çizelgesi harcanan. Bir örnek için bkz [nasıl yapılır: Bir animasyonu hızlandırma veya Yavaşlatma](how-to-accelerate-or-decelerate-an-animation.md). 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -Yüzdesini belirtir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> yavaşlatma bir zaman çizelgesi harcanan. Bir örnek için bkz [nasıl yapılır: Bir animasyonu hızlandırma veya Yavaşlatma](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)
- [Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
- [Animasyon zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970)
