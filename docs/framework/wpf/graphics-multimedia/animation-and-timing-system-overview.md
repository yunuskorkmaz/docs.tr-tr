---
title: Animasyon ve Zamanlama Sistemine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: bfb9a337a604fe8d86d208344d4371748e28f285
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557972"
---
# <a name="animation-and-timing-system-overview"></a>Animasyon ve Zamanlama Sistemine Genel Bakış
Bu konu, zamanlama sistemi animasyon nasıl kullandığını açıklar <xref:System.Windows.Media.Animation.Timeline>, ve <xref:System.Windows.Media.Animation.Clock> özelliklerine animasyon sınıfları.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için kullanabilmek için olmalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] açıklandığı gibi özellikleri, animasyon animasyonları [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Ayrıca bağımlılık özellikleri hakkında bilgi sahibi olmanız yardımcı olur; Daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Zaman çizelgeleri ve saatler  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) nasıl açıklandığı bir <xref:System.Windows.Media.Animation.Timeline> gösteren kesimi süresi ve bir animasyon türüdür <xref:System.Windows.Media.Animation.Timeline> çıkış değerleri üretir. Tek başına bir <xref:System.Windows.Media.Animation.Timeline>, başka hiçbir şey yapmaz yalnızca zaman kesimini açıklanmaktadır. Zaman çizelgesinin olduğu <xref:System.Windows.Media.Animation.Clock> gerçek işi nesne. Benzer şekilde, animasyon gerçekte özelliklerine animasyon değil: bir animasyon sınıfı çıkış değerlerinin nasıl hesaplanması gerektiğini açıklar, ancak bunu <xref:System.Windows.Media.Animation.Clock> animasyonun çıktısını ve özelliklerine uygulayan animasyon için oluşturuldu.  
  
 A <xref:System.Windows.Media.Animation.Clock> için zamanlama ile ilgili çalışma zamanı durumunu koruyan nesne özel bir tür <xref:System.Windows.Media.Animation.Timeline>. Üç animasyon ve zamanlama sistem için gerekli olan BITS bilgi sağlar: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, ve <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> tarafından açıklanan zamanlama davranışlarını kullanarak geçerli saati, ilerleme ve durumunu belirler, <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>ve benzeri.  
  
 Çoğu durumda, bir <xref:System.Windows.Media.Animation.Clock> kendi zaman çizelgesi için otomatik olarak oluşturulur. Animasyon yapıldığında kullanarak bir <xref:System.Windows.Media.Animation.Storyboard> veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi, saatler otomatik olarak zaman çizelgelerini ve animasyonları için oluşturulur ve kendi hedeflenen özelliklere uygulanır. Ayrıca bir <xref:System.Windows.Media.Animation.Clock> kullanarak açıkça <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> yöntemi, <xref:System.Windows.Media.Animation.Timeline>. <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> Yöntemi için uygun türde bir saat yaratır <xref:System.Windows.Media.Animation.Timeline> çağırıldığı üzerinde. Varsa <xref:System.Windows.Media.Animation.Timeline> alt zaman çizelgelerini içeren oluşturduğu <xref:System.Windows.Media.Animation.Clock> bunlar için nesneler de. Elde edilen <xref:System.Windows.Media.Animation.Clock> nesneleri yapısı ağaçlarında düzenlenir <xref:System.Windows.Media.Animation.Timeline> nesneleri ağaç, oluşturuldukları gelen.  
  
 Farklı türde zaman çizelgeleri saatler farklı tür vardır. Aşağıdaki tabloda <xref:System.Windows.Media.Animation.Clock> farklı bazıları karşılık gelen türlerine <xref:System.Windows.Media.Animation.Timeline> türleri.  
  
|Zaman çizelgesi türü|Saat türü|Saat amacı|  
|-------------------|----------------|-------------------|  
|Animasyon (devraldığı <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Bağımlılık özelliği için çıkış değerleri oluşturur.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Bir medya dosyasını işler.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Gruplar ve kendi alt denetimleri <xref:System.Windows.Media.Animation.Clock> nesneleri|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Gruplar ve kendi alt denetimleri <xref:System.Windows.Media.Animation.Clock> nesneleri|  
  
 Herhangi bir uygulama <xref:System.Windows.Media.Animation.AnimationClock> oluşturduğunuz uyumlu bağımlılık özelliklerine kullanarak nesneleri <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> yöntemi.  
  
 Çok sayıda benzer nesnelerin animasyonu gibi performansı yoğun senaryolarda kendi yönetme <xref:System.Windows.Media.Animation.Clock> kullanım performans avantajı sağlayabilir.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Saatler ve zaman Yöneticisi  
 Animasyon yapıldığında nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yöneten zaman yöneticisi olan <xref:System.Windows.Media.MediaPlayer.Clock%2A> , zaman çizelgeleri için oluşturulan nesneler. Zaman Yöneticisi ağacının köküdür <xref:System.Windows.Media.MediaPlayer.Clock%2A> nesneleri ve o ağaçtaki zaman akışını denetler.  Bir zaman Yöneticisi otomatik olarak her biri için oluşturulan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama ve uygulama geliştiricisine görünmezdir. Birçok kez saniyede; "çizgilerine" zaman Yöneticisi her ortaya çizgilerine gerçek sayısını ikinci mevcut sistem kaynaklarının bağlı olarak değişir. Bu çizgilerine her biri sırasında zaman Yöneticisi tüm durumunu hesaplar <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> zamanlama ağacındaki nesneleri.  
  
 Aşağıdaki çizim zaman yöneticisi arasındaki ilişkiyi gösterir ve <xref:System.Windows.Media.Animation.AnimationClock>ve bir animasyonlu bağımlılık özelliği.  
  
 ![Sistem bileşenleri zamanlama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Bir özelliğe animasyon ekleme  
  
 Zaman Yöneticisi işaretlerini zaman zaman güncelleştirmeleri her <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> uygulamadaki. Varsa <xref:System.Windows.Media.Animation.Clock> olan bir <xref:System.Windows.Media.Animation.AnimationClock>, kullandığı <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> onu oluşturulduğu gelen geçerli çıkış değerini hesaplamak için. <xref:System.Windows.Media.Animation.AnimationClock> Sağlayan <xref:System.Windows.Media.Animation.AnimationTimeline> geçerli yerel saat, genellikle temel özellik değeri, bir giriş değerinin ve varsayılan hedef değeri. Animasyonlu değeri aldığınızda özelliğini kullanarak <xref:System.Windows.DependencyObject.GetValue%2A> , yöntemi veya CLR erişimcisi çıktısını almak kendi <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Saat grupları  
 Nasıl farklı türde vardır önceki bölümde açıklanan <xref:System.Windows.Media.Animation.Clock> nesneler için farklı türde zaman çizelgeleri. Zaman Yöneticisi arasındaki ilişki aşağıda gösterilmiştir bir <xref:System.Windows.Media.Animation.ClockGroup>, bir <xref:System.Windows.Media.Animation.AnimationClock>ve bir animasyonlu bağımlılık özelliği. A <xref:System.Windows.Media.Animation.ClockGroup> gibi diğer zaman çizelgelerini Grup zaman çizelgelerini oluşturulan <xref:System.Windows.Media.Animation.Storyboard> animasyonları ve diğer zaman çizelgelerini gruplayan sınıfı.  
  
 ![Sistem bileşenleri zamanlama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Bir ClockGroup  
  
#### <a name="composition"></a>Birleşim  
 Birden çok ilişkilendirmek mümkündür saatin temel değer olarak bir önceki çıktı değerini her saat kullanır; bu durumda, tek bir özelliğe sahip saatini belirtir. Aşağıdaki çizim üç göstermektedir <xref:System.Windows.Media.Animation.AnimationClock> aynı özelliğe uygulanan nesnesi. Clock1 animasyonlu özelliğin temel değerini kendi girişi olarak ve çıktı üretmek için kullanır. Clock2 Clock1 giriş olarak gelen çıktıyı alır ve çıktı üretmek için kullanır. Clock3 Clock2 giriş olarak gelen çıktıyı alır ve çıktı üretmek için kullanır. Aynı anda birden çok saati aynı özelliğe etkilediğinde, bunlar bir birleşim zincirinde söylenir.  
  
 ![Sistem bileşenleri zamanlama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Bir birleşim zinciri  
  
 Giriş ve çıkışı arasında bir ilişki oluşturulur, ancak unutmayın <xref:System.Windows.Media.Animation.AnimationClock> nesneleri birleşim zincirinde zamanlama davranışları etkilenmez; <xref:System.Windows.Media.Animation.Clock> nesneleri (de dahil olmak üzere <xref:System.Windows.Media.Animation.AnimationClock> nesneler) kendi üst öğede hiyerarşik bir bağımlılığa sahip <xref:System.Windows.Media.Animation.Clock> nesneleri.  
  
 Birden çok saati aynı özelliğe uygulamak için kullanmak <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> uygulanırken bir <xref:System.Windows.Media.Animation.Storyboard>, animasyon veya <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Ticks ve olay birleştirme  
 Bunu işaretlerini her zaman çıkış değerleri hesaplama yanı sıra zaman Yöneticisi diğer çalışır: her saat durumunu belirler ve uygun şekilde olayları başlatır.  
  
 Ticks sıklıkla meydana gelirken, çok sayıda arasında çizgilerine gerçekleşmesi için mümkündür. Örneğin, bir <xref:System.Windows.Media.Animation.Clock> durduruldu, başlatıldı ve yeniden, bu durumda durduruldu kendi <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> değeri üç kez değişmiş olur. Teorik, <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olay gerçekleşti, tek bir değer birden çok kez; ancak, olaylar, zamanlama altyapısının birleştirir böylece <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olayının en fazla bir kez ticks '. Bu tüm zamanlama olayları için geçerlidir: en çok bir her tür olayı için bir verilen <xref:System.Windows.Media.Animation.Clock> nesnesi.  
  
 Zaman bir <xref:System.Windows.Media.Animation.Clock> bir durumdan diğerine geçer ve çizgilerine arasında özgün durumuna geri döner (gelen değiştirme gibi <xref:System.Windows.Media.Animation.ClockState.Active> için <xref:System.Windows.Media.Animation.ClockState.Stopped> daha sonra tekrar <xref:System.Windows.Media.Animation.ClockState.Active>), ilişkili olay oluşmaya devam eder.  
  
 Zamanlama olayları hakkında daha fazla bilgi için bkz: [zamanlama olaylarına genel bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Geçerli ve özelliklerinin temel değerleri  
 Canlandırılabilir özelliği iki değerlere sahip olabilir: temel değerini ve geçerli bir değer. CLR erişimcisi kullanarak özellik ayarladığınızda veya <xref:System.Windows.DependencyObject.SetValue%2A> yöntemi, taban değerini ayarlayın. Bir özellik animasyonlu değil, temel ve geçerli değerlerini aynıdır.  
  
 Bir özellik, animasyon eklediğinizde <xref:System.Windows.Media.Animation.AnimationClock> özelliğin ayarlar *geçerli* değeri. Özelliğin değerini kendi CLR erişimcisi aracılığıyla alma veya <xref:System.Windows.DependencyObject.GetValue%2A> yöntemi döndürür çıktısını <xref:System.Windows.Media.Animation.AnimationClock> zaman <xref:System.Windows.Media.Animation.AnimationClock> olan <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling>. Özelliğin temel değerini kullanarak alabilirsiniz <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Zamanlama Olaylarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
