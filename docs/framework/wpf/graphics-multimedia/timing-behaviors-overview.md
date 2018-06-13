---
title: Zamanlama Davranışlarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 31a6b7d3b92e886d9c90fc39d69f31cf72b99666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566330"
---
# <a name="timing-behaviors-overview"></a>Zamanlama Davranışlarına Genel Bakış
Bu konu animasyonların ve diğer zamanlama davranışlarını anlatır <xref:System.Windows.Media.Animation.Timeline> nesneleri.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için temel animasyon özelliklerini tanımanız. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Zaman Çizelgesi türleri  
 A <xref:System.Windows.Media.Animation.Timeline> zaman kesimini temsil eder. Bu kesimin uzunluğu, kaç kez yineleneceğini, ne kadar hızlı kesiminin ve daha fazla zaman ilerledikçe başlatırken belirtmenizi sağlayan özellikleri sağlar.  
  
 Zaman Çizelgesi sınıfından devralınan sınıflar animasyon ve ortam kayıttan yürütme gibi ek işlevsellik sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki sağlar <xref:System.Windows.Media.Animation.Timeline> türleri.  
  
|Zaman çizelgesi türü|Açıklama|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Soyut taban sınıfı için <xref:System.Windows.Media.Animation.Timeline> özellikleri için çıkış değerleri oluşturmak nesneleri.|  
|<xref:System.Windows.Media.MediaTimeline>|Çıkış ortam dosyasından oluşturur.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Bir tür <xref:System.Windows.Media.Animation.TimelineGroup> bu grupları ve denetimleri alt <xref:System.Windows.Media.Animation.Timeline> nesneleri.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Bir tür <xref:System.Windows.Media.Animation.ParallelTimeline> içerdiği zaman çizelgesi nesneleri için hedefleme bilgileri sağlar.|  
|<xref:System.Windows.Media.Animation.Timeline>|Zamanlama davranışlarını tanımlayan soyut taban sınıf.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|İçin soyut sınıf <xref:System.Windows.Media.Animation.Timeline> diğer içerebilen nesneleri <xref:System.Windows.Media.Animation.Timeline> nesneleri.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Zaman çizelgesinin uzunluğunu denetleyen özellikler  
 A <xref:System.Windows.Media.Animation.Timeline> zaman kesimini ve bir zaman çizelgesi uzunluğu farklı şekillerde açıklanan temsil eder. Aşağıdaki tabloda bir zaman çizelgesi uzunluğu açıklamak için birkaç terimleri tanımlar.  
  
|Terim|Açıklama|Özellikler||||  
|----------|-----------------|----------------|-|-|-|  
|Basit süre|Bir zaman çizelgesi tek bir ileriye doğru yineleme yapmak için geçen süre.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Bir yineleme|Bunu bir kez ve İleri yürütmek zaman çizelgesi için geçen süre <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği true ise, geriye dönük bir kez oynat.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Etkin süresi|Bir zaman çizelgesi tarafından belirtilen tüm yinelemeleri tamamlamak için geçen süre, <xref:System.Windows.Media.Animation.RepeatBehavior> özelliği.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration özelliği  
 Daha önce belirtildiği gibi bir zaman çizelgesi zaman kesimini temsil eder. Bu kesimin uzunluğu zaman çizelgesinin tarafından belirlenir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Bir zaman çizelgesi süresinin sonuna ulaştığında, yürütmeyi durdurur. Zaman Çizelgesi alt zaman çizelgeleri varsa, bunlar da yürütmeyi durdurur. Animasyonun, söz konusu olduğunda <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyon geçiş bitiş değeri başlangıç değerinden gereken süreyi belirtir. Zaman çizelgesinin süresi adlandırılır kendi *basit süre*, tek bir yineleme süresini ve animasyon oynadığı tekrarları dahil olmak üzere toplam süreyi birbirinden ayırmak için. Sınırlı saat değeri veya özel değerler kullanarak bir süre belirtebilirsiniz <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>. Animasyonun süresini çözmesi gerektiğini bir <xref:System.Windows.Duration.TimeSpan%2A> değer böylece değerler arasında geçiş.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Media.Animation.DoubleAnimation> ile bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Kapsayıcı zaman çizelgeleri gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, varsayılan süre olan sahip <xref:System.Windows.Duration.Automatic%2A>, bunlar otomatik olarak sona kendi son alt çalma durduğunda anlamına gelir. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Media.Animation.Storyboard> , <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniyede, tüm alt geçen süre uzunluğu çözümler <xref:System.Windows.Media.Animation.DoubleAnimation> tamamlamak için nesneleri.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ayarlayarak <xref:System.Windows.Media.Animation.Timeline.Duration%2A> için bir kapsayıcı zaman çizelgesinin bir <xref:System.Windows.Duration.TimeSpan%2A> değeri zorlayabilirsiniz uzun ya da kendi alt daha kısa yürütmek için <xref:System.Windows.Media.Animation.Timeline> nesneleri Yürüt. Ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kapsayıcı çizelgesinin alt uzunluğundan daha küçük bir değere <xref:System.Windows.Media.Animation.Timeline> nesneleri, alt <xref:System.Windows.Media.Animation.Timeline> nesneleri Durdur kapsayıcı zaman çizelgesi yürütülürken yürütülüyor. Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , <xref:System.Windows.Media.Animation.Storyboard> önceki örneklerle üç saniye. Sonuç olarak, ilk <xref:System.Windows.Media.Animation.DoubleAnimation> üç zaman animasyonlu hedef dikdörtgenin genişliği ile 60 saniye sonra İleri aşamalara durdurur.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior özelliği  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> denetimleri kaç kez basit süresinin tekrarlar. Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği, zaman çizelgesinin kaç kez belirtebilirsiniz (yineleme <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) veya yürütmesi gereken toplam süreyi (yineleme <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). Birçok başına sonuna istenen sayı veya süresini doldurmak gerektiği gibi çalışan her iki durumda da, animasyonun geçtiği. Varsayılan olarak, bir yineleme sayısı zaman çizelgelerini sahip `1.0`, bir kez Oynat ve en etmeyeceği anlamına gelir.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini bir <xref:System.Windows.Media.Animation.DoubleAnimation> bir yineleme sayısı belirterek basit süresince iki kez Yürüt.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 Sonraki örnek kullanır <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation> basit süresinin yarısı oynar.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> etkileşimli olarak veya zamanlama sistemi tarafından durdurulana kadar tekrarlar. Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation> süresiz olarak oynar.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Ek bir örnek için bkz: [animasyonu yineleyin](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse özelliği  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Özellik belirtir olup bir <xref:System.Windows.Media.Animation.Timeline> her ileri yineleme sonunda yürütülüp yürütülmeyeceğini. Aşağıdaki örnek ayarlar <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği bir <xref:System.Windows.Media.Animation.DoubleAnimation> için `true`; sonuç olarak, sıfırdan 100 ve 100'den sıfıra canlandırır. 10 saniye toplamı yürütür.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Kullandığınızda, bir <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> belirtmek için değer <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , bir <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, <xref:System.Windows.Media.Animation.Timeline> olan `true`, tek bir yineleme birini oluşur ileriye doğru yineleme tarafından izlenen bir geriye doğru yineleme.  Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , <xref:System.Windows.Media.Animation.DoubleAnimation> için önceki örnekten bir <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> iki. Sonuç olarak, <xref:System.Windows.Media.Animation.DoubleAnimation> 20 saniye oynar: 5 saniye tekrar geriye doğru beş saniyede için beş saniyede iletmek için iletmek ve sonra beş saniyede için geriye doğru.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Kapsayıcı zaman çizelgesi alt varsa <xref:System.Windows.Media.Animation.Timeline> nesneleri, bunlar ters kapsayıcı zaman çizelgesi yaptığında. Ek örnekler için bkz: [belirtin olup olmadığını bir zaman çizelgesi otomatik olarak ters çevrilip](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime özelliği  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Özelliği bir zaman çizelgesi başladığında belirtmenize olanak sağlar.  Bir zaman çizelgesinin başlama zamanı kendi üst zaman çizelgesi ile ilişkilidir. Zaman Çizelgesi üstü hemen sonra başlayan sıfır saniye anlamına gelir başlama zamanı başlatır; başka bir değer üst zaman çizelgesi oynamaya başladığı ve ne zaman alt zaman çizelgesinin yürütüldüğü arasındaki uzaklığı oluşturur. Örneğin, iki saniye başlama zamanı üst iki saniye cinsinden bir zaman sınırına ulaştığında yürütülmeye zaman çizelgesi başlayacağı anlamına gelir. Varsayılan olarak, tüm zaman çizelgeleri sıfır saniye başlama zamanı sahiptir. Bir zaman çizelgesinin da yerleştirebilir başlama zamanını `null`, önleyen zaman çizelgesi başlatılmasını. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], null kullanarak belirttiğiniz [x: Null işaretleme uzantısı](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
 Başlangıç zamanı Not uygulanan bir zaman çizelgesi yineler nedeniyle her zaman kendi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ayarı. Animasyonun ile oluşturmak için olsaydı bir <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 saniye ve <xref:System.Windows.Media.Animation.RepeatBehavior> , <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, ilk kez ancak art arda gelen her yineleme için animasyon oynanan önce 10 saniye bir gecikme olacaktır. Ancak, animasyonun üst zaman çizelgesi yeniden başlatın veya tekrar olsaydı, 10 saniye arasında bir gecikme olacaktır.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Özelliği zaman çizelgelerini çakışmayacak şekilde düzenlemek için yararlıdır. Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.Storyboard> iki alt olan <xref:System.Windows.Media.Animation.DoubleAnimation> nesneleri. İlk animasyon bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniyelik ve ikinci bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 3 saniyelik. Örnek <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> saniye <xref:System.Windows.Media.Animation.DoubleAnimation> 5 saniyeye başlayacak şekilde sonra ilk çalma <xref:System.Windows.Media.Animation.DoubleAnimation> sona erer.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior özelliği  
 Zaman bir <xref:System.Windows.Media.Animation.Timeline> toplam etkin süresinin sonuna ulaştığında <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği, durdurur veya son değeri sağlayıp sağlamadığını belirtir. Animasyonun ile bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "çıkış değerini tutan": özelliğin animasyonun son değerini korur. Değerini <xref:System.Windows.Media.Animation.FillBehavior.Stop> bittikten sonra hedef özelliği etkilemeyi durdurmasına neden olur.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.Storyboard> iki alt olan <xref:System.Windows.Media.Animation.DoubleAnimation> nesneleri. Her ikisi de <xref:System.Windows.Media.Animation.DoubleAnimation> nesnelere animasyon <xref:System.Windows.FrameworkElement.Width%2A> , bir <xref:System.Windows.Shapes.Rectangle> 0-100. <xref:System.Windows.Shapes.Rectangle> Öğelere sahip hareketli olmayan <xref:System.Windows.FrameworkElement.Width%2A> 500 [aygıttan bağımsız piksel] değerleri.  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Özelliği ilk <xref:System.Windows.Media.Animation.DoubleAnimation> ayarlanır <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, varsayılan değer. Sonuç olarak, 100 sonra dikdörtgenin genişliği kalır <xref:System.Windows.Media.Animation.DoubleAnimation> sona erer.  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> İkinci özelliğinin <xref:System.Windows.Media.Animation.DoubleAnimation> ayarlanır <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> saniye <xref:System.Windows.Shapes.Rectangle> sonra 500 döner <xref:System.Windows.Media.Animation.DoubleAnimation> sona erer.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Bir zaman çizelgesi hızına denetleyen özellikler  
 <xref:System.Windows.Media.Animation.Timeline> Sınıf kendi hızını belirtmek için üç özellik sağlar:  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – Zaman ilerledikçe için üst göre hızı belirten bir <xref:System.Windows.Media.Animation.Timeline>. Birden büyük değerler hızını artırır <xref:System.Windows.Media.Animation.Timeline> ve alt <xref:System.Windows.Media.Animation.Timeline> nesneleri; sıfır ve bir arasındaki değerleri yavaşlaması onu. Bir değeri gösterir <xref:System.Windows.Media.Animation.Timeline> , üst ile aynı hızda ilerler. <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> Ayar kapsayıcı zaman çizelgesinin tüm alt etkiler <xref:System.Windows.Media.Animation.Timeline> nesneler de.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – Yüzdesini belirtir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> hızlandırmaya bir zaman çizelgesi harcanan. Bir örnek için bkz: [nasıl yapılır: hızlandırmak veya animasyonun hızını düşürün](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md). 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -Yüzdesini belirtir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> bir zaman çizelgesi yavaşlatıcı. Bir örnek için bkz: [nasıl yapılır: hızlandırmak veya animasyonun hızını düşürün](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animasyon ve Zamanlama Sistemine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Zamanlama Olaylarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Animasyon zamanlama davranışı örneği](http://go.microsoft.com/fwlink/?LinkID=159970)
