---
title: Zamanlama Olaylarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: a48d1621e5568d556a1177578cc662813d70a283
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="timing-events-overview"></a>Zamanlama Olaylarına Genel Bakış
Bu konu, üzerinde kullanılabilir beş zamanlama olayları kullanmayı açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> nesneleri.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için nasıl oluşturulacağı ve animasyonları kullanın anlamanız gerekir. Animasyon ile çalışmaya başlamak için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Birden çok yolla özelliklerinde animasyon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **Görsel taslak haline getirme nesnelerini kullanma** (biçimlendirme ve kodun): kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard> düzenlemek ve bir veya daha fazla nesnelere animasyon dağıtmak için nesneleri. Bir örnek için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Yerel animasyonları kullanarak** (yalnızca kodu): uygulayabileceğiniz <xref:System.Windows.Media.Animation.AnimationTimeline> doğrudan bunlar animasyon özellikleri nesnelere. Bir örnek için bkz: [özelliği olmadan kullanarak bir film şeridi animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **Saatler kullanarak** (yalnızca kodu): açıkça saati oluşturma yönetmek ve animasyon saatler kendiniz dağıtın.  Bir örnek için bkz: [AnimationClock kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Biçimlendirme ve kodun kullanabilmeniz için bu genel bakıştaki örnekler kullanmak <xref:System.Windows.Media.Animation.Storyboard> nesneleri. Ancak, açıklanan kavramları özellikleri diğer yöntemleri için uygulanabilir.  
  
### <a name="what-is-a-clock"></a>Bir saat nedir?  
 Bir zaman çizelgesi kendisi tarafından gerçekten hiçbir şey yapmaz dışında zaman kesimini açıklanmaktadır. Zaman çizelgesinin olduğu <xref:System.Windows.Media.Animation.Clock> gerçek işi nesne: çalışma zamanı durumunu zamanlama ile ilgili zaman çizelgesi korur. Ne zaman kullanarak film şeritleri gibi çoğu durumda, bir saat için zaman çizelgeniz otomatik olarak oluşturulur. Ayrıca bir <xref:System.Windows.Media.Animation.Clock> kullanarak açıkça <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> yöntemi. Hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Clock> nesneleri bkz [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Olayları neden kullanılır?  
 Biri hariç olmak üzere (son değer çizgisi hizalanmış arama), tüm etkileşimli zamanlama işlemleri zaman uyumsuzdur. Tam olarak ne zaman bunlar yürütülür bilmenin bir yolu yoktur. Zamanlama işleminizi bağımlı olduğu başka bir kod varsa, bir sorun olabilir. Dikdörtgene animasyonlu bir zaman çizelgesi durdurmak istediğinizi varsayalım. Zaman Çizelgesi durdurulduktan sonra dikdörtgen rengini değiştirin.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 Önceki örnekte film şeridi durdurulmadan önce ikinci satır kod yürütebilir. Durdurma zaman uyumsuz bir işlem olduğundan olmasıdır. Bir zaman çizelgesi veya durdurmak için saat söyleyen "zamanlama altyapısının sonraki onay kadar işlenen değil bir durdurma isteği" türlerdeki oluşturur.  
  
 Bir zaman çizelgesi tamamlandıktan sonra komutları yürütmek için zamanlama olayları kullanın. Aşağıdaki örnekte, olay işleyici çalma film şeridi kestikten sonra bir dikdörtgen rengini değiştirmek için kullanılır.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Daha eksiksiz bir örnek için bkz: [alma bildirimi, bir saatin durum değişiklikleri](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Ortak Olaylar  
 <xref:System.Windows.Media.Animation.Timeline> Ve <xref:System.Windows.Media.Animation.Clock> sınıflarının her ikisi de beş zamanlama olayları sağlar. Bu olaylar ve bunları tetikleyen koşullar aşağıdaki tabloda listelenmektedir.  
  
|Olay|Tetikleyici etkileşimli işlemi|Diğer Tetikleyicileri|  
|-----------|--------------------------------------|--------------------|  
|**tamamlandı**|Doldurmak için Atla|Saatin tamamlar.|  
|**CurrentGlobalSpeedInvalidated**|Duraklatma, sürdürme, arama, hız oranını ayarlamak, Atla doldurun, durdurmak için|Saatin tersine çevirir hızlandırır başlatır veya durdurur.|  
|**CurrentStateInvalidated**|Başlamak için Atla doldurun, durdurmak için|Saatin, durdurur, başlatır veya doldurur.|  
|**CurrentTimeInvalidated**|Başlamak için arama, Atla doldurun, durdurmak için|Saat ilerler.|  
|**RemoveRequested**|Kaldır||  
  
## <a name="ticking-and-event-consolidation"></a>Şekilde ilerleyen ve olay birleştirme  
 Animasyon yapıldığında nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animasyonları yönetir zamanlama altyapısıdır. Zamanlama altyapısının zaman ilerleyişini izler ve her animasyon durumunu hesaplar. Bir saniyede gibi birçok değerlendirme geçişleri kolaylaştırır. Bu değerlendirme geçişleri "çizgilerine" adlandırılır  
  
 Ticks sıklıkla meydana gelirken, çok sayıda arasında çizgilerine gerçekleşmesi için mümkündür. Örneğin, bir zaman çizelgesi durduruldu, başlatıldı ve yeniden durduruldu; bu durumda geçerli durumuna üç kez değişmiş. Teorik olarak olay tek bir değer çizgisi içinde birden çok kez oluşturulması; Ancak, böylece her olay sayaç değeri başına en fazla bir kez yükseltilebilir zamanlama altyapısının olayları birleştirir.  
  
## <a name="registering-for-events"></a>Olaylar için kaydetme  
 Zamanlama olaylarını kaydetmek için iki yolu vardır: zaman çizelgesi veya Zaman Çizelgesi'ndan oluşturulan saat ile kaydedebilirsiniz. Yalnızca koddan yapılabilir bir olay için doğrudan bir saatiyle kaydetme oldukça basit olsa. İşaretleme veya kod çizelgesinden olan olaylar için kaydedebilirsiniz. Sonraki bölümde, bir zaman çizelgesi saat olaylarla kaydetmek açıklar.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Bir zaman çizelgesi olan saat olaylar için kaydetme  
 Bir zaman çizelgesi rağmen 's <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, ve <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> olaylar görünür bu olaylar gerçekte ilişkilendirir için olay işleyicisi ile kaydetme zaman çizelgesi ilişkilendirilecek <xref:System.Windows.Media.Animation.Clock> için zaman çizelgesi oluşturulur.  
  
 İçin kaydettiğinizde <xref:System.Windows.Media.Animation.Timeline.Completed> bir zaman çizelgesi olayda, örneğin, gerçekte söyleyen kaydetmek için sistem <xref:System.Windows.Media.Animation.Clock.Completed> oluşturulan her zaman çizelgesi saati olay. Kodda, önce bu olay için kaydetmeniz gerekir <xref:System.Windows.Media.Animation.Clock> için bu zaman çizelgesi; oluşturulan Aksi takdirde, bildirim almazsınız. Bu otomatik olarak gerçekleşir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; ayrıştırıcı önce olayı için otomatik olarak kaydeder <xref:System.Windows.Media.Animation.Clock> oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyon ve Zamanlama Sistemine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
