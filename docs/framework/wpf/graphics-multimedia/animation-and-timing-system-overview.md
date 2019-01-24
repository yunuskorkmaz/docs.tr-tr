---
title: Animasyon ve Zamanlama Sistemine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: e50714e8cf50f42aad41ffa77fda34c55f9adb4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502994"
---
# <a name="animation-and-timing-system-overview"></a>Animasyon ve Zamanlama Sistemine Genel Bakış
Bu konuda, zamanlama sistemi animasyon nasıl kullandığı açıklanmaktadır <xref:System.Windows.Media.Animation.Timeline>, ve <xref:System.Windows.Media.Animation.Clock> özelliklerine animasyon uygulamak için sınıflar.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için kullanılacak erişebileceğinizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri bölümünde anlatıldığı gibi canlandırmak için animasyon [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Bağımlılık özellikleri ile ilgili bilgi sahibi olmasını da sağlar; Daha fazla bilgi için [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Zaman çizelgeleri ve saatler  
 [Animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) nasıl açıklanan bir <xref:System.Windows.Media.Animation.Timeline> temsil zaman ve animasyon bir parçası olan bir tür <xref:System.Windows.Media.Animation.Timeline> , çıktı değerleri üretir. Tek başına bir <xref:System.Windows.Media.Animation.Timeline>, dışında bir şey yapmadı yalnızca zaman kesimini açıklar. Zaman çizelgesinin olan <xref:System.Windows.Media.Animation.Clock> asıl işi yapan bir nesne. Benzer şekilde, animasyon gerçekten özelliklerine animasyon değil: çıkış değerleri nasıl hesaplanacağını bir animasyon sınıfı açıklar, ancak bu <xref:System.Windows.Media.Animation.Clock> özellikleri için geçerlidir ve animasyon çıktısını animasyon için oluşturuldu.  
  
 A <xref:System.Windows.Media.Animation.Clock> özel bir zamanlama ile ilgili çalışma zamanı durumu tutan nesne türüdür <xref:System.Windows.Media.Animation.Timeline>. Üç animasyon ve zamanlama sistemi için gerekli olan bit bilgi sağlar: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, ve <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> tarafından açıklanan zamanlama davranışları kullanarak, geçerli zamanı, ilerleme ve durumu belirler, <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>ve benzeri.  
  
 Çoğu durumda bir <xref:System.Windows.Media.Animation.Clock> zaman çizelgeniz için otomatik olarak oluşturulur. Ne zaman animasyon kullanarak bir <xref:System.Windows.Media.Animation.Storyboard> veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi saatler otomatik olarak zaman çizelgeleri ve animasyon için oluşturulan ve hedeflenen özelliklerini uygulanır. Ayrıca oluşturabileceğiniz bir <xref:System.Windows.Media.Animation.Clock> kullanılarak açık şekilde <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> yöntemi, <xref:System.Windows.Media.Animation.Timeline>. <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> Yöntemi için uygun türde bir saat oluşturur <xref:System.Windows.Media.Animation.Timeline> şirket adı verilir. Varsa <xref:System.Windows.Media.Animation.Timeline> içeren alt öğe zaman çizelgelerini, oluşturduğu <xref:System.Windows.Media.Animation.Clock> nesneler onlar için de. Ortaya çıkan <xref:System.Windows.Media.Animation.Clock> nesneleri yapısı ağaçlarında düzenlenir <xref:System.Windows.Media.Animation.Timeline> nesneleri ağacı, oluşturuldukları öğesinden.  
  
 Saatleri zaman çizelgeleri farklı türleri için farklı türde vardır. Aşağıdaki tabloda <xref:System.Windows.Media.Animation.Clock> farklı bazıları karşılık gelen türlerine <xref:System.Windows.Media.Animation.Timeline> türleri.  
  
|Zaman çizelgesi türü|Saat türünün|Saat amacı|  
|-------------------|----------------|-------------------|  
|Animasyon (devralınan <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Bağımlılık özelliği için çıkış değerleri oluşturur.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Bir medya dosyası işler.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Gruplar ve alt öğe denetimleri <xref:System.Windows.Media.Animation.Clock> nesneleri|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Gruplar ve alt öğe denetimleri <xref:System.Windows.Media.Animation.Clock> nesneleri|  
  
 Tüm uygulama <xref:System.Windows.Media.Animation.AnimationClock> kullanarak uyumlu bağımlılık özellikleri için oluşturma nesneleri <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> yöntemi.  
  
 Çok sayıda benzer nesne animasyon ekleme gibi yoğun performans senaryolarında, kendi yönetme <xref:System.Windows.Media.Animation.Clock> kullanım, performans avantajı sağlayabilir.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Saatler ve saat Yöneticisi  
 Nesnelere animasyon zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yöneten zaman yöneticisi olan <xref:System.Windows.Media.MediaPlayer.Clock%2A> , zaman çizelgeleri için oluşturulan nesneler. Ağacının kök zaman yöneticisidir <xref:System.Windows.Media.MediaPlayer.Clock%2A> nesneler ve zaman içinde o ağaç akışını denetler.  Bir saat Yöneticisi her biri için otomatik olarak oluşturulur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama ve uygulama geliştiriciye görünmez. Birden çok kez saniyede; "ticks" saat Yöneticisi Gerçek her gerçekleşen tıklarının sayısını ikinci kullanılabilir sistem kaynaklarına bağlı olarak değişir. Her biri bu saat döngüsü sırasında zaman Yöneticisi tüm durumu hesaplar <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> zamanlama ağacındaki nesneleri.  
  
 Saat Yöneticisi arasındaki ilişki aşağıda gösterilmiştir ve <xref:System.Windows.Media.Animation.AnimationClock>ve bir animasyonlu bağımlılık özelliği.  
  
 ![Sistem bileşenleri zamanlama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Bir özelliğe animasyon ekleme  
  
 Zaman Yöneticisi işaretlerini, süresini güncelleştirir. her <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> uygulama. Varsa <xref:System.Windows.Media.Animation.Clock> olduğu bir <xref:System.Windows.Media.Animation.AnimationClock>, kullandığı <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> uygulamayı oluşturulduğu öğesinden geçerli çıkış değerini hesaplamak için. <xref:System.Windows.Media.Animation.AnimationClock> Sağlayan <xref:System.Windows.Media.Animation.AnimationTimeline> geçerli yerel saat, genellikle temel özellik değeri, bir giriş değeri ve varsayılan bir hedef değer. Animasyonlu değerini aldığınızda özelliğini kullanarak <xref:System.Windows.DependencyObject.GetValue%2A> , yöntemi veya CLR erişeni çıktısını alın, <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Saat grupları  
 Nasıl farklı türde vardır, önceki bölümde açıklanan <xref:System.Windows.Media.Animation.Clock> zaman çizelgeleri farklı türde nesneler. Saat Yöneticisi arasındaki ilişki aşağıdaki çizimde bir <xref:System.Windows.Media.Animation.ClockGroup>e <xref:System.Windows.Media.Animation.AnimationClock>ve bir animasyonlu bağımlılık özelliği. A <xref:System.Windows.Media.Animation.ClockGroup> gibi diğer zaman çizelgelerine grubunda zaman çizelgeleri için oluşturulan <xref:System.Windows.Media.Animation.Storyboard> animasyonları ve diğer zaman çizelgelerine gruplayan sınıfı.  
  
 ![Sistem bileşenleri zamanlama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Bir ClockGroup  
  
#### <a name="composition"></a>Oluşturma  
 Birden çok ilişkilendirmek mümkündür durumda tek bir özellik ile bir önceki çıkış değeri temel değer olarak saat her saati kullanır saatler. Aşağıdaki çizim üç gösterir <xref:System.Windows.Media.Animation.AnimationClock> nesneleri aynı özelliğe uygulanır. Clock1 için taban değerini animasyonlu özelliği, giriş olarak kullanan ve çıktı üretmek için kullanır. Clock2 Clock1, girdi olarak gelen çıkış alır ve çıktı üretmek için kullanır. Clock3 Clock2, girdi olarak gelen çıkış alır ve çıktı üretmek için kullanır. Birden çok saatleri aynı anda aynı özelliğe etkilediğinde, bunlar bir oluşturma zincirindeki olduğu söylenir.  
  
 ![Sistem bileşenleri zamanlama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Bir oluşum zinciri  
  
 Giriş ve çıkış arasında bir ilişki oluşturulur, ancak unutmayın <xref:System.Windows.Media.Animation.AnimationClock> nesneleri oluşturma zincirinde zamanlama davranışları etkilenmez; <xref:System.Windows.Media.Animation.Clock> nesneleri (dahil olmak üzere <xref:System.Windows.Media.Animation.AnimationClock> nesneleri), üst öğede hiyerarşik bağımlılığa sahip <xref:System.Windows.Media.Animation.Clock> nesneleri.  
  
 Birden çok saatleri aynı özelliğe uygulamak <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> uygulanırken bir <xref:System.Windows.Media.Animation.Storyboard>, animasyon, veya <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Saat döngüsü ve olay birleştirme  
 Bunu işaretlerini her zaman çıkış değerleri hesaplama ek olarak saat Yöneticisi diğer çalışır: her saat durumunu belirler ve olayları uygun olarak oluşturur.  
  
 Saat döngüsü sık meydana gelirken, çok sayıda Ölçü çizgileri arasında gerçekleşmesi için mümkündür. Örneğin, bir <xref:System.Windows.Media.Animation.Clock> durduruldu, çalışmaya ve yeniden, bu durumda durduruldu, <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> değerini üç kez değişmiş olur. Teoride, <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olay gerçekleşti tek bir tick birden çok kez; ancak, zamanlama altyapısı olayları birleştirir böylece <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olay yükseltilebilir en fazla değer çizgisi. Bu tüm zamanlama olayları için geçerlidir: en fazla bir olayı her tür için oluşturulur bir verilen <xref:System.Windows.Media.Animation.Clock> nesne.  
  
 Olduğunda bir <xref:System.Windows.Media.Animation.Clock> bir durumdan diğerine geçer ve saat döngüleri arasında özgün durumuna geri döndürür (gelen değiştirme gibi <xref:System.Windows.Media.Animation.ClockState.Active> için <xref:System.Windows.Media.Animation.ClockState.Stopped> daha sonra tekrar <xref:System.Windows.Media.Animation.ClockState.Active>), ilişkili olay yine de gerçekleşir.  
  
 Zamanlama olayları hakkında daha fazla bilgi için bkz: [zamanlama olaylarına genel bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Geçerli ve özelliklerinin temel değerleri  
 Bir animatable özelliği iki değerlere sahip olabilir: bir temel değerini ve geçerli bir değer. CLR erişeni kullanarak özelliği ayarlandığında ya da <xref:System.Windows.DependencyObject.SetValue%2A> yöntemi, taban değerini ayarlayın. Bir özelliğe animasyon değil, temel ve geçerli değerlerini aynıdır.  
  
 Bir özelliğe animasyon eklediğinizde <xref:System.Windows.Media.Animation.AnimationClock> özelliğin ayarlar *geçerli* değeri. CLR erişeni aracılığıyla özelliğin değerini alma veya <xref:System.Windows.DependencyObject.GetValue%2A> yöntem çıkışı döndürür <xref:System.Windows.Media.Animation.AnimationClock> olduğunda <xref:System.Windows.Media.Animation.AnimationClock> olduğu <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling>. Özelliğin taban değerini kullanarak alabilirsiniz <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Zamanlama Olaylarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)
- [Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
