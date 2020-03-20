---
title: Animasyon ve Zamanlama Sistemine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187715"
---
# <a name="animation-and-timing-system-overview"></a>Animasyon ve Zamanlama Sistemine Genel Bakış
Bu konu, <xref:System.Windows.Media.Animation.Timeline>zamanlama sisteminin özellikleri canlandırmak <xref:System.Windows.Media.Animation.Clock> için animasyonu ve sınıfları nasıl kullandığını açıklar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [Animasyongenel Bakışı'nda](animation-overview.md)açıklandığı gibi özellikleri canlandırmak için animasyonları kullanabilmelisiniz. Ayrıca bağımlılık özellikleri aşina olmak yardımcı olur; daha fazla bilgi için [Bağımlılık Özellikleri Genel Bakış'a](../advanced/dependency-properties-overview.md)bakın.  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>Zaman Çizelgeleri ve Saatler  
 [Animasyona Genel Bakış,](animation-overview.md) bir <xref:System.Windows.Media.Animation.Timeline> zaman kesimini nasıl temsil <xref:System.Windows.Media.Animation.Timeline> ettiğini ve animasyonun çıktı değerleri üreten bir tür olduğunu açıklamıştır. Tek başına, <xref:System.Windows.Media.Animation.Timeline>bir , sadece zaman bir segment tanımlamak dışında bir şey yapmaz. Gerçek işi yapan zaman <xref:System.Windows.Media.Animation.Clock> çizelgesinin nesnesidir. Benzer şekilde, animasyon aslında özellikleri animasyon değil: bir animasyon sınıfı çıkış değerlerinin nasıl <xref:System.Windows.Media.Animation.Clock> hesaplanması gerektiğini açıklar, ancak animasyon çıktısını yönlendiren ve özelliklere uygulayan animasyon için oluşturulan dır.  
  
 A, <xref:System.Windows.Media.Animation.Clock> <xref:System.Windows.Media.Animation.Timeline>zamanlamayla ilişkili çalışma zamanı durumunu koruyan özel bir nesne türüdür. Animasyon ve zamanlama sistemi için gerekli olan üç bilgi <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A> <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>biti <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>sağlar: , ve . <xref:System.Windows.Media.Animation.Clock> A, şu anki zamanını, ilerlemesini ve durumunu, <xref:System.Windows.Media.Animation.Timeline>onun : <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, , ve benzeri tarafından açıklanan zamanlama davranışlarını kullanarak belirler.  
  
 Çoğu durumda, <xref:System.Windows.Media.Animation.Clock> zaman tüneliniz için otomatik olarak bir oluşturulur. Bir <xref:System.Windows.Media.Animation.Storyboard> veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntem kullanarak animasyon yaptığınızda, saatler zaman çizelgeleriniz ve animasyonlarınız için otomatik olarak oluşturulur ve hedeflenen özelliklerine uygulanır. Ayrıca, yöntemini <xref:System.Windows.Media.Animation.Clock> <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> <xref:System.Windows.Media.Animation.Timeline>kullanarak açıkça bir oluşturabilirsiniz. Yöntem, <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> çağrıldığı için uygun türden <xref:System.Windows.Media.Animation.Timeline> bir saat oluşturur. Alt <xref:System.Windows.Media.Animation.Timeline> zaman çizelgeleri içeriyorsa, <xref:System.Windows.Media.Animation.Clock> onlar için de nesneler oluşturur. Elde edilen <xref:System.Windows.Media.Animation.Clock> nesneler, oluşturuldukları <xref:System.Windows.Media.Animation.Timeline> nesne ağacının yapısıyla eşleşen ağaçlarda düzenlenir.  
  
 Farklı zaman çizelgeleri türleri için farklı türde saatler vardır. Aşağıdaki tablo, <xref:System.Windows.Media.Animation.Clock> farklı <xref:System.Windows.Media.Animation.Timeline> türlerden bazılarına karşılık gelen türleri gösterir.  
  
|Zaman çizelgesi türü|Saat türü|Saat amacı|  
|-------------------|----------------|-------------------|  
|Animasyon (devralır) <xref:System.Windows.Media.Animation.AnimationTimeline>|<xref:System.Windows.Media.Animation.AnimationClock>|Bağımlılık özelliği için çıktı değerleri oluşturur.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Bir ortam dosyalarını işler.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Alt <xref:System.Windows.Media.Animation.Clock> nesnelerini gruplatır ve denetler|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Alt <xref:System.Windows.Media.Animation.Clock> nesnelerini gruplatır ve denetler|  
  
 Oluşturduğunuz nesneleri, <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> yöntemi kullanarak uyumlu bağımlılık özelliklerine uygulayabilirsiniz.  
  
 Çok sayıda benzer nesneyi canlandırmak gibi performans yoğun senaryolarda, <xref:System.Windows.Media.Animation.Clock> kendi kullanımınızı yönetmek performans avantajları sağlayabilir.  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>Saatler ve Zaman Yöneticisi  
 Nesneleri animasyona aldığınızda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zaman çizelgeleriniz için oluşturulan <xref:System.Windows.Media.MediaPlayer.Clock%2A> nesneleri yöneten zaman yöneticisidir. Zaman yöneticisi nesnelerden oluşan <xref:System.Windows.Media.MediaPlayer.Clock%2A> bir ağacın köküdür ve o ağaçtaki zaman akışını denetler.  Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama için otomatik olarak bir zaman yöneticisi oluşturulur ve uygulama geliştiricisi tarafından görünmez. Zaman yöneticisi saniyede birçok kez "keneler" ; her saniye meydana gelen kene lerin gerçek sayısı kullanılabilir sistem kaynaklarına bağlı olarak değişir. Bu kenelerin her biri sırasında, zaman yöneticisi zamanlama <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> ağacındaki tüm nesnelerin durumunu hesaplar.  
  
 Aşağıdaki resimde zaman yöneticisi ve <xref:System.Windows.Media.Animation.AnimationClock>animasyonlu bağımlılık özelliği arasındaki ilişki gösterilmektedir.  
  
 ![Zamanlama sistemi bileşenleri](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Bir özelliğin canlanması  
  
 Zaman yöneticisi işaretlendiğinde, uygulamadaki her <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> birinin saatini güncelleştirir. Bir <xref:System.Windows.Media.Animation.Clock> <xref:System.Windows.Media.Animation.AnimationClock>ise, geçerli çıkış <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> değerini <xref:System.Windows.Media.Animation.AnimationTimeline> hesaplamak için oluşturulduğu yöntemkullanır. Geçerli <xref:System.Windows.Media.Animation.AnimationClock> yerel <xref:System.Windows.Media.Animation.AnimationTimeline> saat, genellikle özelliğin temel değeri olan bir giriş değeri ve varsayılan hedef değeri ile birlikte sağlayan lar. Bir <xref:System.Windows.DependencyObject.GetValue%2A> animasyonun değerini yöntem veya CLR erişimini kullanarak özellik tarafından aldığınızda, <xref:System.Windows.Media.Animation.AnimationClock>onun ' un çıktısını alırsınız.  
  
#### <a name="clock-groups"></a>Saat Grupları  
 Önceki bölümde, farklı zaman çizelgeleri <xref:System.Windows.Media.Animation.Clock> türleri için farklı nesne türleri nasıl olduğu açıklanmıştır. Aşağıdaki resimde zaman yöneticisi, a <xref:System.Windows.Media.Animation.ClockGroup>, an <xref:System.Windows.Media.Animation.AnimationClock>ve animasyonlu bağımlılık özelliği arasındaki ilişki gösterilmektedir. A, <xref:System.Windows.Media.Animation.ClockGroup> animasyonları ve diğer zaman çizelgelerini <xref:System.Windows.Media.Animation.Storyboard> gruplayan sınıf gibi diğer zaman çizelgelerini gruplayan zaman çizelgeleri için oluşturulur.  
  
 ![Zamanlama sistemi bileşenleri](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Bir Saat Grubu  
  
#### <a name="composition"></a>Birleşim  
 Birden çok saati tek bir özellik ile ilişkilendirmek mümkündür, bu durumda her saat temel değeri olarak önceki saatin çıkış değerini kullanır. Aşağıdaki resimde, <xref:System.Windows.Media.Animation.AnimationClock> aynı özelliğe uygulanan üç nesne gösterilmektedir. Clock1, giriş olarak animasyonlu özelliğin temel değerini kullanır ve çıktı oluşturmak için kullanır. Clock2, clock1'den çıkışı girdi olarak alır ve çıktı oluşturmak için kullanır. Clock3, clock2'den çıkışı girdi olarak alır ve çıktı üretmek için kullanır. Birden çok saat aynı özelliği aynı anda etkilediğinde, bir kompozisyon zincirinde oldukları söylenir.  
  
 ![Zamanlama sistemi bileşenleri](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Kompozisyon zinciri  
  
 Kompozisyon zincirindeki <xref:System.Windows.Media.Animation.AnimationClock> nesnelerin giriş ve çıktıları arasında bir ilişki oluşturulsa da zamanlama davranışlarının etkilenmediğini unutmayın; <xref:System.Windows.Media.Animation.Clock> nesneler (nesneler <xref:System.Windows.Media.Animation.AnimationClock> dahil) üst <xref:System.Windows.Media.Animation.Clock> nesnelere hiyerarşik bir bağımlılık vardır.  
  
 Aynı özelliğe birden çok saat uygulamak <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> için, <xref:System.Windows.Media.Animation.Storyboard>animasyon veya <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Keneler ve Olay Konsolidasyonu  
 Çıktı değerlerini hesaplamaya ek olarak, zaman yöneticisi her işaretçisinde başka işler yapar: her saatin durumunu belirler ve olayları uygun şekilde yükseltir.  
  
 Keneler sık sık meydana gelirken, keneler arasında birçok şeyin olması mümkündür. Örneğin, bir <xref:System.Windows.Media.Animation.Clock> durdurulabilir, başlatılabilir ve yeniden durdurulabilir, bu durumda değeri <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> üç kez değişmiş olur. Teorik olarak, <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olay tek bir kene birden çok kez yükseltilmiş olabilir; ancak, zamanlama altyapısı olayları birleştirir, <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> böylece olay kene başına en fazla bir kez yükseltilebilir. Bu tüm zamanlama olayları için geçerlidir: her türden en <xref:System.Windows.Media.Animation.Clock> fazla bir olay belirli bir nesne için yükseltilir.  
  
 <xref:System.Windows.Media.Animation.Clock> Bir anahtar durumu değiştirdiğinde ve keneler arasında orijinal durumuna <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Stopped> geri döndüğünde <xref:System.Windows.Media.Animation.ClockState.Active>(örneğin, bu durumdan sonra ve geri değişmek gibi), ilişkili olay yine de gerçekleşir.  
  
 Zamanlama olayları hakkında daha fazla bilgi için [Zamanlama Olaylarına Genel Bakış'a](timing-events-overview.md)bakın.  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>Özelliklerin Geçerli Değerleri ve Temel Değerleri  
 Animatable özelliği iki değere sahip olabilir: bir temel değer ve geçerli bir değer. Özelliği CLR erişimini veya <xref:System.Windows.DependencyObject.SetValue%2A> yöntemini kullanarak ayarladığınızda, temel değerini ayarlarsınız. Bir özellik animasyonlu değilse, tabanı ve geçerli değerleri aynıdır.  
  
 Bir özelliği animasyona aldığınızda, özelliğin <xref:System.Windows.Media.Animation.AnimationClock> *geçerli* değerini ayarlar. CLR erişimcisi veya <xref:System.Windows.DependencyObject.GetValue%2A> yöntemi ile mülkün değerini <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.AnimationClock> almak, mülkün ne <xref:System.Windows.Media.Animation.ClockState.Active> zaman veya <xref:System.Windows.Media.Animation.ClockState.Filling>. <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> Yöntemi kullanarak özelliğin temel değerini alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)
- [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)
